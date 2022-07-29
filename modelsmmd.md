# BulkDataErrorLog

This record describes the application error log.

## Record Properties

+---------+---------+-------------------------------------------+-----+
| Property Name       | Type    | Description      | Optional  |
+---------+---------+-------------------------------------------+-----+
| ti      | (Pl     | The date and time this error log record   | N   |
| mestamp | atform) | was created.                              |     |
|         | Date    |                                           |     |
+---------+---------+-------------------------------------------+-----+
| rowID   | Int     | Incrementing row ID                       | N   |
+---------+---------+-------------------------------------------+-----+
| l       | String  | A string containing the class, function,  | N   |
| ocation |         | and line number that this log was         |     |
|         |         | recorded in.                              |     |
|         |         |                                           |     |
|         |         | Example:                                  |     |
|         |         |                                           |     |
|         |         | "ClassName | FunctionName: @ LineNumber"  |     |
+---------+---------+-------------------------------------------+-----+
| message | String  | The actual log message. This field could  | N   |
|         |         | be quite large.                           |     |
+---------+---------+-------------------------------------------+-----+

# BulkDataGlucose

This record contains information about the current patient glucose value
and trending information. This record only contains the glucose records
calculated by the Dexcom Algorithm, and will not contain any "Display
Only" records.

## Record Properties

+------------------+----------------+-------------------------+-------+
| Property Name    | Type           | Description             | Optio |
|                  |                |                         | nal\* |
+==================+================+=========================+=======+
| timestamp        | (Platform)     | The date and time that  | N     |
|                  | Date           | the display device      |       |
|                  |                | recorded the EGV event  |       |
|                  |                | as occurring.           |       |
+------------------+----------------+-------------------------+-------+
| transmitterID    | String         | The 5 or 6 digit        | N     |
|                  |                | transmitter id that was |       |
|                  |                | used to transmit this   |       |
|                  |                | EGV event.              |       |
+------------------+----------------+-------------------------+-------+
| transmitterTime  | UInt           | An unsigned integer     | N     |
|                  |                | value representing the  |       |
|                  |                | number of seconds since |       |
|                  |                | the transmitter was     |       |
|                  |                | first powered on.       |       |
+------------------+----------------+-------------------------+-------+
| glucoseDate      | (Platform)     | The date and time       | N     |
|                  | Date           | representing the time   |       |
|                  |                | that the transmitter    |       |
|                  |                | calculated the EGV      |       |
|                  |                | value.                  |       |
+------------------+----------------+-------------------------+-------+
| value            | UInt           | This field represents a | N     |
|                  |                | range of calculated     |       |
|                  |                | glucose values. Here    |       |
|                  |                | are the expected        |       |
|                  |                | values, and their       |       |
|                  |                | interpretations.        |       |
|                  |                |                         |       |
|                  |                | 39 – Indicates that the |       |
|                  |                | value was calculated    |       |
|                  |                | and it was less than    |       |
|                  |                | 40. When this happens,  |       |
|                  |                | the Status field is set |       |
|                  |                | to “Low”. Use the value |       |
|                  |                | of 39 for calculations, |       |
|                  |                | but do not display it   |       |
|                  |                | to end users.           |       |
|                  |                |                         |       |
|                  |                | 40 to 400 – This is the |       |
|                  |                | natural range of        |       |
|                  |                | expected glucose        |       |
|                  |                | values. The Status      |       |
|                  |                | field should be blank.  |       |
|                  |                | Use the value in        |       |
|                  |                | calculations and to     |       |
|                  |                | display to end users.   |       |
|                  |                |                         |       |
|                  |                | 401 – Indicates that    |       |
|                  |                | the value was           |       |
|                  |                | calculated and it was   |       |
|                  |                | greater than 400. When  |       |
|                  |                | this happens, the       |       |
|                  |                | Status field is set to  |       |
|                  |                | “High”. Use the value   |       |
|                  |                | of 401 for              |       |
|                  |                | calculations, but do    |       |
|                  |                | not display it to end   |       |
|                  |                | users.                  |       |
+------------------+----------------+-------------------------+-------+
| predictedValue   | UInt           | This field represents a | Y     |
|                  |                | value that the          |       |
|                  |                | algorithm has predicted |       |
|                  |                | that the user will      |       |
|                  |                | experience in the next  |       |
|                  |                | 20 minutes. Only valid  |       |
|                  |                | EGV values are here (39 |       |
|                  |                | to 401)                 |       |
+------------------+----------------+-------------------------+-------+
| status           | Enum           | This field is set to an | Y     |
|                  | Glucos         | enumerated string when  |       |
|                  | eReadingStatus | the calculated glucose  |       |
|                  |                | value falls outside of  |       |
|                  |                | the 40-400 range, or if |       |
|                  |                | the value cannot be     |       |
|                  |                | calculated. If the      |       |
|                  |                | glucose value is in the |       |
|                  |                | 40-400 range, then the  |       |
|                  |                | status field will be    |       |
|                  |                | null.                   |       |
|                  |                |                         |       |
|                  |                | High – Indicates a      |       |
|                  |                | glucose value of more   |       |
|                  |                | than 400.               |       |
|                  |                |                         |       |
|                  |                | Low – Indicates a       |       |
|                  |                | glucose value of less   |       |
|                  |                | than 40.                |       |
|                  |                |                         |       |
|                  |                | OutOfCalibration – the  |       |
|                  |                | device is not           |       |
|                  |                | displaying values       |       |
|                  |                | because it requires     |       |
|                  |                | calibration by the      |       |
|                  |                | user.                   |       |
|                  |                |                         |       |
|                  |                | SensorWarmUp – the      |       |
|                  |                | device is in the 2 hour |       |
|                  |                | sensor warmup period    |       |
|                  |                | and is not displaying   |       |
|                  |                | any values.             |       |
|                  |                |                         |       |
|                  |                | SensorNoise – the       |       |
|                  |                | signal to noise ratio   |       |
|                  |                | too high                |       |
+------------------+----------------+-------------------------+-------+
| trendArrow       | Enum           | This field enumerates   | N     |
|                  | Gluc           | the visibility status   |       |
|                  | oseTrendArrow  | and direction of the    |       |
|                  |                | trend arrow. The        |       |
|                  |                | direction of the arrow  |       |
|                  |                | is based on the Trend   |       |
|                  |                | Rate. Note: you must    |       |
|                  |                | have a valid glucose    |       |
|                  |                | value or LOW or HIGH in |       |
|                  |                | order to have a valid   |       |
|                  |                | trend arrow. It is also |       |
|                  |                | possible to have a      |       |
|                  |                | valid glucose value and |       |
|                  |                | no trend arrow.         |       |
|                  |                |                         |       |
|                  |                | None – No arrow (blank) |       |
|                  |                |                         |       |
|                  |                | DoubleUp – Two arrows   |       |
|                  |                | up between \>= 3 and    |       |
|                  |                | \<= 8 mg/dl/min         |       |
|                  |                |                         |       |
|                  |                | SingleUp – Arrow        |       |
|                  |                | pointing at 12:00       |       |
|                  |                | between \>= 2 and \< 3  |       |
|                  |                | mg/dl/min               |       |
|                  |                |                         |       |
|                  |                | FortyFiveUp – Arrow     |       |
|                  |                | pointing at 1:30        |       |
|                  |                | between \>= 1 and \< 2  |       |
|                  |                | mg/dl/min               |       |
|                  |                |                         |       |
|                  |                | Flat – Flat arrow       |       |
|                  |                | between \> -1 and \< 1  |       |
|                  |                | mg/dl/min               |       |
|                  |                |                         |       |
|                  |                | FortyFiveDown – Arrow   |       |
|                  |                | pointing at 4:30        |       |
|                  |                | between \> -2 and \<=   |       |
|                  |                | -1 mg/dl/min            |       |
|                  |                |                         |       |
|                  |                | SingleDown – Arrow      |       |
|                  |                | pointing at 6:00        |       |
|                  |                | between \> -3 and \<=   |       |
|                  |                | -2 mg/dl/min            |       |
|                  |                |                         |       |
|                  |                | DoubleDown – Two arrows |       |
|                  |                | down between \<= -3 and |       |
|                  |                | \<= -8 mg/dl/min        |       |
|                  |                |                         |       |
|                  |                | NotComputable – This is |       |
|                  |                | returned when the       |       |
|                  |                | algorithm decides that  |       |
|                  |                | it is not reasonable to |       |
|                  |                | compute trend arrow.    |       |
|                  |                |                         |       |
|                  |                | RateOutOfRange – This   |       |
|                  |                | is used when the        |       |
|                  |                | computed filtered rate  |       |
|                  |                | is not within the range |       |
|                  |                | for assigning the       |       |
|                  |                | arrows.                 |       |
+------------------+----------------+-------------------------+-------+
| trendRate        | Double         | This field represents a | Y     |
|                  |                | range of values         |       |
|                  |                | indicating the range.   |       |
|                  |                | The value can be null,  |       |
|                  |                | or a numeric value      |       |
|                  |                | between -8.0 and 8.0.   |       |
+------------------+----------------+-------------------------+-------+
| internalStatus   | Int            | An integer value        | Y     |
|                  |                | representing the        |       |
|                  |                | AlgorithmState Enum or  |       |
|                  |                | Null if an EGV value    |       |
|                  |                | can't be calculated     |       |
+------------------+----------------+-------------------------+-------+
| isBackfilled     | Bool           | A boolean which         | N     |
|                  |                | indicates if this       |       |
|                  |                | record was recorded as  |       |
|                  |                | the current value       |       |
|                  |                | (false), or was         |       |
|                  |                | backfilled as part of a |       |
|                  |                | “catching-up” or        |       |
|                  |                | backfill operation      |       |
|                  |                | (true).                 |       |
+------------------+----------------+-------------------------+-------+
| sessionStartTime | UInt           | Transmitter TICKS       | N     |
|                  |                | (internal absolute time |       |
|                  |                | in seconds since first  |       |
|                  |                | boot) for when the      |       |
|                  |                | session was started.    |       |
|                  |                | For records generated   |       |
|                  |                | when the transmitter is |       |
|                  |                | not in a session this   |       |
|                  |                | field will be set to    |       |
|                  |                | 4294967295 (i.e.        |       |
|                  |                | 0xFFFFFFFF).            |       |
+------------------+----------------+-------------------------+-------+
| capturedByDate   | (Platform)     | The time that the       | N     |
|                  | Date           | display device which    |       |
|                  |                | captured this glucose   |       |
|                  |                | record received the EGV |       |
|                  |                | according to its clock. |       |
+------------------+----------------+-------------------------+-------+
| capturedBySource | Enum           | An enum                 | N     |
|                  | CaptureSource  | representing which      |       |
|                  |                | display captured the    |       |
|                  |                | glucose value from the  |       |
|                  |                | transmitter.            |       |
+------------------+----------------+-------------------------+-------+
| seconda          | UInt8          | The secondary algorithm | Y     |
| ryAlgorithmState |                | state, if any, from the |       |
|                  |                | transmitter. (server    |       |
|                  |                | key                     |       |
|                  |                | "Se                     |       |
|                  |                | condaryAlgorithmState") |       |
+------------------+----------------+-------------------------+-------+

## UserEventType Enum

The describes the type of user event,

+-----------+------------+---------------------------------------------+
| Enum case | String     | Description                                 |
|           | Value      |                                             |
|           | (internal) |                                             |
+===========+============+=============================================+
| carbs     | Carbs      | The user entered an event recording the     |
|           |            | consumption of carbohydrates.               |
+-----------+------------+---------------------------------------------+
| insulin   | Insulin    | The user entered an event recording that    |
|           |            | they took a certain amount of insulin.      |
|           |            |                                             |
|           |            | **NOTE: When entering an insulin event, the |
|           |            | 'value' field should contains the units of  |
|           |            | insulin taken by the patient x 100.**       |
+-----------+------------+---------------------------------------------+
| exercise  | Exercise   | The user is recording an event where they   |
|           |            | exercised for a certain period of time.     |
+-----------+------------+---------------------------------------------+
| health    | Health     | The user recorded a health event.           |
+-----------+------------+---------------------------------------------+
| m         | Medication | The user recorded taking a medication.      |
| edication |            |                                             |
+-----------+------------+---------------------------------------------+
| note      | Note       | The user entered an arbitrary text note.    |
|           |            | This is intended to be a medical diary      |
|           |            | entry or something similar.                 |
+-----------+------------+---------------------------------------------+
| food      | Food       | The user entered a food item they have      |
|           |            | eaten.                                      |
+-----------+------------+---------------------------------------------+
| blo       | BG         | The user entered a blood glucose reading.   |
| odGlucose |            |                                             |
+-----------+------------+---------------------------------------------+

##  
