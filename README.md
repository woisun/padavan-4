# padavan-4.4 #

本项目基于原始 rt-n56u，最新 mtk 4.4.198 内核，取自 D-LINK GPL 代码。

- 特征
  - 基于 4.4.198 Linux 内核
  - 支持基于 MT7621 的设备
  - 支持MT7615D/MT7615N/MT7915D无线芯片
  - 使用legency驱动支持raeth和mt7621 hwnat
  - 支持qca快捷方式-fe
  - 支持基于netfilter的IPv6 NAT
  - 支持集成在内核中的 WireGuard
  - 支持全锥 NAT (by Chion82)
  - 支持通过 sysfs 控制 LED&GPIO


- 支持的设备
  - CR660x
  - JCG-Q20
  - JCG-AC860M
  - JCG-836PRO
  - JCG-Y2
  - DIR-878
  - DIR-882
  - K2P
  - K2P-USB
  - NETGEAR-BZV
  - MR2600
  - MI-4
  - MI-R3G
  - MI-R3P
  - R2100
  - XY-C1

- 编译步骤
  - 安装依赖项
    ```sh
    # Debian/Ubuntu
    sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
        fakeroot kmod cpio git python3-docutils gettext automake autopoint \
        texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
        libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

    ```
  - 克隆源代码
    ```sh
    git clone https://github.com/meisreallyba/padavan-4.4.git
    ```
  - Prepare toolchain
  - 准备工具链
    ```sh
    cd padavan-4.4/toolchain-mipsel

    # （推荐）为 x86_64 或 aarch64 主机下载预构建的工具链
    ./dl_toolchain.sh

    # 或者使用 crosstool-ng 构建工具链
    # ./build_toolchain
    ```
  - 修改模板文件并开始编译
    ```sh
    cd padavan-4.4/trunk

    # （可选）修改模板文件
    # nano configs/templates/K2P.config

    # 开始编译
    fakeroot ./build_firmware_modify K2P

    # 要为其他设备构建固件，请在先前构建之后清理树
    ./clear_tree
    ```

- Manuals
  - Controlling GPIO and LEDs via sysfs
  - How to use NAND RWFS partition
  - How to use IPv6 NAT and fullcone NAT
  - How to add new device support with device tree
