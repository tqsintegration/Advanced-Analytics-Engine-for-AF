
# Sample Library

1) Create Gaussian Noise

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
