# 5559EFI

https://shuklarahul.co.in/415/installing-macos-mojave-on-dell-inspiron-5559-laptops/

Steps:
1. Prepare your USB bootable drive following the guide: https://www.tonymacx86.com/threads/test-drive-how-to-create-a-clover-usb.127134/
2. Copy over the CLOVER folder to your USB
3. Set the BIOS settings to below ( Full guide at https://www.tonymacx86.com/threads/guide-booting-the-os-x-installer-on-laptops-with-clover.148093/ )
        In order to boot the Clover from the USB, you should visit your BIOS settings:
        - "VT-d" (virtualization for directed i/o) should be disabled if possible (the config.plist includes dart=0 in case you can't do this)
        - "DEP" (data execution prevention) should be enabled for OS X
        - "secure boot " should be disabled
        - "legacy boot" optional (recommend enabled, but boot UEFI if you have it)
        - "CSM" (compatibility support module) enabled or disabled (varies) (recommend enabled, but boot UEFI)
        - "fast boot" (if available) should be disabled.
        - "boot from USB" or "boot from external" enabled
        - SATA mode (if available) should be AHCI
        - TPM should be disabled (Trusted Platform Module)
4. In boot menu, select the USB drive and continue to boot
5. If everything is fine, you should get the clover bootloader screen with a menu item listing different boot options.
6. Select "install mac os". If everything is fine, your laptop will boot further and the installation will start.
7. If you see a hang / kernel panic while the booting (At Apple Logo), do the following (You shouldn't see this since everything is fixed up in this repo):
    1. Once in the clover menu goto Options>Graphics Injector>InjectIntel>FakeID
    2. Set FakeID to "0x12345678" from "0x00000000" (This must be set every time you boot through Clover until we resolve the Intel HD 520 Graphics below)
    3. Follow the full guide at https://www.tonymacx86.com/threads/guide-dell-inspiron-i5559-on-macos-sierra-gm.203688/ after installation.
8. Continue the installation.
9. Once installation is complete copy the kext files in CLOVER/kexts/Others/ToLE/ into your /Library/Extensions folder, run 'sudo kextcache -i /' and reboot. You should now have 
    Ethernet, Audio, Graphics, Touchpad etc working perfectly fine.
    
