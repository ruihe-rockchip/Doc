# 一、编译固件
## 1. 代码位置

-  github位置： https://github.com/ruihe-rockchip
-  gitlab外网位置：http://183.250.202.41:5522/rh
-  gitlab内网位置：http://10.10.40.17/


## 2.由github转gitlba下载方法

	在原android工程目录中执行命令： .repo/repo/repo init -u ssh://git@183.250.202.41:5522/rh/manifest.git -m rk3288-rh100-V1.0.xml --repo-url https://mirrors.tuna.tsinghua.edu.cn/git/git-repo  

## 3.编译方法

- 脚本编译
  直接执行 ./build.sh

- 单独编译 uboot
	make rk3288_defconfig && make
	或执行脚本：./make.sh rk3288

- 单独编译 kernel
	make ARCH=arm rockchip_defconfig
	make ARCH=arm rk3288-rh100.dtb
	make ARCH=arm rk3288-rh100.img
	
- 单独编译 Android 上层
	source build/envsetup.sh && lunch rk3288-userdebug
	make

- 生成ota完成包
	make otapackage

- 生成ota差异包
	旧素材包：img/rk3288-target_files-old.zip
	新素材包：rockdev/Image-rk3288/rk3288-target_files-new.zip
	生成的差异包：img/v1.0.2.zip

	执行的命令： ./build/tools/releasetools/ota_from_target_files --block -v -i img/rk3288-target_files-old.zip -p out/host/linux-x86 -k build/target/product/security/testkey  rockdev/Image-rk3288/rk3288-target_files-new.zip img/v1.0.2.zip

# 二、测试映像位置	
- 内网位置：ftp://10.10.40.17:5521/rockchip    用户名：ftpuser，  密码：fjrh123456
- 外网位置：ftp://183.250.202.41:5521/rockchip    用户名：ftpuser，  密码：fjrh123456


# 三、文档
	在目录rh100, rh101