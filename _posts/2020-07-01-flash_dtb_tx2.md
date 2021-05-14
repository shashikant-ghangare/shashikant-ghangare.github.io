---
layout: post
title: "Flashing Jetson TX2/TX2i with Modified DTS"
date: 2020-07-01
---


# Instructions to Flash Jetson TX2i with modified Device Tree Structure
### Working Directory

Linux_For_Tegra

### Install Device Tree Compiler
> sudo apt-get install device-tree-compiler

## Extract DTS
Present at Linux_for_Tegra/kernel/dtb

Copy **"tegra186-quill-p3489-1000-a00-00-ucm1.dtb"** to new location

> dtc -I dtb -O dts tegra186-quill-p3489-1000-a00-00-ucm1.dtb > tegra186-quill-p3489-1000-a00-00-ucm1.dts

### Add following to Line 9721/ after fb2_carveout in reserved-memory section
```
fpga_360M_reserved@d9300000{
			reg = <0x0 0xd9300000 0x0 0x16800000>;
			no-map;
		};
```
### Remove following lines from pcie-controller@10003000
 ```
 iommus = <0x11 0x11>;
 iommu _sodev_map;
```
### After status "okay" in pcie-controller@10003000 add,
```
nvidia, boot-detect-delay = <10000>;
```

## Convert to DTB
> dtc -O dtb -o tegra186-quill-p3489-1000-a00-00-ucm1.dtb tegra186-quill-p3489-1000-a00-00-ucm1.dts

And replace the dtb in original location

## References

https://forums.developer.nvidia.com/t/how-to-update-device-tree-on-tx2/53506/11

https://elinux.org/Jetson/TX2_DTB



