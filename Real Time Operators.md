# Real Time Operators

The following operators can be applied to real time production\process data.

## Compression

Applies compression to time series:
```C#
            var threshold = 1.5;
            
            var compression = new Operator.Compression(threshold);
            var values = compression.Calculate(value);
```

## Exception

Applies exception deviation to time series - the operator mirrors OSIsoft's exception setting:
```C#
            var threshold = 1.5;
            
            var exception = new Operator.Exception(threshold);
            var values = exception.Calculate(value);
```

## Exponential Moving Average (Ema)

Calculates exponential moving average with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;

            var ema = new Operator.Ema(windowSize, Operator.EmaType.Interpolated);
            var values = ema.Calculate(value);
```
## Iterated Exponential Moving Average (IEMA)

Calculates n-times iterated exponential moving average with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;
            var n = 5;

            var iema = new Operator.IEma(windowSize, Operator.EmaType.Interpolated, n);
            var values = iema.Calculate(value);
```


## Continuous Moving Average (CMa)

Calculates continuous moving average with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;
            var n = 5;
            
            var cma = new Operator.CMa(windowSize, Operator.EmaType.Interpolated, n);
            var values = cma.Calculate(value);
```

## Continuous Moving Norm (CNorm)

Calculates continuous moving norm with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;
            var n = 5;
            var p = 2;
            
            var cnorm = new Operator.CNorm(windowSize, Operator.EmaType.Interpolated, n);
            var values = cma.Calculate(value);
```

## Continuous Moving Variance (CVar)

Calculates continuous moving variance with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;
            var n = 5;
            var p = 2;
            
            var cvar = new Operator.CVar(windowSize, Operator.EmaType.Interpolated, n);
            var values = cvar.Calculate(value);
```

## Continuous Moving Standard Deviation (CStd)

Calculates continuous moving variance with window size 30 sec.:
```C#
            var windowSize = TimeSpan.FromSeconds(30);
            var type = Operator.EmaType.Interpolated;
            var n = 5;
            var p = 2;
            
            var cstd = new Operator.CStd(windowSize, Operator.EmaType.Interpolated, n);
            var values = cstd.Calculate(value);
```
