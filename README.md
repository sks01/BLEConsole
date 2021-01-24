# BLEConsole
Windows command-line tool for interacting with Bluetooth LE devices, adapted for semiautomated testing of BLE devices.

## Install
Compile the Visual Studio Project and run it or just copy/paste the BLEConsole.exe to your computer and run it.

### Requirements:

Windows 10, BT 4.0 adapter

### Console commands:

- **help**, **?**                      : show help information (may includes commands that are not actually available in this version, to be updated)
- **quit**, **q**                      : quit from application
- **list**, **ls** [w]                 : show available BLE devices
- **open** <name> or <#>           : connect to BLE device
- **timeout** <sec>                    : show/change connection timeout, default value is 3 sec
- **delay** <msec>                 : pause execution for a certain number of milliseconds
- **close**                        : disconnect from currently connected device
- **stat**, **st**                     : shows current BLE device status
- **print**, **p** <text&vars>*     : prints text and variables to stdout, where are variables are:
	* %id : BlueTooth device ID
	* %addr : device BT address
	* %mac : device MAC address
	* %name : device BlueTooth name
	* %stat : device connection status
	* %NOW, %now, %HH, %hh, %mm, %ss, %D, %d, %T, %t, %z : date/time variables
- **format** [data_format], **fmt**    : show/change display format, can be ASCII/UTF8/Dec/Hex/Bin
- **set** <service_name> or <#>    : set current service (for read/write operations)
- **read**, **r** <name>**              : read value from specific characteristic
- **wrrr** <repeats> <retries> <name>** <value> : write value to a characteristic repeats times, each time reading the same characteristic for a non-empty value a number of retries times
- **write**, **w** <name>** <value>     : write value to specific characteristic
- **subs** <name>**                 : subscribe to value change for specific characteristic
- **unsubs** <name>** [all]         : unsubscribe from value change for specific characteristic or unsubs all for all
- **wait** : wait <timeout> seconds for notification event on value change (you must be subscribed, see above)
	
  _* you can also use standard C language string formating characters like \\t, \\n etc._
  
  _** <name> could be "service/characteristic", or just a char name or # (for selected service)_

### Example of usage:

BLEConsole ver. 0.4.0

BLE: list
#01: Simple BLE Peripheral
#02: TESTER
BLE: open tester
Connecting to TESTER.
Found 3 services:
#00: GenericAccess
#01: Battery
#02: Custom Service: 0235733b-99c5-4197-b856-69219c2a3845
BLE: format hex
Current display format: Hex
BLE: wrrr 10000 1000 #2/#0 06 03 00 00 00 ff ff
Read try 0
BB
BLE:

