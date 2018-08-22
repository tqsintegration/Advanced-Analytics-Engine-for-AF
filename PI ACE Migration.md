
# PI ACE Code Migration

The Advanced Calculation Engine for AF\EF provides the capability to execute C# and VB.Net code through runtime compilation. The engine can be used to migrate [OSIsoft PI-ACE](http://https://techsupport.osisoft.com/Products/PI-Server/PI-ACE/Overview/ "OSIsoft Web Site") projects to the AF system.

Due to the differences in the underlying Software Development Kits SDK's ([PI-SDK](https://techsupport.osisoft.com/Products/Other-Products/PI-SDK/Overview "OSIsoft Web Site") vs [AF-SDK](https://techsupport.osisoft.com/Documentation/PI-AF-SDK/html/1a02af4c-1bec-4804-a9ef-3c7300f5e2fc.htm "OSIsoft Web Site")) the migration is not 1:1 and some changes are required.

OSIsoft has transitioned most PI-SDK functionality into the AF-SDF with two exceptions:
1) Module Database (MDB), this legacy system provided a basic equipment or context model and has been replaced by the Asset Framework (AF)
2) Batch Database (PIBatchDB) is the predecessor of the Event Frame Database and allowed batch, unit batch and sub batch creation
To allow calls to the legacy system, functions to the MDB and PIBatchDB have been wrapped into NET classes that only have an AF-SDK dependency.

Every Advanced Calculation Engine method will have the following format
```vb.net
Imports OSIsoft.AF.Asset
Imports OSIsoft.AF.Time
Imports AACE.Data.Model
Imports AACE.Extension
Imports System

Namespace AFCalculationEngine
    Public Class RealTime
        Private _local As Local

        Public Sub New(ByVal local As Local)
            _local = local
        End Sub

        Public Function Update(ByVal context As Context, ByVal timeRange As AFTimeRange, 
            ByVal n As Integer, ByVal values As AFValues) As AFValues
            Return Data.GetHeartBeatValues(timeRange,n)
        End Function
    End Class
End Namespace
```

The namespace, class, method name and the parameter list will be always the same.


