[b]What is a swing high or swing low?[/b]
Swing highs and lows are price extremes. For example say we set our swing length to 5. A candle that is a swing high with a swing length of 5 will have 5 bars to the left that are lower and 5 bars to the right that are lower. A candle that is a swing low with a swing length of 5 will have 5 bars to the left that are higher and 5 bars to the right that are higher.

[b]How are the trend candles calculated?[/b]
The trend candles are calculated by storing and comparing historical swing lows and swing highs.
The pinescript code goes as follows:
[pine]The pinescript code goes as follows:
var int trend = na
trend := ((hh and high >= psh) or close > csh) ? 1 : ((ll and low <= psl) or close < csl) ? -1 : lh or hl ? 0 : trend[1][/pine]

What does that gibberish mean?
-Candle can be GREEN IF - We have a higher high (current swing high is greater than the previous swing high) and the high is greater than the previous swing high - OR The current close is greater than the current swing high

-Candle can be RED IF - We have a lower low (current swing low is less than the previous swing low) and the low is less than the previous swing low - OR The current close is less than the current swing low

-Candle can be YELLOW IF - We have a new swing high and the new swing high is less than the previous swing high - OR We have a new swing low and the new swing low is greater than the previous swing low

If none of the conditions above are true then we continue with whatever color the previous bar was.

[b]What is repainting?[/b]
Repainting is "script behavior causing historical vs realtime calculations or plots to behave differently." That definition comes directly from Tradingview. If you want to read the full explanation you can visit it here [url=https://www.tradingview.com/pine-script-docs/en/v5/concepts/Repainting.html#future-leak-with-request-security]https://www.tradingview.com/pine-script-docs/en/v5/concepts/Repainting.html#future-leak-with-request-security[/url] . The price-action candles use swing highs and swing lows which need bars to the left (past) and bars to the right ("future") in order to confirm the swing level. Because of the need to wait for confirmation to for swing levels the plot style can be repainting. With the price-action candles indicator the only repainting part of the indicator is the labels. The price-action candles themselves WILL NOT REPAINT. The labels however can be set to repaint or not depending on the user preference. If the user opts to use repainting then the label location is shifted back by the length of the price-action. So if the "Price-Action Length" input is set to 10, and the user wants repainting, the swing high/low label will be shifted back 10 bars. If the user opts for no repainting, the label will not be shifted and instead show on the exact bar the swing level was confirmed.
Examples Below.

[b]Repaint[/b]
Here the labels are shifted back the price-action length.
[image]https://www.tradingview.com/x/IDVqdeKp/[/image]

[b]Non-Repaint[/b]
Here the labels are not shifted back because the input setting is set to not repaint.
[image]https://www.tradingview.com/x/08oO41Hs/[/image]

[b]Multi-timeframe Analysis[/b]
The users can view the trend from multiple different timeframes at once with a table displayed at the bottom of their charts. The timeframe can be lower or higher than the chart timeframe.
[image]https://www.tradingview.com/x/dy39wiwL/[/image]

[b]More examples[/b]
[image]https://www.tradingview.com/x/KRK0c7QL/[/image]
[image]https://www.tradingview.com/x/Up2DfZXk/[/image][image]https://www.tradingview.com/x/CJAg9ec9/[/image]

Be on the lookout for the Price Action Candles (Lower) indicator where you can view the multi-timeframe labels on a lower price grid in order to see the history over time!
