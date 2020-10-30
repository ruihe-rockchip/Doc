# 一、编译固件
## 1. 代码位置

-  github位置： https://github.com/ruihe-rockchip
-  gitlab外网位置：http://183.250.202.41:5522/rh
-  gitlab内网位置：http://10.10.40.17/


## 2.由github转gitlba下载方法

	在原android工程目录中执行命令： .repo/repo/repo init -u ssh://git@183.250.202.41:5522/rh/manifest.git -m rk3399-rh200-V1.0.xml --repo-url https://mirrors.tuna.tsinghua.edu.cn/git/git-repo  

## 3.编译方法

- 脚本编译
  直接执行 ./build.sh

- 单独编译 uboot
	make ruihe-rk3399_defconfig && make
	或执行脚本： ./make.sh ruihe-rk3399

- 单独编译 kernel
	make ARCH=arm64 rockchip_defconfig
	make ARCH=arm64 rk3399-rh200-android.dtb
	make ARCH=arm64 rk3399-rh200-android.img
	
- 单独编译 Android 上层
	source build/envsetup.sh && rk3399-userdebug
	make

- 生成ota完成包
	make otapackage

- 生成ota差异包
	 与rh100相同

# 二、测试映像位置	
- 内网位置：ftp://10.10.40.17:5521/rockchip    用户名：ftpuser，  密码：fjrh123456
- 外网位置：ftp://183.250.202.41:5521/rockchip    用户名：ftpuser，  密码：fjrh123456


# 三、文档
	在目录rh200, rh201