Build and Test Environment based on Ubuntu 14.04 LTS for the STM32F4-Discovery

如何编写代码
    1. 进入某个工程目录
        如： cd ~/stm32/examples/led
        执行 "code ."
    2. 工程的目录结构
        bin/                  可执行二进制文件
        inc/                  头文件
        src/                  源文件，main就在其中
        Makefile              编译脚本文件
        stm32_flash.ld        链接脚本文件

如何编译:
    1. source 环境变量  
        cd /home/chao/stm32 
        source SOURCE_ME
    2. 进入 工程目录
        如： cd examples/led
    3. 编译工程
        编译优化的发行版： make
        编译调试版本:     make release 

        编译完成后，会在当前工程根目录的 bin/ 目录下,生成两个可执行二进制文件 *.elf *.hex

如何烧录程序：
    1. JFlashLiteExe
        选择设备 -> STM32F407ZG  选择接口 -> JTAG  选择默认速率   ==>  OK
        选择要烧录的可执行文件 -> 工程目录下的 bin/*.elf           ==>  Program device

如何调试程序：
    1. 运行Ozone调试工具
        进入某个工程目录，如：   cd  ~/stm32/examples/led
        运行   Ozone
    2.  选择设备 STM32F407ZG ,Peripherals 默认      ==>> next
        接口 JTAG 频率默认;    Host interface 默认   ==>> next
        选择二进制文件：   bin/*.elf 文件             ==>finish





# 1. File Organization

- [examples](https://github.com/istarc/stm32/tree/master/examples) have the following status: [![Build Status](https://travis-ci.org/istarc/stm32.svg?branch=master)](https://travis-ci.org/istarc/stm32)
- [build-ARM-toolchain](http://istarc.wordpress.com/2014/07/21/stm32f4-build-your-toolchain-from-scratch/)
- [freertos](https://github.com/istarc/freertos) library
- [mbed](http://mbed.org/) library
- [mbed-project-wizard](http://istarc.wordpress.com/2014/08/04/stm32f4-behold-the-project-wizard/)
- [STM32F4-Discovery_FW_V1.1.0 library](http://www.st.com/web/catalog/tools/FM116/SC959/SS1532/PF252419) library
- [test]()

# 2. How to Setup the Environment
## 2.1 Ubuntu 14.04 LTS Users

Ubuntu 14.04 LTS users install the environment directly on host OS. :-)

    cd ~
    sudo apt-get install git
    git clone https://github.com/istarc/stm32.git
    cd ~/stm32
    git submodule update --init
    ./setup-env.sh

Linux, Windows or Mac users should install the environment indirectly:

- via [Docker using LXC virtualization](https://github.com/istarc/stm32/blob/master/README-Docker.md);
- via [Vagrant using Virtualbox virtualization](https://github.com/istarc/stm32/blob/master/README-Vagrant.md).

# 3. Usage
## 3.1 Build Existing Projects

    cd ~/stm32/
    make clean
    make -j4

## 3.2 Deploy an Existing Project

    cd ~/stm32/examples/Template.mbed
    make clean
    make -j4
    sudo make deploy

## 3.3 Test Existing Projects using Buildbot:

    firefox http://localhost:8010
    Login U: admin P: admin (Upper right corner)
    Click: Waterfall -> test-build -> [Use default options] -> Force Build
    Check: Waterfall -> F5 to Refresh

# 4. More Info

 - [http://istarc.wordpress.com/][1]
 - [https://github.com/istarc/stm32][2]
 - [https://registry.hub.docker.com/u/istarc/stm32/][3]
 - [https://vagrantcloud.com/istarc/stm32][4]

  [1]: http://istarc.wordpress.com/
  [2]: https://github.com/istarc/stm32
  [3]: https://registry.hub.docker.com/u/istarc/stm32/
  [4]: https://vagrantcloud.com/istarc/stm32

