# geezr-keyboards
List of keyboard key mapping files for geezr 

### File format

The keyboard mapping files are standard case-sensitive `ini` configuration files. The files must fulfill these criteria:

* The `[info]` section group should come first
	* Use `name`, `author`, `description` and `version` keys to fill out information.
	* Use `include` entry to extend an existing ini file.
* The `[keymap]` section group should come last
	* Key mappings in the keymap section are case-sensitive

### Sample Configuration

Here is a sample configuration

```
[info]
name=CaseInverter
description=Case inverter for A key
author=Geezr
version=1.0
include=MybaseMap
default=true

[keymap]
a=A
A=a
```

This configuration assumes there is a `MybaseMap.ini` configuration file and extends it to include keymap that inverts cases for the letter `A`
