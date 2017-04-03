# avahiswitch

Raspberry Pi service to turn on avahi-daemon if /boot/avahi is present.
To be used with ethernet gadget mode to allow to image Sticky Fingers Kali-Pi and enable
ethernet gadget mode by editing the following two files in the /boot partition:
– cmdline.txt: Add “modules-load=dwc2,g_ether” after “rootwait”
– config.txt: Add “dtoverlay=dwc2“

Add a file called "avahi" in /boot will enable the avahi-daemon, which in turn makes the raspberry pi discoverable via the name "kali-pi.local".

This is particularly useful when using ethernet gadget mode for the initial headless setup of a raspberry pi.

I advise to disable the avahi-daemon service after the initial setup (systemctl disable avahi-daemon)



To install the service:

sudo cp avahiswitch.service /lib/systemd/system/
sudo cp -f avahi-daemon.conf /etc/avahi/
systemctl enable avahiswitch.service
