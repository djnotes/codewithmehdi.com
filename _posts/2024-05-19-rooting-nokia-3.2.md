# Rooting Nokia 3.2: This is not a comprehensive guide! DO NOT FOLLOW! Will update if this becomes a proven and complete method of rooting for me.

Here are the steps that I took in trying to root a Nokia 3.2 device. However, because of the problems that process created, I had to reverse the process and thankfully get to a working state.

- Unlocking the bootloader. This involves doing some setting changes and running some adb commands. What I didn't read in instructions was that this ERASES the whole device! So, back up first!
- Installing Magisk. This requires a boot image compatible with your device. I didn't find an image for Android 11 so used one for Android 10. That created issues: Wifi didn't work and there was no sound.
- Tried flashing an image for Android 11 from SD Card and using adb sideload. both failed because verification failed
- Tried flashing TWRP for Nokia 3.2, (command: adb flash recovery twrp-xxx.img) but it failed. Gemini suggested it might be case that the recovery image is installed in boot partition. I tried "adb flash boot twrp-xxx.img" and like a miracle, the flash succeeded. Then the device booted up and sound and Wifi were good again. 


