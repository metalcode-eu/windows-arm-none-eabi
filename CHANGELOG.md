### Version 0.1.6
Version 8-2018-q4-major for Windows  
Released: December 20, 2018

### Version 0.1.2
Fixed typo in path to repository causing a wrong link in the marketplace.

Added a path to the libgcc files. 
- arm-none-eabi.libgcc

When you do bare metal development, you often exclude all standard libraries 
but you still need libgcc.a for integer division etc. The path to this file 
contains a version number that changes with every release of the toolchain. 
Using this variable you do not need to update your makefiles with every new 
release of the toolchain. 

### Version 0.1.0
Version 7-2018-q2-update for Windows

### Version 0.0.5
Operating system specific PATH environment variable. 

### Version 0.0.2
Changed ${env:HOME} to ${env:USERPROFILE}.

### Version 0.0.1
GNU Make 4.2.1

Version 7-2017-q4-major for Windows 
Released: December 18, 2017