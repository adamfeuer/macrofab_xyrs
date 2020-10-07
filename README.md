# Macrofab XYRS for KiCad

"macrofab.com" is an intriguing service. This script allows you to generate XYRS file
for KiCad designs. Instead of loading *.kicad_pcb file into macrofab, you can instead 
load *.xyrs file into macrofab to allow it to figure out the BOM and part placement.

Part placement can be figured out from just the *.kicad_pcb file but this file does not contain
extra part attributes. If you add an MPN (Manufacturer Part Number) attribute on the items in the
schematic, this attribute is dropped in kicad_pcb file. Macrofab documentation tells us that
MPN is a special column in XYRS file. This field allows it to suggest part numbers as you review
the BOM. This saves a lot of time.

So the solution is to look at both the *.kicad_pcb and *.net files to generate the XYRS file.


## How to run the script

The script has to be run using the python included in the KiCad for automation. I use windows so here
is how I run it. I have KiCad installed in c:\Tools\KiCad. For example, if you have a project called
cook.kicad_pcb with an accompanying cook.net, you can issue the following commands

```
C:\Tools\KiCad\bin\python.exe gen_xyrs.py -i cook.kicad_pcb -o ./xyrs/cook.xyrs

C:\Tools\KiCad\bin\python.exe gen_xyrs.py -i cook.kicad_pcb
```


###Linux

On Linux, using KiCAD 5.1.7, I can do the following:

    export PYTHONPATH=/usr/share/kicad/scripting:/usr/share/kicad/scripting/plugins:/usr/share/kicad/scripting:/usr/share/kicad/scripting/plugins
    python gen_xyrs.py -i my_board.kicad_pcb -o my_board.xyrs 


TODO:
1) Read a NOPOP attribute in .net file

Enjoy!
