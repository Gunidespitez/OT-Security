# Parking Lot System :
## Aim: 
  * Create a parking lot system for 5 cars 
  * When a car approaches the gate , a sensor will activate a motor and the gate will open up and take a spot, until thees no spot left, hence gate wont open for sixth one
## Components: 
  * Outputs - Motor (output to indicate input being true
  * Inputs - PL-1 , PL-2 , PL-3, PL-4 , PL-5 and P-S (sensor)
## Working:
  * A car arrives at the entrance gate.
    The Entry Sensor (P-S) detects the car and sends a signal to the PLC.
  * PLC checks the status of each parking spot sensor (PL-1 to PL-5).
  * If at least one spot is free:
      The PLC activates Motor-1.
      The gate opens automatically.
  * If no spot is free (all 5 occupied):
       The PLC keeps Motor-1 OFF.
  * The gate remains closed, preventing entry.
  * For this we connect all inputs as Normally Closed inputs and sesnor is Normally open.
# Traffic Light System:
## Aim:
  * Red light turns on for 10 seconds
  * Yellow light then turns on for 3 seconds 
  * Then the Green light turns on for 10 seconds.
  * After the green light turns off, the system restarts. 
## Components: 
  * Outputs - red , yellow and green coils.
  * Inputs 
  * Timer - Use Pulse timer , so output will be on until timer and then turn off. 
## Working:
  * Use t1 timer's Q(ouput bit) as the coil output for i1 - red. 
  * We use Done bits as output to trigger the next action. 
  * we start Red Light & Begin Timer T1
  * When the start button is pressed, Red Light turns ON.
    T1 starts counting 20 seconds.
    After 20 seconds, T1 finishes.
  * Red Light turns OFF, and Yellow Light turns ON for 5 sec.
  * Yellow Light turns OFF, and Green Light turns ON for 20 sec.
   After 20 sec, T3 finishes.
  * Green Light turns OFF, and Yellow Light turns ON for 5 sec.
   After 5 sec, T4 finishes.
  * When T4 finishes , the entire simulation repeats. 
