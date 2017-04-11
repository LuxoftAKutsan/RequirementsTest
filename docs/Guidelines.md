## Table of contents

 #### 1. [BasicCommunication](#basiccommunication) 
 -   [1.1. ActivateApp](#1-activateapp)
 -   [1.2. AllowDeviceToConnect](#2-allowdevicetoconnect)
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

#### 3. [Common](#common)  
-  3.1. [Enumerations](#enumerations)  
-  3.2. [Structs](#structs)

#### 4. [Configuration file](#sdls--configuration-file-structure-ini-file)  

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
|priority|[Common.AppPriority](#apppriority)|false||
|level|[Common.HMILevel](#hmilevel)|false||

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

### 2. AllowDeviceToConnect
* Type: Function
  * Sender: SDL
  * Purpose: Permit device to connect to head unit

### Behavior

!!! must

Check whether the device is allowed to connect to the head unit and response appropriately

!!!

!!! may

  1. Request the user's permission via VR, UI pop-up, etc.
  2. Implement a use case in which a user's device is not allowed to connect

!!!

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|device|[Common.DeviceInfo](#deviceinfo)|true||

### Response

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|allow|Boolean|true||

### Example Request
```json
{
  "id" : 87,
  "jsonrpc" : "2.0",
  "method" : "BasicCommunication.AllowDeviceToConnect",
  "params" :
  [
    "deviceInfo" : {
        "name" : "Mary`s Phone",
        "id" : 8
    }
  ]
}
```

### Example Response

```json
{
  "id" : 87,
  "jsonrpc" : "2.0",
  "result" :
  {
   "allow" : true,
    "code" : 0,
    "method" : "BasicCommunication.AllowDeviceToConnect"
  }
}
```

### Error Message
```json
{
  "id" : 87,
  "jsonrpc" : "2.0",
  "error" :
  {
    "code" : 22,
    "message" : "An unknown error occurred",
    "data" :
    {
      "method" : "BasicCommunication.AllowDeviceToConnect"
    }
  }
}
```

### Sequence Diagrams

AllowDeviceToConnect Messaging
![Allow Device To Connect](./assets/AllowDeviceToConnect.png)

## 3. DialNumber

Type
: Function

Sender
: SDL

Purpose
: SDL initiates a call to a specific phone number.

!!! NOTE

SDL looks to see if the phone number entered is correct before passing to the HMI. The checks performed are:

  1. Strip any characters except of 0-9 and * # , ;+ and pass resulting number to HMI.
  2. Return INVALID_DATA to mobile side without transferring "number" to the HMI if "number" is empty after stripping invalid characters.
  3. Return INVALID_DATA to mobile side without transferring "number" to HMI if the characters "/n" , "/t", or spaces are included in "number".

!!!

!!! MUST

  1. Show DialNumber pop-up on HMI with 2 buttons, "Call" and "Cancel".
  2. Send the notification OnAppDeactivated(PHONECALL) to SDL when the phone call is started on the HMI. The notification must be sent to all applications that have active audio sources on the HMI.
  3. Send the notification BC.OnOnPhoneCall(isActive:true) to SDL when the phone call is started on the HMI.
  3. Send the notification BC.OnOnPhoneCall(isActive:false) to SDL when the phone call is ended on the HMI.
  4. Always respond to BC.DialNumber with a response code. If the HMI does not respond, the mobile application will never get a response from from SDL because default timeouts do not apply to the DailNumber mobile API.

!!!

The request is considered to have been executed successfully only after the user presses the "Call" button included in the DialNumber dialog.

### Request

#### Parameters

|Name|Type|Mandatory|Additional|
|:---|:---|:--------|:---------|
|number|String||maxlength: 40|
|appID|Integer|true||

### Response

#### Parameters

This RPC has no additional parameter requirements

### Sequence Diagrams

DialNumber Success
![DialNumberSuccess](./assets/DialNumberSuccess.jpg)

DialNumber Failed
![DialNumberFailed](./assets/DialNumberFailed.png)


### Example Request

```json
{
  "id" : 59,
  "jsonrpc" : "2.0",
  "method" : "BasicCommunication. DialNumber",
  "params" :
  {
        "number" : "*111#",
        "appID" : 65537
  }
}
```
### Example Response

```json
{
  "id" : 59,
  "jsonrpc" : "2.0",
  "result" :
  {
    "code" : 0,
    "method" : "BasicCommunication.DialNumber"
  }
}
```

### Example Error

```json
{
  "id" : 59,
  "jsonrpc" : "2.0",
  "error" :
  {
    "code" : 5,
    "message" : " HMI is busy with higher priority RPC ",
    "data" :
    {
      "method" : "BasicCommunication.DialNumber"
    }
  }
}
```

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

## Enumerations

### KeyboardEvent

|Name|Value|Description|
|:---|:----|:----------|
|KEYPRESS|0||
|ENTRY_SUBMITTED|1||
|ENTRY_VOICE|2||
|ENTRY_CANCELLED|3||
|ENTRY_ABORTED|4||

### FuelCutoffStatus

|Name|Value|Description|
|:---|:----|:----------|
|TERMINATE_FUEL|0||
|NORMAL_OPERATION|1||
|FAULT|2||

### TransportType

|Name|Value|Description|
|:---|:----|:----------|
|BLUETOOTH|0||
|USB|1||
|WIFI|2||

### ButtonPressMode

|Name|Value|Description|
|:---|:----|:----------|
|LONG|0||
|SHORT|1||

### VRCommandType

|Name|Value|Description|
|:---|:----|:----------|
|Choice|0||
|Command|1||

### AppHMIType

|Name|Value|Description|
|:---|:----|:----------|
|DEFAULT|0||
|COMMUNICATION|1||
|MEDIA|2||
|MESSAGING|3||
|NAVIGATION|4||
|INFORMATION|5||
|SOCIAL|6||
|BACKGROUND_PROCESS|7||
|TESTING|8||
|SYSTEM|9||

### SpeechCapabilities

|Name|Value|Description|
|:---|:----|:----------|
|TEXT|0||
|SAPI_PHONEMES|1||
|LHPLUS_PHONEMES|2||
|PRE_RECORDED|3||
|SILENCE|4||

### TextFieldName

|Name|Value|Description|
|:---|:----|:----------|
|mainField1|0||
|mainField2|1||
|mainField3|2||
|mainField4|3||
|statusBar|4||
|mediaClock|5||
|mediaTrack|6||
|alertText1|7||
|alertText2|8||
|alertText3|9||
|scrollableMessageBody|10||
|initialInteractionText|11||
|navigationText1|12||
|navigationText2|13||
|ETA|14||
|totalDistance|15||
|audioPassThruDisplayText1|16||
|audioPassThruDisplayText2|17||
|sliderHeader|18||
|sliderFooter|19||
|menuName|20||
|secondaryText|21||
|tertiaryText|22||
|menuTitle|23||
|navigationText|24||
|notificationText|25||
|locationName|26||
|locationDescription|27||
|addressLines|28||
|phoneNumber|29||
|timeToDestination|30||
|turnText|31||

### AmbientLightStatus

|Name|Value|Description|
|:---|:----|:----------|
|NIGHT|0||
|TWILIGHT_1|1||
|TWILIGHT_2|2||
|TWILIGHT_3|3||
|TWILIGHT_4|4||
|DAY|5||
|UNKNOWN|6||
|INVALID|7||

### StatisticsType

|Name|Value|Description|
|:---|:----|:----------|
|iAPP_BUFFER_FULL|0||

### VehicleDataEventStatus

|Name|Value|Description|
|:---|:----|:----------|
|NO_EVENT|0||
|NO|1||
|YES|2||
|NOT_SUPPORTED|3||
|FAULT|4||

### KeyboardLayout

|Name|Value|Description|
|:---|:----|:----------|
|QWERTY|0||
|QWERTZ|1||
|AZERTY|2||

### ButtonEventMode

|Name|Value|Description|
|:---|:----|:----------|
|BUTTONUP|0||
|BUTTONDOWN|1||

### VrCapabilities

|Name|Value|Description|
|:---|:----|:----------|
|TEXT|0||

### TextAlignment

|Name|Value|Description|
|:---|:----|:----------|
|LEFT_ALIGNED|0||
|RIGHT_ALIGNED|1||
|CENTERED|2||

### DeviceState

|Name|Value|Description|
|:---|:----|:----------|
|UNKNOWN|0||
|UNPAIRED|1||

### SystemContext

|Name|Value|Description|
|:---|:----|:----------|
|MAIN|0||
|VRSESSION|1||
|MENU|2||
|HMI_OBSCURED|3||
|ALERT|4||

### SoftButtonType

|Name|Value|Description|
|:---|:----|:----------|
|TEXT|0||
|IMAGE|1||
|BOTH|2||

### DriverDistractionState

|Name|Value|Description|
|:---|:----|:----------|
|DD_ON|0||
|DD_OFF|1||

### MethodName

|Name|Value|Description|
|:---|:----|:----------|
|ALERT|0||
|SPEAK|1||
|AUDIO_PASS_THRU|2||
|ALERT_MANEUVER|3||

### CharacterSet

|Name|Value|Description|
|:---|:----|:----------|
|TYPE2SET|0||
|TYPE5SET|1||
|CID1SET|2||
|CID2SET|3||

### DeactivateReason

|Name|Value|Description|
|:---|:----|:----------|
|AUDIO|0||
|PHONECALL|1||
|NAVIGATIONMAP|2||
|PHONEMENU|3||
|SYNCSETTINGS|4||
|GENERAL|5||

### SamplingRate

|Name|Value|Description|
|:---|:----|:----------|
|8KHZ|0||
|16KHZ|1||
|22KHZ|2||
|44KHZ|3||

### PrerecordedSpeech

|Name|Value|Description|
|:---|:----|:----------|
|HELP_JINGLE|0||
|INITIAL_JINGLE|1||
|LISTEN_JINGLE|2||
|POSITIVE_JINGLE|3||
|NEGATIVE_JINGLE|4||

### MediaClockFormat

|Name|Value|Description|
|:---|:----|:----------|
|CLOCK1|0||
|CLOCK2|1||
|CLOCK3|2||
|CLOCKTEXT1|3||
|CLOCKTEXT2|4||
|CLOCKTEXT3|5||
|CLOCKTEXT4|6||

### TouchType

|Name|Value|Description|
|:---|:----|:----------|
|BEGIN|0||
|MOVE|1||
|END|2||

### HmiZoneCapabilities

|Name|Value|Description|
|:---|:----|:----------|
|FRONT|0||
|BACK|1||

### AlertType

|Name|Value|Description|
|:---|:----|:----------|
|UI|0||
|BOTH|1||

### ECallConfirmationStatus

|Name|Value|Description|
|:---|:----|:----------|
|NORMAL|0||
|CALL_IN_PROGRESS|1||
|CALL_CANCELLED|2||
|CALL_COMPLETED|3||
|CALL_UNSUCCESSFUL|4||
|ECALL_CONFIGURED_OFF|5||
|CALL_COMPLETE_DTMF_TIMEOUT|6||

### ClockUpdateMode

|Name|Value|Description|
|:---|:----|:----------|
|COUNTUP|0||
|COUNTDOWN|1||
|PAUSE|2||
|RESUME|3||
|CLEAR|4||

### DeviceLevelStatus

|Name|Value|Description|
|:---|:----|:----------|
|ZERO_LEVEL_BARS|0||
|ONE_LEVEL_BARS|1||
|TWO_LEVEL_BARS|2||
|THREE_LEVEL_BARS|3||
|FOUR_LEVEL_BARS|4||
|NOT_PROVIDED|5||

### SystemAction

|Name|Value|Description|
|:---|:----|:----------|
|DEFAULT_ACTION|0||
|STEAL_FOCUS|1||
|KEEP_CONTEXT|2||

### ButtonName

|Name|Value|Description|
|:---|:----|:----------|
|OK|0||
|SEEKLEFT|1||
|SEEKRIGHT|2||
|TUNEUP|3||
|TUNEDOWN|4||
|PRESET_0|5||
|PRESET_1|6||
|PRESET_2|7||
|PRESET_3|8||
|PRESET_4|9||
|PRESET_5|10||
|PRESET_6|11||
|PRESET_7|12||
|PRESET_8|13||
|PRESET_9|14||
|CUSTOM_BUTTON|15||
|SEARCH|16||

### KeypressMode

|Name|Value|Description|
|:---|:----|:----------|
|SINGLE_KEYPRESS|0||
|QUEUE_KEYPRESSES|1||
|RESEND_CURRENT_ENTRY|2||

### WiperStatus

|Name|Value|Description|
|:---|:----|:----------|
|OFF|0||
|AUTO_OFF|1||
|OFF_MOVING|2||
|MAN_INT_OFF|3||
|MAN_INT_ON|4||
|MAN_LOW|5||
|MAN_HIGH|6||
|MAN_FLICK|7||
|WASH|8||
|AUTO_LOW|9||
|AUTO_HIGH|10||
|COURTESYWIPE|11||
|AUTO_ADJUST|12||
|STALLED|13||
|NO_DATA_EXISTS|14||

### LayoutMode

|Name|Value|Description|
|:---|:----|:----------|
|ICON_ONLY|0||
|ICON_WITH_SEARCH|1||
|LIST_ONLY|2||
|LIST_WITH_SEARCH|3||
|KEYBOARD|4||

### Language

|Name|Value|Description|
|:---|:----|:----------|
|EN-US|0||
|ES-MX|1||
|FR-CA|2||
|DE-DE|3||
|ES-ES|4||
|EN-GB|5||
|RU-RU|6||
|TR-TR|7||
|PL-PL|8||
|FR-FR|9||
|IT-IT|10||
|SV-SE|11||
|PT-PT|12||
|NL-NL|13||
|EN-AU|14||
|ZH-CN|15||
|ZH-TW|16||
|JA-JP|17||
|AR-SA|18||
|KO-KR|19||
|PT-BR|20||
|CS-CZ|21||
|DA-DK|22||
|NO-NO|23||

### FileType

|Name|Value|Description|
|:---|:----|:----------|
|GRAPHIC_BMP|0||
|GRAPHIC_JPEG|1||
|GRAPHIC_PNG|2||
|AUDIO_WAVE|3||
|AUDIO_MP3|4||
|AUDIO_AAC|5||
|BINARY|6||
|JSON|7||

### AudioType

|Name|Value|Description|
|:---|:----|:----------|
|PCM|0||

### TBTState

|Name|Value|Description|
|:---|:----|:----------|
|ROUTE_UPDATE_REQUEST|0||
|ROUTE_ACCEPTED|1||
|ROUTE_REFUSED|2||
|ROUTE_CANCELLED|3||
|ETA_REQUEST|4||
|NEXT_TURN_REQUEST|5||
|ROUTE_STATUS_REQUEST|6||
|ROUTE_SUMMARY_REQUEST|7||
|TRIP_STATUS_REQUEST|8||
|ROUTE_UPDATE_REQUEST_TIMEOUT|9||

### VehicleDataResultCode

|Name|Value|Description|
|:---|:----|:----------|
|SUCCESS|0||
|TRUNCATED_DATA|1||
|DISALLOWED|2||
|USER_DISALLOWED|3||
|INVALID_ID|4||
|VEHICLE_DATA_NOT_AVAILABLE|5||
|DATA_ALREADY_SUBSCRIBED|6||
|DATA_NOT_SUBSCRIBED|7||
|IGNORED|8||

### DisplayType

|Name|Value|Description|
|:---|:----|:----------|
|CID|0||
|TYPE2|1||
|TYPE5|2||
|NGN|3||
|GEN2_8_DMA|4||
|GEN2_6_DMA|5||
|MFD3|6||
|MFD4|7||
|MFD5|8||
|GEN3_8_INCH|9||

### ApplicationToNONEReason

|Name|Value|Description|
|:---|:----|:----------|
|DRIVER_DISTRACTION_VIOLATION|0||
|USER_EXIT|1||

### IgnitionStatus

|Name|Value|Description|
|:---|:----|:----------|
|UNKNOWN|0||
|OFF|1||
|ACCESSORY|2||
|RUN|3||
|START|4||
|INVALID|5||

### EmergencyEventType

|Name|Value|Description|
|:---|:----|:----------|
|NO_EVENT|0||
|FRONTAL|1||
|SIDE|2||
|REAR|3||
|ROLLOVER|4||
|NOT_SUPPORTED|5||
|FAULT|6||

### HMILevel

|Name|Value|Description|
|:---|:----|:----------|
|FULL|0||
|LIMITED|1||
|BACKGROUND|2||
|NONE|3||

### AppPriority

|Name|Value|Description|
|:---|:----|:----------|
|EMERGENCY|0||
|NAVIGATION|1||
|VOICE_COMMUNICATION|2||
|COMMUNICATION|3||
|NORMAL|4||
|NONE|5||

### PowerModeQualificationStatus

|Name|Value|Description|
|:---|:----|:----------|
|POWER_MODE_UNDEFINED|0||
|POWER_MODE_EVALUATION_IN_PROGRESS|1||
|NOT_DEFINED|2||
|POWER_MODE_OK|3||

### ApplicationsCloseReason

|Name|Value|Description|
|:---|:----|:----------|
|IGNITION_OFF|0||
|MASTER_RESET|1||
|FACTORY_DEFAULTS|2||
|SUSPEND|3||

### Dimension

|Name|Value|Description|
|:---|:----|:----------|
|NO_FIX|0||
|2D|1||
|3D|2||

### ImageType

|Name|Value|Description|
|:---|:----|:----------|
|STATIC|0||
|DYNAMIC|1||

### IgnitionStableStatus

|Name|Value|Description|
|:---|:----|:----------|
|IGNITION_SWITCH_NOT_STABLE|0||
|IGNITION_SWITCH_STABLE|1||
|MISSING_FROM_TRANSMITTER|2||

### WarningLightStatus

|Name|Value|Description|
|:---|:----|:----------|
|OFF|0||
|ON|1||
|FLASH|2||
|NOT_USED|3||

### VehicleDataNotificationStatus

|Name|Value|Description|
|:---|:----|:----------|
|NOT_SUPPORTED|0||
|NORMAL|1||
|ACTIVE|2||
|NOT_USED|3||

### SystemError

|Name|Value|Description|
|:---|:----|:----------|
|SYNC_REBOOTED|0||
|SYNC_OUT_OF_MEMMORY|1||

### PowerModeStatus

|Name|Value|Description|
|:---|:----|:----------|
|KEY_OUT|0||
|KEY_RECENTLY_OUT|1||
|KEY_APPROVED_0|2||
|POST_ACCESORY_0|3||
|ACCESORY_1|4||
|POST_IGNITION_1|5||
|IGNITION_ON_2|6||
|RUNNING_2|7||
|CRANK_3|8||

### ComponentVolumeStatus

|Name|Value|Description|
|:---|:----|:----------|
|UNKNOWN|0||
|NORMAL|1||
|LOW|2||
|FAULT|3||
|ALERT|4||
|NOT_SUPPORTED|5||

### PrimaryAudioSource

|Name|Value|Description|
|:---|:----|:----------|
|NO_SOURCE_SELECTED|0||
|USB|1||
|USB2|2||
|BLUETOOTH_STEREO_BTST|3||
|LINE_IN|4||
|IPOD|5||
|MOBILE_APP|6||

### RequestType

|Name|Value|Description|
|:---|:----|:----------|
|HTTP|0||
|FILE_RESUME|1||
|AUTH_REQUEST|2||
|AUTH_CHALLENGE|3||
|AUTH_ACK|4||
|PROPRIETARY|5||
|QUERY_APPS|6||
|LAUNCH_APP|7||
|LOCK_SCREEN_ICON_URL|8||
|TRAFFIC_MESSAGE_CHANNEL|9||
|DRIVER_PROFILE|10||
|VOICE_SEARCH|11||
|NAVIGATION|12||
|PHONE|13||
|CLIMATE|14||
|SETTINGS|15||
|VEHICLE_DIAGNOSTICS|16||
|EMERGENCY|17||
|MEDIA|18||
|FOTA|19||

### ConsentSource

|Name|Value|Description|
|:---|:----|:----------|
|GUI|0||
|VUI|1||

### CompassDirection

|Name|Value|Description|
|:---|:----|:----------|
|NORTH|0||
|NORTHWEST|1||
|WEST|2||
|SOUTHWEST|3||
|SOUTH|4||
|SOUTHEAST|5||
|EAST|6||
|NORTHEAST|7||

### BitsPerSample

|Name|Value|Description|
|:---|:----|:----------|
|8_BIT|0||
|16_BIT|1||

### EmergencyState

|Name|Value|Description|
|:---|:----|:----------|
|EMERGENCY_ON|0||
|EMERGENCY_OFF|1||

### Result

|Name|Value|Description|
|:---|:----|:----------|
|SUCCESS|0||
|UNSUPPORTED_REQUEST|1||
|UNSUPPORTED_RESOURCE|2||
|DISALLOWED|3||
|REJECTED|4||
|ABORTED|5||
|IGNORED|6||
|RETRY|7||
|IN_USE|8||
|DATA_NOT_AVAILABLE|9||
|TIMED_OUT|10||
|INVALID_DATA|11||
|CHAR_LIMIT_EXCEEDED|12||
|INVALID_ID|13||
|DUPLICATE_NAME|14||
|APPLICATION_NOT_REGISTERED|15||
|WRONG_LANGUAGE|16||
|OUT_OF_MEMORY|17||
|TOO_MANY_PENDING_REQUESTS|18||
|NO_APPS_REGISTERED|19||
|NO_DEVICES_CONNECTED|20||
|WARNINGS|21||
|GENERIC_ERROR|22||
|USER_DISALLOWED|23||
|TRUNCATED_DATA|24||

### CarModeStatus

|Name|Value|Description|
|:---|:----|:----------|
|NORMAL|0||
|FACTORY|1||
|TRANSPORT|2||
|CRASH|3||

### ImageFieldName

|Name|Value|Description|
|:---|:----|:----------|
|softButtonImage|0||
|choiceImage|1||
|choiceSecondaryImage|2||
|vrHelpItem|3||
|turnIcon|4||
|menuIcon|5||
|cmdIcon|6||
|appIcon|7||
|graphic|8||
|showConstantTBTIcon|9||
|showConstantTBTNextTurnIcon|10||
|locationImage|11||

### VehicleDataType

|Name|Value|Description|
|:---|:----|:----------|
|VEHICLEDATA_GPS|0||
|VEHICLEDATA_SPEED|1||
|VEHICLEDATA_RPM|2||
|VEHICLEDATA_FUELLEVEL|3||
|VEHICLEDATA_FUELLEVEL_STATE|4||
|VEHICLEDATA_FUELCONSUMPTION|5||
|VEHICLEDATA_EXTERNTEMP|6||
|VEHICLEDATA_VIN|7||
|VEHICLEDATA_PRNDL|8||
|VEHICLEDATA_TIREPRESSURE|9||
|VEHICLEDATA_ODOMETER|10||
|VEHICLEDATA_BELTSTATUS|11||
|VEHICLEDATA_BODYINFO|12||
|VEHICLEDATA_DEVICESTATUS|13||
|VEHICLEDATA_ECALLINFO|14||
|VEHICLEDATA_AIRBAGSTATUS|15||
|VEHICLEDATA_EMERGENCYEVENT|16||
|VEHICLEDATA_CLUSTERMODESTATUS|17||
|VEHICLEDATA_MYKEY|18||
|VEHICLEDATA_BRAKING|19||
|VEHICLEDATA_WIPERSTATUS|20||
|VEHICLEDATA_HEADLAMPSTATUS|21||
|VEHICLEDATA_BATTVOLTAGE|22||
|VEHICLEDATA_ENGINETORQUE|23||
|VEHICLEDATA_ACCPEDAL|24||
|VEHICLEDATA_STEERINGWHEEL|25||

### UpdateResult

|Name|Value|Description|
|:---|:----|:----------|
|UP_TO_DATE|0||
|UPDATING|1||
|UPDATE_NEEDED|2||

### PRNDL

|Name|Value|Description|
|:---|:----|:----------|
|PARK|0||
|REVERSE|1||
|NEUTRAL|2||
|DRIVE|3||
|SPORT|4||
|LOWGEAR|5||
|FIRST|6||
|SECOND|7||
|THIRD|8||
|FOURTH|9||
|FIFTH|10||
|SIXTH|11||
|SEVENTH|12||
|EIGHTH|13||
|FAULT|14||

### VehicleDataStatus

|Name|Value|Description|
|:---|:----|:----------|
|NO_DATA_EXISTS|0||
|OFF|1||
|ON|2||


## SDL’s  configuration file structure (ini-file)  
To configure some specific SDL rules or to define the filepathes and other SDL settings, smartDeviceLink.ini file is used. The file is divided into a sections, each section relates to the configuration of some functional area. Some of the settings have no reference to HMI behavior, anyway they are described for information purposes to understand particular properties.  

### HMI
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|ServerAddress|String|ServerAddress = 127.0.0.1|Address to connect HMI (web-socket only);See also WebSocket Transport| 
|ServerPort|Integer|ServerPort = 8087|ServerPort (web-socket only); See also WebSocket Transport|
|VideoStreamingPort|Integer|VideoStreamingPort = 5050|Port number for streaming video (in case of socket type); See also Configuring audio/video streaming parameters in smartDeviceLink.ini file|
|AudioStreamingPort|Integer|AudioStreamingPort = 5080|Port number for streaming audio (in case of socket type); See also Configuring audio/video streaming parameters in smartDeviceLink.ini file
|LaunchHMI|Boolean|LaunchHMI = false|Parameter defines whether SDL should wait for launching HMI; Open the $LinkToWebHMI in chromium browser|
|LinkToWebHMI|String|LinkToWebHMI = HMI//index.html|Link to index HMTL page|

### MAIN
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|SDLVersion|String|SDLVersion = {GIT_COMMIT}|SDL source version, represents as a git commit hash value|
|LogsEnabled|Boolean|LogsEnabled = true|SDL logging output enabled/disabled on system|
|AppConfigFolder|String|AppConfigFolder =|The path to application configuration folder where hmi_capabilities,smartDeviceLink.ini, log4cxx.properties are stored.Storage of Policy table files (preload, snapshot) is valid for OpenSource only. The default value is current working directory|
|AppStorageFolder|String|AppStorageFolder = /fs/rwdata/storage/sdl|The root folder for storing all applications folder|
|AppResourceFolder|String|AppResourceFolder =audio8bit.wav|Contains resourses. Default value is SDL working directory|
|ThreadStackSize|Integer|ThreadStackSize = 20480|ThreadStackSize used by SDL only if its required by sytem/platform, wisean empty value is defined or no such parameter exists, stack size will be PTHREAD`_`STACK_MIN(only SDL’s configurable value), which for<br>Ubuntu:<br>THREAD_STACK_MIN = 16384<br>QNX:<br>PTHREAD_STACK_MIN = 256
|MixingAudioSupported|Boolean|MixingAudioSupported = true|Defines if HMI support attenuated mode (able to mix audio sources)|
|HMICapabilities|String|HMICapabilities = hmi_capabilities.json|The filepath to the file of default HMICapabilities. In case HMI doesn’t send some capabilities to SDL, the values from the file are used by SDL|
|MaxCmdID|Int64|MaxCmdID = 2000000000|Maximum cmdId of VR command which may be registered on SDL|
|DefaultTimeout|Integer|DefaultTimeout = 10000|The response must be send to mobile application (SDL must respond after this timeout if HMI  haven’t respond to a request)|
|AppDirectoryQuota|Int64|AppDirectoryQuota = 104857600|Definines folder size in bytes limitation for any application on SDL|
|AppHMILevelNoneTimeScaleMaxRequests|Integer|AppHMILevelNoneTimeScaleMaxRequests = 100|Number of the requests allowed for the application in NONE HMI Level. If exceeded, the application will be unregistered|
|AppHMILevelNoneRequestsTimeScale|Integer|AppHMILevelNoneRequestsTimeScale = 10|Time period in which AppHMILevelNoneTimeScaleMaxRequests requests number allowed for the application in NONE HMI Level. If exceeded, the application will be unregistered|
|AppTimeScaleMaxRequests|Integer|AppTimeScaleMaxRequests = 1000|Number of the requests allowed for the application in any HMI Level except of NONE. If exceeded, the application will be unregistered|
|AppRequestsTimeScale|Integer|AppRequestsTimeScale = 10|Time period in which AppTimeScaleMaxRequests  requests number allowed for the application in any HMI Level except of NONE. If exceeded, the application will be unregistered|
|PendingRequestsAmount|Integer|PendingRequestsAmount = 5000|Number of the SDL pending requests allowed for an application. If exceeded, the application will be unregistered. If the value is “0”, the check will be skipped|
|HeartBeatTimeout|Integer|HeartBeatTimeout = 7000|Heart beat timeout used for protocol v3. Timeout must be specified in milliseconds. If timeout is 0 heart beat between Mobile device and SDL will be disabled|
|SupportedDiagModes|String Array=true|SupportedDiagModes = <br>0x01, 0x02, 0x03,<br>0x05, 0x06, 0x07,<br>0x09, 0x0A, 0x18,<br>0x19, 0x22, 0x3E|The list of diagnostic modes supported on a vehicle. Only only the stated values are allowed by SDL in terms of DiagnosticMessage RPC, others are rejected|
|SystemFilesPath|String|SystemFilesPath = /fs/images/ivsu`_`cache|The path to the system file directory for interoperation between SDL and System (e.g. IVSU files and others). If parameter is empty, SDL uses /tmp/fs/mp/images/ivsu_cache by default|
|UseLastState|Boolean|UseLastState = true|To restore the last TCP/IP transport state (name, applications or channels) on SDL on a new device connection and on disconnect|
|TimeTestingPort|Integer|TimeTestingPort = 8090|Port to obtain the performance information about   messages processing  on different component levels. Enabled if SDL built with TIME_TESTER flag|
|ReadDIDRequest|Integer,Array[2]=true|ReadDIDRequest = 5, 1|Limitation for a number of ReadDID requests (the 1st value) per seconds (the 2nd value)|
|GetVehicleDataRequest|Integer, Array[2]=true|GetVehicleDataRequest = 5, 1|Limitation for a number of GetVehicleData requests (the 1st value) per seconds (the 2nd value)|

### MEDIA MANAGER
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|StartStreamRetry|Integer, Array[2]=true|StartStreamRetry = 3, 1000|Where the 1st one of the values is a number of retries and the 2nd number is a timeout in seconds for request frequency|
|EnableRedecoding|Boolean|EnableRedecoding = false|If decoding on HMI is required?APTHR|
|VideoStreamConsumer|String|VideoStreamConsumer = socket|Pipe/file or socket type of data streaming|
|AudioStreamConsumer|String|AudioStreamConsumer = socket|Pipe/file or socket type of data streaming
|NamedVideoPipePath|String|NamedVideoPipePath = video`_`stream`_`pipe|Named pipe will be defined as:<br>1.	`<fileName>` file in AppStorageFolder if the format of the parameter matchs the template: NamedVideoPipePath = `<fileName>`<br>2.	`<fileName>` file in `<path>` folder if the format of the parameter matchs the template: NamedVideoPipePath =`<path/fileName>`<br>3.	“video`_`stream`_`pipe” file in AppStorageFolder if NamedVideoPipePath has  an empty value<br>4.	“video`_`stream`_`pipe” file in AppStorageFolder if SDL has no permissions to write to `<path/fileName>` defined in NamedVideoPipePath|
|NamedAudioPipePath|String|NamedAudioPipePath = audio`_`stream`_`pipe|Named pipe will be defined as:<br>1.	`<fileName>` file in AppStorageFolder if the format of the parameter matchs the template: NamedAudioPipePath = `<fileName>`<br>2.	`<fileName>` file in `<path>` folder if the format of the parameter matchs the template: NamedAudioPipePath =`<path/fileName>`<br>3.	“audio`_`stream_pipe” file in AppStorageFolder if NamedAudioPipePath has  an empty value<br>4. “audio`_`stream_pipe” file in AppStorageFolder if SDL has no permissions to write to `<path/fileName>` defined in NamedAudioPipePath|
|VideoStreamFile|String|VideoStreamFile = video`_`stream`_`file|File path will be constructed using AppStorageFolder + VideoStreamFile|
|AudioStreamFile|String|AudioStreamFile = audio`_`stream`_`file|File path will be constructed using AppStorageFolder + name|
|RecordingFileSource|String|RecordingFileSource = audio.8bit.wav|The "RecordingFileSource" parameter defines the recording file source which used for emulation PerformAudioPassThru|	
|RecordingFileName|String|RecordingFileName = audio.wav|The "RecordingFileName" parameter defines the name and format of audio file for PerformAudioPassThru_request|	
|StopStreamingTimeout|Integer|StopStreamingTimeout = 1000|The timeout in milliseconds for mobile to stop streaming or end up session|
|AudioDataStoppedTimeout|Integer|AudioDataStoppedTimeout = 1000|Defines time in milliseconds for SDL to wait for the next package of raw data over audio service|
|VideoDataStoppedTimeout|Integer|VideoDataStoppedTimeout = 1000	|Defines time in milliseconds for SDL to wait for the next package of raw data over video service| 

### GLOBAL PROPERTIES
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|TTSDelimiter|Char|TTSDelimiter = ,|Defines the delimiter, which will be appended to each TTS chunck, e.g. helpPrompt/timeoutPrompt|
|HelpPrompt|String|HelpPrompt = Please speak one of the following commands,Please say a command|Default prompt items, separated by comma. The value is set up in case ResetGlobalProperties request from the application or SDL (in case of TTSGlobalPropertiesTimeout)|
|TimeoutPrompt|String|TimeoutPrompt = Please speak one of the following commands,<br>Please say a command|Default prompt to be spoken by VR-engine timeout (when system expects some action by user and the time for this action is going to be out)|
|HelpTitle|String|HelpTitle = Available Vr Commands List|Text to be set-up for default value of the title of help list
|TTSGlobalPropertiesTimeout|Integer|TTSGlobalPropertiesTimeout = 20|In case mobile app didn't send global properties request, then default global properties will be sent defined timeout in seconds<br>Max value<br>TTSGlobalPropertiesTimeout 64K

### FILESYSTEM RESTRICTIONS
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|PutFileRequest|Integer|PutFileRequest = 5|Max allowed number of PutFile requests for one application in NONE. The application will be unregistered in case the number of requests exceeded the limitation|
|DeleteFileRequest|Integer|DeleteFileRequest = 5|Max allowed number of DeleteFile requests for one application in NONE. The application will be unregistered in case the number of requests exceeded the limitation| 
|ListFilesRequest|Integer|ListFilesRequest = 5|Max allowed number of ListFiles requests for one application in NONE. The application will be unregistered in case the number of requests exceeded the limitation|

### VR COMMANDS
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|HelpCommand|String|HelpCommand = Help|Default command which initiates VR Help of the application|

###  AppInfo
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|AppInfoStorage|String|AppInfoStorage = app_info.dat|The path for applications information storage (for resumption purposes)|

### Security Manager
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|Protocol|String|Protocol = TLSv1.2|Supported protocol version|
|KeyPath|String|KeyPath = mykey.pem|Certificate and key path to pem file|
|CertificatePath|String|CertificatePath = mycert.pem|Certificate and key path to pem file|
|SSLMode|String|SSLMode = CLIENT|SSL mode could be SERVER or CLIENT|
|CipherList|String|CipherList = ALL|Could be “ALL” ciphers or a list of chosen|
|VerifyPeer|Boolean|VerifyPeer  = true|Defines if Mobile app certificate must be verified or not(could be used in both SSLMode Server and Client)|
|CACertificatePath|String|CACertificatePath = .|Preloaded CA certificates directory|
|ForceProtectedService|String|ForceProtectedService = Non|Force protected services (could be id's from 0x01 to 0xFF or “Non” value)|
|ForceUnprotectedService|String|ForceUnprotectedService = Non|Force unprotected services (could be id's from 0x01 to 0xFF or “Non” value)
|UpdateBeforeHours|Integer|UpdateBeforeHours = 24|The "UpdateBeforeHours" parameter defines the amount of time in hours for certificate expiration AND after expiration PTU sequence will be triggered|

### Policy
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|EnablePolicy|Boolean|EnablePolicy = true|Turn on/off policies|
|PreloadedPT|String|PreloadedPT = sdl`_`preloaded`_`pt.json|The filename of the preloaded policy table|
|PathToSnapshot|String|PathToSnapshot = sdl_snapshot.json|The filename of  the policy table snapshot|
|AttemptsToOpenPolicyDB|Integer|AttemptsToOpenPolicyDB = 5|Number of attempts to open policy DB|
|OpenAttemptTimeoutMs|Integer|OpenAttemptTimeoutMs = 500|Timeout between attempts during opening DB in milliseconds|

### TransportManager
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|TCPAdapterPort|Integer|TCPAdapterPort = 12345|Listening port form incoming mobile connection|

### ProtocolHandler
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|MaximumPayloadSize|Integer|MaximumPayloadSize = 1488|Packet with a payload bigger than # MaximumPayloadSize will be marked as a malformed. Parameter must be used for protocol v3 or higher.<br>1)In case of emty value,SDL uses the default value of 1488 bytes for validating MTU (maximum transferring unit) size.<br>2) If the value defined in MaximumPayloadSize parameter is less than 1488,the default value of 1488 bytes must be used by SDL.|
|FrequencyCount|Integer|FrequencyCount = 1000|Application shall send not more than<br>#FrequencyCount messages per #FrequencyTime mSecs<br>Frequency check could be disabled by setting #FrequencyTime or #FrequencyCount to “0”|
|FrequencyTime|Integer|FrequencyTime = 1000|The limitation in ms for sending number of the requests not more than #FrequencyCount|
|MalformedMessageFiltering|Integer|MalformedMessageFiltering = true|Enable filtering transport data stream;<br>On #MalformedMessageFiltering disabling, SDL will close the connection with the first malformed message detection|
|MalformedFrequencyCount|Integer|MalformedFrequencyCount = 10|Boundary value of malformed message detection for connection closure<br>Can be disabled by setting<br>#MalformedFrequencyTime or<br>#MalformedFrequencyCount to “0”
|MalformedFrequencyTime|Integer|MalformedFrequencyTime = 1000|Boundary value of malformed message detection for connection closure. In case the frequency of mailformed requests will be more than per#MalformedFrequencyTime, SDL will close the connection
|ExpectedConsecutiveFramesTimeout|Integer|ExpectedConsecutiveFramesTimeout = 10000|Timeout for waiting CONSECUTIVE frames of multiframe|


### ApplicationManager
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|ApplicationListUpdateTimeout|Integer|ApplicationListUpdateTimeout = 2000|Application list update timeout ms|
|ThreadPoolSize|Integer|ThreadPoolSize = 1|Max allowed threads for handling mobile requests. Currently max allowed is 2|
|HashStringSize|Integer|HashStringSize = 32|The max size of hash which is used by OnHashUpdated()|

### SDL4
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|EnableProtocol4|Boolean|EnableProtocol4 = true|Enables SDL 4.0 support. Parameter allows to switch SDL4 functionality on SDL|
|AppIconsFolder|String|AppIconsFolder = storage|The path where apps’ icons must be stored. Upon each start SDL  must check whether the folder ‘AppIconsFolder’ exists and read/write permissions.<br>In case folder doesn’t exist, SDL creates it and uses it as assigned|
|AppIconsFolderMaxSize|Integer|AppIconsFolderMaxSize = 104857600|Max size of the folder in bytes. Parameter defines the allowed size in bytes of the folder for SDL to store the applications icons.|
|AppIconsAmountToRemove|Integer|AppIconsAmountToRemove = 1|Amount of the oldest icons to remove from "AppIconsFolder" in case of max folder size was reached.<br>In case the value ‘AppIconsAmountToRemove’ is equal zero SDL internally logs error and  continues working without storing the icon.| 

### Resumption
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|ApplicationResumingTimeout|Integer|ApplicationResumingTimeout = 3000|# Timeout in milliseconds for resumption Application HMILevel and resolving conflicts in case if multiple applications initiate resumption|
|AppSavePersistentDataTimeout|Integer|AppSavePersistentDataTimeout = 10000|Timeout in milliseconds for pereodical saving resumption persisten data|
|ResumptionDelayBeforeIgn|Integer|ResumptionDelayBeforeIgn = 30|Timeout in seconds to store hmi`_`level for media app before ign_off|
|ResumptionDelayAfterIgn|Integer|ResumptionDelayAfterIgn = 30|Timeout in seconds to restore hmi_level for media app after sdl run|
|UseDBForResumption|Boolean|UseDBForResumption = false|Resumption ctrl uses JSON if UseDBForResumption=false for store data otherwise uses DB|
|AttemptsToOpenResumptionDB|Integer|AttemptsToOpenResumptionDB = 5|Number of attempts to open resumption DB|
|OpenAttemptTimeoutMsResumptionDB|Integer|OpenAttemptTimeoutMsResumptionDB = 500|Timeout between attempts during opening DB in milliseconds|

### AppLaunch
|Parameter|Type|Example|Description|
|:---|:----|:----|:----------|
|AppLaunchWaitTime|Integer|AppLaunchWaitTime = 5000|Time in milliseconds started from device connection - after expiring SDL remotely launches all known not-yet-registered apps from this device|
|AppLaunchMaxRetryAttempt|Integer|AppLaunchMaxRetryAttempt = 3|The number of times SDL attempts to launch an application after device connection - applied separately to each application from the given device|
|AppLaunchRetryWaitTime|Integer|AppLaunchRetryWaitTime = 15000|Time in milliseconds started by SDL after app launch request. if expired and app did not register, SDL sends new launch request. applied separately|
|RemoveBundleIDattempts|Integer|RemoveBundleIDattempts = 3|The number of the given device connections that the requested application failed to register after SDL's launch attempts - SDL removes app's bundleID|
|MaxNumberOfiOSDevice|Integer|MaxNumberOfiOSDevice = 10|The maximum number of iOS devices for which entries can be remembered by SDL|
|WaitTimeBetweenApps|Integer|WaitTimeBetweenApps = 4000|Time in milliseconds started after request to launch the first app. after either expires or the first app registers SDL requests to launch|
|EnableAppLaunchIOS|Boolean|EnableAppLaunchIOS = true|App Launch on iOS devices SDL feature enabler/disabler
