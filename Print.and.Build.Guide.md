# V4 Print and Build Guide
So you want to build a QuantumSlime tracker huh? Well, you've come to the right place.

## What files to print
You will need to print [`V4.Case.Top.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/V4.Case.Top.stl), [`V4.Case.Bottom.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/V4.Case.Bottom.stl), and [`V4.Components.Plate.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/V4.Components.Plate.stl) for the case, and then a [mounting plate](https://github.com/Quantum-Red/QuantumSlimes/tree/main/V4/Mounting%20Plates) to be able to attach the tracker to your body. Choose from one of the [already available mounting plates](https://github.com/Quantum-Red/QuantumSlimes/tree/main/V4/Mounting%20Plates) or download and modify [`V4.Template.Mounting.Plate.stl`](https://github.com/Quantum-Red/QuantumSlimes/blob/main/V4/Mounting%20Plates/V4.Template.Mounting.Plate.stl) to design your own mounting solution. If you do end up making your own design, please share it with the community by uploading it in a pull request to the [mounting plates directory](https://github.com/Quantum-Red/QuantumSlimes/tree/main/V4/Mounting%20Plates).

___

## Recommended printer settings
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
So now that you've got all your parts printed out and all your electronics have arrived in the mail, it's time to start putting it all together into a working tracker!

Tools you'll need:
- Soldering iron
- Solder (flux core solder highly recommended)
- Flux (if your solder is not flux core)
- 24 gauge wire (stranded wire over solid core is preferred)
- Wire strippers (or scissors/knife if you're very, *very* careful)
- M3 allen wrench/hex key
- Soldering station or helping hands (optional, but highly recommended)

_Now let's get started!_

While this guide is meant to be read along step-by-step while building, I encourage you to first scan through the pictures so that you know how everything is supposed to go together in the end.

###### NOTE: This build guide is for a single standalone tracker with no auxiliary tracker. Once I design and build one myself, I'll write a separate build guide for that.

### Step 0 - CAUTION
Do you currently have caffeine in your system? If yes, then I recommend doing this later, as caffeine jitters will make soldering very hard. Anything that will affect your ability to hold things still will make soldering everything together much harder and increase the chance of accidentally slipping and melting a bit of the case or burning a component. You have been warned.

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
Insert the D1-Mini into the mounting plate as shown below. The metal caseing on the board should slot into the matching-sized hole on the mounting plate.

![insert_d1mini.gif](https://github.com/Quantum-Red/QuantumSlimes/blob/main/Misc/Build%20Guide%20Photos/insert_d1mini.gif "insert_d1mini.gif")

___

### Step 5 - work in progress
