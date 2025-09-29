Building
========


```
export ARCH=arm64
export CROSS_COMPILE=aarch64-none-linux-gnu-

# Load the kernel configuration
make am6442_custom_defconfig

# Modify the configuration as necessary
make menuconfig

# Build the linux kernel image, device tree blobs, and kernel modules
make -j$(nproc) dtbs Image modules


# Install kernel modules
sudo make modules_install INSTALL_MOD_PATH=<sd_card_rootfs>
```

Copy the kernel image and device tree to the boot folder

```
sudo cp arch/arm64/boot/dts/ti/k3-am642-sk.dtb <sd_card_rootfs>/boot
sudo cp arch/arm64/boot/Image <sd_card_rootfs>/boot
```
