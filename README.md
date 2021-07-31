[![Build Status](https://travis-ci.com/quangthanh010290/keyboard_mouse_emulate_on_raspberry.svg?branch=master)](https://travis-ci.com/quangthanh010290/keyboard_mouse_emulate_on_raspberry)

# Make things work first 

## Step 1: Setup 

```
 sudo ./setup.sh
```
 
 
## Step 2: Run the Server

```
sudo ./boot.sh
```

## Step 3: Run Keyboard Client (no need physical keyboard, send string through dbus)

- Dont need a physical keyboard connected to raspberry PI board

```
python3 ./keyboard/send_string.py "hello client, I'm a keyboard"
```

# To understand what I'm doing in the background 
[Make Raspberry Pi3 as an emulator bluetooth keyboard](https://thanhle.me/make-raspberry-pi3-as-an-emulator-bluetooth-keyboard/)

# Pairing

Before the keyboard can talk to a host, it needs to be paired.  This can be tricky.
1. Open (yet another) dedicated terminal window and run the *bluetoothctl* utility,

> sudo /usr/bin/bluetoothctl

2. Type the following commands, pressing enter after each

> agent on
> default-agent
> discoverable on

3. Go to the host machine and look at the Bluetooth Settings.
If all is going well, the Raspberry Pi keyboard should be visible as ready to pair.
Click the device and select pair.  You will see a dialog with a passcode. Don't click anything yet.

4. Go back to the *bluetoothctl* window on the Pi and wait a few seconds,  You should then be prompted to accept or reject the pairing request from the host.
Type *yes*

5. Quickly go back to the Windows host and click OK.  If everything has worked the keyboard should pair and Windows will start installing a keyboard driver for the emulator.  You should also see a connection message in the *btkserver* window.



