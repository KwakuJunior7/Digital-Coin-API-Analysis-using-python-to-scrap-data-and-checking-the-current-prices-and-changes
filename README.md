

# Digital Coin API Analysis
# This analysis provides a 30-Day Price & Volatility Review of Bitcoin, Ethereum & Dogecoin using Python and CoinGecko API.

# 1. Executive Summary

This notebook fetches 30 days of daily price data each day for Bitcoin (BTC), Ethereum (ETH), and Dogecoin (DOGE) from the CoinGecko API and creates daily OHLC candlestick charts for each coin. It then generates a cross-coin summary of each coin's returns, volatility, and price range. As of the most recent data point, Bitcoin traded at $69,350 (+1.46% over 7 days), Ethereum at $2,269 (+8.94% over 7 days, the strongest weekly mover of the three), and Dogecoin at $0.0751 (+3.55% over 7 days). The three coins closed the window with a dramatic single-day surge from a string of steady declines over the past few weeks. In part of the second half of the notebook, there is a methodological problem in that BTC, ETH, and DOGE are all statistically the same in the correlation chart, the volatility chart, and the return-distribution chart (they are all 1.000 in the correlation chart; the volatility bars are the same length; and the return-distribution curves overlap entirely). Noted that this is in direct opposition to the summary table in the notebook themselves, which indeed lists different values of volatility per coin (0.31% BTC, 0.42% DOGE and 0.49% ETH). Please read the explanation of the probable cause and solution in Section 5 below.

# 2. 30-Day Price Summary


<img width="1077" height="552" alt="image" src="https://github.com/user-attachments/assets/9510d495-9f04-4517-8a3d-e2a9af413ca7" />



However, while Ethereum's volatility (σ = 0.49%) is the highest of all three, it is about 2–6x the amount of change over 7 days as Bitcoin and Dogecoin have. Over that period, Ethereum's volatility (σ = 0.49%) is about two to six times higher than Bitcoin's and Dogecoin's over the same time period, consistent with the higher-risk, higher-reward profile of the coin over the last 7 days. By comparison, Bitcoin is the most defensive of the three assets in terms of volatility and 7-day move, trading with the least volatility currently (0.31%). The crypto has traded in the middle ground between the two extremes in terms of volatility and potential returns and had the biggest pullback in 24 hours of the three (-1.16%).

# 3.Daily Price Action (OHLC)

The notebook's price series was used to recreate the daily open/high/low/close candlesticks (green indicates that the price ended up higher than the price started that day; red indicates that the price ended up lower than the price started that day).



 <img width="719" height="327" alt="image" src="https://github.com/user-attachments/assets/a653588b-6c7b-4aaf-995c-0689fbf4086b" />

Figure 1. Bitcoin daily OHLC, last 30 days.


Bitcoin's price opened at ~$65,500 on Jul 20, dipped to a low of ~$63,000 on Jul 31 – Aug 1 and returned to its 30-day highs within the first half of August before surging upward on the last day of the month to close near $69,350.



 <img width="719" height="327" alt="image" src="https://github.com/user-attachments/assets/2a6b9c0b-7787-4f59-a5fd-bbe938c301be" />

Figure 2. Ethereum daily OHLC lasts 30 days.



Ethereum follows a similar pattern as Bitcoin on the same time frame (late-July/early-August low, then a steady rise, and the same final-day breakout) but the final-day breakout is proportionately much larger (+18% day-over-day versus much smaller for Bitcoin), as mentioned in Section 2, due to the time-frame change.



 <img width="719" height="327" alt="image" src="https://github.com/user-attachments/assets/14263bb3-0a43-4954-bec4-c1eb0d639b40" />

Figure 3. Dogecoin daily OHLC, last 30 days.



All the three assets were reacting to the same market-wide conditions over this time, as dogecoin has the same overall trough-then-recovery trend as BTC and ETH, even though Section 5 raises some questions about the way that co-movement was measured later in the notebook.

# 4. Cross-Coin Ranking

The notebook ranks each coin (1 = best/highest) based on 6 metrics. The lower the volatility rank, and the higher the return/price rank, the better; however, this depends on an investor's objective:


<img width="1077" height="379" alt="image" src="https://github.com/user-attachments/assets/ffc9a495-5714-4e19-b8b6-c74f81c4724d" />




Bitcoin is best (lowest) for volatility and worst (3rd) for price/mean price, but best (lowest) for 7-day return the traditional large cap preference for stability versus momentum in this time frame. Ethereum is the opposite; worst on 7-day returns, best on volatility. While this table is a good starting point for discussions on risk tolerance, a 30-day period is a short time, and the rankings may differ over a longer time frame.




# 5. Conclusions & Recommendations

●	In terms of the 7-day return, Ethereum had the best performance, but the highest volatility, while Bitcoin had the highest stability and the lowest 7-day return. This is a standard and useful context in which to make position sizing decisions in all three assets.

●	Even though the notebook produces the correlation number (1.000) over this time period (in the late part of July/early August), and this figure should not be accepted as, there is certainly market-wide co-movement over this time period (as evidenced by the same trough and sharp final day rally in the OHLC charts for all three coins in Figures 1-3).


●	Short window caveat: All figures mentioned in this report are for a 30-day period (Jul 20 - Aug 19). However, a 90-day or longer period would provide a more consistent picture of relative volatility/momentum before making any definitive calls, especially given the dramatic 7-day change which was caused by the final day of trading.

●	Extending the export of the fixed analysis to include the corrected returns_df would make it easy to hand off or automate the fixed analysis; the notebook already exports the summary_table to crypto_summary.xlsx, so adding the corrected returns_df would complement that.

