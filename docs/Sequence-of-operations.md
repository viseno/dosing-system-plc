The Sequence Of Operation (SOO) consists of several major stages.
## 1. Starting Conditions
- All motors and actuators are off.
- All indicators are off.
- Available amount are known through analyzer-load cells.
- Operators set the required amount from each silo.
- System compares the available and required amount (if the available amount is less than the required amount, NotEnough and FillActive indicator turns on)
- Operator presses start system push button

## 2. Start Dosing Silo 1
1. If NotEnough and FillActive Indicator turn on, then
### 1. Start Filling Silo 1
    - Operator input FillAmount or presses the repeat fill button (to repeat filling the same amount as before)
    - Operator presses start filling push button
    - Start filling by turning on Elevator 1 motor coil (Elev1MotorCoil = 1)
    - Continuosly compare the value between AmountFilled and FillAmount
    - When AmountFilled >= FillAmount, stop stop filling by turning off Elevator 1 motor coil (Elev1MotorCoil = 0) and turn on done filling silo 1 signal
    - If the NotEnough indicator is still on, repeat the filling silo 1 process
    - If operator wants to change the FillAmount during filling process (Elev1MotorCoil = 1), then press the stop filling push button, change the input FillAmount, then press the resume filling push button.
2. (This section will only happen after NotEnough = 0 and FillActive = 0) Start Extracting liquid from silo 1 by turning on spiral 1 motor (Spiral1Motor = 1).
3. Continuously compare the value between extracted amount and reqired amount.
4. When extracted amount >= required amount, turn off spiral 1 motor (Spiral1Motor = 0) and turn on done dosing silo 1 signal.
5. Give start dosing silo 2 signal.

## 3. Start Dosing Silo 2
1. If NotEnough and FillActive Indicator turn on, then
### 1. Start Filling Silo 2
    - Operator input FillAmount or presses the repeat fill button (to repeat filling the same amount as before)
    - Operator presses start filling push button
    - Start filling by turning on Elevator 1 motor coil (Elev1MotorCoil = 1)
    - Continuosly compare the value between AmountFilled and FillAmount
    - When AmountFilled >= FillAmount, stop stop filling by turning off Elevator 1 motor coil (Elev1MotorCoil = 0) and turn on done filling silo 2 signal
    - If the NotEnough indicator is still on, repeat the filling silo 2 process
    - If operator wants to change the FillAmount during filling process (Elev1MotorCoil = 1), then press the stop filling push button, change the input FillAmount, then press the resume filling push button.
2. (This section will only happen after NotEnough = 0 and FillActive = 0) Start Extracting liquid from silo 2 by turning on spiral 2 motor (Spiral1Motor = 1).
3. Continuously compare the value between extracted amount and reqired amount.
4. When extracted amount >= required amount, turn off spiral 2 motor (Spiral1Motor = 0) and turn on done dosing silo 2 signal.
5. Give start mixing signal.

## 3. Start Mixing
1. Start mixer timer (MixerTimerActive = 1) and mixer coil (MixerCoil = 1)
2. When MixerTimerDone = 1, turn off mixer coil (MixerCoil = 0) and DoneMixing = 1
3. Give start discharge signal

## 4. Start Discharge process
1. Start gate timer (GateTimerActive = 1) and gate coil (GateCoil = 1)
2. When GateTimerDone = 1, turn off gate coil (GateCoil = 0) and CloseGate = 1
3. End of process

NB: In along any of the process there is an overload from any of the motor or the stop system push button is pressed, the whole system will stop and pressing start system push button will repeat the whole system from the beginning
