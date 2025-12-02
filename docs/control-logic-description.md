## 1. Start Dosing Silo 1

Silo 1 dosing begins when all of the following conditions are met:

- **NotEnough = 0**  
  Meaning: Required amount ≤ Available amount.
- **FillActive = 0**  
  Meaning: Filling process for silo 1 is not currently running and Required amount <= Available amount.
- **StartSystem = 1**  
  Meaning: Operator has initiated the process.

When these conditions are met:
- Spiral1MotorCoil = 1 starts the Silo 1 dosing motor.

The motor continues to run until:
- Extracted >= Required amount

At that point:
- Spiral1MotorCoil = 0 
- DoneDosingSilo1 = 1

When NotEnough = 1 and FillActive = 1:
### Start Filling Silo 1
- After inputting the FillAmount, filling process will start when StartFilling = 1
  Meaning : Operator input the fill amount and initiated the filling process.

When this condition are met:
- Elev1MotorCoil = 1 starts the Silo 1 filling motor.

The motor will run until:
- Filled >= FillAmount

At that point:
- Elev1MotorCoil = 0
- DoneFillingSilo1 = 1

If Operator wants to change the filling amount:
- **StopFilling = 1**
  Meaning : Operator stops the filling process
- **Input new FillAmount**
- **ResumeFilling = 1**
  Meaning : Operator resume the filling process with the new FillAmount

## 2. Start Dosing Silo 2

Silo 2 dosing will be started after DoneDosingSilo1 = 1. 
Silo 2 dosing and filling follows the same logic as silo 1.
 
## 3. Start Mixing

Mixing process will begin when all of the following conditions are met:
- **Silo1DoneDosing = 1**  
  Meaning: Silo 1 dosing process is finished.
- **Silo2DoneDosing = 1**  
  Meaning: Silo 2 dosing process is finished.

When these conditions are met:
- **MixingTimerActive = 1**  
  Meaning: Starts Mixing timer 
- **MixingCoil = 1**  
  Meaning: Mixing motor starts running and mixing the product

The motor will run until:
- MixingTimerDone = 1 which means the Mixer timer is up.

At that point:
- MixingCoil = 0
- DoneMixing = 1

## 4. Start Discharge

Discharge process will begin when DoneMixing = 1

When the condition are met:
- **GateTimerActive = 1**  
  Meaning: Starts Gate timer
- **GateCoil = 1**  
  Meaning: Gate motor starts running and product is in the process of discharging

The motor will run until:
- GateTimerDone = 1 which means the Gate timer is up.

At that point:
- GateCoil = 0
- DoneDischarge = 1

At this point, CycleDone = 1 means the process has reached the end and stops the entire system.

## 5. Safety and Stops

If at any moment during the whole process that an overload/overcurrent happens, then EMGC = 1 which means that the emegency signal is triggered and thesystem will stop completely.
If an operator presses the stop system push button, StopSystem = 1 means that the system will also stop completely.
