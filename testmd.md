pandoc -f docx -t markdown \--wrap=none g7-sensorstate-table.docx -o
g7ssmd.txt

+---------+---------------+------------------------------+-----------+
| Primary | Internal SDK  | Secondary algorithm state    | Published |
| al      | state (Enum)  |                              | sensor    |
| gorithm |               |                              |           |
| state   |               |                              |           |
+=========+===============+==============================+===========+
| \`0\`   | \`none\`      | \`N/A\`                      | \`N/A\`   |
+---------+---------------+------------------------------+-----------+
| \`1\`   | \`deployed\`  | \`N/A\`                      | \`i       |
|         |               |                              | nWarmup\` |
+---------+---------------+------------------------------+-----------+
| \`2\`   | \`warmup\`    | \`sivPassed = 0\`            | \`i       |
|         |               |                              | nWarmup\` |
|         |               | \`parametersUpdated = 1\`    |           |
|         |               |                              |           |
|         |               | \`signalProcessing = 2\`     |           |
|         |               |                              |           |
|         |               | \`error = 255\`              |           |
+---------+---------------+------------------------------+-----------+
| \`6\`   | \`inSession\` | \`low = 7\`                  | \`in      |
|         |               |                              | Session\` |
|         |               | \`lowNoPrediction = 6\`      |           |
|         |               |                              |           |
|         |               | \`lowNoTrend = 5\`           |           |
|         |               |                              |           |
|         |               | \`lowNoTrendOrPrediction =   |           |
|         |               | 4\`                          |           |
|         |               |                              |           |
|         |               | \`inRange                    |           |
|         |               | g7-sensorstate-table = 15\`  |           |
|         |               |                              |           |
|         |               | \`inRangeNoPrediction = 14\` |           |
|         |               |                              |           |
|         |               | \`inRangeNoTrend = 13\`      |           |
|         |               |                              |           |
|         |               | \`inRangeNoTrendOrPrediction |           |
|         |               | = 12\`                       |           |
|         |               |                              |           |
|         |               | \`high = 11\`                |           |
|         |               |                              |           |
|         |               | \`highNoPrediction = 10\`    |           |
|         |               |                              |           |
|         |               | \`highNoTrend = 9\`          |           |
|         |               |                              |           |
|         |               | \`highNoTrendOrPrediction =  |           |
|         |               | 8\`                          |           |
|         |               |                              |           |
|         |               | \`bgTriggered = 31\`         |           |
|         |               |                              |           |
|         |               | \`bgTriggeredNoPrediction =  |           |
|         |               | 30\`                         |           |
|         |               |                              |           |
|         |               | \`bgTriggeredNoTrend = 29\`  |           |
|         |               |                              |           |
|         |               | \`bg                         |           |
|         |               | TriggeredNoTrendOrPrediction |           |
|         |               | = 28\`                       |           |
|         |               |                              |           |
|         |               | \`bgTriggeredLow = 23\`      |           |
|         |               |                              |           |
|         |               | \`bgTriggeredLowNoPrediction |           |
|         |               | = 22\`                       |           |
|         |               |                              |           |
|         |               | \`bgTriggeredLowNoTrend =    |           |
|         |               | 21\`                         |           |
|         |               |                              |           |
|         |               | \`bgTri                      |           |
|         |               | ggeredLowNoTrendOrPrediction |           |
|         |               | = 20\`                       |           |
|         |               |                              |           |
|         |               | \`bgTriggeredHigh = 27\`     |           |
|         |               |                              |           |
|         |               | \                            |           |
|         |               | `bgTriggeredHighNoPrediction |           |
|         |               | = 26\`                       |           |
|         |               |                              |           |
|         |               | \`bgTriggeredHighNoTrend =   |           |
|         |               | 25\`                         |           |
|         |               |                              |           |
|         |               | \`bgTrig                     |           |
|         |               | geredHighNoTrendOrPrediction |           |
|         |               | = 24\`                       |           |
+---------+---------------+------------------------------+-----------+
| \`6\`   | \`inSession\` | \`error = 255\`              | \`        |
|         |               |                              | inSession |
|         |               |                              | Invalid\` |
+---------+---------------+------------------------------+-----------+
| \`18\`  | \`inSes       | \`invalid = 0\`              | \`        |
|         | sionInvalid\` |                              | inSession |
|         |               | \`validPrediction = 1\`      | Invalid\` |
|         |               |                              |           |
|         |               | \`validTrend = 2\`           |           |
|         |               |                              |           |
|         |               | \`validTrendAndPrediction =  |           |
|         |               | 3\`                          |           |
|         |               |                              |           |
|         |               | \`bgInvalid = 16\`           |           |
|         |               |                              |           |
|         |               | \`bgInvalidValidPrediction = |           |
|         |               | 17\`                         |           |
|         |               |                              |           |
|         |               | \`bgInvalidValidTrend = 18\` |           |
|         |               |                              |           |
|         |               | \`bgIn                       |           |
|         |               | validValidTrendAndPrediction |           |
|         |               | = 19\`                       |           |
|         |               |                              |           |
|         |               | \`error = 255\`              |           |
+---------+---------------+------------------------------+-----------+
| \`24\`  | \`ses         | \`validEgv = 15\`            | \`sensor  |
|         | sionExpired\` |                              | Expired\` |
|         |               | \`validEgvNoPrediction = 14' |           |
|         |               |                              |           |
|         |               | \`validEgvNoTrend = 13'      |           |
|         |               |                              |           |
|         |               | \                            |           |
|         |               | `validEgvNoTrendOrPrediction |           |
|         |               | = 12'                        |           |
|         |               |                              |           |
|         |               | \`invalidEgv = 3'            |           |
|         |               |                              |           |
|         |               | \`invalidEgvNoPrediction =   |           |
|         |               | 2'                           |           |
|         |               |                              |           |
|         |               | \`invalidEgvNoTrend = 1'     |           |
|         |               |                              |           |
|         |               | \`i                          |           |
|         |               | nvalidEgvNoTrendOrPrediction |           |
|         |               | = 0'                         |           |
|         |               |                              |           |
|         |               | \`case error = 255\`         |           |
+---------+---------------+------------------------------+-----------+
| \`25\`  | \`se          | \`unspecified = 0\`          | \         |
|         | ssionFailed\` |                              | `failed\` |
|         |               | \`Permanent sensor failure   |           |
|         |               | (e.g, extreme low, low,      |           |
|         |               |                              |           |
|         |               | high, delta resid, sensor    |           |
|         |               | disconnection                |           |
|         |               | re-connection)'              |           |
|         |               |                              |           |
|         |               | \`sensorFailure = 1'         |           |
|         |               |                              |           |
|         |               | \`Algorithm failure: algo    |           |
|         |               | assumption violation(e.g.    |           |
|         |               | PSD, suppress signal, signal |           |
|         |               | shift)'                      |           |
|         |               |                              |           |
|         |               | \`algorithmFailure = 2'      |           |
|         |               |                              |           |
|         |               | \`Algorithm failure          |           |
|         |               | unexpected error (e.g. cal   |           |
|         |               | error)'                      |           |
|         |               |                              |           |
|         |               | \`unexpectedAlgorithmFailure |           |
|         |               | = 3'                         |           |
|         |               |                              |           |
|         |               | \`Prolonged data blanking:   |           |
|         |               | Glucose data not reliably    |           |
|         |               | available for an extended    |           |
|         |               | period of time\`             |           |
|         |               |                              |           |
|         |               | \`noData = 4'                |           |
|         |               |                              |           |
|         |               | \`Transmitter returned an    |           |
|         |               | invalid value'               |           |
|         |               |                              |           |
|         |               | \`error = 255\`              |           |
+---------+---------------+------------------------------+-----------+
| \`26\`  | \`manu        | \`none = 0\`                 | \`        |
|         | allyStopped\` |                              | stopped\` |
|         |               | \`skip = 1\`                 |           |
|         |               |                              |           |
|         |               | \`other = 2\`                |           |
|         |               |                              |           |
|         |               | \`bestTimingForMe = 3\`      |           |
|         |               |                              |           |
|         |               | \`inaccurate = 4\`           |           |
|         |               |                              |           |
|         |               | \`noReadings = 5\`           |           |
|         |               |                              |           |
|         |               | \`sensorFellOff = 6\`        |           |
|         |               |                              |           |
|         |               | \`discomfort = 7\`           |           |
|         |               |                              |           |
|         |               | \`error = 255\`              |           |
+---------+---------------+------------------------------+-----------+
| \`27\`  | \`transm      |                              | \         |
|         | itterFailed\` |                              | `failed\` |
+---------+---------------+------------------------------+-----------+
| \`28\`  | \`sivFailed\` |                              | \         |
|         |               |                              | `failed\` |
+---------+---------------+------------------------------+-----------+
| \`29\`  | \             |                              | \`        |
|         | `sessionFaile |                              | failedOut |
|         | dOutOfRange\` |                              | OfRange\` |
+---------+---------------+------------------------------+-----------+
