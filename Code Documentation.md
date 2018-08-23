# Code Documentation

The following are functions built into the AACE.Extension Data class library.

#### Creating Constant Values
##### Decription:  

Returns AFValues having the same constant value.

##### Usage: 
```C#
public static GetConstantValues(AFTimeRange timeRange, int numberOfValues, object value, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
value is an object desired to be constantly generated, i.e. a real number, a string, etc.  
attribute is an AFAttribute. (Currently set to null)

##### Example:

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Simulated Heartbeat Values
##### Decription:  

Returns AFValues with values that represent a simulated heartbeat.

##### Usage: 
```C#
public static GetHeartBeatValues(AFTimeRange timeRange, int numberOfValues, int prevValue = 0, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
prevValue is an integer that represents the absence of a heartbeat. (Currently set to 0)  
attribute is an AFAttribute. (Currently set to null)

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Random Values
##### Decription:  

Returns AFValues with random values between 0 and 1.

Usage:
```C#
public static GetRandomValues(AFTimeRange timeRange, int numberOfValues, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
attribute is an AFAttribute. (Currently set to null)

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Gaussian Noise
##### Decription:  

Returns AFValues with random values generated from a Gaussian distribution.

##### Usage: 
```C#
public static GetGaussianRandomValues(AFTimeRange timeRange, int numberOfValues, double mean, double stdDev, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
mean is a real number representing the mean of the Gaussian distribution.  
stdDev is a real number representing the standard deviation of the Gaussian distribution.  
attribute is an AFAttribute. (Currently set to null) 

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Sinusoidal Values
##### Decription:  
Returns AFValues with values generated from a sine wave.

##### Usage: 
```C#
public static GetSinusoidValues(AFTimeRange timeRange, int numberOfValues, double height, double signalPerDay, TimeSpan shift, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
height is a real number representing the height of the rectangular wave.  
signalPerDay is a real number that represents the number of signals (or periods) desired per day.  
shift is a TimeSpan structure that represents a time interval to horizontally shift the sine wave by.  
attribute is an AFAttribute. (Currently set to null) 

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Seesaw (or Sawtooth) Values
##### Decription:  

Returns AFValues with values generated from a seesaw (or sawtooth) wave.

##### Usage: 
```C#
public static GetSeesawValues(AFTimeRange timeRange, int numberOfValues, double height, double signalPerDay, TimeSpan shift, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
height is a real number that represents the desired maximum of the seesaw wave that the values will be generated from.  
signalPerDay is a real number that represents the number of signals (or periods) desired per day.  
shift is a TimeSpan structure that represents a time interval to horizontally shift the seesaw wave by.  
attribute is an AFAttribute. (Currently set to null)

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Rectangular Values
##### Decription:  

Returns AFValues with values generated from a rectangular wave.

##### Usage: 
```C#
public static GetRectangularValues(AFTimeRange timeRange, int numberOfValues, TimeSpan zeroSpan, TimeSpan oneSpan, double height, TimeSpan shift, AFAttribute attribute = null)
```

##### Parameters:  

timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
zeroSpan is a TimeSpan structure that represents the time interval in which the recatangular wave is zero.  
oneSpan is a TimeSpan structure that represents the time interval in which the recatangular wave is not zero.  
height is a real number that represents the desired maximum of the rectangula wave that the values will be generated from.  
shift is a TimeSpan structure that represents a time interval to horizontally shift the seesaw wave by.  
attribute is an AFAttribute. (Currently set to null)

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Creating Random Walk Values
##### Decription:  

Returns AFValues with values generated from a random walk model.

##### Usage: 
```C#
GetRandomWalkValues(AFTimeRange timeRange, int numberOfValues, double previousValue, double lowerLimit=0, double upperLimit = 100, AFAttribute attribute = null)
```

##### Parameters:  
timeRange is an AFTimeRange structure representing the desired time range of interest.  
numberOfValues is an integer that represents the number of points desired to be generated.  
previousValue is a real number that represents  
lowerLimit is a real number that represents the lower limit of the random walk. (Currently set to 0)  
upperLimit is a real number that represents the upper limit of the random walk. (Currently set to 100)
attribute is an AFAttribute. (Currently set to null)

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

The following functions are built-in to the AACE.Extension Data class library.

#### Getting Compresses AFValues
##### Decription:  

Returns the values of AFValues as AFValues.

##### Usage: 
```C#
public static AFValues GetCompressed(this AFValues values, Local local)
```

##### Parameters:  
values is an AFValues collection representing the AFValues of interest. 
local is a Local.

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Setting A Value At A Specific Time
##### Decription:  

Returns AFValues with values generated from a random walk model.

##### Usage: 
```C#
private static AFValues SetValueAtTime(this AFValues values, object newValue, AFTime timeStamp)
```

##### Parameters:  
values is an AFValues collection representing the AFValues of interest.
newValue is an object the represents the value to be set at a specific time stamp.
timeStamp is an AFTime that represents the time stamp corresponding to object newValue.

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding The Minimum Value
##### Decription:  

Returns AFValues with the smallest value.

##### Usage: 
```C#
public static AFValues Min(this AFValues values, AFTime timeStamp)
```

##### Parameters:  
values is an AFValues collection representing the AFValues of interest.
timeStamp is an AFTime that represents the time stamp that will correspond with the minimum value.

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding The Maximum Value
##### Decription:  

Returns AFValues with the largest value.

##### Usage: 
```C#
public static AFValues Max(this AFValues values, Local local, AFTime timeStamp)
```

##### Parameters:  
values is an AFValues collection representing the AFValues of interest.
local is a Local.
timeStamp is an AFTime that represents the time stamp that will correspond with the maximum value.

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding The Median (indexed by half of the total number of values)
##### Decription:  

Sorts AFValues values and returns the value indexed by half of the total number of values.

##### Usage: 
```C#
public static AFValues PositionMedian(this AFValues values, AFTime timeStamp)
```

##### Parameters:  
values is an AFValues collection representing the AFValues of interest.
timeStamp is an AFTime that represents the time stamp that will correspond with the returned value.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding the Median
##### Decription:  

Sorts the AFValues values and returns the median.

##### Usage: 
```C#
public static AFValues Median(this AFValues values, AFTime timeStamp)
```

##### Parameters:  
values is an AFValues collection representing the AFValues of interest. 
timeStamp is an AFTime that represents the time stamp that will correspond with the returned value.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

The following are built into the AACE.Extension Operator class library.

#### Finding the Exponentially Weighed Moving Average (EMA)
##### Decription:  

Calculates and returns the exponentially weighed moving average.

##### Usage: 
```C#
EMA(TimeSpan tau, EmaType Type).Calculate(AFValue dv)
```

##### Parameters:  
tau is a TimeSpan that represents the length of the rolling time window.  
Type is an EmaType that representes the type of interpolation method to be used.  
dv is an AFValue that represents the operand.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding the Iterated Exponentially Weighed Moving Average
##### Decription:  

Calculates and returns the iterated exponentially weighed moving average.

##### Usage: 
```C#
NEMA(TimeSpan tau, EmaType Type, int n).Calculate(AFValue dv)
```

##### Parameters:  
tau is a TimeSpan that represents the length of the rolling time window.  
Type is an EmaType that representes the type of interpolation method to be used.  
n is an integer that represents the number of iterations to be performed.  
dv is an AFValue that represents the operand.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding the Moving Average
##### Decription:  

Calculates and returns the moving average.

##### Usage: 
```C#
MA(TimeSpan tau, EmaType Type, int n).Calculate(AFValue dv)
```

##### Parameters:  
tau is a TimeSpan that represents the length of the rolling time window.  
Type is an EmaType that representes the type of interpolation method to be used.  
n is an integer that represents the number of iterations to be performed.  
dv is an AFValue that represents the operand.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding the Moving Norm
##### Decription:  

Calculates and returns the moving norm.

##### Usage: 
```C#
MNORM(TimeSpan tau, EmaType Type, int n, int p).Calculate(AFValue dv)
```

##### Parameters:  
tau is a TimeSpan that represents the length of the rolling time window.  
Type is an EmaType that representes the type of interpolation method to be used.  
n is an integer that represents the number of iterations to be performed.  
dv is an AFValue that represents the operand.  
p is an integer that represents the p-moment.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding the Moving Variance
##### Decription:  

Calculates and returns the moving variance.

##### Usage: 
```C#
MVAR(TimeSpan tau, EmaType Type, int n, int p).Calculate(AFValue dv)
```

##### Parameters:  
tau is a TimeSpan that represents the length of the rolling time window.  
Type is an EmaType that representes the type of interpolation method to be used.  
n is an integer that represents the number of iterations to be performed.  
dv is an AFValue that represents the operand.  
p is an integer that represents the p-moment.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.

#### Finding the Moving Standard Deviation
##### Decription:  

Calculates and returns the moving standard deviation.

##### Usage: 
```C#
MSD(TimeSpan tau, EmaType Type, int n, int p).Calculate(AFValue dv)
```

##### Parameters:  
tau is a TimeSpan that represents the length of the rolling time window.  
Type is an EmaType that representes the type of interpolation method to be used.  
n is an integer that represents the number of iterations to be performed.  
dv is an AFValue that represents the operand.  
p is an integer that represents the p-moment.  

##### Example:  

Please visit the [Sample Library](https://github.com/tqsintegration/Advanced-Calculation-Engine-for-AF/blob/master/Sample%20Library.md) for an example.
