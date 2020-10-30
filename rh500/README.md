# 一、编译固件
## 1. 代码位置

-  github位置： https://github.com/ruihe-rockchip
-  gitlab外网位置：http://183.250.202.41:5522/rh
-  gitlab内网位置：http://10.10.40.17/


## 2.由github转gitlba下载方法

	在原android工程目录中执行命令： .repo/repo/repo init -u ssh://git@183.250.202.41:5522/rh/manifest.git -m rk3399pro-rh500-V1.0.xml --repo-url https://mirrors.tuna.tsinghua.edu.cn/git/git-repo  

## 3.编译方法

- 脚本编译
	编译A板： ./build.sh -b rh500A
	编译B板： ./build.sh -b rh500B

- 单独编译 uboot
	make rk3399pro_dual_defconfig && ./make.sh rk3399pro_dual
	或执行脚本： ./make.sh rk3399pro_dual

- 单独编译 kernel
	make ARCH=arm rockchip_defconfig
	编译A板android内核： ./make.sh android rh500A
	编译A板linux内核： 	./make.sh linux   rh500A
	编译B板android内核： ./make.sh android rh500B
	编译B板linux内核： 	./make.sh linux   rh500B
	生成boot.img:		mkbootimg --kernel arch/arm64/boot/Image --ramdisk $OUT/ramdisk.img --second resource.img --os_version 8.1.0 --os_patch_level 2019-08-05 --cmdline buildvariant=userdebug --output boot.img
	
- 单独编译 Android 上层
	source build/envsetup.sh && lunch rk3399pro-userdebug
	make

- 生成ota完成包
	make otapackage

- 生成ota差异包
	与rh100相同

# 二、测试映像位置	
- 内网位置：ftp://10.10.40.17:5521/rockchip    用户名：ftpuser，  密码：fjrh123456
- 外网位置：ftp://183.250.202.41:5521/rockchip    用户名：ftpuser，  密码：fjrh123456


# 三、文档
	在目录rh500