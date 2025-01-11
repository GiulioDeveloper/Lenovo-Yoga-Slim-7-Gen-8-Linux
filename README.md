# Intro

This is a short tutorial for those trying to use Linux on the laptop Lenovo Yoga Slim 7 Gen 8 (14APU8). The main two issues are:
- [Audio](https://github.com/darinpp/yoga-slim-7): the speaker produce horrible sound by default and the speaker may also be damaged after prolonged use.
- [Stand-by](https://gitlab.freedesktop.org/drm/amd/-/issues/2812): the system can't enter standby mode. It just immediately wakes up after you try to suspend.

I have found this fixes to work on Fedora 40 and 41 without any issue. Credits to the people in the linked websites for their work on providing these solutions. The link about audio also talks about other settings I did not explore, they shouldn't be necessary for simple usage.

Hope somebody finds this useful.

**I DO NOT TAKE ANY RESPONSIBILITY FOR ANY DAMAGE TO YOUR DEVICES AFTER FOLLOWING THESE STEPS**

# Fixing Stand-by

1. Disable Secure Boot in the BIOS of the laptop
2. Download the file "slim7-ssdt" from this repo
3. Copy it in /boot
4. Add the line 'GRUB_EARLY_INITRD_LINUX_CUSTOM="slim7-ssdt"' in /etc/defalt/grub
5. Update your grup configuration:
   1. Fedora:
   ```
    sudo grub2-mkconfig -o /boot/grub
   ```
   2. Ubuntu
   ```
    sudo update-grub
   ```

# Fixing Stand-by

To fix audio, just copy the two files in the "Audio" folder repo to /lib/firmware on your laptop. The original firmware is also provided may something go wrong. 
