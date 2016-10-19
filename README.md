README and documentation aside, this repository was generated using the following commands :

```bash
git clone --depth 1 --branch v4.8 git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
export CROSS_COMPILE=armv7a-hardfloat-linux-gnueabi-
export ARCH=arm
make mrproper
wget -O .config https://raw.githubusercontent.com/mqmaker/linux-rockchip/develop-4.4/arch/arm/configs/rk3288-miqi_defconfig
make menuconfig
# Modified the Local Version String in to recognise it from others
make rk3288-miqi.dtb zImage modules -j3
# Kernel compiled
#  The remaining commands were only used to generate this git tree and
# can be ignored.
mkdir /tmp/MyyQi
mkdir /tmp/MyyQi/boot
make INSTALL_MOD_PATH=/tmp/MyyQi modules_install
make INSTALL_PATH=/tmp/MyyQi/boot install
cp arch/arm/boot/zImage /tmp/MyyQi/boot/zImage
cp arch/arm/boot/dts/rk3288-miqi.dtb /tmp/MyyQi/boot/
cd /tmp/MyyQi
git init .
git add .
git commit -a -s -S -m "First try of a MiQi compatible kernel build"
git remote add origin https://github.com/Miouyouyou/MyyQi-kernel.git
git push -u origin master
```
The user [peba](http://www.bitkistl.com/), on the [mqmaker's forums](https://forum.mqmaker.com/t/mainline-kernel-compilation/572/9), were able to boot kernels built that way successfully on a [MiQi board](https://mqmaker.com/doc/introduction-to-miqi/) using a Debian 9 distribution.

![Peba's Debian system using a 4.8.0 kernel built that way](./img/peba-debian-miqi-using-4-8-0-OfTheMiouyouyou-kernel.png)

TODO
----

- [ ] Document how to use the generated kernel and boot it
- [ ] Add the [Open Source Kernel-space Mali Midgard drivers](http://malideveloper.arm.com/resources/drivers/open-source-mali-midgard-gpu-kernel-drivers/)
- [ ] Add [gator](https://github.com/ARM-software/gator)
- [ ] Document how to use [DS-5 : Streamline](https://developer.arm.com/products/software-development-tools/ds-5-development-studio/streamline/overview) to analyse OpenGL 
ES 2.x/3.x programs running on MiQi boards using such kernels.
