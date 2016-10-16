README file aside, this repository was generated using the following commands :

```bash
git clone --depth 1 --branch v4.8 git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
export CROSS_COMPILE=armv7a-hardfloat-linux-gnueabi-
export ARCH=arm
make mrproper
wget -O .config https://raw.githubusercontent.com/mqmaker/linux-rockchip/develop-4.4/arch/arm/configs/rk3288-miqi_defconfig
make menuconfig
# Modified the Local Version String in to recognise it from others
make rk3288-miqi.dtb zImage modules
mkdir /tmp/MyyQi
mkdir /tmp/MyyQi/boot
make INSTALL_MOD_PATH=/tmp/MyyQi modules_install
make INSTALL_PATH=/tmp/MyyQi/boot install
cd /tmp/MyyQi
git init .
git add .
git commit -a -s -S -m "First try of a MiQi compatible kernel build"
git remote add origin https://github.com/Miouyouyou/MyyQi-kernel.git
git push -u origin master
```

