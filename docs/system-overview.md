This project is an automated dosing and mixing system delevoped with PLC programming on CODESYS platform.
The system doses from 2 different silos containing 2 different liquid material, mixes the material in a mixing tank and eventually discharge it through a gate system.

This projects demonstrate an understanding in a typical industrial automation concepts such as:
1. sequencial control
2. Interlocks
3. Timer-based operations
4. Actuator controls (motor coils)
5. State transition
6. Batch processing logic
7. Weight-based dosing

This system is mainly used in industries such as food and beverage (F&B), chemicals, liquid mixing, etc.

The system is consists of several components including:
1. Silo 1 & 2
   These silo contains different liquid that will be mixed according to a certain ratio between them in the mixer. Each of these silo consists of components such as load cells (to measure the weight of the liquid inside each silo),
   Spiral motor (acts as an actuator to extract a certain amount of liquid from each silo), Circuit Breaker to protect from overcurrent and overload
2. Elevator 1 & 2
   These Elevator are used to fill each of the silo when given a certain signal. Each elevator consist of a motor that will carry the liquid and fill it to the corresponding silo), Circuit Breaker to protect from overcurrent and overload
3. Mixer
   The Mixer consist of a mechanical agitator that will be used to mix the liquid inside the mixing silo. A timer is also present to provide a "done mixing signal", Circuit Breaker to protect from overcurrent and overload
4. Gate
   The Gate is used to release the mixed product into the next process (stage). The Gate consist of a gate actuator (open/close coil). A timer is also present to provide a "close gate signal", Circuit Breaker to protect from overcurrent and overload
5. SCADA-HMI
   The SCADA system is connected to the PLC through an OPC UA communication protocol and a HMI display to control the entire system. The HMI consist of components such as indicators (lights, graphic displays, LED displays) and actuators (Push Buttons, nominal input),
   Circuit Breaker to protect from overcurrent and overload

The major sequence in this system is the following:
1. Start System
2. Dose material from Silo 1
3. Dose material from Silo 2
4. Start Mixing both materials in the Mixer
5. Mix for a certain time
6. Open gate to discharge product
7. Close gate and end process

To ensure safety of the system, interlocks are introduced:
1. Dosing of each silo will only happen if the there is enough liquid in the silo and the filling activate indicator for that certain silo is not active.
2. Any overload of from the motor will trip the emergency (EMGC) signal and stops all current process.
3. Stop system (PB) and Emergency (PB) will stops entire process instantly.
4. Any particular process/steps will only be executed after a done signal is sent from the previous process.
