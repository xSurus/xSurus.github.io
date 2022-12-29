---
title: "Rusty Trader"
date: 2022-12-28T16:28:02+01:00
draft: true
toc: false
images:
tags:
  - Personal project
  - Trading
technologies:
  - Rust
  - Regex
  - Crontab
  - Raspberry Pi
---
## Motivation
Almost a year ago, Fireship, a great Youtube creator and developer, released a video on his channel, where he created a [stock trading bot](https://www.youtube.com/watch?v=BrcugNqRwUs&t=132s) based on the [inverse Jim Cramer](https://www.whitecoatinvestor.com/jim-cramer-inverse-etf/) strategy. The idea behind this being, that Jim Cramer gives terrible stock picks and doing the opposite might actually result in a positive return. I was very intrigued by this video and decided to try it out myself.

Furthermore, I had been reading frequently about how US senators [tend outperform the market](https://www.reddit.com/r/options/comments/n940ze/i_analyzed_9000_trades_made_by_us_senators_in_the/), and I wanted to see if I could replicate this.

So after a few months of procrastinating, and in the wake of a project presentation for some interviews I had at Optiver, I decided to give it a try.
## The project
Since I wanted to grow more accustomed to Rust, I decided to use Rust over a language such as JavaScript or Python. With a clear goal in mind, I got started with working on the integration of the Alpaca API. For this I used the crate provided [here](https://github.com/d-e-s-o/apca). This crate provides an integration into rust for all the endpoints of the Alpaca API. This was very useful, since I could focus on the actual trading strategy instead of the API integration.

To connect to the Alpaca API I used something along the lines of the following code:
{{< highlight rust >}}
let args = Cli::parse(); // retrieve the API key and API secret key from the environment variables
let api_info = ApiInfo::from_env().unwrap();
let client = Client::new(api_info);
let account = client.issue::<account::Get>(&()).await.unwrap();
{{< /highlight >}}

To extract the information of what trades were placed by US house members, I used [this website](https://housestockwatcher.com/). It provides a list of all the trades made by US house members. This was very useful, since I could extract the information I needed from the website, without having to manually extract the information from the documents in which they were submitted. I then create a request using the (reqwest crate)[https://docs.rs/reqwest/latest/reqwest/] to the API endpoint (which came to using 16 .unwrap() on 25 lines) to query the trades placed on day X. I fixed X to be about 3 days in the past, since it normally took a few days until all the trades were fully transcribed. This website was very useful, since I could extract the information I needed from the it, without having to manually extract the information from the documents myself.
The response from the API endpoint was a JSON object, which I parsed using the serde_json crate. After parsing the JSON object I extracted the information I needed from the JSON object using regex. I was interested in three pieces of information: what was traded (ticker symbol), was it a buy or a (partial) sell, and for how much was this order executed (the price). This was done using the following code:
{{< highlight rust >}}
fn extract_ticker(input: &str) -> Option<&str> {
    // regex expression to extract everything between > and <, which comes out to be the ticker
    lazy_static! {
        static ref RE: Regex = Regex::new(
            ">([A-Z]+)<"
        ).unwrap();
    }
    RE.captures(input).and_then(|cap| cap.get(1)).map(|m| m.as_str())
}

fn extract_amount(input: &str) -> Option<i64> {
    // regex expression to extract amount given by $250,001 - $500,000 and then average it
    lazy_static! {
        static ref RE: Regex = Regex::new(
            r"\$([\d+,]+) - \$([\d+,]+)"
        ).unwrap();
    }
    let min = RE.captures(input).and_then(|cap| cap.get(1)).map(|m| m.as_str())?;
    let min = min.replace(",", "").parse::<i64>().unwrap();
    let max = RE.captures(input).and_then(|cap| cap.get(2)).map(|m| m.as_str())?;
    let max = max.replace(",", "").parse::<i64>().unwrap();
    return Some((min + max) / 2);
}
{{< /highlight >}}

Equipped with this information, I created an order struct that contained the ticker symbol, the amount, and the type of the order. All of these orders were then added to a vector and passed to the Alpaca API.

To actually execute an order, I had to know how many shares I wanted to buy, which depends on the amount of money I have available as well as the current price the share trades at. This posed a bit of a challenge, since live data is not fully accessible with the free version of the API. Thus I settled on using data, that was slightly older (15 minutes) from a secondary marketplace (not the nasdaq). 

One last functionality that I wanted to implement was the ability to get an overview of one's portfolio. I wanted to get the current value of the portfolio, each individual stock and the total return for each of the stock as well as the portfolio's standing. This was done using the following code:
{{< highlight rust >}}
pub async fn print_positions(client: Client, cash: Num) -> () {
    let positions = get_positions(&client).await;
    let mut sum = 0;
    println!(
        "{0: >10} | {1: >12} | {2: >10} | {3: >10} | {4: >10}",
        "Name", "Amount", "Relative gain", "Absolute gain", "Market value"
    );
    println!("=========================================================================");
    for position in positions.unwrap() {
        let value = position.market_value.unwrap();
        sum += value.to_i64().unwrap();
        println!(
            "{0: >10} | {1: >12.2} | {2: >12.2}% | {3: >12.2}$ | {4: >10.2}$",
            position.symbol,
            position.quantity,
            position.unrealized_gain_total_percent.unwrap(),
            position.unrealized_gain_total.unwrap(),
            value
        );
    }
    println!("=========================================================================");
    println!("Your total balance is: {:.2}", sum + cash.to_i64().unwrap());
}
{{< /highlight >}}

After a few days of working on the API integration I had a working version of the bot. I decided to run the bot on a raspberry pi, since I had one lying around. I also decided to run the bot on a schedule, so that I could run it every day at 17:30 (since the NASDAQ opens at 3:30 and I am situated in Switzerland). For this I used the crontab utility. This utility allows you to schedule tasks to run at a specific time at specific intervals.
## The results
I have now had this program running for about a month. So far, the returns have not been astonishing.
I started by putting 1044$ into my alpaca account. At the time of writing this post, my portfolio's worth stands at about 950$, which corresponds to a loss of about 9.5%. Comparing this to the S&P 500, which stands at -4.5% over the last month, we are down 5%.

The reason for this is up to speculation. Since US house members need to report their trades in a timeframe of 45 days, this might have an impact on the performance of this program. As explained in the above mentioned blog post, however, despite this lag, on average the members would have still outperformed the S&P 500 by a considerable margin.
Another reason might just me that either the timing might be bad or that these picks are unlucky at this time.
## What I learned
Through this project I managed to improve my skills in rust. I got to work a lot with different APIs as well as trying out some regex for the first time (which initially was extremely painful). This is definitely one of the bigger projects of mine to this date and I hope to expand it to a point where it might be useful to other people as well.

I am very pleased with how this project turned out (despite the returns not being stellar) and will definitely make use of what I learned throughout this.
## What the future holds
At the moment I am working on expanding this project to track, which senators made the best trades and adjust my actions according to these statistics. This would allow me to optimize this trading strategy in the long run.

I am also planning to implement a portfolio tracker for some other assets I have, with the goal being to have a CLI for all purposes in the end.