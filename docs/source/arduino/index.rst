.. _arduino:

===============
Arduino 
===============

Introduction
-------------

In this page you will find everything you need to know about the arduino used in the Donnie robot. 
You'll learn how to assembly and manufacture the arduino part, how the firmware works in it  
and everything else related to the arduino.

Assembly the Arduino Part
-------------
Donnie's PCB
------------

The `repository <https://github.com/lsa-pucrs/donnie-assistive-robot-hw>`__ 
has all files related to Donnie's hardware (PCB design,
schematics, eletrical diagrams, gerber files, BOM files). Donnie has two
daugther boards (or 'shields'). One for the Arduino Mega and the other for 
the Raspberry Pi.

| The following image shows Donnie's brain and its electronics.
| |Meet Donnie Brain!!!|

Manufacturing the boards
------------------------

Send the Gerber for manufacturing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you just want to manufacture these boards as they are, we recommend
the following steps:

1. Send the Gerber ZIP files
   (`arduino-shield <https://github.com/lsa-pucrs/donnie-assistive-robot-hw/blob/master/ard-shield/gerbers/ard_shield-160322-gerbers.zip>`__
   and
   `raspberrypi-shield <https://github.com/lsa-pucrs/donnie-assistive-robot-hw/blob/master/rasp-shield/gerber_files/rasp_shield-gerber_files-160118.zip>`__)
   to manufacture to Seeedstudio. You should use the following tutorial
   `Fusion PCB Order Submission
   Guidelines <http://support.seeedstudio.com/knowledgebase/articles/422482-fusion-pcb-order-submission-guidelines>`__

Arduino Shield
~~~~~~~~~~~~~

.. image:: ArduinoShield.jpg

Raspberry Pi Shield
~~~~~~~~~~~
.. image:: RaspShield.jpg

Assembly
~~~~~~~~

After you receive the PCBs, then follow these steps to assemble the
boards:

1. First of all, separe and buy the components indicated in BOM file
   (`arduino-shield <https://github.com/lsa-pucrs/donnie-assistive-robot-hw/blob/master/ard-shield/BOM.txt>`__ and
   `raspberrypi-shield <https://github.com/lsa-pucrs/donnie-assistive-robot-hw/blob/master/rasp-shield/BOM.txt>`__);
2. Print the PDF schemmatic and BOM file;
3. Place and weld the componnects in the PCB with the BOM's indicated
   PART.

Change the PCB Design
---------------------

If you want to change the PCB design, we recommend to use Eagle version
XYZ.

.. |Meet Donnie Brain!!!| image:: donnie-elet3.png

Arduino Firmware
-------------

Before explaining how the arduino firmware arrangement works,
it’s important to learn a little about where the firmware takes 
place throughout the project.
There is the high level language called 
`GoDonnie <https://donnie-user-manual.readthedocs.io/en/stable/docs/godonnie/index.html>`__,
which connects with the Stage and the simulated robot or with the physical robot. 
When this connection is established with the physical robot the Raspberry Pi, 
that communicates with the language, translates the high level commands 
into lower level commands and then sends them to the arduino. The arduino, 
in turn, commands directly the sensors and the actuators of the physical robot.


.. image:: firmware.png


The firmware is the code that intermediate between the GoDonnie 
language and the hardware device, and it runs in the arduino.
The arduino firmware it’s directly connected with the Raspberry Pi, 
which sends commands to the arduino that causes the motors to move 
and the sensors to function. Shortly thereafter the arduino sends back 
to the Raspberry Pi the information obtained by the sensors. The 
`Player <https://playerstage-manual.readthedocs.io/en/latest/>`__
server runs in the Rasp, which is connected with the GoDonnie 
through the computer. The robot’s camera is also connected through 
the Rasp, that receives the image from the camera and sends to the 
Player, which processes the images.

Finnaly, to make your robot work you'll need to upload the `.ino file <https://github.com/lsa-pucrs/donnie-assistive-robot-sw/blob/devel/firmware/donnie/firmware/firmware.ino>`__ 
into the arduino. 