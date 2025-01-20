The terminal is the quickest way to configure virtual machines using QEMU. With a few simple commands, you can set up a usable QEMU VM running Ubuntu.

To begin, first, create a new folder for the virtual machine files and move the downloaded Ubuntu ISO into the newly created directory:

        
`mkdir Ubuntu-VM`
`sudo mv /path/to/ubuntu.iso ./Ubuntu-VM`

    

Run the following command to create an image file in the current directory:

        
`qemu-img create -f qcow2 Image.img 20G`

    

The above command will create a virtual disk image file that's 20GB in size. The virtual machine will use this disk image to store data, so make sure to specify a size accordingly.

Next, run the following command to start the Ubuntu virtual machine:

        
`qemu-system-x86_64 -enable-kvm -cdrom ubuntu.iso -boot menu=on -drive file=Image.img -m 4G -cpu host -vga virtio -display sdl,gl=on`

    

The virtual machine window will pop up. Press Escape to open the boot menu and select the appropriate option to boot from the ISO file.

`qemu-system-x86_64 -enable-kvm -boot menu=on -drive file=Image.img -m 4G -cpu host -vga virtio -display sdl,gl=on`
