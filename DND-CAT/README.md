This plate / strip setup is compatible with the sample environment at APS 5-ID-D DND-CAT beamline. The sample plate / 9-strip holder is secured on the beamline using the 96x2 well plate holder. Use "w150_stage" to initialize the plate setup, and "w135_stage" to initialize the 9-strip holder.


\\plate1.do
\\row is from A to J for 150 cell, A to I for 135 cell (9 strips)
\\column is 1 to 15, notch is drawn on the 

area_detectors_set_param("SampleThickness",0.234)
snapshoton
for (mycellrow=asc("A");mycellrow<=asc("I");mycellrow++) {
 area_detectors_take_background
 for (mycellcol=1;mycellcol<=15;mycellcol++) {
  printf("%c %d\n",mycellrow,mycellcol)
  eval(sprintf("w135_samp %d %d",mycellrow,mycellcol))
  swcollectexpert
  mvr samp_v 0.75;waitmove
  swcollectexpert
  mvr samp_v 0.75;waitmove
  swcollectexpert
 }
}

![image](https://github.com/stupplab/SAXScells/assets/71526800/c04644ff-61be-4dfa-8d48-25306b6848d0)
