# PLC Basics (Ladder Logic)
## Basic components:
  * Network/Rung: Through which flow of current happens.
  * Inputs -
      -normally opem
      -normally closed
      -positive edge contact
      -negative edge contact
  * Coils -
      -coil
      -negated coil
      -set coil
      -reset coil
  * Timers -
      - Timer Pulse (if input true ---> output true till timer goes off then output---> false)
      - TON (If input true--->output false till timer then output --> true)
      - TOF (Input false ---> Output true ; it stays true even after input turns false until the timer)
## Series:
  * AND -
      - Series connection - Only when both inputs are true , the output is true , else the output is false
  * OR -
      - Parallel connection - Even if one of the inputs are true; the output becomes true
  * XOR - connecting a negated input1 in series with input 2 which is in parallel with the same connection (switching i2 and i1) < /br>
          here , the output is false when both bits are high or low, o.w it is true.

