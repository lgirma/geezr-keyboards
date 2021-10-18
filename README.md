# Geezr Keyboards

List of keyboard key mapping files for Geezr, the Amharic/Geez locale utility software.

### File format

The keyboard mapping files are standard case-sensitive `ini` configuration files. The files must fulfill these criteria:

* The `[info]` section group should come first
	* Use `name`, `author`, `description` and `version` keys to fill out information.
	* Use `include` entry to extend an existing ini file.
* The `[keymap]` section group should come last
	* Key mappings in the keymap section are case-sensitive

Key mapping is a sequence of key strokes followed by the replacement output character. For example,

```
^2=²
```

means when the user strikes the keys <kbd>^</kbd> and <kbd>2</kbd> consequitively, 
then the two characters will be replaced by the unicode character U+00B2

### Sample Configuration

Here is a sample configuration

```
[info]
name=Case Inverter
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
	* For example, `=0=Z` (<kbd>=</kbd><kbd>0</kbd>=<kbd>Z</kbd>) is a valid mapping while, `/eq==` is not.

2. You cannot have multiple keys as an input without defining first portion of the key combination. For example,


```
	usd=$
```

is invalid. The key combinations for `u` and `us` must first be defined. A correct form of the above key mapping:

```
	u=u
	us=s
	usd=$
```

3. Comments are not supported. Conventional INI commenting using `;` or `#` is not allowed since it will conflict with key mappings for <kbd>;</kbd> or <kbd>#</kbd> keys.

4. You cannot have more that one character as the output. For example, `eq=EQ` is invalid.

### For ibus in Linux

To use geezr in linux operating systems using ibus (tested in Ubuntu 20.04)

#### 1. Install ibus and ibus-table

```shell
sudo apt install ibus ibus-clutter ibus-gtk ibus-gtk3 ibus-qt4
sudo apt install ibus-table
```

#### 2. Setup ibus

```shell
ibus-setup
```

Change default keyboard input method to ibus:

```shell
im-switch -s ibus
```

#### 3. Install the Geezr input method

Then, download the `PhoneticGeez-ibus.txt` on your PC and

```shell
sudo ibus-table-createdb -n /usr/share/ibus-table/tables/geezr-am.db -s phonetic-imtable.txt
ibus-daemon -drx
```

Then, open the ibus settings using

```shell
ibus-setup
```

Then, go to `Input Method` tab and click the "Add" button. Then in the "Select an input method" dialog click on the more icon (three dots). Then, either pick `Amharic` if it is available or click `other` at the end of the list. Then add the Geezr input method.