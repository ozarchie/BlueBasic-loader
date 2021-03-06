#bbload
#bbloadlines
Linux upload script for <b>BLE BlueBasic interpreter</b> (https://github.com/aanon4/BlueBasic) .  
An (only?) option to upload the bluebasic code for non-OSX world.  

This script reads from a file and uploads the content of that file to the selected device.  
It will not clear any existing line numbers that are not in the file being uploaded.  
The user still needs to clear any previous program or lines that exists.  
Possible methods are:  
	1. Issue "NEW" from the linux bbconsole app  
	2. Make the first line of the upload file a "NEW" command (no line number)  
  
On the Raspberry Pi 3 , the GATT writes fail using bbload.  
Use <i>bbloadlines</i> ( a line by line loader) instead.  
  
Needs <b>gatttool</b> from bluez package.  
  
<b>Usage:  
==================  
bbload &lt;MAC address&gt; &lt;file&gt;  
bbloadlines &lt;MAC address&gt; &lt;file&gt;   
</b>
  
The script will hang if the BTLE device is already open in the bbconsole application.  

You can use <b>hcitool</b> to discover the MAC address of any BlueBasic devices.  

Example:  
  
<b>$sudo hcitool lescan</b>   
<i>LE Scan ...    
68:64:4B:4A:53:24 (unknown)    
68:64:4B:4A:53:24 (unknown)    
B4:99:4C:21:5A:97 BASIC#97    
B4:99:4C:21:5A:97 (unknown)</i> 
    
Note that all BlueBasic devices return a name such as BASIC#NN.  
NN is typically the last two digits of the MAC address.
This could be used to provide a device selection capability.  
  
Once again, the BlueBasic device will not show if it is open in bbconsole.  
