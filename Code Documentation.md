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

The following code may be input into the code editor of the graphical user interface and calculated to obtain the desired results. 
Please note that the time range, timeRange, and number of points, n, and are automatically derived and inserted for you based off 
of the AFTime values reflected in the Start Time, End Time, and No Points fields located on the GUI.
```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
            return Data.GetConstantValues(timeRange,n,5);
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
            return Data.GetHeartBeatValues(timeRange, n);
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
            return Data.GetRandomValues(timeRange,n);
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
            return Data.GetGaussianRandomValues(timeRange,n,0,3);
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
            return Data.GetSinusoidValues(timeRange,n,100,4,
				TimeSpan.FromSeconds(0));
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
            return Data.GetRectangularValues(timeRange,n,TimeSpan.FromSeconds(1),TimeSpan.FromSeconds(3),5, TimeSpan.FromSeconds(5));
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;

using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;
using System.Linq;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		public RealTime(Local local)
        {
            _local=local;

        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
			var newValues=Data.GetRectangularValues(
				timeRange,
				n,TimeSpan.FromMinutes(10),TimeSpan.FromMinutes(5),100,
				TimeSpan.Zero,null);
            return  newValues;
        }
    }
}
```

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

```C#
using OSIsoft.AF.Asset;
using OSIsoft.AF.Time;
using AACE.Data.Model;
using AACE.Extension;
using System;
using System.Linq;

namespace AFCalculationEngine
{
    public class RealTime
    {
        private Local _local;
		private double _previousValue;
		public RealTime(Local local)
        {
            _local=local;
			_previousValue=0;
        }
        public AFValues Update(Context context, AFTimeRange timeRange,
			int n, AFValues values)
        {
			var newValues=Data.GetRandomWalkValues(
				timeRange,
				n,
			_previousValue,0,100,null);
			_previousValue=Convert.ToDouble(newValues.Last().Value.ToString());
            return  newValues;
        }
    }
}
```
