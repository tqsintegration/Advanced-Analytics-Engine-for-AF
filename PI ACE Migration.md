
# PI ACE Code Migration

The Advanced Calculation Engine for AF\EF provides the capability to execute C# and VB.Net code through runtime compilation. The engine can be used to migrate [OSIsoft PI-ACE](http://https://techsupport.osisoft.com/Products/PI-Server/PI-ACE/Overview/ "OSIsoft Web Site") projects to the AF system.

Due to the differences in the underlying Software Development Kits SDK's ([PI-SDK](https://techsupport.osisoft.com/Products/Other-Products/PI-SDK/Overview "OSIsoft Web Site") vs [AF-SDK](https://techsupport.osisoft.com/Documentation/PI-AF-SDK/html/1a02af4c-1bec-4804-a9ef-3c7300f5e2fc.htm "OSIsoft Web Site")) the migration is not 1:1 and some changes are required.

OSIsoft has transitioned most PI-SDK functionality into the AF-SDK with two exceptions:
1) Module Database (MDB), this legacy system provided a basic equipment or context model and has been replaced by the Asset Framework (AF)
2) Batch Database (PIBatchDB) is the predecessor of the Event Frame Database and allowed batch, unit batch and sub batch creation
To allow calls to the legacy system, functions to the MDB and PIBatchDB have been wrapped into NET classes that only have an AF-SDK dependency.

Here some quick links to navigate the section:


Every Advanced Calculation Engine method will have the following format
```vbnet
#Region "Imports"
    Imports OSIsoft.AF.Asset
    Imports OSIsoft.AF.Time
    Imports AACE.Data.Model
    Imports AACE.Extension
    Imports System
#End Region

Namespace AFCalculationEngine
    Public Class RealTime
#Region "Private Fields"
        Private _local As Local
        Private ACE_Raw_Date As AFAttribute
        Private ACE_Raw_Phosphate As AFAttribute
        Private ACE_Raw_Glucose As AFAttribute
        Private ACE_Raw_Acetate As AFAttribute
#End Region
        Public Sub New(ByVal local As Local)
#Region "Constructor"
            _local = local
            ACE_Raw_Date = _local.Attributes`["ACE_Raw_Date"`]
            ACE_Raw_Phosphate = _local.Attributes`["ACE_Raw_Phosphate"`]
            ACE_Raw_Glucose = _local.Attributes`["ACE_Raw_Glucose"`]
            ACE_Raw_Acetate = _local.Attributes`["ACE_Raw_Acetate"`]
#End Region
        End Sub

        Public Function Update(ByVal context As Context, ByVal timeRange As AFTimeRange, 
            ByVal n As Integer, ByVal values As AFValues) As AFValues
#Region "Function"
            ' 
            Return Data.GetHeartBeatValues(timeRange,n)
            '
#End Region
        End Function
    End Class
End Namespace
```
The namespace, class, method name and the parameter list will be always the same.

## Region: Imports
The namespaces have changed from PI-ACE - please use the new namespaces for import.


| PI-ACE  | AF Advanced Calculation Engine|
| ------------- | ------------- |
| Imports OSIsoft.PI.ACE  |Imports OSIsoft.AF.Asset|
||Imports OSIsoft.AF.Time|
||Imports AACE.Data.Model|
||Imports AACE.Extension|
||Imports System|

## Region: Private Fields

PIACEPoint was a way to map module specific aliases to a field. This data type has been replaced by AF Attributes. It follows the following scheme:

PI Module = AF Element
PI Alias = AF Attribute


| PI-ACE  | AF Advanced Calculation Engine |
| ------------- | ------------- |
||Private _local As Local
|Private ACE_Raw_Date As PIACEPoint|Private ACE_Raw_Date As AFAttribute|
|Private ACE_Raw_Phosphate As PIACEPoint|Private ACE_Raw_Phosphate As AFAttribute|
|Private ACE_Raw_Glucose As PIACEPoint|Private ACE_Raw_Glucose As AFAttribute|
|Private ACE_Raw_Acetate As PIACEPoint|Private ACE_Raw_Acetate As AFAttribute|


## Region: Constructor

PI Ace initialized fields in the following sub procedure:
```vb.net
Protected Overrides Sub InitializePIACEPoints()
...
End Sub
```
In the Advanced Calculation Engine there is simply a constructor that can be used to initialize private fields.
Mappings to the element attributes is performed using the Local object:

| PI-ACE  | AF Advanced Calculation Engine |
| ------------- | ------------- |
||_local = local|
|ACE_Raw_Date = GetPIACEPoint("ACE_Raw_Date")|ACE_Raw_Date = _local.Attributes`["ACE_Raw_Date"`]|
|ACE_Raw_Phosphate = GetPIACEPoint("ACE_Raw_Phosphate")|ACE_Raw_Phosphate = _local.Attributes`["ACE_Raw_Phosphate"`]|
|ACE_Raw_Glucose = GetPIACEPoint("ACE_Raw_Glucose") |ACE_Raw_Glucose = _local.Attributes`["ACE_Raw_Glucose"`]|
|ACE_Raw_Acetate = GetPIACEPoint("ACE_Raw_Acetate")|ACE_Raw_Acetate = _local.Attributes`["ACE_Raw_Acetate"`]|

## Region: Private Fields

PI ACE used the following sub procedure to define calculations:

```vb.net
Public Overrides Sub ACECalculations()
...
End Sub
```

This code can be moved into the function declaration.

## Module dependent Initialization and Termination
Each PI ACE module contains the following startup and tear down routines:

```vb.net
'
' User-written module dependent initialization code
'
Public Sub ModuleDependentInitialization()
End Sub

'
' User-written module dependent termination code
'
Public Sub ModuleDependentTermination()
End Sub
```

These procedures are no longer required. If required, dispoing of managed and unmanaged resource can be implemented using the IDisposable pattern.

## PI ACE specific Properties, Methods and Functions

For all PI-SDK functions that 


| PI-ACE  | AF Advanced Calculation Engine |
| ------------- | ------------- |
|Inherits PIACENetClassModule | not required|
|Example As PIACEPoint | Example as AFAttribute|
|Dim server As PISDK.Server | Dim server as LegacyServer|
|Dim nvAttrs As PISDKCommon.NamedValue| not required|
|Dim pisdk As New PISDK.PISDK| not required|
|Dim aliases As PISDK.PIAliases | Dim aliases as AFAttributes|
|Dim alias As PISDK.PIAlias | Dim alias As AFAttribute|
|Dim value As PISDK.PIValue | Dim value As AFValue|
|Dim values As New PISDK.PIValues| Dim values as new AFValues|
|Dim tag As PISDK.PIPoint| Dim tag as PIPoint|

