# Compiling-Android-L-System

## 修改启动界面
- 启动界面为bmp图片，24位，建议使用PS转换
- PS转换时，先把图片垂直反转,并保存为bmp格式
- 转换后，把bmp图片重命名成splash.img
- 把修改后splash.img覆盖原来的splash.img
- 覆盖原来路径 `/common/build/splash.img`

![splash setting](./img/splash.png)

## 修改开机动画和结束动画
- 开机动画，`/system/media/bootanimation.zip`
- 关机动画，`/system/media/shutdownanimation.zip`

## 修改桌面壁纸
- 覆盖原来路径 `/frameworks/base/core/res/res/drawable-nodpi/default_wallpaper.jpg`
- 找到原来壁纸位置，覆盖原来的default_wallpaper.jpg
- 桌面壁纸大小和屏幕分辨率一致即可

## 系统应用
- LINUX/android/build/target/product/core.mk



## 第三方应用

`LINUX/android/device/qcom/common/base.mk`

	packages/apps/pemt/UsbSync.apk:data/app/UsbSync.apk
 	packages/apps/pemt/manual.apk:system/app/manual.apk  
 	packages/apps/pemt/manual.apk:system/app/manual.apk

### MK

	LOCAL_PATH := $(call my-dir)
	include $(CLEAR_VARS)

	# Module name should match apk name to be installed.
	LOCAL_MODULE := sgcc
	LOCAL_MODULE_TAGS := optional eng
	LOCAL_SRC_FILES := $(LOCAL_MODULE).apk
	LOCAL_MODULE_CLASS := APPS
	LOCAL_MODULE_SUFFIX := $(COMMON_ANDROID_PACKAGE_SUFFIX)
	LOCAL_MODULE_PATH := $(TARGET_OUT_DATA_APPS)
	LOCAL_CERTIFICATE := platform
	LOCAL_MULTILIB      := 32
	LOCAL_PREBUILT_JNI_LIBS := \
		lib/armeabi-v7a/libcepri_dev.so			\
		lib/armeabi-v7a/libzlib.so
	
	include $(BUILD_PREBUILT)
