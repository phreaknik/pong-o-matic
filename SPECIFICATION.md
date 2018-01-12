# Project Specification
## Functional Overview
The objective of this project is to develop a device(s) that can be attached to a ping pong table to assist with score keeping, player serve order, and other useful statistics. the system should be easy to attach to any table, reliably be able to detect and monitor game play, and provide useful information to the players in real time.

### Core Features
* Detect which side of the table a ball strikes to track information about which player serves and which player wins each volley.
* Display current score to players.
* Indicate which player's turn it is to serve.
* Keypad with buttons to allow:
  * Allow players to "redo" a volley.
  * Allow players to cancel a game.
  * Allow players to indicate a "let" serve.
  * Keypad should be forward thinking, to accommodate for future features in the [Optional Features list](#optional-features).

### Optional Features
* Player identification system (RFID badge, user ID, etc).
* Player stats calculation.
* Wireless connectivity to upload data to cloud service.

## System Description
### Camera module
A camera & compute module mounted on the ceiling above the table. This module will be the "central controller" of the whole system. This module will use machine vision to detect and track the ball as players hit it back and forth. Machine vision can be done using an [OpenMV sensor](https://www.openmv.io).

This overhead module will also comunicate to the display units mounted under the table on each player's side of the table. This communication could be via BLE or IR. Display information such as score, current server, etc will be relayed to the display units. The display units will also include an accelerometer, to communicate exactly when the ball strikes the table. This is necessary, because one camera above the table will have no depth detection, and may frequently be unable to tell when a ball actually strikes the surface.

The camera + machine vision data and the sensor data from the display module can be used by an "application compute" module to calculate which things like player score, current server, player stastics, etc. This can be done by a cheap SBC (Onion Omega, Rasperry PI, BeagleBone Black, etc).

Camera Module BOM:
* [OpenMV sensor](https://www.openmv.io)
* BLE / IR comms
* Onion Omega / Raspberry PI / BeagleBone for application compute

### Display module
