# open-ventilator
open source mechanical ventilator for educational purposes

### background
The goal of this project is to build a simple mechanical ventilator that facilitates understanding of the mechanics and technology in modern ventilators. The purpose is pedagogical; ***this is not intended for medical or veterinary use.***

Mechanical ventilators are complex machines. Often the best way to understand the nuances of a complex machine is to tinker with a simple open-source version. Unfortunately, ***_ventilators aren't cheap_*** (even the lowest cost veterinary ventilator will typically set you back at least $500) and ***_no open source ventilator exists_***. This makes it hard for medical personnel (physicians, nurses, respiratory therapists, etc) and biomedical engineers to fully [grok](https://en.wikipedia.org/wiki/Grok) the technology they are working with and depend upon.

![](https://ars.els-cdn.com/content/image/3-s2.0-B9780323390064000259-f25-15-9780323390064.jpg)
![](https://clinicalgate.com/wp-content/uploads/2015/02/B9780702030949000103_f010-001-9780702030949.jpg)

The purpose of this project is to build a simple, open-source, mechanical ventilator (hardware, control system, and interface) that can be used as a starting point for biomedical engineers and healthcare professionals to understand mechanical ventilation.

For a primer on mechanical ventilation see [here](). For a history of how modern mechanical ventilators have evolved see [here]().


### components
There are three key components of the ***open-ventilator***:
* the ***_hardware_*** - servo to force air into/out of a cylinder, solenoid valves to control airflow, and pressure sensors
* the ***_control system_*** - a microcontroller (e.g. [Arduino Micro](https://store.arduino.cc/usa/arduino-micro) that controls the hardware; ideally this should be a realtime system to enable quick and reliable responses
* the ***_user interface_*** - a single board computer (e.g. [RasPi 4](https://www.raspberrypi.org/blog/raspberry-pi-4-on-sale-now-from-35/)) connected to a touchscreen LCD display

![high level system architecture](https://github.com/nickmmark/open-ventilator/blob/master/figures/open_vent_components.png)

### project objectives
The ideal project would be able to:
* provide mandatory ***volume control*** ventilation - deliver a ```tidal volume``` at a set ```rate```
* provide mandator ***pressure control*** ventilation - deliver a ```inspiratory pressure``` for a ```inspiratory time``` at a set ```rate```
* allow triggered breathing, such as ***pressure support*** - deliver an ```inspiratory pressure``` every time a breath is detected using a pressure trigger
* perform simple respiratory maneuvers such as ***plateau pressure*** - deliver a breath and measure the pressure
* alert to unsafe conditions (e.g. ***alarms***): peak pressure alarm, low volume alarm, etc
* stream the data over a serial connection to an attached computer
* display data and allow settings to be changed on a touchscreen  display



### hardware
- use an open source pump as a starting point; for example the [programmable-air](https://www.crowdsupply.com/tinkrmind/programmable-air) project includes a simple hardware and [arduino compatible software package](https://github.com/programmable-air/code).
- another option is to use an [open source syringe pusher](https://www.appropedia.org/Open-source_syringe_pump) which includes [files for 3d printing](https://www.youmagine.com/designs/syringe-pump) and the [arduino code](https://github.com/naroom/OpenSyringePump)

### control system
* will likely use an Arduino and build a ```open-ventilator``` library to control the system. The [library](https://www.arduino.cc/en/hacking/libraries) that controls the microcontrolled would be extremely useful for understanding a operation of a mechanical ventilator. The library could enable commands at different levels of abstraction:
  * ***direct control of components*** - e.g. ```inspiratoryValve == OPEN``` (set the valve on the inspiratory circuit to open)
  * ***coordinated activation of components*** - e.g. ```deliverPressureBreath (pressure = 30, iTime = 1, alarms = TRUE)``` (deliver a breath with a pressure of 30 cmH2O over 1 second)
  * ***automated delivery of ventilation*** - e.g. ```volumeControlStart (rate = 12, volume = 500)``` (begins volume control ventilation at a rate of 12 breaths per minute and a tidal volume of 500cc per breath)
  * ***administering advanced ventilatory maneuvers*** - e.g. ```inspiratoryHold()``` (deliver a breath, close the inspiratory and expiratory valves, and measure the airway pressure continuously)

[figure - abstraction layers]

### user interface
* the ideal user interface should be intuitive and straightforward
* ideas
  * consistently color code the core concepts, both in the graphs and in the settings, so users connect a particular color to a particular concept:
    ```diff 
    + volume 
    - pressure 
    * flow
    ```
  * imagine this curve with each colored appropriately:
  ![](https://lh3.googleusercontent.com/proxy/WUhVWTUumVW4bOodXZmHeIo4K67XV_GO7d9ewP4P1pYKJGdfexay6J5e0IxfQQRPA6MgzgbxwnXk4RnAxDREs4FhQFLFCvH-wmwuNvuzVcQox8liPScmKX-PLKYkFENs-zMCHG5LDeo1NnZqdy8)

### references
* [A Portable Ventilator with Integrated Physiologic Monitoring for Hyperpolarized 129Xe MRI in Rodents](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6719309/)
* [Open-Source Syringe Pump Library](https://www.appropedia.org/Open-source_syringe_pump)
* [Programmable Air](https://www.programmableair.com/)
https://i2.wp.com/makerfaire.com/wp-content/uploads/gravity_forms/208-6bb1cbe29fec28d54a67e4aeaf9487ea/2018/09/Programmable-Air-PCB-Render.jpg?fit=750%2C500&strip=all&ssl=1
* [Advanced Ventilator Modes](https://www.sap.org.ar/docs/congresos_2014/Emergencias%20y%20Cuidados%20Criticos/PDFs/venkataraman_modos_ventilatorios_avanzados.pdf)
