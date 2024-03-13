This design is compatible with the automatic sample exchanger robot at NSLS-II LIX beamline. Place the frame-like "transparency" piece on top of the aluminum base plate, then place the sample strip on top. The notch should be placed toward the door when mounted on the beamline (notch is close to the handle).
```
mc_measure_holder('samples-proc.xlsx','<strip name>',exp=<exposure time>, scan=True,check_sname=True,cell_format='flat15')
```
2023/12: For 2023-3 cycle, we tested the mesh scan with robotic arm sample exchange:
```
mc_auto_measure_samples('samples-proc.xlsx',configName='a1',cell_form='flat15',scan='mesh',xrange=1,offset_y=0.5) #configName is defined as a set of strips with their holder positions in the auto-exchanger
```
throughput ~ 11.5 min / 15 samples.

**File description:**

- slot_guide.stl: 3D model of a guide to place the double adhesive tape to the strip. We find it not very necessary (alignment by eye is usually sufficient), but if you are having difficulty applying the tape straight, this may help.
- strip_brookhaven.svg: 2D vector file for the main compartment for flat15 cells. This should be laser-cut out of cast acrylic plates with known thickness.
- tape_brookhaven.svg: 2D vector file for the double adhesive tape for flat15 cells. This should be laser-cut applied to both sides of the main compartment strip.
- transparency_brookhaven.svg: 2D vector file for spacing between the aluminum arm and the sample strips to prevent the glass from contacting the aluminum. This should be laser-cut out of 1mm thick cast acrylic plate (or anything thicker than tape + glass, and is uniform in thickness).
- centrifuge_rack_v1.stl, racklid_2mm_v1.1.stl: 3D model of a storage rack / centrifugation adaptor to remove bubbles from the samples. Use a 96-well plate swinging bucket holder (deep form factor). We print ours with PLA with support at the bottom, infill of 15% with gyroids, 0.3mm draft resolution in a Prusa MK3S+ FDM printer.
*Experimental*
- stripT_brookhaven.svg and tapeT_brookhaven.svg: T-shaped cell to reduce volume and focus on sedimented materials. May not work on 2mm thick spacers due to the beam hitting the PMMA walls. The bottom of the cell is at the same height, the top is 1mm higher. Tape is centered against the T.
