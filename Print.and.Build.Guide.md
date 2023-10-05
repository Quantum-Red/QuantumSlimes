# V4 Print and Build Guide
So you want to build a QuantumSlime tracker, huh? Well, you've come to the right place.

For a list of components and how to source them, refer back to the [release page](https://github.com/Quantum-Red/QuantumSlimes/releases/tag/V4).

## What files to print
You will need to print [`V4.Case.Top.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/V4.Case.Top.stl), [`V4.Case.Bottom.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/V4.Case.Bottom.stl), and [`V4.Components.Plate.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/V4.Components.Plate.stl) for the case, and then a [mounting plate](https://github.com/Quantum-Red/QuantumSlimes/tree/main/V4/Mounting%20Plates) to be able to attach the tracker to your body. Choose from one of the [already available mounting plates](https://github.com/Quantum-Red/QuantumSlimes/tree/main/V4/Mounting%20Plates) or download and modify [`V4.Template.Mounting.Plate.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/Mounting%20Plates/V4.Template.Mounting.Plate.stl) to design your own mounting solution. If you do end up making your own design, please share it with the community by uploading it in a pull request to the [mounting plates directory](https://github.com/Quantum-Red/QuantumSlimes/tree/main/V4/Mounting%20Plates).

___

## Recommended printer settings
_(Tested with PLA+ fillament)_

For `V4.Case.Top.stl`, `V4.Case.Bottom.stl`, and `V4.Components.Plate.stl`, these are the settings I recommend:
Layer height | 0.16mm
:--- | :---:
**Infill density** | **15-30%**
**Print cooling** | **yes**
**Generate support** | **no**
**Build plate adhesion** | **optional**

For `Mounting Plate`, these are the settings I recommend:
Layer height | 0.16mm
:--- | :---:
**Infill density** | **100%**
**Print cooling** | **no**
**Generate support** | **yes**
**Build plate adhesion** | **optional**

Any other print settings will be up to you and what works best for your printer and material.

___

## Assembly
So now that you've got all your parts printed out and all your electronics have arrived in the mail, it's time to start putting it all together into a working tracker! (If you haven't purchased your parts yet, check the [parts list](https://github.com/Quantum-Red/QuantumSlimes/releases/tag/V4) first before continuing)

Tools you'll need:
- Soldering iron
- Solder (flux core solder highly recommended)
- Flux (if your solder is not flux core)
- 24 gauge wire (stranded wire over solid core is preferred)
- Wire strippers (or scissors/knife if you're very, *very* careful)
- M3 Allen wrench/hex key
- Soldering station or helping hands (optional, but highly recommended)

_Now let's get started!_

While this guide is meant to be read along step-by-step while building, I encourage you to first scan through the pictures so that you know how everything is supposed to go together in the end.

###### NOTE: This build guide is for a single standalone tracker with no auxiliary tracker. Once I design and build one myself, I'll write a separate build guide for that.

### Step 0 - CAUTION
Do you currently have caffeine in your system? If yes, then I recommend doing this later, as caffeine jitters will make soldering very hard. Anything that will affect your ability to hold things still will make soldering everything together much harder and increase the chance of accidentally slipping and melting a bit of the case or burning a component. Also, try and not burn yourself, that's bad. And if you're using ABS or another plastic that releases toxic fumes when melted, don't go burning the casing, or better yet, work in a well-ventilated space. You have been warned.

___

### Step 1 - Prep 3D prints
Remove any support material, stringing, or minor defects from your 3D prints. There will be support material underneath the clips on the mounting plate, so make sure to remove that.

![print_layout.jpeg](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/print_layout.jpeg "print_layout.jpeg")

___

### Step 2 - Insert battery and prep TP4056
Insert the battery (in my case face-down) so that the wires come out on the top left side, as shown in the photo below. Cut the wires fairly short so that they won't get in the way, but not so short that you don't have enough length. You may want to line up the TP4056 with where it will go so that you can make sure to cut your wires to the proper length. Black wire goes to `B-` and red wire goes to `B+`.

Once you've cut your wires, strip them to expose roughly 1.2-2.0 mm of wire. Then, take your TP4056 away from the case and pre-solder the 4 terminals at the back of the board (the ones with the wires coming out of them in the picture below). Then, solder the battery wires to the TP4056.

*Throughout this guide, make sure to solder away from any other component or the case, especially the battery. If you need to remove a component temporarily to solder it, do it.*

![insert_battery.jpeg](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/insert_battery.jpeg "insert_battery.jpeg")

___

### Step 3 - Inserting mounting plate and wiring up TP4056 and switch to D1-Mini
Insert the mounting plate into the case above the battery. The plate should snap into place on either side of the case where there are slots for the plate to go. Then, insert the TP4056 and switch as shown below. Make sure to keep the switch in its right position, as this is off. You don't want to accidentally turn that on while working on the rest of the build.

Next, measure out wires for the `OUT+` to `switch-left-pin`, `switch-middle-pin` to `5V`, and `OUT-` to `G`, as shown in the picture below. It is important that the wires go out exactly the same way as shown, as running them another way will cause clearance issues. The `OUT-` to `switch-left-pin` must run over the USB-C port, as taking a more direct route would interfere with the D1-Mini once it's in position. The `switch-middle-pin` to `5V` wire must run around the mounting plate as shown, otherwise it will also interfere with the D1-Mini once it's in position.

Once everything is to length, remove the components from the components plate and pre-solder all the pads you will need. You will need to apply solder to holes `5V`, `G`, `D2`, `D1`, `3V3`, and `D5` on the D1-Mini. Next, solder the wire from `OUT-` to `G` as shown below, and solder individual wires to `5V` and `OUT+`. To solder these wires from `5V` and `OUT+` to the switch, heat up the pin on the switch and apply solder till the hole is filled. Then, melt the solder and insert the wire. Make sure to bend the wires down on the switch as shown below to avoid clearance issues with the D1-Mini.

![wire_tp4056_switch_d1mini.jpeg](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/wire_tp4056_switch_d1mini.jpeg "wire_tp4056_switch_d1mini.jpeg")

___

### Step 4 - Insert D1-Mini
Insert the D1-Mini into the mounting plate as shown below. The metal casing on the board should slot into the matching-sized hole on the mounting plate.

![insert_d1mini.gif](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/insert_d1mini.gif "insert_d1mini.gif")

___

### Step 5 - Insert IMU
Pre-solder pins `VCC`, `GND`, `SCL`, `SDA`, and `INT` on your IMU. Then, insert the IMU (in my case, a GY-BNO08X) into the slot at the back of the case. The surface-mounted chips should face away from the battery, with the row of pins facing upwards. If you're having trouble getting it in all the way, try holding a soldering iron near the slot to slightly melt and expand it. Printer tolerances can cause hole openings to shrink slightly, making it difficult to fit things through. You'll know the IMU is all the way in when it's just about level height-wise with the micro-usb port on the D1-Mini.

![insert_imu.jpeg](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/insert_imu.jpeg "insert_imu.jpeg")

___

### Step 6 - Wiring up IMU to D1-Mini
_You're almost done, this is the last soldering you need to do! You've got this :)_

I recommend soldering these wires from left to right on the IMU in order to make cable management easy. Keep in mind, all the wires need to be at the level of or below the micro-usb port vertically, or else they'll get in the way of being able to put the lid on the case. I recommend following the wiring layout shown below.

Pins on IMU should connect to pins on the D1-Mini as follows:
IMU | D1-Mini
:---: | :---:
`VCC` | `3V3`
`GND` | `G`
`SCL` | `D1`
`SDA` | `D2`
`INT` | `D5`

![wire_imu.jpeg](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/wire_imu.jpeg "wire_imu.jpeg")

___

### Step 7 - Flashing firmware
Congrats, you've wired everything together! It's time to flash the SlimeVR firmware onto your new tracker before we close the case up.

To get started, make sure the switch is in the `off` position (to the right or away from the USB-C charging port), then plug in your D1-Mini via micro-usb to your computer. You should see a blue light underneath the D1-Mini begin flashing. (Make sure you are using a data-transfer cable and not just a charging cable.)

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/flash_d1mini.jpeg" alt="flash_d1mini.jpeg" title="flash_d1mini.jpeg" width="300"/>

If you are using a Chromium based browser such as Chrome, Edge, Opera, or Brave, you can use the web installer found [here](https://slimevr-firmware-tool.futurabeast.com/). If you do not have access to a Chromium based browser or other cannot get this method to work, follow the instructions found [here](https://docs.slimevr.dev/firmware/setup-and-install.html).

If using the web installer, here are the options you will want to select:
Option | Selection
:---: | :---:
`Firmware Version` | `Latest`
`Board` | `BOARD_WEMOSD1MINI`
`IMU Type` | `IMU_BNO080`
`IMU Rotation (DEG)` | `270`
`IMU INT Pin` | `D5`
`Wifi Settings` | `Enter your wifi network credentials`

Once you have successfully uploaded your firmware, let's double-check to make sure everything is working. It's bad karma to close up an electronics project before testing it, after all.

If you don't already have it installed, you're going to need to download the installer for [SlimeVR Server](https://github.com/SlimeVR/SlimeVR-Installer/releases/latest/download/slimevr_web_installer.exe). Once the download completes, run through the installation setup; then after it's installed, open SlimeVR server. The beautifully designed SlimeVR Server application will guide you through first-time setup of your new tracker. Ensure that the tracker is detected and working, after which, you are free proceed to step 8 and close up the tracker.

<img src="https://docs.slimevr.dev/assets/img/Setup_Welcome.png" alt="SlimeVR_server_setup.png" title="SlimeVR_server_setup.png"/>

If that doesn't happen, you most likely did something wrong. Some troubleshooting steps to take would be:
- Make sure your tracker is connected to a 2.4ghz wifi network, not 5ghz
- Try re-flashing the D1-Mini
- Double check for any de-soldered wires
- If your board is not detected when plugged in, make sure to run the [SlimeVR Web Installer](https://github.com/SlimeVR/SlimeVR-Installer/releases/latest/download/slimevr_web_installer.exe) and tick the box to install the USB drivers. If your board is still not detected, try rebooting, and double check that your cable is capable of data transfer and that it is not a charging-only cable.

If none of those work, reach out for help in the `#diy` channel on the [SlimeVR Discord Server](https://discord.gg/SlimeVR).

If everything is working, go ahead and turn off your tracker, celebrate a bit, and move on to step 8.

___

### Step 8 - Build case lid
Insert the two M3 nuts into their respective holes as shown below. Note, you may want to use some superglue to keep the nuts in if they seem too loose for you.

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/nut_placement.jpeg" alt="nut_placement.jpeg" title="nut_placement.jpeg" width="300"/>

If you're having trouble inserting the nuts in all the way, try partially screwing in a screw (not enough to come out the other side of the nut) and using that to push the nut in all the way.

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/insert_nuts.jpeg" alt="insert_nuts.jpeg" title="insert_nuts.jpeg" width="300"/>

___

### Step 9 - Putting it all together
Take the lid and snap it on to the top of the case. It's alright if it doesn't seem to want to stay on, that's what the screws are for!

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/snap_case_together.jpeg" alt="snap_case_together.jpeg" title="snap_case_together.jpeg" width="300"/>

Next, insert the two M3\*20 screws into screw holes.

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/screw_placement.jpeg" alt="screw_placement.jpeg" title="screw_placement.jpeg" width="300"/>

Finally, screw the screws into the nuts. Be very careful not to overtighten, as the nuts can pop out of their holes if too much force is applied. In normal use however, this shouldn't happen. If it does, superglue the nuts into the lid.

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/tighten_screws.jpeg" alt="tighten_screws.jpeg" title="tighten_screws.jpeg" width="300"/>

You're almost done! All that's left is mounting the tracker to your body.

___

### Step 10 - Mounting
By the very nature of this case design, you can choose to mount this tracker to your body in any way you want without having to print out a whole new case design and swapping the internals over. All you need to do is print out a small mounting plate with your desired method of mounting and screw it on to the tracker!

To install your mounting plate, line up the clips on the mounting plate with the matching holes on the tracker.

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/lineup_mounting_plate.jpeg" alt="lineup_mounting_plate.jpeg" title="lineup_mounting_plate.jpeg" width="300"/>

Then, insert plate into tracker until flush.

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/insert_mounting_plate.jpeg" alt="insert_mounting_plate.jpeg" title="insert_mounting_plate.jpeg" width="300"/>

And finally, turn!

<img src="https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/turn_mounting_plate.gif" alt="turn_mounting_plate.gif" title="turn_mounting_plate.gif"/>

___

## Congratulations! You've built your very own QuantumSlime tracker!
Share your results in the `#diy-gallery` channel on the [SlimeVR Discord Server](https://discord.gg/SlimeVR)!

To begin using your tracker, simply start up the SlimeVR Server software, turn on and put on your trackers, [configure](https://docs.slimevr.dev/server/configuring-trackers.html) your trackers, start up SteamVR, calibrate, and profit. If using trackers in VRChat on standalone Oculus (Meta) headsets, read [here](https://docs.slimevr.dev/server/osc-information.html).

Something not working or having problems with software? Ask for assistance in the `#diy` channel on the Discord server.

_This concludes my TedTalk, thank you for reading :D_
###### _Designed and written by QuantumRed - 🄍 CC0 Public Domain - Last updated October 5th, 2023_
