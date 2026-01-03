# FPUCheck
A simple little program for verifying that floating point values are being displayed correctly in Basilisk II.

This is a CodeWarrior Pro 4 project for Mac OS (68k).

I've been having issues when debugging my software on Basilisk II due to floating point values been mis-rendered in text. I'm not sure why this is, and it doesn't appear to impact actual programatical use (i.e. you can perform maths and evaluate the values correctly, but if you printf, an incorrect value is shown). I have found the same issue in both code compiled with CodeWarrior Pro 4, and in RealBasic.

In Basilisk II, I was using a IIci ROM with a 68040 and FPU, running B1-7.5.5. So to experiment, I set it to a 68030+68882... same issue... so I set it to be a 68030 without FPU... and the code works (using the SANE traps). Given this, I have written a little test program. I'm curious how widespread this issue is - is it just my setup? Is it just on Linux? Is it a specific version of Basilisk II? (By the way - how do you check the version easily?)

The weirdest thing is it is actually difficult to detect in code - if I test the value and compare with an integer, they compare as normal! It is almost as if the bug is in the code that displays a float, or converts it to a string, but only when emulating a physical FPU? (Edit - or possibly they've modified how floats are stored in their patches, but not updated the routine that displays a float?)

I'd be interested to know if other people see similar behaviour? You can change the CPU / FPU under the "Memory/Misc" tab in Basilisk II Settings. For now I'll be leaving mine set to 68030 without FPU.
