This is a fork of the Bochs emulator.
With a small modification which is, we can now control the state of the A20 line in a BIOS-independent way via the bochsrc file before the bootloader takes control.

This will allow us as BIOS and OS developers to test our code to enable the A20 line.

Also it will allow systems (such as old DOSes) that assume there is nothing called the A20 line to work.
And now we can test BIOSes that enable the A20 line and we don't have access to their source code.

Of course I made a pull request but the author rejected it because I typed "NEW NEW NEW NEW" comments in areas where I edited the code. A very strong reason.

# Why
I made this to test my bootloader logic to enable the A20 line.
(This is not my first bootloader, this is the 108339383973917484029th time I make a bootloader, but I used QEMU before).

# Usage
In your bochsrc file, type:
```
A20: enable=0
```
This way, the A20 line will be disabled before the bootloader takes control (0x7c00).

If the line is absent or the "enable" parameter equals to anything other than 0, Bochs will enable the A20 line as usual.

#Limitation
This works only if Bochs is running with 1 CPU, or the internal debugger is running.
