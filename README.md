# open-ventilator
open source mechanical ventilator for educational purposes

### background
The goal of this project is to build a simple mechanical ventilator that facilitates understanding of the mechanics and technology in modern ventilators. The purpose is pedagogical; ***this is not intended for medical or veterinary use.***

The ideal project would be able to demonstrate:
* volume control ventilation
* pressure control ventilation
* simple respiratory maneuvers (plateau pressure)
* rudimentary alarms (peak pressure alarm, low volume alarm, etc)
* a simple graphical display (either via serial connection to a computer or on a small attached LCD dispay)

This project is a starting point for building open-source educational ventilators and potentially developing an arduino library for controlling them. 


### components

- mechanical pump
- pneumotachymeter
- pressure sensor
- inspiratory/expiratory valve


### ideas
- use an open source pump as a starting point; for example the [programmable-air](https://www.crowdsupply.com/tinkrmind/programmable-air) project includes a simple hardware and [arduino compatible software package](https://github.com/programmable-air/code).
- another option is to use an [open source syringe pusher](https://www.appropedia.org/Open-source_syringe_pump) which includes [files for 3d printing](https://www.youmagine.com/designs/syringe-pump) and the [arduino code](https://github.com/naroom/OpenSyringePump)


### references
* [A Portable Ventilator with Integrated Physiologic Monitoring for Hyperpolarized 129Xe MRI in Rodents](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6719309/)
* [Open-Source Syringe Pump Library](https://www.appropedia.org/Open-source_syringe_pump)
* [Programmable Air](https://www.programmableair.com/)

