# Frosty Bill of Materials
## MREN 403 · Group 9 · Lynxmotion A4WD1 snow-clearing rover · Updated November 8, 2026

### Use this file to track what we have, what needs to be purchased, and what needs to be fabricated. Update each item’s status and actual cost when it is sourced. Record decisions and bench results below so we can follow how the design changed.


### Budget
All amounts are CAD. Planned amounts are allowances, and the remaining budget depends on final quotes and loan availability.

|Budget Item                             |Amount  |
|----------------------------------------|--------|
|Team Budget                             |$500.00 |
|Planned parts before tax                |$XXX.XX |
|Tax allowance at 13%                    |$XX.XX  |
|Planned total before shipping           |$XX.XX  |
|Available for shipping and price changes|$XX.XX  |
|YTD spend recorded                      |$0.00   |


### Purchase and Quote List
|ID  | Item                              | Qty | Status     | Planned CAD | Actual | Specification                                                                       |
|----|-----------------------------------|-----|------------|-------------|--------|-------------------------------------------------------------------------------------|
|P01 | 3S LiPO Battery with XT60 11.1V   |1    | Requesting | $84.20      |  xxx   |https://ca.robotshop.com/products/lynxmotion-lss-led-module-3s-111v-4000mah-lipo-battery|
|P02 | 5V, 9A Step-Down Voltage Regulator|1    | Requesting | $52.60      | xxx    | buck for pi https://ca.robotshop.com/products/pololu-5v-9a-step-down-voltage-regulator-d24v90f5 |
|P03 | 8A, 200W adjustable stepdown      | 1/2 | Rqeusting| $9.98 ea    | xxx    | buck for servos https://abra-electronics.com/voltage-regulator-modules/dc-dc-step-down-converters/8a-200w-adjustable-step-down-converter-xl4016.html|
|P04 | Cytron MDD3A dual motor driver    | 2   | Requesting| $12.63 ea   | xxx    | The 3S LiPo reaches 12.6 V fully charged. Many common L298N modules have an onboard 5 V regulator that manufacturers recommend disabling when the motor supply exceeds 12 V. Using the Cytron would be easier https://ca.robotshop.com/products/cytron-3a-4-16v-dual-channel-dc-motor-driver|
|P05 | E-S Motor GM37, 12 V, 89 RPM with encoder | 4  | Considering| $19.48 ea  | xxx      | incase we need motors with higher torque https://ca.robotshop.com/products/e-s-motor-gm37-geared-motor-w-encoder-12v-89rpm|
|P06 | Lynxmotion A4WD1 Rover            |1    |Obtained    |Obtained at no cost from 203 | $0.00 | Chassis, including 4 DC motors, wheels, and encoders. |
|P07 | LiDAR Livox Avia                  |1    | Obtained   | Obtained at no cost from Prof. Gammell | $0.00 | LiDAR with Livox Converter 2.0 - so we do not need a buck boost converter  |
|P08 | 12V DC Motor 12kg-cm 350RPM w/Encoder | 4 | Considering | $41.43 ea | xxx | Second option for replacement DC motors, pricier than first option so we will see how much budget remaining| 
|P09 | M9N GPS | 2 | Obtained | Obtained at no cost from Prof. Gammell| $0.00 | GPS https://holybro.com/products/m9n-gps?variant=46575105081533 | 
