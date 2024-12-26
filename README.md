# SIM7600E-H_4G_HAT Setup Guide for Raspberry Pi 5

This guide provides steps to set up the SIM7600E-H_4G_HAT on a Raspberry Pi 5, following the official guide from Waveshare’s wiki. Additionally, it includes fixes for issues specific to Raspberry Pi 5.

## Prerequisites

https://www.waveshare.com/wiki/SIM7600E-H_4G_HAT#Quick_Test

Ensure you have completed the assembly and initial setup as per the official guide linked above.

### Step 1: Enable S0 Interface

Modify the config.txt file to enable the required interface:

Open the configuration file: 

	$ sudo nano /boot/firmware/config.txt


Add the following line at the end of the file:

	dtoverlay=disable-bt


Save and exit (Ctrl+X, Y, Enter).
Reboot your Raspberry Pi:

	$ sudo reboot -h

## Step 2: Run the Demo

The demo provided in the official documentation might not work out-of-the-box on Raspberry Pi 5.

### Test Minicom

Run the following commands, depending on your setup:

For AMA0 interface:

	$ sudo minicom -D /dev/ttyAMA0 -b 115200


For S0 interface:

	$ sudo minicom -D /dev/ttyS0 -b 115200

## Step 3: Fix Demo Issues on Raspberry Pi 5

Demo files: https://files.waveshare.com/upload/2/29/SIM7600X-4G-HAT-Demo.7z

The default RPi.GPIO library may cause compatibility issues on Raspberry Pi 5. Resolve this by switching to the updated rpi-lgpio library:

Remove the existing GPIO library:

	$ sudo apt remove python3-rpi.gpio


Install the updated library:

	$ pip3 install rpi-lgpio


Update the interface used in the demo files (replace AMA0 or S0 with the correct interface for your setup).
Run the demo. It should now work without freezes or errors.

## Troubleshooting

If you encounter issues:

	Double-check your HAT connections and Raspberry Pi configuration.
	Ensure you’ve selected the correct interface (/dev/ttyAMA0 or /dev/ttyS0 or other  ¯\_(ツ)_/¯).
	Verify that rpi-lgpio is installed correctly.

For additional details, refer to the official Waveshare wiki.

I hope it helps : ) 
