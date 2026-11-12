# Frosty Bill of Materials
## MREN 403 · Group 9 · Lynxmotion A4WD1 snow-clearing rover · Updated November 8, 2026

### Use this file to track what we have, what needs to be purchased, and what needs to be fabricated. Update each item’s status and actual cost when it is sourced. Record decisions and bench results below so we can follow how the design changed.


## Budget
All amounts are CAD. Planned amounts are allowances, and the remaining budget depends on final quotes and loan availability.

|Budget Item                             |Amount  |
|----------------------------------------|--------|
|Team Budget                             |$500.00 |
|Planned parts before tax                |$XXX.XX |
|Tax allowance at 13%                    |$XX.XX  |
|Planned total before shipping           |$XX.XX  |
|Available for shipping and price changes|$XX.XX  |
|YTD spend recorded                      |$0.00   |


## Purchase and Quote List
|ID  | Item                              | Qty | Status     | Planned CAD | Actual | Specification                                                                       |
|----|-----------------------------------|-----|------------|-------------|--------|-------------------------------------------------------------------------------------|
|P01 | 3S LiPO Battery with XT60 11.1V   |1    | Requesting | $84.20      |  xxx   |https://ca.robotshop.com/products/lynxmotion-lss-led-module-3s-111v-4000mah-lipo-battery|
|P02 | 5V, 9A Step-Down Voltage Regulator|1    | Requesting | $52.60      | xxx    | buck for pi https://ca.robotshop.com/products/pololu-5v-9a-step-down-voltage-regulator-d24v90f5 |
|P03 | 8A, 200W adjustable stepdown      | 1/2 | Rqeusting| $9.98 ea    | xxx    | buck for servos https://abra-electronics.com/voltage-regulator-modules/dc-dc-step-down-converters/8a-200w-adjustable-step-down-converter-xl4016.html|
|P04 | Cytron MDD3A dual motor driver    | 2   | Requesting| $12.63 ea   | xxx    | The 3S LiPo reaches 12.6 V fully charged. Many common L298N modules have an onboard 5 V regulator that manufacturers recommend disabling when the motor supply exceeds 12 V. Using the Cytron would be easier https://ca.robotshop.com/products/cytron-3a-4-16v-dual-channel-dc-motor-driver|
|P05 | E-S Motor GM37, 12 V, 89 RPM with encoder | 4  | Considering| $19.48 ea  | xxx      | incase we need motors with higher torque if we exceed rover rated weight of 5 lb. https://ca.robotshop.com/products/e-s-motor-gm37-geared-motor-w-encoder-12v-89rpm|
|P06 | Lynxmotion A4WD1 Rover            |1    |Obtained    |Obtained at no cost from 203 | $0.00 | Chassis, including 4 DC motors, wheels, and encoders. |
|P07 | LiDAR Livox Avia                  |1    | Obtained   | Obtained at no cost from Prof. Gammell | $0.00 | LiDAR with Livox Converter 2.0 - so we do not need a buck boost converter  |
|P08 | 12V DC Motor 12kg-cm 350RPM w/Encoder | 4 | Considering | $41.43 ea | xxx | Second option for replacement DC motors, pricier than first option so we will see how much budget remaining| 
|P09 | M9N GPS | 2 | Obtained | Obtained at no cost from Prof. Gammell| $0.00 | GPS https://holybro.com/products/m9n-gps?variant=46575105081533 | 
|P10 | Tenergy TN267 1-4 Cells LiPO/LiFE Balance Charger|1|Requesting|$48.56|xxx|We need this to charge our battery  https://ca.robotshop.com/products/tenergy-tn267-1-4-cells-lipo-life-balance-charge|



## Component Selection and Justification
For our autonomous snow-clearing robot, the electrical power system must supply sufficient power to the Raspberry Pi 5, four DC drive motors, two MG996R plow servos, webcam, and Livox Avia LiDAR.

### Revision 1: 2026-11-12
The proposed design uses one 3S LiPo battery, two adjustable DC-DC buck converters, and two Cytron MDD3A dual-channel motor drivers.

The main goal is to create a power system that is reliable, affordable, relatively simple to integrate, and suitable for a university proof-of-concept rather than a fully commercial outdoor robot.

### 3S 11.1V LiPO Battery (1): 
Why we need it: Portable power to the entire rover, allowing autonomous operation without an external power supply.

Why we chose it:
- 1ts 9.9V-12.6V operating range is compatible with our proposed motor drivers and Livox Converter 2.0
- Provides a relatively lightweight, rechargeable energy source capable of supplying motor and electronics loads.
- A single battery simplifies power distribution compared with separate batteries for motors and electronics.
Compared with alternatives: A 2S battery would provide lower voltage, while a 4S battery reaches 16.8 V fully charged, exceeding the MDD3A's 16 V maximum. A 3S pack is therefore a practical match for our hardware.


### Polulu D24V90F5 5V 9A Step-Down: Provides regulated 5V to the Raspberry Pi 5
Why we need it: The Raspberry Pi 5 requires a stable 5 V supply, while the battery provides a higher, variable voltage.

Why we chose it:
- Fixed 5 V output eliminates the need to manually adjust the voltage.
- Offers substantial current headroom for the Raspberry Pi and connected peripherals.
- Includes reverse-voltage, overcurrent, short-circuit, and thermal protection.
- Efficient switching regulation reduces energy losses and heat.
Compared with the ABRA: We preferred the Pololu for the Pi because its fixed output, integrated protections, and documented performance make it a more predictable power source for our sensitive computing hardware


### ABRA PSM-162 Adjustable 8A Buck: Provides regulated 6V to two MG996R servos
Why we need it: Our MG996R servos require approximately 4.8–6.6 V and cannot be connected directly to the 3S battery.

Why we chose it:
- Adjustable output allows us to set the servo supply to 6 V.
- Advertised 8 A maximum output offers capacity for both servos, subject to thermal limits.
- Lower cost than the Pololu regulator.
- Suitable for supplying our servo subsystem without requiring a more expensive regulator.
Compared with the Pololu: The servos benefit from a 6 V output for greater torque, making the adjustable ABRA more suitable than the fixed 5 V Pololu.


### Cytron MDD3A Drivers: Controls four DC Motors
Why we need them: The Raspberry Pi cannot directly supply the power required by our four DC motors. Motor drivers receive PWM control signals from the Pi and use battery power to control motor speed and direction.

Why we chose them:
- Directly compatible with our 3S battery (4–16 V input).
- Supports 3.3 V Raspberry Pi GPIO control signals.
- Each driver independently controls two motors, so two modules control all four wheels.
- Rated for 3 A continuous and 5 A peak per channel.
- Includes built-in testing buttons, simplifying motor testing before ROS integration.
Compared with the L298N: The MDD3A uses more efficient MOSFET-based circuitry, has lower voltage losses, and eliminates the L298N module's separate 5 V logic-supply complications

## Why do we need two bucks?
Although we could theoretically power the Raspberry Pi and servos from one high-current converter, we selected two separate regulators to improve reliability and allow different output voltages.

|Requirement|Raspberry Pi|Plow Servos|
|-----------|------------|-----------|
|Voltage    | 5V         | 6V optimal|
|Behaviour  | Sensitive to undervoltage | High transient current during movement |
|Selected Converter | Polulu 5V 9A| ARBA adjustable 8A|
|Priority | Stable computing power | Torque and Current delivery |

There are three main reasons for separating them:

### 1. Preventing Raspberry Pi undervoltage

Servos can draw large current spikes, especially when moving a loaded plow or approaching a stall. If the servos and Pi shared one regulator, these spikes could cause voltage dips, resulting in Raspberry Pi resets or interruptions to autonomous operation.

### 2. Different voltage requirements

The Pi needs approximately 5 V, while the MG996R servos can operate at 6 V for improved torque. Two regulators allow us to optimize the voltage for each subsystem.

### 3. Easier testing and troubleshooting

Separate power branches allow us to independently test the computing system and plow mechanism. Problems with the servo power supply are less likely to affect the Pi.

The additional converter increases cost slightly, but provides worthwhile reliability benefits for autonomous operation.

## Why Cytron MDD3A instead of other motor drivers?
We considered retaining the existing L298N driver, but selected two Cytron MDD3A modules as a more suitable solution.

| Feature | L298N | Cytron MDD3A |
|---|---|---|
| Motor control channels | 2 | 2 |
| Technology | Bipolar-transistor H-bridge | MOSFET H-bridge |
| Efficiency | Lower, higher voltage losses | Higher, lower voltage losses |
| Raspberry Pi GPIO compatibility | Requires additional considerations | Direct 3.3 V compatibility |
| Logic power supply | Regulator/jumper configuration | No separate 5 V logic input required |
| Built-in motor testing | Module-dependent | Dedicated onboard buttons |
| Integration complexity | Greater | Lower |

**Why we selected the Cytron MDD3A:** The Cytron offers more efficient motor control, reduced voltage losses, direct compatibility with the Raspberry Pi's 3.3 V GPIO signals, and simpler wiring. Two MDD3A modules provide independent control of all four drive motors.

**Note:** Motor current requirements must be verified against the MDD3A's 3 A continuous and 5 A peak per-channel ratings.
