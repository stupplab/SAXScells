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
