编译步骤

安装依赖项
# Debian/Ubuntu
sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
    fakeroot kmod cpio git python3-docutils gettext automake autopoint \
    texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
    libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin
克隆源代码
git clone https://github.com/xiaiohuan/padavan-4.4.git
准备工具链
cd padavan-4.4/toolchain-mipsel

#（推荐）为 x86_64 或 aarch64 主机下载预构建的工具链
./dl_toolchain.sh

#或者使用 crosstool-ng 构建工具链
# ./build_toolchain
修改模板文件并开始编译
cd padavan-4.4/trunk

#（可选）修改模板文件
# nano configs/templates/K2P.config

#开始编译
fakeroot ./build_firmware_modify K2P

#要为其他设备构建固件，请在先前构建之后清理树
./clear_tree
手册

通过 sysfs 控制 GPIO 和 LED
如何使用 NAND RWFS 分区
如何使用 IPv6 NAT 和全锥 NAT
如何使用设备树添加新设备支持
