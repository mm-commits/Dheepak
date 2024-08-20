IDENTIFICATION DIVISION.
PROGRAM-ID. CHECK-BBG-SECURITY.

DATA DIVISION.
WORKING-STORAGE SECTION.
01  WS-SOURCE             PIC X(10).
01  WS-SEC-MAIN-TYPE      PIC X(2).
01  WS-SEC-TYPE           PIC X(7).
01  WS-ALERT-FLAG         PIC X VALUE 'N'.

PROCEDURE DIVISION.

    * Sample input values for testing
    MOVE 'BBG' TO WS-SOURCE
    MOVE 'XX' TO WS-SEC-MAIN-TYPE
    MOVE 'WC CERT' TO WS-SEC-TYPE

    * Check if source is BBG
    IF WS-SOURCE = 'BBG'
        * Check if security main type is not 'Fl' or security type is not 'WC CERT'
        IF WS-SEC-MAIN-TYPE NOT = 'Fl' OR WS-SEC-TYPE NOT = 'WC CERT'
            MOVE 'Y' TO WS-ALERT-FLAG
        END-IF
    END-IF

    * Trigger alert if condition is met
    IF WS-ALERT-FLAG = 'Y'
        DISPLAY 'Blocking Alert B001: Security does not meet criteria.'
        * Additional logic to handle the blocking of the process can be added here.
    ELSE
        DISPLAY 'Security meets criteria.'
    END-IF

    STOP RUN.


