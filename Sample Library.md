
# Sample Library

1) Create Gaussian Noise

using OSIsoft.AF.Asset;</br>
using OSIsoft.AF.Time;</br>
using AACE.Data.Model;</br>
using AACE.Extension;</br>
using System;</br>
</br>
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
