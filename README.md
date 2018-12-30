# GNU Arm embedded toolchain for Windows 

The GNU Embedded Toolchain for Arm is a ready-to-use, open source suite of tools
for C, C++ and Assembly programming targeting Arm Cortex-M and Cortex-R family 
of processors. It includes the GNU Compiler (GCC) and is available free of 
charge directly from Arm for embedded software development on Windows, Linux and
macOS operating systems.

<div>
<img src="https://raw.githubusercontent.com/metalcode-eu/windows-arm-none-eabi/master/images/Windows10.png" alt="Windows10" width="24%">
<img src="https://raw.githubusercontent.com/metalcode-eu/windows-arm-none-eabi/master/images/GNU.png" alt="GNU" width="24%">
<img src="https://raw.githubusercontent.com/metalcode-eu/windows-arm-none-eabi/master/images/Cortex-M.png" alt="Cortex-M" width="24%">
<img src="https://raw.githubusercontent.com/metalcode-eu/windows-arm-none-eabi/master/images/Cortex-R.png" alt="Cortex-R" width="24%">
</div>

This repository is the original Windows version of the GNU Compiler from Arm 
packaged for Visual Studio Code:

[GNU Arm embedded toolchain](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)

## Install
In Visual Studio Code goto extensions (Shift+Ctrl+X), search for '*metalcode-eu*' 
and install the extension that is suited for your operating system. 

The extension has four paths for the toolchain. You can use this in the 
tasks.json.

- arm-none-eabi.bin
- arm-none-eabi.include
- arm-none-eabi.lib
- arm-none-eabi.libgcc

Here is an example of tasks.json for GNU make. 
```javascript
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build firmware",
      "type": "shell",
      "command": "make test",
      "options": {
        "env": {
          "INCLUDE": "${config:arm-none-eabi.include}",
          "LIB": "${config:arm-none-eabi.lib}",
          "LIBGCC": "${config:arm-none-eabi.libgcc}/thumb/v6-m/libgcc.a",
        }
      },
      "osx": {
        "options": {
          "env": {
            "PATH": "${config:arm-none-eabi.bin}:${env:PATH}",
          }
        },
      },
      "linux": {
        "options": {
          "env": {
            "PATH": "${config:arm-none-eabi.bin}:${env:PATH}",
          }
        },
      },
      "windows": {
        "options": {
          "env": {
            "PATH": "${config:arm-none-eabi.bin};${env:PATH}",
          }
        },
      },
      "group": {
        "kind": "build",
        "isDefault": true,
      },
      "problemMatcher": "$gcc"
    }
  ]
}
```
With the following makefile:
```makefile
.PHONY: test

test:
	@echo $(PATH)
	@echo $(INCLUDE)
	@echo $(LIB)
	@echo $(GCCLIB)
```

## Release Notes

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