# Ernest

### Atmospheric data collector and thermostat

**This code / schematics are currently undergoing frequent revision!**
**NO guarantees that it is a working system as of yet.**

A while ago I put together the [Arnest](https://github.com/rschlaikjer/ArNest)
, which was a nice simple alternative to
other smart thermostat systems that was compatible with the old wiring in my
apartment. It worked, but I couldn't keep track of the temperature at more than
one point in the apartment. I was also interested to see what other atmospheric
data could be collected by a network of sensors. mostly because graphs are cool.

This project is the next step - moving from a single unit that does temp
readings and then controls the heater relay to a multi-point system that reads
various data and communicates them to a base station, which aggregates and sends
the information to a server that stores the readings and acts as control.

To that end, there are four subrepos of Ernest:
- [Slave Node Scheamatics](https://github.com/rschlaikjer/ernest-slave-eagle).
    The 'slave' nodes are the data collectors,
    equipped with temperature, barometric pressure and humidity sensors
    as well as a 2.4GHz radio transciever for communicating with the base
    station. I've tried to make these relatively inexpensive to build, since you
    will most likely want a couple of them.
- [Slave Node Code](https://github.com/rschlaikjer/ernest-slave-code).
    The control program for the slave nodes in Arduino code.
    The original version of the slave node used an entire Arduino Micro, but to
    reduce cost rev4 uses a bare ATMEGA328-P. The tip of these two repos may not
    be in sync, so be sure to check pin definitions when building this yourself.
- [Master Node Code](https://github.com/rschlaikjer/ernest-master-code).
    The master node simply listens for data on the radio and
    posts it to a managing server. There's no integrated schematic for this yet,
    but it's simple enough to construct one out of an arduino.
- [Server Code](https://github.com/rschlaikjer/ernest-server).
    The server interacts with the master node, tracking the
    collected data and making the decision of whether or not the master node
    should activate the furnace.

## Pictures
### First slave node revision
![First Version](/rev1.jpg?raw=true "Early prototype")

### Schematics for slave rev4
![Schematic](/ernest_schematic.png?raw=true "Schematic")

![Board Layout](/ernest_board.png?raw=true "Board Layout")

