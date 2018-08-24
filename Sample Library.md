
# Sample Library



#### Creating Constant Values
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
#### Getting Compressed AFValues
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
            return Data.GetCompressed(Data.GetSinusoidValues(timeRange,n,100,4,
				TimeSpan.FromSeconds(0)), _local);
        }
    }
}
```

#### Finding The Minimum Value
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
            return Data.Min(Data.GetSinusoidValues(timeRange,n,100,4,
				TimeSpan.FromSeconds(0)), AFTime.Now);
        }
    }
}
```

#### Finding The Maximum Value
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
            return Data.Max(Data.GetSinusoidValues(timeRange,n,100,4,
				TimeSpan.FromSeconds(0)), _local, AFTime.Now);
        }
    }
}
```

#### Finding The Median (indexed by half of the total number of values)
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
            return Data.PositionMedian(Data.GetSinusoidValues(timeRange,n,100,4,
				TimeSpan.FromSeconds(0)), AFTime.Now);
        }
    }
}
```

#### Finding the Median
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
            return Data.Median(Data.GetSinusoidValues(timeRange,n,100,4,
				TimeSpan.FromSeconds(0)), AFTime.Now);
        }
    }
}
```
#### Finding the Exponentially Weighed Moving Average (EMA)
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
	private AACE.Extension.Operator.EMA _ema;
	public RealTime(Local local)
        {
            _local = local;
	    _ema = new AACE.Extension.Operator.EMA(TimeSpan.FromMinutes(1),
		    AACE.Extension.Operator.EmaType.Interpolated);
        }
        public AFValues Update(Context context, AFTimeRange timeRange, int n, 
            AFValues values)
        {
	    var newValues=Data.GetSinusoidValues(timeRange,n,100,4,
		TimeSpan.FromSeconds(0));
	    AFValues result = new AFValues();
	    foreach(var value in newValues )
	    {
		result.Add(_ema.Calculate(value)[0].Clone());
	    }
            return result;
        }
    }
}
```

#### Finding the Iterated Exponentially Weighed Moving Average
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
	private AACE.Extension.Operator.NEMA _nema;
	public RealTime(Local local)
        {
            _local = local;
	    _nema = new AACE.Extension.Operator.NEMA(TimeSpan.FromMinutes(1),
				AACE.Extension.Operator.EmaType.Interpolated, 5);
        }
        public AFValues Update(Context context, AFTimeRange timeRange, int n, 
            AFValues values)
        {
	    var newValues=Data.GetSinusoidValues(timeRange,n,100,4,
		TimeSpan.FromSeconds(0));
	    AFValues result = new AFValues();
	    foreach(var value in newValues )
	    {
		result.Add(_nema.Calculate(value)[0].Clone());
	    }
            return result;
        }
    }
}
```
