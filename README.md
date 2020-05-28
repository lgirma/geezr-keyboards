# Geezr Keyboards

List of keyboard key mapping files for Geezr, the Amharic/Geez locale utility software.

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

### Limitations

The keyboard mapping has the following limitations:

1. You cannot add the `=` sign as the output. But it can be used as an input.
	* For example, `=0=Z` is a valid mapping while, `/eq==` is not.
1. You cannot have multiple keys as an input without defining first portion of the key combination. For example,

```
usd=$
```

is invalid. The key combinations for `u` and `us` must first be defined. A correct form of the above key mapping:

```
u=u
us=s
usd=$
```
1. Comments using `;` or `#` are not allowed since they can conflict with key mappings for `;` or `#` keys.