# S&P 500 Sentiment Analysis

## Introduction
A subscription to access an option order flow sentiment screener costs $69 per month. Obtaining valuable data and analysis is expensive for retail traders looking to better understand the market. This project aims to recreate a basic analysis on the options flow sentiment for the S&P 500 Index (SPX).

Why look at options? The theory is options dedicate all ebbs and flows of the market. There is less liquidity in the market as before due to less traders. All liquidity would be the result of dealer hedging and option trading, but not due to traditional buying and selling. 

Thus, options sentiment analysis is a distinct indicator of market trends based on actual investor trading data that has a direct influence on the market. Trader's sentiment on market direction is determined by their willingness to purchase puts or calls above market price or sell puts or calls below market price. By calculating option sentiment based on investors' desires, this analysis may obtain valuable insight on future market trends.

This analysis will use free data from TD Ameritrade Thinkorswim (Time and Sales) to illustrate SPX options sentiment and market fragility (how vulnerable the market is to a large price change given a relatively small event) from its monthly expiration options chain. 

The files contain an analysis performed on 8/3/2022.

### Final Result

![index](https://user-images.githubusercontent.com/105828433/183554464-f4234994-f4b4-4b71-9eca-714ca73a297b.jpg)

![index2](https://user-images.githubusercontent.com/105828433/183541801-16c2cc57-f0b9-4b96-81f0-f73c66c87dc2.jpg)

* Data from 8/3/2022

## Approach

Since there is no method that I am aware of to export Thinkorswim's Time and Sales data to Excel, the data must be manually copy and pasted daily to the excel sheet: 'spx_options_timesales.xlsx'. Other sources require a subscription, so is such the price of free market data?

The Thinkorswim Time and Sales features allows me to filter some data, which I took the liberty in the following way to remove small position sizes and low prices:

<img width="283" alt="Screenshot 2022-08-08 182458" src="https://user-images.githubusercontent.com/105828433/183542534-663c738b-bbfe-4cc7-9483-9cb6477c04eb.png">

Note: 
* Time series: Monthly Expirations from front month to next quarterly option's expiration (OpEx). For example if today was August 3rd, August to December monthly expirations would be selected. If today was December 22nd, January to March monthly expirations would be selected.The quarterly OpEx are March, June, September, December.
* Condition: None selected (Spreads, Straddle, BuyWrite, Combo)

The data is then cleaned and manipulated to locate where the option was purchased. If the option was traded above market, then it is considered bought. If the option was traded below market, then it is considered sold. If the option was traded exactly at market price, then it is unclear whether it was bought or sold and is left out of this analysis.

## Conclusion

With this analysis, you can make inferences such as on 8/3/2022:

From the graphics, we can observe:
* Greater call option purchases than puts (short term bullish)
* Aug-Sep saw significant call writing with Sep put purchasing (short term bearish)
* EOD: traders are shedding their calls and purchasing puts as insurance (bearish)

In short, end of day hedging activity may mark the end of this week's bullish run. Until August 19, it is possible for the bullish trend to continue, since more calls were bought today than yesterday. However, bearish option sentiment for the September expiry predicts potential headwinds coming soon. While call buying dominated in the October through December monthlies today, bearish option trades were more prevalent in the past week. Meanwhile the near term put premium chart does not illustrate market fragility yet. Once puts bought is near equal to puts sold, the market is at risk.

## Limitations
The major limitation of this analysis is determining whether an option is bought or sold. Deciding whether an option is purchased or written depending on its trade price relative to the bid and ask is too simple of a methodology. For example, a call filled at the bid may not be a sell but rather a limit buy order.

Another limitation is that this analysis cannot determine the reason behind an option trade. With this method, it is impossible to tell whether an option trade is to exit a position, add to a position, or part of a complex strategy.

Thus, this sentiment inference indicator cannot be solely used for stock market analysis, but rather as another tool in the toolbox.

Despite these restrictions, using this to have a peek behind the curtains is still better than continuing to meander blindly through the labyrinth that is the market.
