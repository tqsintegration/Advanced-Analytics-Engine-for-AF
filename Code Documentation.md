# Code Documentation

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
GetRectangularValues(AFTimeRange timeRange, int numberOfValues, TimeSpan zeroSpan, TimeSpan oneSpan, double height, TimeSpan shift, AFAttribute attribute = null)
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
