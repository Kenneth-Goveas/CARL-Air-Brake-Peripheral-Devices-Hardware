# Organization

Upon properly cloning this repository according to the instructions in
[cloning.md][cln], you should end up with the following directory structure.

```
CARL-Air-Brake-Peripheral-Devices-Hardware/
|__ CARL-Air-Brake-Peripheral-Devices-Hardware.kicad_pro
|__ CARL-Air-Brake-Peripheral-Devices-Hardware.kicad_sch
|__ CARL-Air-Brake-Peripheral-Devices-Hardware.kicad_pcb
|__ production/
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.bom.csv
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.boardoutline.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.toplayer.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.bottomlayer.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.topsoldermask.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.bottomsoldermask.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.toppaste.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.bottompaste.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.topsilkscreen.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.bottomsilkscreen.ger
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.drills_pth.xln
|   |__ CARL-Air-Brake-Peripheral-Devices-Hardware.holes_npth.xln
|__ fp-lib-table -> ./library/fp-lib-table
|__ sym-lib-table -> ./library/sym-lib-table
|__ library/
|   |__ symbols/
|   |__ footprints/
|   |__ models/
|   |__ fp-lib-table
|   |__ sym-lib-table
|   |__ README.md
|__ README.md
|__ documentation/
    |__ images/
    |__ description.md
    |__ cloning.md
    |__ prerequisites.md
    |__ organization.md
    |__ flashing.md
```

The KiCad project, schematic, and board files are located in the root directory.
The bill of materials file, and the gerber and drill files for production are
located in the [production][prod-dir] directory. The KiCad component library
[KiCad Libraries][lib-repo] is contained as a submodule in the
[library][lib-dir] directory. Symbolic links [fp-lib-table][fp-lnk] and
[sym-lib-table][sym-lnk] in the root directory point to the library table files
[fp-lib-table][fp-file] and [sym-lib-table][sym-file] in the [library][lib-dir]
directory. These symbolic links are required for KiCad to be able to locate the
component library.

[cln]:      ./cloning.md

[prod-dir]: ../production

[fp-lnk]:   ../fp-lib-table
[sym-lnk]:  ../sym-lib-table
[fp-file]:  ../library/fp-lib-table
[sym-file]: ../library/sym-lib-table

[lib-dir]:  ../library
[lib-repo]: https://github.com/Kenneth-Goveas/KiCad-Libraries
