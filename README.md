## Ham Transceiver Power Supply

<p align="center">
<img src="./img/front_main.jpg" width="1000" height="300"/>
</p> 

## Credits

*   Zygi SP5ELA for advise on what server power supply is easiest to modify
*   Patryk SP5GPK for pointing out the good quality guide describing in detail HP power supply modification steps
*   Robert DJ3KJ for excellent youtube video describing original server power supply modification
*   Krzysztof SP5OXF for suggesting Transil based overvoltage protection method

## Project Scope

This is a very simple project aiming to modify HP HSTNS-PL14 server switch-mode power supply (originally rated as 460W, 12V/38.3A) so it is capable of supplying 13.8V and about 33A of current. Additionally the power supply has been enhaced with:
*   power switch, which turns off entire unit by cutting off AC power
*   PZEM-051 based multimeter capable of measuring voltage, current, power and energy consumption
*   15V transil based overvoltage protection
*   safe chassis

## Design Details

The most difficult part of this project is to perform modification of HP HSTNS-PL14 so it is capable of producing 13.8V voltage level.
This step is very well described in youtube video [1] by Robert DJ3KJ , but due to very small size of smd components involved it requires magnification glass (or at least mobile phone with magnifying glass application) and a lot of manual skills.
In the refenernced video author suggests the following four modifications:

*   Bridging of control pins to allow power supply to start after AC power is supplied. It is very tempting to put power switch in series to the resistor, but such design is not optimal since switch placed here will not turn off entire power supply unit, leaving e.g. fun running even if power switch is off...

<p align="center">
<img src="./img/HP_Pwr_Supp_Modification_Step1.png" width="600" height="400"/>
</p>

*   Bridging one of SMD resistors to increse original output voltage range from 11.8-12.7 up to 13.8V 

<p align="center">
<img src="./img/HP_Pwr_Supp_Modification_Step2.png" width="600" height="400"/>
<img src="./img/HP_Pwr_Supp_Modification_Step2a.png" width="600" height="400"/>
</p>

*   Adding external resistor of 5.6k as depicted on the picture below to further increase output voltage to 13.4-14V. This step did not work for me,
 i.e. adding this resistor prevented the power supply from starting up. According to original post [1] lowering external resistor value to 4.7k would increase output voltage range further to 13.9-15V, this option was not however tested by myself. 

<p align="center">
<img src="./img/HP_Pwr_Supp_Modification_Step3.png" width="600" height="400"/>
</p>

*   Increase of overvoltage protection by adjusting potentiometer shown below:

<p align="center">
<img src="./img/HP_Pwr_Supp_Modification_Step4.png" width="600" height="400"/>
</p>

High level block/circuit diagram can be found below:

<p align="center">
<img src="./img/PWR_Supp_Circuit_Diagram.png" width="800" height="600"/>
</p>

Due to DC current of up to 33A expected at the output of power supply, all cabling is screw mounted (M4), cables used are LgY 4.00mm (except those connecting multimeter, which are LgY 0.50mm), for easy reconfiguration fork connectors clamped on the cables were used.

Bananna plugs used are 50A/60V rated (more robust version then those found in orginary equipment).

Interconnecting PZEM-051 multimeter unit is relatively easy. It is enough to follow cabling drawing on the back of the unit.

When physically mounting PZEM multimeter it is important to keep microswitch to the right of the panel.

Overvoltage protection is implemented using transil diode D1 1.5KE-15 [2]. When used as overvoltage protection, transil is connected in reverse polarity. When voltage applied  to this component is smaller then Ubr (breakdown voltage) the diode does not conduct significantly, allowing only small leakage current Ib to pass through. When voltage on the diode reaches Ubr, the diode transitions rapidly to low impedance state allowing high current Ib to pass through while stabilizing diode voltage at around Ubr and effectively clamping voltage applied to protected circuit. At this stage fuse F2 shall be blown as well.
Note that when connected in forward polarity the transil behaves as regular diode.

Mechanical design has been shown on the following pictures:

<p align="center">
<img src="./img/internals_2.jpg" width="800" height="600"/>
</p>

<p align="center">
<img src="./img/front_1.jpg" width="600" height="400"/>
</p>

<p align="center">
<img src="./img/back_1.jpg" width="600" height="400"/>
</p>

## Transceiver Power Consumption Measurements
One application of installed multimeter is indication of both current and power consumption for by your transceiver. Summary of such measurements for my unit AnyTone AT-5888UV has been summarized below:

<p align="center">
<img src="./meas/Power_Consumption_Measurements.png" width="600" height="800"/>
</p>

## References

[1] HP power supply modification youtube instruction by Robert (DJ3KJ) - https://www.youtube.com/watch?v=KWyucJ1VKY4

[2] [Transil application notes](<./docs/Application_Notes/>)

[3] PZEM-051 multimeter review by Robojax - https://www.youtube.com/watch?v=tgneN2hzRe0

[4] [Hardware BoM for this project](<./docs/Power_Supply_BoM.xlsx >)