# SummerPrinter

Here you will find information about our 3D printer design.  This 3D printer was developed for our Build Your Own 3D Printer summer camps, which we ran in the summer of 2019 in Boulder, Colorado, USA.  At present we have 3D model files for all the 3D printed components of the printer, basic documentation, a bill of materials, and firmware configurations for Marlin.  More information is to come, and updates to the design as we improve it!

Our goals for this printer are, in no particular order, that this printer should:
* Print quickly and with high quality (not necessarily at the same time)
* Be compact and portable
* Be able to be assembled and commissioned by a teenager -- under supervision -- in a week-long half-day summer camp
* Print the three common materials (PLA, PETG, ABS)
* Have low cost
* Use standard components as much as possible to enable expansion and experimentation

(One motivation behind these goals was that, if we turned out to not get sign-ups for the camp, I wanted printer kits that I would be happy to assemble and use myself in our other classes.  Thus we would need to carry these printers into classrooms or community centers and use them without much setup, and we would use them to quickly print small objects that students design during a workshop or class.)

These goals led to the following design decisions:
* The printer uses a cartesian (Makerbot-style) motion system.  A Prusa-style motion system has limited acceleration due to the need to move the build plate and print horizontally.  CoreXY and delta motion systems support fast printing, but both systems are harder to comprehend in terms of how motor movement translates to motion of the printhead.  CoreXY systems also tend to be more complex and have long, difficult-to-thread belt paths, and delta systems are sensitive to misalignments during assembly.
* To support quick printing the X gantry is driven by a small NEMA 14 stepper motor and uses 6 mm rods.  These are acceptable for a small printer with a light-weight printhead, but would not scale up well.
* The printer has a 160 x 160 x 160 mm print area in a frame with outer dimensions 300 x 340 x 343 mm.  The printable area puts the printer in the 'mini' size category, but it is at the larger end of that range.  The small build plate makes running a heated bed on 12 V practical, even at ABS temperatures.
* All moving parts of the printer are contained within the frame, except for the bowden tube running between the printhead and extruder.  Thus the printer can easily be semi-enclosed (front, back, sides, and bottom) for ABS printing by installing coroplast or other plastic panels on the outside of the frame.
* Despite the small size, the build plate is supported at both ends.  The build plate remains stable even when using z-hop during printing.
* The printer has a basic graphical display and SD card slot, so it can print without being tethered to a computer via USB or a network.
* The low-cost goal requires a number of compromises, of course, the most significant of which are the following:
  * The motion system uses smooth rods and linear bearings sourced from low-cost providers via Aliexpress -- thus they often do not meet their advertised specifications and have significant slop.  This is mitigated somewhat in the Y and Z axes with preload putting opposing side-load on the two linear bearings on each axis.  For better print quality the rods and bearings can easily be replaced with ones from reputable suppliers, such as Misumi, at increased cost.
  * The printer uses 8-bit electronics -- the old standard of an Arduino Mega, RAMPS, and A4988 or similar stepper drivers.  Due to the current draw of the heated bed a RAMPS 1.6 or 1.6+ is needed, or a heat sink could be added to the bed MOSFET of a RAMPS 1.4.  The printer can stall when printing detailed models from an SD card due to falling behind processing lines of G-code.  To avoid that problem the electronics can be upgraded to a 32-bit board, such as an SKR 1.3 or Smoothieboard, which also makes the graphical display more responsive.
  * Many quality-of-life features are not included in the design, such as any sort of automated bed levelling or a filament runout sensor.  It is envisioned that students may wish to add these features on their own after the conclusion of camp.
