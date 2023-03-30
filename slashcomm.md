This is a test command

/table
+--------------+---------------------------+--------------------------+
| Primary      | Secondary algorithm state | Tx Algorithm State       |
| algorithm    |                           |                          |
| state        |                           |                          |
+==============+===========================+==========================+
| 0            | none                      | OutOfS                   |
|              |                           | ession.TransmitterFailed |
+--------------+---------------------------+--------------------------+
| 1            | deployed                  | InSession.Warmup         |
+--------------+---------------------------+--------------------------+
| 2            | sivPassed = 0             | InSession.Warmup         |
|              | parametersUpdated = 1     |                          |
|              | signalProcessing = 2      |                          |
|              |                           |                          |
|              | error = 255               |                          |
+--------------+---------------------------+--------------------------+
