
# 1.测试环境

## 1.1 BOOTHR-FRONT：
	1.拉取代码
	2.本地编译
	3.本地编译通过push到gitlab仓库
	4.触发webhook重新构建应用

## 1.2 BOOTHR-CTL
	1.拉取vo core rmi  wfe pe workauth 代码，并将jar包上传至maven私服
	2.拉取ctl 代码
	3.将代码push到gitlab私有仓库。
	4.触发webhook重新构建应用

## 1.3 BOOTHR-HRTRAIN
	1.拉取代码并将依赖的jar包上传至maven私服
	2.将代码push到gitlab私有仓库
	3.触发webhook重新构建应用


## 1.4 BOOTHR-FS-STORE
	1.拉取代码并将依赖的jar包上传至maven私服
	2.将代码push到gitlab私有仓库
	3.触发webhook重新构建应用

## 1.5 NC57

### 项目重新构建

## 生产环境

### 项目重新构建
