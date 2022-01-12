### Volume Indicators

Volumne indicators measure the strength of a trend based the volume.

- [Accumulation/Distribution (A/D)](#accumulationdistribution-ad)
- [On-Balance Volume (OBV)](#on-balance-volume-obv)
- [Money Flow Index (MFI)](#money-flow-index-mfi)

#### Accumulation/Distribution (A/D)

The [accumulationDistribution](./accumulationDistribution.ts) is a cumulative indicator that uses volume and price to assess whether a stock is being accumulated or distributed.

The Accumulation/Distribution seeks to identify divergences between the stock price and the volume flow.

```
MFM = ((Closing - Low) - (High - Closing)) / (High - Low)
MFV = MFM * Period Volume
AD = Previous AD + CMFV
```

Based on [Accumulation/Distribution Indicator (A/D)](https://www.investopedia.com/terms/a/accumulationdistribution.asp).

```TypeScript
import {accumulationDistribution} from 'indicatorts';

const result = accumulationDistribution(highs, lows, closings, volumes);
```

#### On-Balance Volume (OBV)

The [onBalanceVolume](./onBalanceVolume.ts) function calculates a technical trading momentum indicator that uses volume flow to predict changes in stock price.

```
                  volume, if Closing > Closing-Prev
OBV = OBV-Prev +       0, if Closing = Closing-Prev
                 -volume, if Closing < Closing-Prev
```

```TypeScript
import {onBalanceVolume} from 'indicatorts';

const result = onBalanceVolume(closings, volumes);
```

#### Money Flow Index (MFI)

The [moneyFlowIndex](./moneyFlowIndex.ts) function analyzes both the closing price and the volume to measure to identify overbought and oversold states. It is similar to the Relative Strength Index (RSI), but it also uses the volume.

```
Raw Money Flow = Typical Price * Volume
Money Ratio = Positive Money Flow / Negative Money Flow
Money Flow Index = 100 - (100 / (1 + Money Ratio))
```

```TypeScript
import {moneyFlowIndex} from 'indicatorts';

const result = moneyFlowIndex(14, highs, lows, closings, volumes);
```

The [defaultMoneyFlowIndex](./moneyFlowIndex.ts) function uses the default period of 14.

## Disclaimer

The information provided on this project is strictly for informational purposes and is not to be construed as advice or solicitation to buy or sell any security.

## License

Copyright (c) 2022 Onur Cinar. All Rights Reserved.

The source code is provided under MIT License.
