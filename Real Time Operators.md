# Real Time Operators

The following operators can be applied to real time production\process data.

## Exponential Moving Average (EMA)

Calculates exponential moving average with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;

            var ema = new Operator.EMA(windowSize, Operator.EmaType.Interpolated);
            ema.Calculate(value);
```
