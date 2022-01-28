This is a repository for the CAD and STL for the EVA to Voron conversion. 

This is not an original work. All of this is the work of the EVA team and Voron Design. I only made minor modifications to allow the use of the excellent EVA hotend system. Please visit them at https://main.eva-3d.page/ 

The goal was to make as little change to either system as possible. So primarily I wanted to not have to redesign the belt pathing on the Voron or relocate the rail. And to minimize the changes to the EVA and retain as much as I could of the EVA compatibility. 
Primarily what this means is I added heat sets to the top of some mounts and added a spacer/endstop with mounting holes for the faceplate to the MGN12. 
Homing does need to be modified to work with this modification. I am using Homing override to ensure that I home x and they move to a location away from the corner before I home the y axis. 

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
  
## Probe

### Probe offset 
```
x_offset: -24
y_offset: 30
```
### Mesh max 
Needs to be shrunk as it looks at the nozzle location not the offset. 
```
mesh_max: 250,260 
```
## Z-tilt
And the Z-tilt will need to be adjusted for your particular bed. My bed is not a standard so would not be helpful. Just keep in mind that the probe offset is not used when setting these. 
# Auto-z
This I am looking to improve 
But currently this is the changes I used to make this work in my configuration. 
These are the ADDTIONAL besides the normal changes to configure auto z. 
The below are found in the klicky-probe-for_VT.cfg on my configuration. 
### Probe Entry 
The below needs to be modified to change where it starts the dock and undock from. 

```
# Probe entry location
        #set the below location to 20 mm to the right of the dock location. 
         G0 X 143 Y 275 F3600
        #G0 X{Dx|int - Ax|int} Y{Dy|int - Ay|int} F{St}
        #{% if Dz != -128 %}
        #    G0 Z{Dz|int - Az|int} F{Sd}
        #{% endif %}
```

### Dock move
Below needs to be added:
```
#dock move
Variable_dockmove_x:             0
Variable_dockmove_y:           -40
Variable_dockmove_z:             0

#attach move
Variable_attachmove_x:         -40
Variable_attachmove_y:           0
Variable_attachmove_z:           0
```   
   
   

