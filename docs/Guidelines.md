## Table of contents

 #### 1. [BasicCommunication](#basiccommunication) 
 -   [1.1. ActivateApp](#1-activateapp)
 -   [1.2. AllowDeviceToConnect]()
 -   [1.3. DialNumber]()
 -   [1.4. GetSystemInfo]()
 -   [1.5. MixingAudioSupported]()
 -   [1.6. OnAppActivated]()
 -   [1.7. OnAppDeactivated]()
 -   [1.8. OnAppRegistered]()
 -   [1.9. OnAppUnregistered]()
 -   [1.10. OnAwakeSDL]()
 -   [1.11. OnDeviceChosen]()
 -   [1.12. OnEmergencyEvent](BasicCommunication/OnEmergencyEvent/index.md#onemergencyevent)
 -   [1.13. OnExitAllApplications](BasicCommunication/OnExitAllApplications/index.md#onexitallapplications)
 -   [1.14. OnExitApplication](BasicCommunication/OnExitApplication/index.md#onexitapplication)
 -   [1.15. OnFileRemoved](BasicCommunication/OnFileRemoved/index.md#onfileremoved) 
 -   [1.16. OnFindApplications](BasicCommunication/OnFindApplications/index.md#onfindapplications) 
 -   [1.17. OnIgnitionCycleOver](BasicCommunication/OnIgnitionCycleOver/index.md#onignitioncycleover)
 -   [1.18. OnPhoneCall](BasicCommunication/OnPhoneCall/index.md#onphonecall)
 -   [1.19. OnPutFile](BasicCommunication/OnPutFile/index.md#onputfile)
 -   [1.20. OnReady](BasicCommunication/OnReady/index.md#onready)
 -   [1.21. OnResumeAudioSource](BasicCommunication/OnResumeAudioSource/index.md#onresumeaudiosource)
 -   [1.22. OnSDLClose](BasicCommunication/OnSDLClose/index.md#onsdlclose)
 -   [1.23. OnSDLPersistenceComplete](BasicCommunication/OnSDLPersistenceComplete/index.md#onsdlpersistencecomplete)
 -   [1.24. OnStartDeviceDiscovery](BasicCommunication/OnStartDeviceDiscovery/index.md#onstartdevicediscovery)
 -   [1.25. OnSystemInfoChanged](BasicCommunication/OnSystemInfoChanged/index.md#notification)  
 
 #### 2. Buttons  
 -   [2.1. GetCapabilities](Buttons/GetCapabilities/index.md#getcapabilities)
 -   [2.2. OnButtonEvent](Buttons/OnButtonEvent/index.md#onbuttonevent)
 -   [2.3. OnButtonPress](Buttons/OnButtonPress/index.md#onbuttonpress) 
 -   [2.4. OnButtonSubscription](Buttons/OnButtonSubscription/index.md#onbuttonsubscription) 

#### 3. Common  
-  [3.1. Enumerations](Common/Enums/index.md#enumerations)  
-  [3.2. Structs](Common/Structs/index.md#structs)

#### [4. Configuration file](Configuration file/index.md)  

#### [5. Getting Started](Getting Started/index.md#getting-started)  

#### 6. Navigation  
-  [6.1. AlertManeuver](Navigation/AlertManeuver/index.md#alertmaneuver) 
-  [6.2. IsReady](Navigation/IsReady/index.md#isready) 
-  [6.3. OnAudioDataStreaming](Navigation/OnAudioDataStreaming/index.md#onaudiodatastreaming) 
-  [6.4. OnTBTClientState](Navigation/OnTBTClientState/index.md#ontbtclientstate) 
-  [6.5. OnVideoDataStreaming](Navigation/OnVideoDataStreaming/index.md#onvideodatastreaming) 
-  [6.6. SendLocation](Navigation/SendLocation/index.md#sendlocation) 
-  [6.7. ShowConstantTBT](Navigation/ShowConstantTBT/index.md#showconstanttbt) 
-  [6.8. StartAudioStream](Navigation/StartAudioStream/index.md#startaudiostream) 
-  [6.9. StartStream](Navigation/StartStream/index.md#startstream) 
-  [6.10. StopAudioStream](Navigation/StopAudioStream/index.md#stopaudiostream) 
-  [6.11. StopStream](Navigation/StopStream/index.md#stopstream) 
-  [6.12. UpdateTurnList](Navigation/UpdateTurnList/index.md#updateturnlist) 

#### [7. Overview](Overview/index.md#overview)  

#### 8. SDL
-   [8.1. ActivateApp](SDL/ActivateApp/index.md#activateapp)
-   [8.2. AddStatisticsInfo](SDL/AddStatisticsInfo/index.md#addstatisticsinfo)  
-   [8.3. GetListOfPermissions](SDL/GetListOfPermissions/index.md#getlistofpermissions)
-   [8.4. GetStatusUpdate](SDL/GetStatusUpdate/index.md#getstatusupdate)  
-   [8.5. GetURLS](SDL/GetURLS/index.md#geturls)  
-   [8.6. GetUserFriendlyMessage](SDL/GetUserFriendlyMessage/index.md#getuserfriendlymessage)  
-   [8.7. OnAllowSDLFunctionality](SDL/OnAllowSDLFunctionality/index.md#onallowsdlfunctionality)
-   [8.8. OnAppPermissionChanged](SDL/OnAppPermissionChanged/index.md#onapppermissionchanged)  
-   [8.9. OnAppPermissionConsent](SDL/OnAppPermissionConsent/index.md)  
-   [8.10. OnDeviceStateChanged](SDL/OnDeviceStateChanged/index.md#ondevicestatechanged)  
-   [8.11. OnPolicyUpdate](SDL/OnPolicyUpdate/index.md#onpolicyupdate)  
-   [8.12. OnReceivedPolicyUpdate](SDL/OnReceivedPolicyUpdate/index.md#onreceivedpolicyupdate)  
-   [8.13. OnSDLConsentNeeded](SDL/OnSDLConsentNeeded/index.md#onsdlconsentneeded)
-   [8.14. OnStatusUpdate](SDL/OnStatusUpdate/index.md#onstatusupdate)
-   [8.15. OnSystemError](SDL/OnSystemError/index.md#onsystemerror)
-   [8.16. UpdateSDL](SDL/UpdateSDL/index.md#updatesdl)

#### 9. TTS 

#### 10. UI

#### 11. VR

#### 12. VehicleInfo  

#### [13. WebSocket Transport](WebSocket Transport/index.md#connecting-to-sdl)

## BasicCommunication

### 1. ActivateApp

!!! note

The activated application is assumed to receive access to the head unit's display, audio and control system which are:
  * Supported by the head unit and
  * Confirmed to be supported via responses to `IsReady` requests sent by SDL for the corresponding component

In the case of a successful HMILevel resumption, SDL will first assign a 'default_hmi' level from policies with a 3 second timeout, before resuming the application to either FULL or LIMITED.

If the HMI receives `ActivateApp` it can be assumed that the HMI has also already been provided with detailed information about the application through the [OnAppRegistered](../OnAppRegistered) RPC

!!!

!!! may

This request may be sent:
  * After SDL restores the application's state saved during a previous ignition off

!!!

### Behavior

!!! must

  1. Activate the application on the HMI
    * Display [UI.Show](../../UI/Show) related parameters associated with the named `appID` in the case they were previously requested within ignition cycle
    * Display the corresponding template in the case one was previously requested by [UI.SetDisplayLayout](../../UI/SetDisplayLayout) for that application
    * Apply [UI.SetGlobalProperties](../../UI/SetGlobalProperties) associated with the named `appID`, if any
    * Apply [UI.AddSubMenu](../../UI/AddSubMenu) associated with the named `appID`, if any
  2. Make VR commands accessible from previous [VR.AddCommand](../VR/AddCommand) for the named `appID` during the same ignition cycle
  3. Apply [TTS.SetGlobalProperties](../../TTS/SetGlobalProperties) associated with the `appID` in case previously requested since application registration
  4. Assign priority based on the `priority` parameter received. If the parameter is omitted, the HMI must assign a priority of `NONE` by default
  5. Respond with `SUCCESS` result code after the previous requirements have been met
  6. Set up the application as the active audio source if it is a media or navigation type application

!!!

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|appID|Integer|true||
|priority|[Common.AppPriority](../../common/enums/#apppriority)|false||
|level|[Common.HMILevel](../../common/enums/#hmilevel)|false||

### Response

#### Parameters

This RPC has no additional parameter requirements

### Example Request

```json
{
  "id" : 47,
  "jsonrpc" : "2.0",
  "method" : "BasicCommunication.ActivateApp",
  "result" :
  {
    "appID" : 65368
  }
}
```
### Example Response

```json
{
  "id" : 47,
  "jsonrpc" : "2.0",
  "result" :
  {
    "code" : 0,
    "method" : "BasicCommunication.ActivateApp"
  }
}
```

### Example Error

```json
{
  "id" : 47,
  "jsonrpc" : "2.0",
  "error" :
  {
    "code" : 13,
    "message" : "One of the provided IDs is not valid.",
    "data" :
    {
      "method" : "BasicCommunication.ActivateApp"
    }
  }
}
```

### Sequence Diagrams

Activate App after successful Resumption
![Activate App Successful Resume](./assets/ActivateAppSuccessfulResume.png)

Activate App after failed Resumption
![Activate App Failed Resume](./assets/ActivateAppFailedResume.png)

Activate App after Unexpected Disconnect
![Activate App Unexpected Disconnect](./assets/ActivateAppUnexpectedDisconnect.png)

Activate App after Accepted Data Consent Prompt
![Activate App Successful Data](./assets/ActivateAppSuccessfulData.png)

Activate App after Failed Data Consent Prompt
![Activate App Failed Data](./assets/ActivateAppFailedData.png)


## Common

## Structs

### ImageResolution

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|resolutionWidth|Integer|true|minvalue: 1<br>maxvalue: 10000||
|resolutionHeight|Integer|true|minvalue: 1<br>maxvalue: 10000||

### UserFriendlyMessage

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|messageCode|String|true|||
|ttsString|String|false|||
|label|String|false|||
|line1|String|false|||
|line2|String|false|||
|textBody|String|false|||

### HMICapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|navigation|Boolean|false|||
|phoneCall|Boolean|false|||

### MenuParams

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|parentID|Integer|false|minvalue: 0<br>maxvalue: 2000000000||
|position|Integer|false|minvalue: 0<br>maxvalue: 1000||
|menuName|String|true|maxlength: 500||

### TireStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|pressureTelltale|Common.WarningLightStatus|false|||
|leftFront|Common.SingleTireStatus|false|||
|rightFront|Common.SingleTireStatus|false|||
|leftRear|Common.SingleTireStatus|false|||
|rightRear|Common.SingleTireStatus|false|||
|innerLeftRear|Common.SingleTireStatus|false|||
|innerRightRear|Common.SingleTireStatus|false|||

### ECallInfo

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|eCallNotificationStatus|Common.VehicleDataNotificationStatus||||
|auxECallNotificationStatus|Common.VehicleDataNotificationStatus||||
|eCallConfirmationStatus|Common.ECallConfirmationStatus||||

### DIDResult

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|resultCode|Common.VehicleDataResultCode|true|||
|didLocation|Integer|true|minvalue: 0<br>maxvalue: 65535||
|data|String|false|maxlength: 5000||

### TTSChunk

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|text|String|true|maxlength: 500||
|type|Common.SpeechCapabilities|true|||

### TextField

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|name|Common.TextFieldName||||
|characterSet|Common.CharacterSet||||
|width|Integer||minvalue: 1<br>maxvalue: 500||
|rows|Integer||minvalue: 1<br>maxvalue: 8||

### TouchCoord

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|x|Integer|true|minvalue: 0<br>maxvalue: 10000||
|y|Integer|true|minvalue: 0<br>maxvalue: 10000||

### AudioPassThruCapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|samplingRate|Common.SamplingRate|true|||
|bitsPerSample|Common.BitsPerSample|true|||
|audioType|Common.AudioType|true|||

### ServiceInfo

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|url|String|true|||
|policyAppId|String|false|||

### HeadLampStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|lowBeamsOn|Boolean|true|||
|highBeamsOn|Boolean|true|||
|ambientLightSensorStatus|Common.AmbientLightStatus|true|||

### ClusterModeStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|powerModeActive|Boolean||||
|powerModeQualificationStatus|Common.PowerModeQualificationStatus||||
|carModeStatus|Common.CarModeStatus||||
|powerModeStatus|Common.PowerModeStatus||||

### KeyboardProperties

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|language|Common.Language|false|||
|keyboardLayout|Common.KeyboardLayout|false|||
|keypressMode|Common.KeypressMode|false|||
|limitedCharacterList|String|false|array: true<br>minsize: 1<br>maxsize: 100<br>maxlength: 1||
|autoCompleteText|String|false|maxlength: 1000||

### Choice

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|choiceID|Integer|true|minvalue: 0<br>maxvalue: 65535||
|menuName|String|false|maxlength: 500||
|image|Common.Image|false|||
|secondaryText|String|false|maxlength: 500||
|tertiaryText|String|false|maxlength: 500||
|secondaryImage|Image|false|||

### DeviceStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|voiceRecOn|Boolean|false|||
|btIconOn|Boolean|false|||
|callActive|Boolean|false|||
|phoneRoaming|Boolean|false|||
|textMsgAvailable|Boolean|false|||
|battLevelStatus|Common.DeviceLevelStatus|false|||
|stereoAudioOutputMuted|Boolean|false|||
|monoAudioOutputMuted|Boolean|false|||
|signalLevelStatus|Common.DeviceLevelStatus|false|||
|primaryAudioSource|Common.PrimaryAudioSource|false|||
|eCallEventActive|Boolean|false|||

### GPSData

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|longitudeDegrees|Float|false|minvalue: -180<br>maxvalue: 180||
|latitudeDegrees|Float|false|minvalue: -90<br>maxvalue: 90||
|utcYear|Integer|false|minvalue: 2010<br>maxvalue: 2100||
|utcMonth|Integer|false|minvalue: 1<br>maxvalue: 12||
|utcDay|Integer|false|minvalue: 1<br>maxvalue: 31||
|utcHours|Integer|false|minvalue: 0<br>maxvalue: 23||
|utcMinutes|Integer|false|minvalue: 0<br>maxvalue: 59||
|utcSeconds|Integer|false|minvalue: 0<br>maxvalue: 59||
|compassDirection|Common.CompassDirection|false|||
|pdop|Float|false|minvalue: 0<br>maxvalue: 10||
|hdop|Float|false|minvalue: 0<br>maxvalue: 10||
|vdop|Float|false|minvalue: 0<br>maxvalue: 10||
|actual|Boolean|false|||
|satellites|Integer|false|minvalue: 0<br>maxvalue: 31||
|dimension|Common.Dimension|false|||
|altitude|Float|false|minvalue: -10000<br>maxvalue: 10000||
|heading|Float|false|minvalue: 0<br>maxvalue: 359.99||
|speed|Float|false|minvalue: 0<br>maxvalue: 500||

### SingleTireStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|status|Common.ComponentVolumeStatus|true|||

### SoftButtonCapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|shortPressAvailable|Boolean|true|||
|longPressAvailable|Boolean|true|||
|upDownAvailable|Boolean|true|||
|imageSupported|Boolean|true|||

### HMIApplication

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|appName|String|true|maxlength: 100||
|ngnMediaScreenAppName|String|false|maxlength: 100||
|icon|String|false|||
|deviceInfo|Common.DeviceInfo|true|||
|policyAppID|String|true|minlength: 1<br>maxlength: 50||
|ttsName|Common.TTSChunk|false|array: true<br>minsize: 1<br>maxsize: 100||
|vrSynonyms|String|false|array: true<br>minsize: 1<br>maxsize: 100<br>maxlength: 40||
|appID|Integer|true|||
|hmiDisplayLanguageDesired|Common.Language|false|||
|isMediaApplication|Boolean|false|||
|appType|Common.AppHMIType|false|array: true<br>minsize: 1<br>maxsize: 100||
|greyOut|Boolean|false|||
|requestType|Common.RequestType|false|array: true<br>minsize: 0<br>maxsize: 100||

### VehicleType

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|make|String|false|maxlength: 500||
|model|String|false|maxlength: 500||
|modelYear|String|false|maxlength: 500||
|trim|String|false|maxlength: 500||

### ButtonCapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|name|Common.ButtonName|true|||
|shortPressAvailable|Boolean|true|||
|longPressAvailable|Boolean|true|||
|upDownAvailable|Boolean|true|||

### VrHelpItem

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|text|String|true|maxlength: 500||
|image|Common.Image|false|||
|position|Integer|true|minvalue: 1<br>maxvalue: 100||

### BodyInformation

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|parkBrakeActive|Boolean|true|||
|ignitionStableStatus|Common.IgnitionStableStatus|true|||
|ignitionStatus|Common.IgnitionStatus|true|||
|driverDoorAjar|Boolean|false|||
|passengerDoorAjar|Boolean|false|||
|rearLeftDoorAjar|Boolean|false|||
|rearRightDoorAjar|Boolean|false|||

### BeltStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|driverBeltDeployed|Common.VehicleDataEventStatus|false|||
|passengerBeltDeployed|Common.VehicleDataEventStatus|false|||
|passengerBuckleBelted|Common.VehicleDataEventStatus|false|||
|driverBuckleBelted|Common.VehicleDataEventStatus|false|||
|leftRow2BuckleBelted|Common.VehicleDataEventStatus|false|||
|passengerChildDetected|Common.VehicleDataEventStatus|false|||
|rightRow2BuckleBelted|Common.VehicleDataEventStatus|false|||
|middleRow2BuckleBelted|Common.VehicleDataEventStatus|false|||
|middleRow3BuckleBelted|Common.VehicleDataEventStatus|false|||
|leftRow3BuckleBelted|Common.VehicleDataEventStatus|false|||
|rightRow3BuckleBelted|Common.VehicleDataEventStatus|false|||
|leftRearInflatableBelted|Common.VehicleDataEventStatus|false|||
|rightRearInflatableBelted|Common.VehicleDataEventStatus|false|||
|middleRow1BeltDeployed|Common.VehicleDataEventStatus|false|||
|middleRow1BuckleBelted|Common.VehicleDataEventStatus|false|||

### Turn

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|navigationText|Common.TextFieldStruct|false|||
|turnIcon|Common.Image|false|||

### EmergencyEvent

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|emergencyEventType|Common.EmergencyEventType||||
|fuelCutoffStatus|Common.FuelCutoffStatus||||
|rolloverEvent|Common.VehicleDataEventStatus||||
|maximumChangeVelocity|Common.VehicleDataEventStatus||||
|multipleEvents|Common.VehicleDataEventStatus||||

### VehicleDataResult

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|dataType|Common.VehicleDataType||||
|resultCode|Common.VehicleDataResultCode||||

### PresetBankCapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|onScreenPresetsAvailable|Boolean|true|||

### TouchEvent

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|id|Integer|true|minvalue: 0<br>maxvalue: 9||
|ts|Integer|true|array: true<br>minsize: 1<br>maxsize: 1000<br>minvalue: 0<br>maxvalue: 2147483647||
|c|Common.TouchCoord|true|array: true<br>minsize: 1<br>maxsize: 1000||

### PermissionItem

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|name|String|true|||
|id|Integer|true|||
|allowed|Boolean|false|||

### TouchEventCapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|pressAvailable|Boolean|true|||
|multiTouchAvailable|Boolean|true|||
|doublePressAvailable|Boolean|true|||

### ScreenParams

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|resolution|Common.ImageResolution|true|||
|touchEventAvailable|Common.TouchEventCapabilities|false|||

### TextFieldStruct

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|fieldName|Common.TextFieldName|true|||
|fieldText|String|true|maxlength: 500||

### DeviceInfo

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|name|String|true|||
|id|String|true|||
|transportType|Common.TransportType|false|||
|isSDLAllowed|Boolean|false|||

### SoftButton

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|type|Common.SoftButtonType|true|||
|text|String|false|maxlength: 500||
|image|Common.Image|false|||
|isHighlighted|Boolean|false|||
|softButtonID|Integer|true|minvalue: 0<br>maxvalue: 65535||
|systemAction|Common.SystemAction|true|||

### AirbagStatus

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|driverAirbagDeployed|Common.VehicleDataEventStatus||||
|driverSideAirbagDeployed|Common.VehicleDataEventStatus||||
|driverCurtainAirbagDeployed|Common.VehicleDataEventStatus||||
|passengerAirbagDeployed|Common.VehicleDataEventStatus||||
|passengerCurtainAirbagDeployed|Common.VehicleDataEventStatus||||
|driverKneeAirbagDeployed|Common.VehicleDataEventStatus||||
|passengerSideAirbagDeployed|Common.VehicleDataEventStatus||||
|passengerKneeAirbagDeployed|Common.VehicleDataEventStatus||||

### DisplayCapabilities

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|displayType|Common.DisplayType|true|||
|textFields|Common.TextField|true|array: true<br>minsize: 0<br>maxsize: 100||
|imageFields|Common.ImageField|false|array: true<br>minsize: 1<br>maxsize: 100||
|mediaClockFormats|Common.MediaClockFormat|true|array: true<br>minsize: 0<br>maxsize: 100||
|imageCapabilities|Common.ImageType|false|array: true<br>minsize: 0<br>maxsize: 2||
|graphicSupported|Boolean|true|||
|templatesAvailable|String|true|array: true<br>minsize: 0<br>maxsize: 100<br>maxlength: 100||
|screenParams|Common.ScreenParams|false|||
|numCustomPresetsAvailable|Integer|false|minvalue: 1<br>maxvalue: 100||

### TimeFormat

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|hours|Integer|true|minvalue: 0<br>maxvalue: 59||
|minutes|Integer|true|minvalue: 0<br>maxvalue: 59||
|seconds|Integer|true|minvalue: 0<br>maxvalue: 59||

### Image

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|value|String|true|maxlength: 65535||
|imageType|Common.ImageType|true|||

### MyKey

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|e911Override|Common.VehicleDataStatus|true|||

### ImageField

|Name|Type|Mandatory|Additional|Description|
|:---|:---|:--------|:---------|:----------|
|name|Common.ImageFieldName|true|||
|imageTypeSupported|Common.FileType|false|array: true<br>minsize: 1<br>maxsize: 100||
|imageResolution|Common.ImageResolution|false|||
