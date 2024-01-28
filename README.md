# Ham Transceiver Power Supply

<p align="center">
<img src="./img/front_main.jpg" width="1000" height="300"/>
</p> 

## Credits

## Design Overview

Implementation of crystal radio in its simplest form does not include active amplifier and that is why can function without external power supply. 

<p align="center">
<img src="./img/internals_2.jpg" width="800" height="600"/>
</p>

<p align="center">
<img src="./img/PWR_Supp_Circuit_Diagram.png" width="800" height="600"/>
</p>

There are three building blocks of such radio: bandpass filter based on RLC circuit, detector/demodulator stage and high impedance headphones (common today 32ohm headphones can be used as well, but would require amplification stage).

<p align="center">
<img src="./img/front_1.jpg" width="600" height="400"/>
</p>

<p align="center">
<img src="./img/back_1.jpg" width="600" height="400"/>
</p>

## Transceiver Power Consumption Measurements
<p align="center">
<img src="./meas/Power_Consumption_Measurements.png" width="600" height="400"/>
</p>

## References