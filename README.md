MOVE '180' TO WS-SEC-MAIN-TYPE
           MOVE 'WC' TO WS-SEC-TYPE
           MOVE 'BLOOMBERG' TO WS-INTERNAL-SOURCE

      
           IF WS-INTERNAL-SOURCE = 'BLOOMBERG'
               AND (WS-SEC-MAIN-TYPE NOT = 'F1' OR WS-SEC-TYPE NOT = 'WC CERT')
               THEN
                   MOVE 'B001' TO WS-BLOCKING-ALERT
                   DISPLAY 'Blocking Alert Triggered: ' WS-BLOCKING-ALERT
           ELSE
            
               DISPLAY 'No Blocking Alert Triggered.'
           END-IF.

           STOP RUN.
