## Table of contents

 #### 1. BasicCommunication
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
|||
Activate App after successful Resumption
![Activate App Successful Resume](./assets/ActivateAppSuccessfulResume.png)
|||
|||
Activate App after failed Resumption
![Activate App Failed Resume](./assets/ActivateAppFailedResume.png)
|||
|||
Activate App after Unexpected Disconnect
![Activate App Unexpected Disconnect](./assets/ActivateAppUnexpectedDisconnect.png)
|||
|||
Activate App after Accepted Data Consent Prompt
![Activate App Successful Data](./assets/ActivateAppSuccessfulData.png)
|||
|||
Activate App after Failed Data Consent Prompt
![Activate App Failed Data](./assets/ActivateAppFailedData.png)
|||
