![Orbiter](https://github.com/majarspeed/Voron-EVA-conversion/blob/main/Pics/Orbiter_EVA.jpeg "EVA on Voron")
![fusion](https://github.com/majarspeed/Voron-EVA-conversion/raw/main/Pics/EVA%20for%20Voron.JPG "EVA on Voron")

This is a repository for the CAD and STL for the EVA to Voron conversion. 

This is not an original work. All of this is the work of the EVA team and Voron Design. I only made minor modifications to allow the use of the excellent EVA hotend system. Please visit EVA at https://main.eva-3d.page/ and Voron Design https://vorondesign.com/ and consider suppoting both of these worthy projects. 

The goal was to make as little change to either system as possible. So primarily I wanted to not have to redesign the belt pathing on the Voron or relocate the rail. And to minimize the changes to the EVA and retain as much as I could of the EVA compatibility. 

Primarily what this means is I added heat sets to the top of some mounts and added a spacer/endstop with mounting holes for the faceplate to the MGN12. 
Homing does need to be modified to work with this modification. I am using Homing override to ensure that I home x and they move to a location away from the corner before I home the y axis.

# Update 2 

Added some addtional spacing on the housing. Some was just a little to close. 
Added ad spacer using a df2 microswitch. 
Added sherpa mini top. 

Began testing of a MGN 9 variant. 

Some have asked for a weight comparsion. Weighed a EVA with Sherpa top all parts except hotend and extruder. 124 grams 


# UPDATE 1 Voron EVA conversion gets better Klicky
I have created a klicky duct that is based off of Whooppingpochard from the Voron discords design. And adapted it to the trihorn ducts. This is a much easier method and allows the use of the stock klicky and auto z configuration. This makes this a much easier conversion overall. Will retain the previous instructions in the klicky readme if you would still prefer to use this with that configuration. 

Also adding a user mod for some user based alternative parts. 
Adding a clamp style multipart uface desigh thanks to DoubleT ont he Voron Discord. 
 

# READ FIRST: THIS IS A CHALLENGING MOD. 
*"This mod may require significant individualization. Evaluate your own build and select your parts as needed." --Corvidbuild V2
This is an excellent description.*

I have a mix of modified parts and unmodified parts. 
Primarily you will need the modified Universal face and modified corexy back. The modified face has 4 holes to mount to the mgn 12 and 2 holes for heat sets to mount the hotend adapters. The modified universal plate should work with all popular hot end mounts these are un-modified (please visit the EVA site to get the files mount to fit your particular hot end.)I initially had the belts clamped with the mgn12 while effective you need 5 arms to get it lined up correctly. So I have added loops and secure the belts with zip ties.

The bottom is modified with heat sets for custom side mounted klicky mount if wanted.

The tops for several extruders are modified to work with this. LGX and LGX lite modified top as well as Orbiter 1.5/2.0 modified top and BMG modified top are included in the files. 

The x end stop is located on the carriage and is integrated with a new part I created called universal spacer.

I have a thinner versions of the rear universal wire mount.

All screw sizes are the same as stock with the exception of the through screws which need at least 5 extra mm to reach.

## THIS IS A CHALLENGING conversion please do not take this lightly.


# Configuration Changes

## Homing 
Below is an example of my homing changes to ensure I do not hit the AB motor mounts. 

```
[homing_override]
axes: z
set_position_z: 0
gcode:
   G90
   G0 Z5 F600
   G28 X
   ## Set X below to a sale location off of the right corner to ensure that you do not hit the AB mount when HOMING. 
   G0 X225 F7200
   G28 Y
   ##	XY Location of the Z Endstop Switch
   ##	Update X0 and Y0 to your values (such as X157, Y305) after going through
   ##	Z Endstop Pin Location Definition step.
   G0 X163.00 Y295 F3600 
   G28 Z
   G0 Z10 F1800
   ##Park after Homing
   G0 X163 Y260 Z30 F7200 
   ```
  

   
   

