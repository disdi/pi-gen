1. Copy created image in test directory

2. Extract kernel and dtb using extract script -
 
**sudo extract_kernel.sh (Image) **

3. Resize image to 4G using qemu-img with below command -

**sudo qemu-img resize (Image) 4G **

For qemu-system-aarch64, relevant files are -

**Kernel - kernel8.img 
Device Tree - bcm2710-rpi-3-b.dtb **

4. Boot the image for aarch64 with below command -
5. 
**qemu-system-aarch64 -machine raspi3b -device usb-mouse -device usb-kbd -drive file=(Image),if=sd -netdev user,id=net0,hostfwd=tcp::8022-:22 -device usb-net,netdev=net0 -kernel ./kernel8.img -append console=serial0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait initcall_debug=1 bcm2708_fb.fbwidth=1024 bcm2708_fb.fbheight=768 dwc_otg.fiq_fsm_enable=0 -dtb ./bcm2710-rpi-3-b.dtb -no-reboot **

