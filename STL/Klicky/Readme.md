The new duct based mount is a simpler and easier to implement solution. You just need to print the slightly longer arm mount or use the variable height arm from the Klicky mod repo. And fllow the standard setup for klicky mod. 

I also added a thicker klicky side mount and moved the directions for this here in case you still wish to utilize it. 



# Side mount Klicky needed changes.
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
