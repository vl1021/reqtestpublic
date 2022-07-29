Models (Bulk Data API)

Software Architecture Space

Exported on Jul 29, 2022

# BulkDataSourceStream

This describes the source (platform + app) of the bulk data stream.
These values are assigned by the server team.

## Enum BulkDataSourceStream, iOS:

| Enum case    | String Value (internal) | Description                       |
|--------------|-------------------------|-----------------------------------|
| g6commercial | Phone7                  | iOS G6 Commercial (AKA Gemeni)    |
| g6DexcomOne  | Phone15                 | iOS G6 Dexcom One                 |
| g7Commercial | Phone17                 | iOS G7 Application                |
| frontier     | Phone19                 | iOS Frontier (Type 2) Application |
| g7Watch      | watch1                  | iOS G7 Apple Watch App            |

## EnumBulkDataSourceStream, Android:

| Enum case    | String Value (internal) | Description                           |
|--------------|-------------------------|---------------------------------------|
| g6commercial | Phone8                  | Android G6 Commercial                 |
| g6DexcomOne  | Phone16                 | Android G6 Dexcom One                 |
| g7Commercial | Phone18                 | Android G7 Application                |
| frontier     | Phone20                 | Android Frontier (Type 2) Application |

# BulkDataAlertEvent

This record captures when an alert happens on the patient\'s device. The
goal of this event is to notify the follower that an alert was displayed
on a patient\'s device, and to also notify them when it has been
acknowledged by the user.

## Record Properties

| Property Name | Type                | Description                                                                                           | Optional |
|---------------|---------------------|-------------------------------------------------------------------------------------------------------|----------|
| timestamp     | (Platform) Date     | The date and time this record was created.                                                            | N        |
| alertID       | UUID                | UUID for this alert                                                                                   | N        |
| alertName     | **AlertName** enum  | The name of the alert being shown to the patient.                                                     | N        |
| alertState    | **AlertState** enum | An enum that describes the state of the alert (e.g., is it a new alert, or has it been acknowledged?) | N        |

## AlertName enum

The name of the alert being shown to the patient.

### Glucose Alerts/Notifications

| Enum Case     | String Value (internal) | Description                                                                                                                                                                                                                                                                                    |
|---------------|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| falling       | Fall                    | The rate the user\'s glucose is falling faster than a specified level.                                                                                                                                                                                                                         |
| high          | High                    | The glucose level is above a specified level.                                                                                                                                                                                                                                                  |
| low           | Low                     | The glucose level is below a specified level.                                                                                                                                                                                                                                                  |
| outOfRange    | OutOfRange              | The user\'s display device is out of range of the transmitter for a defined period of time.                                                                                                                                                                                                    |
| rising        | Rise                    | The rate the user\'s glucose is rising faster than a specified level.                                                                                                                                                                                                                          |
| fixedLow      | FixedLow                | The glucose level is below a fixed level (55 mg/dL)                                                                                                                                                                                                                                            |
| urgentLowSoon | UrgentLowSoon           | The system is predicting the user will be below a fixed level in the near future (currently the G6 algorithm predicts 20 minutes into the future). This value is always 55 mg/dL                                                                                                               |
| noReadings    | NoReadings              | This alert notifies the user that the display device has connected to the transmitter successfully, however, that display device was unable to pull data from the transmitter. (In G6, this is displayed after 20 minutes of successfully connecting to the transmitter, but not reading data) |
| defaultCase   | Default                 | Default value when an alert value is unknown                                                                                                                                                                                                                                                   |
| noData        | NoData                  | Notification to Follower when the Sharer hasn\'t shared data within a time allotted                                                                                                                                                                                                            |

### Fixed Alerts

| Enum case                     | String Value (internal/server) | Description                                                                                                                                                                    |
|-------------------------------|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lowWedge                      | LowWedge                       | The user entered a BG that was greater than the HighWedge bound sent by the transmitter within the last 5.5 minutes                                                            |
| highWedge                     | HighWedge                      | The user entered a BG that was less than the LowWedge bound sent by the transmitter within the last 5.5 minutes                                                                |
| twoStartupCalibrations        | TwoStartupCalibrations         | The system requires two calibrations to begin reporting EGVs at the start of a sensor session                                                                                  |
| secondStartupCalibration      | SecondStartupCalibration       | The system has received one of the two required calibrations, and needs the second calibration to begin reporting EGVs                                                         |
| failedSensor                  | FailedSensor                   | The user\'s sensor has determined to be failed                                                                                                                                 |
| lowTransmitterBattery         | LowTransmitterBattery          | The transmitter\'s battery is critically low                                                                                                                                   |
| sensorExpiration24Hr          | SensorExpiration24Hr           | The user\'s sensor session will expire in 24 hours                                                                                                                             |
| sensorExpiration6Hr           | SensorExpiration6Hr            | The user\'s sensor session will expire in 6 hours                                                                                                                              |
| sensorExpiration2Hr           | SensorExpiration2Hr            | The user\'s sensor session will expire in 2 hours                                                                                                                              |
| sensorExpiration30Min         | SensorExpiration30Min          | The user\'s sensor session will expire in 30 minutes                                                                                                                           |
| sensorExpiration0Min          | SensorExpiration0Min           | The user\'s sensor session has just expired                                                                                                                                    |
| calibrationRequired           | CalibrationRequired            | The system is requiring the user to enter a calibration to continue to get estimated glucose values. (This is different than a calibration requested)                          |
| transmitterError              | TransmitterError               | The user\'s transmitter is not working                                                                                                                                         |
| calibrationRequested          | CalibrationRequested           | The system is requesting that the user calibrate their receiver                                                                                                                |
| longActingDoseReminder1       | LongActingDoseReminder1        | The user is being prompted to take their first insulin dose of the day                                                                                                         |
| longActingDoseReminder2       | LongActingDoseReminder2        | The user is being prompted to take their second insulin dose of the day                                                                                                        |
| transmitterEOL3Weeks          | TransmitterEOL3Weeks           | The transmitter\'s battery is getting low; transmitter is expected to last about 3 more weeks                                                                                  |
| transmitterEOL2Weeks          | TransmitterEOL2Weeks           | The transmitter\'s battery is getting low; transmitter is expected to last about 2 more weeks                                                                                  |
| transmitterEOLLastSession     | TransmitterEOLLastSession      | The transmitter\'s battery is very low; This is the last sensor session the transmitter will work with                                                                         |
| transmitterEOLReplace         | TransmitterEOLReplace          | The transmitter\'s battery is critically low. The transmitter needs to be replaced.                                                                                            |
| sensorNoise                   | SensorNoise                    | The sensor has picked up noise                                                                                                                                                 |
| noBluetooth                   | NoBluetooth                    | The user has disabled bluetooth on their smart device                                                                                                                          |
| locationServicesOff           | LocationServicesOff            | The user disabled location services on their Android phone. Location services must be enabled to pair with a transmitter.                                                      |
| transmitterNotFound           | TransmitterNotFound            | The transmitter entered by the patient cannot be contacted for initial pairing                                                                                                 |
| diskSpaceOk                   | DiskSpaceOk                    | The user has enough disk space for the application to work normally. (This is not currently used)                                                                              |
| diskSpaceLow                  | DiskSpaceLow                   | The user\'s smart device is low on disk space. The user is alerted of this state (\<250MB as of G5) to let the user proactively free up space                                  |
| diskSpaceVeryLow              | DiskSpaceVeryLow               | The user\'s smart device is very low on disk space. The user is alerted of this state (\<100MB as of G5) to let the user proactively free up space                             |
| diskSpaceCritical             | DiskSpaceCritical              | The user\'s smart device is very, very low on available space. The user is alerted of this state (\<20MB), and the app is likely not working, as it cannot store any more data |
| pairingRequest                | PairingRequest                 | The user\'s phone has discovered the new transmitter, and is requesting to bluetooth pair with the transmitter                                                                 |
| terminatedAlert               | TerminatedAlert                | The Dexcom application has stopped running on the user\'s smart device.                                                                                                        |
| recoverableSQLError           | RecoverableSQLError            | The app has failed in such a way that it can recover from the error, however, the phone needs to be restarted                                                                  |
| unrecoverableSQLError         | UnrecoverableSQLError          | The app has stopped working due to a database issue. The only way to fix this is to uninstall the app and reinstall.                                                           |
| transmitterCompatibility      | TransmitterCompatibility       | The transmitter is not compatible with the phone/receiver. (Currently, only exists on Android)                                                                                 |
| coarseLocationOff             | CoarseLocationOff              | The app is unable to access the coarse location on the phone. This is required to be able to enable Bluetooth on Android Devices.                                              |
| sensorFailedDueToRestart      | SensorFailedDueToRestart       | The user attempted to start a new sensor session using the same sensor used in the previous session.                                                                           |
| transmitterPaired             | TransmitterPaired              | The user successfully paired the transmitter.                                                                                                                                  |
| alertSettingsReset            | AlertSettingsReset             | The user\'s alert settings were reset to default values                                                                                                                        |
| technicalAlert                | TechnicalAlert                 | Alerts that are informative to the behavior of the system, but are not directly related to the user\'s glucose value.                                                          |
| warmUpComplete                | WarmUpComplete                 | The user has completed warmup and is now receiving glucose values.                                                                                                             |
| gracePeriod2HourExpiration    | GracePeriod2HourExpiration     | There are 2 hours left on the 12-hour grace period.                                                                                                                            |
| gracePeriod30MinuteExpiration | GracePeriod30MinuteExpiration  | There are 30 minutes left on the 12-hour grace period.                                                                                                                         |
| gracePeriodExpired            | GracePeriodExpired             | The 12-hour grace period has expired.                                                                                                                                          |
| calibrationNotUsed            | CalibrationNotUsed             | The requested calibration value was not used by the transmitter.                                                                                                               |
| timeLoss                      | TimeLoss                       | The user has entered into a time uncertainty state.                                                                                                                            |
| unrecoverableDatabase         | UnrecoverableDatabase          | An unrecoverable database error has occurred.                                                                                                                                  |
| pairingTakingTooLong          | PairingTakingTooLong           | Pairing has taken more than 10 minutes.                                                                                                                                        |
| transmitterAlreadyPaired      | TransmitterAlreadyPaired       | This transmitter has already been paired.                                                                                                                                      |
| appTerminated                 | AppTerminated                  | The application was terminated.                                                                                                                                                |

### Push Notifications

| Enum case                   | String Value (internal)     | Description                                                  |
|-----------------------------|-----------------------------|--------------------------------------------------------------|
| optedOutDataSharingDisabled | OptedOutDataSharingDisabled | The user has opted out from sharing their data to the cloud. |

## AlertState enum

The state of the alert (is it a new alert, or has it been acknowledged)

| Value          | String Value (internal) | Description                                                                                                        |
|----------------|-------------------------|--------------------------------------------------------------------------------------------------------------------|
| activeAlarming | ActiveAlarming          | The alert is actively being shown to the user and requires user action.                                            |
| activeSnoozed  | ActiveSnoozed           | The user has snoozed the alert. The user has acknowledged the alert.                                               |
| inactive       | Inactive                | The alert is no longer being shown to the user. The alert has been cleared by the device or confirmed by the user. |
| unknown        | Unknown                 | The alert state is not known.                                                                                      |

BulkDataAlertSchedule

This record describes the patient\'s alert schedule.

## Record Properties

| Property Name     | Type                           | Description                                                                       | Optional? |
|-------------------|--------------------------------|-----------------------------------------------------------------------------------|-----------|
| timestamp         | (Platform) Date                | Current time when this record was created.                                        | N         |
| alertScheduleList | Array of **AlertScheduleItem** | An array that contains all of the AlertScheduleItem\'s that apply to this record. | N         |

## AlertScheduleItem

An individual Bulk Data Alert Schedule Item containing the schedule
settings and alert settings list.

| Property Name         | Type                              | Description                                                         | Optional? |
|-----------------------|-----------------------------------|---------------------------------------------------------------------|-----------|
| alertScheduleSettings | Array of **AlertScheduleSetting** | The information about what times and day the alert values apply to  | N         |
| alertSettings         | Array of **AlertSetting**         | A list of AlertSetting items that define the alerts and its values. | N         |

## AlertScheduleSetting

An individual Alert Schedule Setting for the specified alert schedule.

| Property Name     | Type                  | Description                                                                                                                                                                                                                                      | Optional? |
|-------------------|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| alertScheduleName | String                | The name of the AlertSchedule.                                                                                                                                                                                                                   | N         |
| isEnabled         | Bool                  | Set to **true** if the user has enabled the alert schedule setting on their display device and false otherwise.                                                                                                                                  | N         |
| shouldAlwaysSound | Bool                  | Set to **true** if the user has enabled the always sound feature (the mute switch will be overridden)                                                                                                                                            | N         |
| startTime         | String                | A string in the format \"hh:mm\" representing the time of day that this alert schedule item starts (e.g., \"18:30\")                                                                                                                             | N         |
| endTime           | String                | A string in the format \"hh:mm\" representing the time of day that this alert schedule item ends (e.g., \"21:30\")                                                                                                                               | N         |
| daysOfWeek        | Array of String       | An array containing one (or more) of the following strings in English: \"Sunday\", \"Monday\", \"Tuesday\", \"Wednesday\", \"Thursday\", \"Friday\" or \"Saturday\", indicating the days of the week that this alert schedule setting is active. | N         |
| isDefaultSchedule | Bool                  | If set to true, then these alert schedule settings are used if no other alert schedule exists.                                                                                                                                                   | N         |
| isActive          | Bool                  | server key \"IsActive\"                                                                                                                                                                                                                          | Y         |
| override          | AlertOverrideSettings | server key \"Override\"                                                                                                                                                                                                                          | Y         |

## AlertOverrideSettings

| Property Name     | Type                       | Description                                                           | Optional? |
|-------------------|----------------------------|-----------------------------------------------------------------------|-----------|
| isOverrideEnabled | Bool                       | Is the alert override enabled. Server key \"IsOverrideEnabled\"       | N         |
| mode              | **AlertOverrideMode** enum | The mode of the alert override, quiet or vibrate. Server key \"Mode\" | N         |
| endTime           | (Platform) Date            | The time that the override settings will end. Server key \"EndTime\"  | Y         |

## AlertOverrideMode Enum

The mode of the alert override setting.

| Enum case | String Value (internal) | Description                                          |
|-----------|-------------------------|------------------------------------------------------|
| quiet     | Quiet                   | The override mode is set to silence for all alerts.  |
| vibrate   | Vibrate                 | The override mode is set to vibrate for all alerts.  |

## AlertSetting

This record describes the alert settings configured on the display
device.

<table style="width:100%;">
<colgroup>
<col style="width: 29%" />
<col style="width: 13%" />
<col style="width: 46%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Property Name</th>
<th>Type</th>
<th>Description</th>
<th>Optional?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>timestamp</td>
<td>(Platform) Date</td>
<td>The time the display device recorded this alert value being set.</td>
<td>N</td>
</tr>
<tr class="even">
<td>name</td>
<td><strong>AlertName</strong> enum</td>
<td>The name of the alert.</td>
<td>N</td>
</tr>
<tr class="odd">
<td>value</td>
<td>Int</td>
<td>The value the alert is set at. The units are based on the name of the alert (and are documented in there). NOTE: For "Rising Fast" and "Falling Fast", this is the threshold rate and not the value.</td>
<td>N</td>
</tr>
<tr class="even">
<td>delay</td>
<td>Int</td>
<td>An integer representing the time (in minutes) before alarming after the threshold (in the Value field) has been exceeded</td>
<td>N</td>
</tr>
<tr class="odd">
<td>snooze</td>
<td>Integer</td>
<td>An integer representing the time (in minutes) before resuming alarming after the alert has been acknowledged and cleared</td>
<td>N</td>
</tr>
<tr class="even">
<td>sound</td>
<td>String</td>
<td>The name of the sound being played (on the phone) or the user profile (on the receiver) when the user exceeds the limit.</td>
<td>N</td>
</tr>
<tr class="odd">
<td>isEnabled</td>
<td>Bool</td>
<td>Set to 'true' if this alert is enabled or 'false' if it is disabled</td>
<td>N</td>
</tr>
<tr class="even">
<td>version</td>
<td>String</td>
<td>Set to "1.1", server key "RecordVersion"</td>
<td>N</td>
</tr>
<tr class="odd">
<td>secondaryTriggerCondition</td>
<td>Integer</td>
<td><p>For "Rising Fast" and "Falling Fast", this is the mg/dl value that must be exceeded for the alert to be triggered.</p>
<p>Server key "SecondaryTriggerCondition"</p></td>
<td>Y</td>
</tr>
<tr class="even">
<td>soundTheme</td>
<td>String</td>
<td>The name of the theme this sound applies to. Server key "SoundTheme"</td>
<td>N</td>
</tr>
<tr class="odd">
<td>soundOutputMode</td>
<td>String</td>
<td>The sound output mode for this alert: "Sound", "Vibrate" or "Match". Server key "SoundOutputMode"</td>
<td>N</td>
</tr>
</tbody>
</table>

# BulkDataBGMeter

A blood glucose reading from the patient\'s device used for calibrating
the transmitter. Server record type is \"MeterRecord\". A version of
\"1.1\" will indicate the BGMeterEntryType has been expanded to include
G7-specific enum mapped values.

Server IDD: MeterRecord

## Record Properties

| Property Name   | Type                  | Description                                                                                              | Optional |
|-----------------|-----------------------|----------------------------------------------------------------------------------------------------------|----------|
| timestamp       | (Platform) Date       | The date and time this crash log record was created.                                                     | N        |
| meterSystemTime | (Platform) Date       | The approximate time that the meter value was used by the transmitter                                    | N        |
| transmitterID   | String                | The transmitter ID/serial number.                                                                        | Y        |
| transmitterTime | UInt                  | An unsigned integer value representing the number of seconds since the transmitter was first powered on. | Y        |
| value           | Int                   | The Calibration value entered by the user                                                                | Y        |
| entryType       | BGMeterEntryType enum | The type of BG entry this record represents.                                                             | Y        |
| recordVersion   | String                | Set to \"1.1\", server key \"RecordVersion\"                                                             | N        |

## BGMeterEntryType enum

This is the mapping from current app status or the the transmitter
calibration status response, to the enum cases below. Enum
Capitalization may be language/platform specific

| SDK                                                                |                                                                                                                                                  | Server Side                                                        |         |
|--------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|---------|
| SDK Enum case                                                      | SDK Description                                                                                                                                  | Server string value                                                | Notes   |
| UserEntered                                                        | A meter value was entered by the user, but has not been sent to the transmitter yet                                                              | UserEntered                                                        | G6 & G7 |
| CommandCancelled                                                   | A meter value that was previously entered by the user, but will not be sent to the transmitter to use as part of the algorithm                   | CommandCancelled                                                   | G6 & G7 |
| SentToTransmitterCalibrationSuccess                                | The meter value was sent to the transmitter, and accepted by the algorithm                                                                       | SentToTransmitterCalibrationSuccess                                | G6      |
| SentToTransmitterCalibrationError0                                 | Internal Error, meter value rejected by transmitter                                                                                              | SentToTransmitterCalibrationError0                                 | G6      |
| SentToTransmitterCalibrationError1                                 | Internal Error, meter value rejected by transmitter                                                                                              | SentToTransmitterCalibrationError1                                 | G6      |
| SentToTransmitterCalibrationLinearityFitFailure                    | Meter value was rejected by algorithm                                                                                                            | SentToTransmitterCalibrationLinearityFitFailure                    | G6      |
| SentToTransmitterOutlierCalibrationFailure                         | Sent to transmitter outlier calibration failure                                                                                                  | SentToTransmitterOutlierCalibrationFailure                         | G6      |
| SentToTransmitterBGOutsideOf40to400Fail                            | Sent to transmitter blood glucose outside of 40 to 400 fail                                                                                      | SentToTransmitterBGOutsideOf40to400Fail                            | G6      |
| SentToTransmitterSecondStartupBGRequired                           | First (of two) meter values was sent to the transmitter, and was accepted, but it needs a second meter value to be able to start displaying EGVs | SentToTransmitterSecondStartupBGRequired                           | G6      |
| SentToTransmitterSecondStartupBGRequired                           | Old G6 Value                                                                                                                                     | SentToTransmitterSecondStartupBGRequired                           | G6      |
| SentToTransmitterBGOutsideOf40to400Pass                            | Old G6 Value                                                                                                                                     | SentToTransmitterBGOutsideOf40to400Pass                            | G6      |
| SentToTransmitterOutlierCalibrationRequest                         | Old G6 Value                                                                                                                                     | SentToTransmitterOutlierCalibrationRequest                         | G6      |
| SentToTransmitterBGUnmatched                                       | Old G6 Value                                                                                                                                     | SentToTransmitterBGUnmatched                                       | G6      |
| SentToTransmitterBGOutsideOf20to600                                | Old G6 Value                                                                                                                                     | SentToTransmitterBGOutsideOf20to600                                | G6      |
| SentToTransmitterNotInSession                                      | Old G6 Value                                                                                                                                     | SentToTransmitterNotInSession                                      | G6      |
| SentToTransmitterBGTimestampInTheFuture                            | Old G6 Value                                                                                                                                     | SentToTransmitterBGTimestampInTheFuture                            | G6      |
| SentToTransmitterBGIsDuplicate                                     | Old G6 Value                                                                                                                                     | SentToTransmitterBGIsDuplicate                                     | G6      |
| SentToTransmitterBGTimestampTooEarly                               | Old G6 Value                                                                                                                                     | SentToTransmitterBGTimestampTooEarly                               | G6      |
| SentToTransmitterBGTimestampEarlierThanSessionStartCommandReceived | Old G6 Value                                                                                                                                     | SentToTransmitterBGTimestampEarlierThanSessionStartCommandReceived | G6      |
| SentToTransmitterBGNotInChronologicalOrder                         | Old G6 Value                                                                                                                                     | SentToTransmitterBGNotInChronologicalOrder                         | G6      |
| SentToTransmitterCalibrationAlreadyDoneWithOtherDevice             | Old G6 Value                                                                                                                                     | SentToTransmitterCalibrationAlreadyDoneWithOtherDevice             | G6      |
| FactoryCalibrated                                                  | Cal Status Primary=0 Secondary=0                                                                                                                 | FactoryCalibrated                                                  | G7      |
| BGAcceptedHighMatchLikelihood                                      | Cal Status Primary=1 Secondary=0                                                                                                                 | BGAcceptedHighMatchLikelihood                                      | G7      |
| BGAcceptedHighMatchWithCalibrationError0                           | Cal Status Primary=1 Secondary=1                                                                                                                 | BGAcceptedHighMatchWithCalibrationError0                           | G7      |
| BGAcceptedHighMatchWithCalibrationError1                           | Cal Status Primary=1 Secondary=2                                                                                                                 | BGAcceptedHighMatchWithCalibrationError1                           | G7      |
| BGAcceptedLowMatchLikelihood                                       | Cal Status Primary=2 Secondary=0                                                                                                                 | BGAcceptedLowMatchLikelihood                                       | G7      |
| BGAcceptedLowMatchWithCalibrationError0                            | Cal Status Primary=2 Secondary=1                                                                                                                 | BGAcceptedLowMatchWithCalibrationError0                            | G7      |
| BGAcceptedLowMatchWithCalibrationError1                            | Cal Status Primary=2 Secondary=2                                                                                                                 | BGAcceptedLowMatchWithCalibrationError1                            | G7      |
| BGRejectedUnspecified                                              | Cal Status Primary=3 Secondary=0                                                                                                                 | BGRejectedUnspecified                                              | G7      |
| BGRejectedOutsideAcceptableRange                                   | Cal Status Primary=3 Secondary=1                                                                                                                 | BGRejectedOutsideAcceptableRange                                   | G7      |
| [BGRejectedTimestampInTheFuture]{.ul}                              | Cal Status Primary=3 Secondary=2                                                                                                                 | [BGRejectedTimestampInTheFuture]{.ul}                              | G7      |
| [BGRejectedDuplicate]{.ul}                                         | Cal Status Primary=3 Secondary=3                                                                                                                 | [BGRejectedDuplicate]{.ul}                                         | G7      |
| [BGRejectedTimestampEarlierThanSessionStartTime]{.ul}              | Cal Status Primary=3 Secondary=4                                                                                                                 | [BGRejectedTimestampEarlierThanSessionStartTime]{.ul}              | G7      |
| [BGRejectedNotInChronologicalOrder]{.ul}                           | Cal Status Primary=3 Secondary=5                                                                                                                 | [BGRejectedNotInChronologicalOrder]{.ul}                           | G7      |
| [BGRejectedAlreadyEnteredInTheSameOrAnotherDevice]{.ul}            | Cal Status Primary=3 Secondary=6                                                                                                                 | [BGRejectedAlreadyEnteredInTheSameOrAnotherDevice]{.ul}            | G7      |
| BGRejectedCalibrationModuleIsDisabled                              | Cal Status Primary=3 Secondary=7                                                                                                                 | BGRejectedCalibrationModuleIsDisabled                              | G7      |
| BGRejectedCalibrationIsNotPermittedOrReady                         | Cal Status Primary=3 Secondary=8                                                                                                                 | BGRejectedCalibrationIsNotPermittedOrReady                         | G7      |
| BGRejectedCalboundFailed                                           | Cal Status Primary=3 Secondary=9                                                                                                                 | BGRejectedCalboundFailed                                           | G7      |
| BGRejectedOutsideOfCalboundAndFlaggedAsExtremeOutlier              | Cal Status Primary=3 Secondary=10                                                                                                                | BGRejectedOutsideOfCalboundAndFlaggedAsExtremeOutlier              | G7      |
| BGRejectedStale                                                    | Cal Status Primary=3 Secondary=11                                                                                                                | BGRejectedStale                                                    | G7      |

# BulkDataCrashLog

A crash log from the patient\'s device.

## Record Properties

| Property Name | Type            | Description                                                                                                     | Optional |
|---------------|-----------------|-----------------------------------------------------------------------------------------------------------------|----------|
| timestamp     | (Platform) Date | The date and time this crash log record was created.                                                            | N        |
| crashFile     | String          | The actual plain text crash file from the device. This will be zipped & base64\'d before sending to the server. | Y        |
| unixTimestamp | Int             | A unix timestamp at second resolution that should probably be an Int.                                           | Y        |
| message       | String          | The actual crash log message                                                                                    | Y        |
| stackTrace    | String          | The stack trace of the crash                                                                                    | Y        |
| appVersion    | String          | Version of the application that generated the crash log.                                                        | Y        |
| otherThread   | Array of String | Other thread information (Android)                                                                              | Y        |

# BulkDataDeviceSettings

This record contains information about the configured device settings.

## Record Properties

| Property Name      | Type            | Description                                                                                           | Optional |
|--------------------|-----------------|-------------------------------------------------------------------------------------------------------|----------|
| timestamp          | (Platform) Date | The date and time that the display device recorded this record.                                       | N        |
| is24HourMode       | Bool            | If the user\'s phone is showing a 24 hour clock (vs a 12 hour aka AM/PM) clock                        | N        |
| isBlindedMode      | Bool            | Notifies if the display device is in \"blinded\" mode, where no glucose alerts are shown to the user. | N        |
| isMmolDisplayMode  | Bool            | If the display device is displaying mMol/L units to the patient (true) or mg/dL units (false)         | N        |
| language           | String          | A string defining the language that the device is running in.                                         | N        |
| appSoftwareNumber  | String          | The internal Software Number used to identify the display device.                                     | N        |
| appSoftwareVersion | String          | The software version of the display device                                                            | N        |
| transmitterID      | String          | The 5 or 6 digit transmitter id the display device is connected to                                    | N        |

# BulkDataErrorLog

This record describes the application error log.

## Record Properties

<table>
<colgroup>
<col style="width: 15%" />
<col style="width: 14%" />
<col style="width: 60%" />
<col style="width: 10%" />
</colgroup>
<thead>
<tr class="header">
<th>Property Name</th>
<th>Type</th>
<th>Description</th>
<th>Optional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>timestamp</td>
<td>(Platform) Date</td>
<td>The date and time this error log record was created.</td>
<td>N</td>
</tr>
<tr class="even">
<td>rowID</td>
<td>Int</td>
<td>Incrementing row ID</td>
<td>N</td>
</tr>
<tr class="odd">
<td>location</td>
<td>String</td>
<td><p>A string containing the class, function, and line number that this log was recorded in.</p>
<p>Example:</p>
<p>"ClassName | FunctionName: @ LineNumber"</p></td>
<td>N</td>
</tr>
<tr class="even">
<td>message</td>
<td>String</td>
<td>The actual log message. This field could be quite large.</td>
<td>N</td>
</tr>
</tbody>
</table>

# BulkDataGlucose

This record contains information about the current patient glucose value
and trending information. This record only contains the glucose records
calculated by the Dexcom Algorithm, and will not contain any \"Display
Only\" records.

## Record Properties

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 24%" />
<col style="width: 36%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Property Name</th>
<th>Type</th>
<th>Description</th>
<th>Optional*</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>timestamp</td>
<td>(Platform) Date</td>
<td>The date and time that the display device recorded the EGV event as occurring.</td>
<td>N</td>
</tr>
<tr class="even">
<td>transmitterID</td>
<td>String</td>
<td>The 5 or 6 digit transmitter id that was used to transmit this EGV event.</td>
<td>N</td>
</tr>
<tr class="odd">
<td>transmitterTime</td>
<td>UInt</td>
<td>An unsigned integer value representing the number of seconds since the transmitter was first powered on. </td>
<td>N</td>
</tr>
<tr class="even">
<td>glucoseDate</td>
<td>(Platform) Date</td>
<td>The date and time representing the time that the transmitter calculated the EGV value.</td>
<td>N</td>
</tr>
<tr class="odd">
<td>value</td>
<td>UInt</td>
<td><p>This field represents a range of calculated glucose values. Here are the expected values, and their interpretations.</p>
<p>39 – Indicates that the value was calculated and it was less than 40. When this happens, the Status field is set to “Low”. Use the value of 39 for calculations, but do not display it to end users.</p>
<p>40 to 400 – This is the natural range of expected glucose values. The Status field should be blank. Use the value in calculations and to display to end users.</p>
<p>401 – Indicates that the value was calculated and it was greater than 400. When this happens, the Status field is set to “High”. Use the value of 401 for calculations, but do not display it to end users.</p></td>
<td>N</td>
</tr>
<tr class="even">
<td>predictedValue</td>
<td>UInt</td>
<td>This field represents a value that the algorithm has predicted that the user will experience in the next 20 minutes. Only valid EGV values are here (39 to 401)</td>
<td>Y</td>
</tr>
<tr class="odd">
<td>status</td>
<td>Enum GlucoseReadingStatus</td>
<td><p>This field is set to an enumerated string when the calculated glucose value falls outside of the 40-400 range, or if the value cannot be calculated. If the glucose value is in the 40-400 range, then the status field will be null.</p>
<p>High – Indicates a glucose value of more than 400.</p>
<p>Low – Indicates a glucose value of less than 40.</p>
<p>OutOfCalibration – the device is not displaying values because it requires calibration by the user.</p>
<p>SensorWarmUp – the device is in the 2 hour sensor warmup period and is not displaying any values.</p>
<p>SensorNoise – the signal to noise ratio too high</p></td>
<td>Y</td>
</tr>
<tr class="even">
<td>trendArrow</td>
<td>Enum GlucoseTrendArrow </td>
<td><p>This field enumerates the visibility status and direction of the trend arrow. The direction of the arrow is based on the Trend Rate. Note: you must have a valid glucose value or LOW or HIGH in order to have a valid trend arrow. It is also possible to have a valid glucose value and no trend arrow.</p>
<p>None – No arrow (blank)</p>
<p>DoubleUp – Two arrows up between &gt;= 3 and &lt;= 8 mg/dl/min</p>
<p>SingleUp – Arrow pointing at 12:00 between &gt;= 2 and &lt; 3 mg/dl/min</p>
<p>FortyFiveUp – Arrow pointing at 1:30 between &gt;= 1 and &lt; 2 mg/dl/min</p>
<p>Flat – Flat arrow between &gt; -1 and &lt; 1 mg/dl/min</p>
<p>FortyFiveDown – Arrow pointing at 4:30 between &gt; -2 and &lt;= -1 mg/dl/min</p>
<p>SingleDown – Arrow pointing at 6:00 between &gt; -3 and &lt;= -2 mg/dl/min</p>
<p>DoubleDown – Two arrows down between &lt;= -3 and &lt;= -8 mg/dl/min</p>
<p>NotComputable – This is returned when the algorithm decides that it is not reasonable to compute trend arrow.</p>
<p>RateOutOfRange – This is used when the computed filtered rate is not within the range for assigning the arrows.</p></td>
<td>N</td>
</tr>
<tr class="odd">
<td>trendRate</td>
<td>Double</td>
<td>This field represents a range of values indicating the range. The value can be null, or a numeric value between -8.0 and 8.0.</td>
<td>Y</td>
</tr>
<tr class="even">
<td>internalStatus</td>
<td>Int</td>
<td>An integer value representing the AlgorithmState Enum or Null if an EGV value can't be calculated</td>
<td>Y</td>
</tr>
<tr class="odd">
<td>isBackfilled</td>
<td>Bool</td>
<td>A boolean which indicates if this record was recorded as the current value (false), or was backfilled as part of a “catching-up” or backfill operation (true).</td>
<td>N</td>
</tr>
<tr class="even">
<td>sessionStartTime</td>
<td>UInt</td>
<td>Transmitter TICKS (internal absolute time in seconds since first boot) for when the session was started. For records generated when the transmitter is not in a session this field will be set to 4294967295 (i.e. 0xFFFFFFFF).</td>
<td>N</td>
</tr>
<tr class="odd">
<td>capturedByDate</td>
<td>(Platform) Date</td>
<td>The time that the display device which captured this glucose record received the EGV according to its clock.</td>
<td>N</td>
</tr>
<tr class="even">
<td>capturedBySource</td>
<td>Enum CaptureSource</td>
<td>An enum representing which display captured the glucose value from the transmitter.</td>
<td>N</td>
</tr>
<tr class="odd">
<td>secondaryAlgorithmState</td>
<td>UInt8</td>
<td>The secondary algorithm state, if any, from the transmitter. (server key "SecondaryAlgorithmState")</td>
<td>Y</td>
</tr>
</tbody>
</table>

## CaptureSource Enum

This describes what device captured the glucose reading from the
transmitter, and will either be the phone or the watch.

| Enum case | String Value (internal) | Description                                                    |
|-----------|-------------------------|----------------------------------------------------------------|
| phone     | Phone                   | A smart phone captured the glucose value from the transmitter. |
| watch     | Watch                   | A smart watch captured the glucose value from the transmitter. |

## GlucoseReadingStatus Enum

The status of the glucose reading.

| Enum case        | String Value (internal) | Description                                                                      |
|------------------|-------------------------|----------------------------------------------------------------------------------|
| high             | High                    | Indicates a glucose value of more than 400.                                      |
| low              | Low                     | Indicates a glucose value of less than 40.                                       |
| outOfCalibration | OutOfCalibration        | The device is not displaying values because it requires calibration by the user. |
| sensorWarmUp     | SensorWarmUp            | The device is in the sensor warmup period and is not displaying any values.      |
| sensorNoise      | SensorNoise             | The signal to noise ratio too high.                                              |

## GlucoseTrendArrow Enum

The visibility status and direction of the trend arrow.

| Enum case      | String Value (internal) | Description                                                                  |
|----------------|-------------------------|------------------------------------------------------------------------------|
| none           | None                    | No arrow (blank)                                                             |
| doubleUp       | DoubleUp                | Two arrows up (rate is \>= 3 and \<= 8 mg/dl/min)                            |
| singleUp       | SingleUp                | Single arrow pointing at 12:00 (rate is \>= 2 and \< 3 mg/dl/min)            |
| fortyFiveUp    | FortyFiveUp             | Single arrow pointing at 1:30 (rate is \>= 1 and \< 2 mg/dl/min)             |
| flat           | Flat                    | Single arrow pointing at 3:00 (rate is \> -1 and \< 1 mg/dl/min)             |
| fortyFiveDown  | FortyFiveDown           | Single arrow pointing at 4:30 (rate is \> -2 and \<= -1 mg/dl/min)           |
| singleDown     | SingleDown              | Single arrow pointing at 6:00 (rate is \> -3 and \<= -2 mg/dl/min)           |
| doubleDown     | DoubleDown              | Two arrows down (rate is \<= -3 and \<= -8 mg/dl/min)                        |
| notComputable  | NotComputable           | The algorithm decided that it is not reasonable to compute trend arrow.      |
| rateOutOfRange | RateOutOfRange          | The computed filtered rate is not within the range for assigning the arrows. |

# BulkDataInventory

This record is designed to describe the system that is providing glucose
information to the patient.  This record is intended to be uploaded to
the server upon the initial launch of the app, and each time one of the
listed items changes.

## Record Properties

| Property Name              | Type                                  | Description                                                                                                                                                                                                                                                                                                               | Optional? |
|----------------------------|---------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| timestamp                  | (Platform) Date                       | The Time that the display device created this record.                                                                                                                                                                                                                                                                     | N         |
| recordID                   | UUID                                  | A UUID string that uniquely identifies this inventory record.                                                                                                                                                                                                                                                             | N         |
| transmitterID              | String                                | The 5 or 6 digit transmitter id that the app is connected to                                                                                                                                                                                                                                                              | N         |
| transmitterFirmwareVersion | String                                | The firmware revision of the transmitter                                                                                                                                                                                                                                                                                  | Y         |
| transmitterSoftwareNumber  | String                                | The software number of the transmitter                                                                                                                                                                                                                                                                                    | Y         |
| transmitterTicks           | UInt                                  | The number of ticks on the transmitter when this record is created                                                                                                                                                                                                                                                        | Y         |
| hostSoftwareNumber         | String                                | The software number of the host running the CGM app                                                                                                                                                                                                                                                                       | N         |
| hostAppVersion             | String                                | The version number of the CGM app running on the host                                                                                                                                                                                                                                                                     | N         |
| hostDeviceModel            | String                                | The model name of the device (ie. iPhone8,1, iPodTouch, SM-G920F,etc)                                                                                                                                                                                                                                                     | N         |
| hostOSVersion              | String                                | The OS version the host is running                                                                                                                                                                                                                                                                                        | N         |
| accessories                | Array of **InventoryAccessory **items | A list of connected accessories (such as wearables, smart watches, etc) that have any interaction with our CGM app. If the CGM app is running on a watch, then it\'s possible that the phone might be listed as an accessory. List is not optional, however it can be an empty list, if nothing is connected to the host. | N         |

## InventoryAccessory

This record describes the connected accessories to the host device
(likely a smart phone, but could be a regular phone) that interact with
our CGM suite. (ie. The app would list an attached smart watch, but not
list a connected heart rate monitor)

| Property Name      | Type                        | Description                                      | Optional? |
|--------------------|-----------------------------|--------------------------------------------------|-----------|
| accessoryModel     | String                      | The device model name of the attached accessory. | N         |
| accessoryOSVersion | String?                     | The os version of the attached accessory.        | Y         |
| accessoryType      | Enum InventoryAccessoryType | The type of accessory this record represents.    | N         |

## InventoryAccessoryType Enum

This describes the type of inventory accessory.

| Enum  | Description                                           |
|-------|-------------------------------------------------------|
| watch | A smart watch (ie. AppleWatch or Android Wear device) |
| phone | A smart phone (ie. iPhone, Android Phone, etc)        |
| other | A non-watch/phone wearable.                           |

# BulkDataSensorSession

Contains information about the session of the device. Sessions are
considered started and stopped when the transmitter receives the command
and starts or stops.

## Record Properties

| Property Name          | Type                                  | Description                                                                                                                                                                                                                                                                                          | Optional? |
|------------------------|---------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| timestamp              | (Platform) Date                       | The Time that the display device recorded the Sensor Session event as occurring.                                                                                                                                                                                                                     | N         |
| transmitterID          | String                                | The 5 or 6 digit transmitter id that was used to transmit this EGV event.                                                                                                                                                                                                                            | N         |
| transmitterTime        | UInt                                  | An unsigned integer value representing the number of seconds since the transmitter was first powered on.                                                                                                                                                                                             | N         |
| sessionState           | Enum **SensorSessionState**           | An enum value representing the SessionState                                                                                                                                                                                                                                                          | N         |
| sensorSessionLength    | UInt                                  | The number of seconds that a sensor session is expected to last. (7 days = 604,800 seconds, 10 days = 864,000 seconds and 14 days = 1,209,600 seconds)                                                                                                                                               | N         |
| sensorWarmupLength     | UInt                                  | The number of seconds the sensor warmup is expected to take on this device. Expected values are 1 hour (3600 seconds) or 2 hours (7200 seconds)                                                                                                                                                      | N         |
| sessionID              | String                                | A unique identifier for this sensor session. All sensor session records that are generated during this sensor session will have the same SessionId. **This value is defined as the transmitter id, a pipe (\"\|\") and the number of ticks on the transmitter when the sensor session was started.** | N         |
| sessionCalibrationMode | Enum **SensorSessionCalibrationMode** | An enumeration describing the type of calibrations being requested by the algorithm.  This can be used to determine how often the user is going to be asked to calibrate.                                                                                                                            | N         |

## SensorSessionState Enum

The state of the sensor session.

| Enum Case                         | String Value (internal)                    | Description                                                                                                                                                                                             |
|-----------------------------------|--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| sessionStartedOnTxFromThisDisplay | SessionStartedOnTransmitterFromThisDisplay | User starts a session on a smart transmitter from this display device                                                                                                                                   |
| joinedSessionOnTransmitter        | JoinedSessionOnTransmitter                 | User\'s display device connected to a transmitter that was already in a session                                                                                                                         |
| sessionStoppedOnTxFromThisDisplay | SessionStoppedOnTransmitterFromThisDisplay | User stopped the session on a smart transmitter from this display device                                                                                                                                |
| sessionAlreadyStoppedOnTx         | SessionAlreadyStoppedOnTransmitter         | User attempted to stop the sensor session, but the session was already stopped by another display device                                                                                                |
| staleStartCommand                 | StaleStartCommand                          | A start command for that session has already been received                                                                                                                                              |
| staleStopCommand                  | StaleStopCommand                           | A stop command for that session has already been received                                                                                                                                               |
| noMatchingSessionForStop          | NoMatchingSessionForStop                   | User attempts to stop the sensor session, but the smart transmitter does not find a session id that matches the value sent in the stop session command                                                  |
| sessionStoppedDueToTxError        | SessionStoppedDueToTransmitterError        | A transmitter error occurred, and the session was stopped. The Phone display is the only device that reports this message                                                                               |
| sessionStoppedDueToTxEndOfLife    | SessionStoppedDueToTransmitterEndOfLife    | The smart transmitter reached its maximum runtime and is no longer operating.                                                                                                                           |
| transmitterInANewerSession        | TransmitterInANewerSession                 | The transmitter has received a sensor session command from the receiver, but the transmitter is already in a newer session than the one indicated in the command. This is reported by the receiver only |
| sensorShutoffDueToTimeLoss        | SensorShutoffDueToTimeLoss                 | The display device lost track of time, and it had to end the sensor session.                                                                                                                            |
| sessionExpired                    | SessionExpired                             | The sensor session was ended due to the sensor reaching its maximum lifetime                                                                                                                            |
| inSession                         | InSession                                  | The sensor is in session.                                                                                                                                                                               |
| sessionStopped                    | SessionStopped                             | The sensor session has stopped.                                                                                                                                                                         |

## SensorSessionCalibrationMode Enum

The calibration mode of the current sensor session.

| Enum case  | String Value (internal) | Description                                                                                                                                                   |
|------------|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| g6Mode     | G6CalMode               | The algorithm requires 2 calibrations at sensor warmup, calibrations at 12 & 24 hours after the session has started, and then once every 24 hours afterwards. |
| sensorCode | SensorCodeCalMode       | This describes a calibration mode where no calibrations are required.                                                                                         |
| oncePerDay | OncePerDayCalMode       | This describes a calibration mode where the user would have to calibrate once every 24 hours.                                                                 |
| factory    | FactoryCalMode          | This describes a scenario where no calibrations are requested and the user is not allowed to enter calibrations.                                              |
| unknown    | Unknown                 | The calibration mode is not known.                                                                                                                            |

# BulkDataTxDiagnostics v1.0

This record contains the transmitter diagnostic data. This data includes
the application state of the transmitter, and the internal algorithm
states used to calculate the EGV. This data on the transmitter is
encrypted, so the phone application is expected to send the data from
different partitions to the server. The server will have the ability to
determine the key used to encrypt the data, and decode it.

## Record Properties

| Property Name      | Type                    | Description                                                                                      | Optional? |
|--------------------|-------------------------|--------------------------------------------------------------------------------------------------|-----------|
| timestamp          | (Platform) Date         | The Time that the display device created this record.                                            | N         |
| transmitterID      | String                  | The current patient\'s transmitter ID                                                            | N         |
| referenceTicks     | UInt                    | The last reference tick count from the last communications with the transmitter                  | N         |
| referenceTimestamp | String                  | The last reference date from the last communications with the transmitter (ISO-8601, Local base) | N         |
| manifest           | **TxMetaData**          | The transmitter manifest for this set of data (NOT present in v2.0 record)                       | N         |
| encryptionInfo     | **TxMetaData**          | The transmitter encryption information for this set of data                                      | N         |
| dataSets           | Array of **TxDataSet**  | The actual transmitter data sets                                                                 | N         |

# BulkDataTxDiagnostics v2.0

This record contains the transmitter diagnostic data. This data includes
the application state of the transmitter, and the internal algorithm
states used to calculate the EGV. This data on the transmitter is
encrypted, so the phone application is expected to send the data from
different partitions to the server. The server will have the ability to
determine the key used to encrypt the data, and decode it.

## Record Properties

| Property Name      | Type                    | Description                                                                                                                         | Optional? |
|--------------------|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------|-----------|
| timestamp          | (Platform) Date         | The Time that the display device created this record.                                                                               | N         |
| transmitterID      | String                  | The current patient\'s transmitter ID                                                                                               | N         |
| referenceTicks     | UInt                    | The last reference tick count from the last communications with the transmitter                                                     | N         |
| referenceTimestamp | String                  | The last reference date from the last communications with the transmitter (ISO-8601, Local base)                                    | N         |
| encryptionInfo     | **TxMetaData**          | The transmitter encryption information for this set of data                                                                         | N         |
| dataSets           | Array of **TxDataSet**  | The actual transmitter data sets                                                                                                    | N         |
| entityCertificate  | Data                    | The entity certificate used to communicate with the transmitter (v2.0 record only, converted to base 64 string when sent to server) | N         |

## TxMetaData

This is used to describe the manifest and encryption information in the
Transmitter diagnostics record.

| Property Name | Type   | Description                                                                                   | Optional? |
|---------------|--------|-----------------------------------------------------------------------------------------------|-----------|
| timestamp     | String | Date when the record was received by the app (ISO-8601, Local base)                           | N         |
| transmitterID | String | The current patient\'s transmitter ID                                                         | N         |
| data          | String | A base-64 encoded string containing the (encrypted) manifest or encryption on the transmitter | N         |

## TxDataSet

The actual diagnostics data from the transmitter.

| Key           | Type   | Description                                                                   | Optional? |
|---------------|--------|-------------------------------------------------------------------------------|-----------|
| timestamp     | String | Date when the data set was created by the transmitter (ISO-8601, Local base). | N         |
| transmitterID | String | The current patient\'s transmitter ID.                                        | N         |
| txStartTicks  | UInt   | Transmitter ticks of the transmitter at the earliest entry into this data.    | N         |
| txEndTicks    | UInt   | Most recent Transmitter Ticks of the last entry in this data.                 | N         |
| data          | Data   | The (encrypted) binary data.                                                  | N         |

# BulkDataUserActivity

This record describes the user\'s activity while using the app.

## Record Properties

| Property Name       | Type                 | Description                                               | Optional? |
|---------------------|----------------------|-----------------------------------------------------------|-----------|
| recordedTime        | (Platform) Date      | The Time that the display device created this record.     | N         |
| userActivityType    | String               | The type of user activity being logged.                   | N         |
| userActivitySubType | String               | The sub type of user activity being logged.               | N         |
| data                | Codable/Serializable | A JSON dictionary of additional data about this activity. | N         |

# BulkDataUserEvent

This record contains a list of events entered by the user. These events
include carb events, health events, and exercise events.

## Record Properties

| Property Name | Type                    | Description                                                        | Optional? |
|---------------|-------------------------|--------------------------------------------------------------------|-----------|
| timestamp     | (Platform) Date         | The Time that this user event record was recorded by the system.   | N         |
| eventTime     | Date                    | The Time that the event occurred (entered by the patient).         | N         |
| eventId       | UUID                    | The UUID of this event.                                            | N         |
| name          | Enum **EventType**      | A string enumeration of the event types.                           | N         |
| subType       | Enum **EventSubType**   | The sub type of the event.                                         | Y         |
| value         | String                  | The value for the event as entered by the patient.                 | Y         |
| units         | Enum **UnitsOfMeasure** | The Units of Measure for this user event, if any.                  | Y         |
| recordStatus  | Enum **RecordStatus**   | The status of the user event record (ie. New, Modified or Deleted) | N         |

## UserEventType Enum

The describes the type of user event,

<table>
<colgroup>
<col style="width: 15%" />
<col style="width: 17%" />
<col style="width: 67%" />
</colgroup>
<thead>
<tr class="header">
<th>Enum case</th>
<th>String Value (internal)</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>carbs</td>
<td>Carbs</td>
<td>The user entered an event recording the consumption of carbohydrates.</td>
</tr>
<tr class="even">
<td>insulin</td>
<td>Insulin</td>
<td><p>The user entered an event recording that they took a certain amount of insulin.</p>
<p><strong>NOTE: When entering an insulin event, the 'value' field should contains the units of insulin taken by the patient x 100.</strong></p></td>
</tr>
<tr class="odd">
<td>exercise</td>
<td>Exercise</td>
<td>The user is recording an event where they exercised for a certain period of time.</td>
</tr>
<tr class="even">
<td>health</td>
<td>Health</td>
<td>The user recorded a health event.</td>
</tr>
<tr class="odd">
<td>medication</td>
<td>Medication</td>
<td>The user recorded taking a medication.</td>
</tr>
<tr class="even">
<td>note</td>
<td>Note</td>
<td>The user entered an arbitrary text note. This is intended to be a medical diary entry or something similar.</td>
</tr>
<tr class="odd">
<td>food</td>
<td>Food</td>
<td>The user entered a food item they have eaten.</td>
</tr>
<tr class="even">
<td>bloodGlucose</td>
<td>BG</td>
<td>The user entered a blood glucose reading.</td>
</tr>
</tbody>
</table>

## UserEventSubType Enum

For Insulin, Health, and Exercise events, this field describes the sub
type of the event.

| When UserEventType = | Enum case    | String Value (internal) | Description                                                               |
|----------------------|--------------|-------------------------|---------------------------------------------------------------------------|
| Insulin              | fastActing   | Fast-Acting             | The user reported taking a fast acting insulin dose.                      |
|                      | longActing   | Long-Acting             | The user reported taking a long acting insulin dose.                      |
|                      |              |                         |                                                                           |
| Health               | illness      | Illness                 | The user reported having an illness.                                      |
|                      | stress       | Stress                  | The user reported that they feel stress.                                  |
|                      | highSymptoms | HighSymptoms            | The user reported having symptoms related to having a high glucose value. |
|                      | lowSymptoms  | LowSymptoms             | The user reported having symptoms related to having a low glucose value.  |
|                      | cycle        | Cycle                   | The (female) user is reporting their monthly menstruation cycle has begun |
|                      | alcohol      | Alcohol                 | The user reported that they have consumed alcohol.                        |
|                      |              |                         |                                                                           |
| Exercise             | light        | Light                   | The user reported a light intensity workout.                              |
|                      | medium       | Medium                  | The user reported a medium intensity workout.                             |
|                      | heavy        | Heavy                   | The user reported a high intensity workout.                               |

## UnitsOfMeasure Enum

The unit of measure used in the \'value\' field of this record.

| Enum Case | String Value (internal) | Description                                                     |
|-----------|-------------------------|-----------------------------------------------------------------|
| grams     | grams                   | The standard SI gram unit.                                      |
| minutes   | minutes                 | The common unit of time.                                        |
| units     | units                   | A common unit that insulin is dosed in x 100.                   |
| mgdl      | mgdl                    | Milligrams per deciliter, a common measurement of blood glucose |

## RecordStatus Enum

The database status of this record.

|               |                             |                                                                                  |
|---------------|-----------------------------|----------------------------------------------------------------------------------|
| **Enum Case** | **String Value (internal)** | **Description**                                                                  |
| new           | New                         | This is the first entry of this value from the Dexcom application\'s perspective |
| updated       | Updated                     | The user made a change to an existing record according to the Health Database    |
| deleted       | Deleted                     | The user deleted this entry out of the Health Database.                          |

# BulkDataUploadReceipt

When the client calls the upload() function, it\'s possible that many
data posts are uploaded to the server, each in their HTTP request. The
postIDs and other pertinent information will be returned to the caller
via the BulkDataUploadReceipt object.

## BulkDataUploadReceipt Spec

| Property Name   | Type                         | Optional | Comment                                                          |
|-----------------|------------------------------|----------|------------------------------------------------------------------|
| accountID       | String                       | N        | Patient or AccountID that is logged in and requesting the upload |
| beginUploadTime | (Platform) Date              | N        | Date and time the overall upload request started                 |
| endUploadTime   | (Platform) Date              | Y        | Date and time the upload request finished                        |
| status          | Enum BulkDataUploadStatus    | N        | Status of the overall upload request (all posts)                 |
| serverPosts     | Array of BulkDataPostReceipt | N        | Array of each post to the server for this upload request         |

### BulkDataPostReceipt

The receipt for the individual bulk data post. There should be one
receipt per BulkDataPost upload attempt.

| Property Name | Type                         | Optional | Comment                                                      |
|---------------|------------------------------|----------|--------------------------------------------------------------|
| sequenceID    | Int                          | N        | Sequence ID for this bulk data post                          |
| uploadTime    | (Platform) Date              | N        | Date and time of this bulk data post upload request          |
| serverPostID  | String?                      | Y        | The post ID received from the server for this bulk data post |
| error         | SecureNetworkError?          | Y        | The error, if any, for this particular data post             |
| recordCounts  | Array of BulkDataRecordCount | N        | Array of record counts for this bulk data post               |

### BulkDataRecordCount

The count of each Bulk Data record type that was uploaded to the server.

| Property Name | Type                    | Optional | Comment                           |
|---------------|-------------------------|----------|-----------------------------------|
| recordType    | Enum BulkDataRecordType | N        | Type of record                    |
| count         | Int                     | N        | Count of records of \<recordType> |

### Enum BulkDataRecordType

This describes the type of Bulk Data record.

| Enum case                   | Server Record Type   | Description                                                    |
|-----------------------------|----------------------|----------------------------------------------------------------|
| alertEventRecord            | AlertEventRecord     | Alert Event record type                                        |
| alertScheduleRecord         | AlertScheduleRecord  | Alert Schedule record type                                     |
| crashLogRecord              | CrashLogRecord       | Crash Log record type                                          |
| deviceSettingsRecord        | DeviceSettingsRecord | Device Settings record type                                    |
| errorLogRecord              | ErrorLogRecord       | Error Log record type                                          |
| glucoseRecord               | GlucoseRecord        | Glucose record type                                            |
| inventoryRecord             | InventoryRecord      | Inventory record type                                          |
| sensorSessionRecord         | SensorSessionRecord  | Sensor Session record type                                     |
| transmitterDiagnosticRecord | TxDiagnosticRecord   | Transmitter Diagnostics record type (Transmitter Private Data) |
| userActivityRecord          | UserActivityRecord   | User Activity record type                                      |
| userEventRecord             | UserEventRecord      | User Event record type                                         |

### Enum BulkDataUploadStatus

Overall status of the upload request.

| Enum case       | Description                              |
|-----------------|------------------------------------------|
| completedOK     | The upload attempt succeeded.            |
| partialUpload   | Some but not all Bulk Data was uploaded. |
| noDataUploaded  | No Bulk Data was uploaded.               |
| requestTimedOut | The server request timed out. (iOS only) |
