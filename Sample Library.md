
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
