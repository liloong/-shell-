
# 1.测试环境-应用版本更新

## 1.1 BOOTHR-FRONT PC前端应用
	1.拉取代码
	2.本地编译
	3.本地编译通过push到gitlab仓库
	4.触发webhook重新构建应用
 
## 1.2 BOOTHR-CTL 会话层
	1.拉取vo core rmi  wfe pe workauth 代码，并将jar包上传至maven私服
	2.拉取ctl 代码
	3.将代码push到gitlab私有仓库。
	4.触发webhook重新构建应用

## 1.3 BOOTHR-HRTRAIN 培训模块微服务
	1.拉取代码并将依赖的jar包上传至maven私服
	2.将代码push到gitlab私有仓库
	3.触发webhook重新构建应用


## 1.4 BOOTHR-FS-STORE 文件存储微服务
	1.拉取代码并将依赖的jar包上传至maven私服
	2.将代码push到gitlab私有仓库
	3.触发webhook重新构建应用

## 1.5 NC57基础镜像
	1.精简 生产环境的NC代码
	2.编写 Dockerfile制作NC57基础镜像
	3.将制作好的镜像打上标签（用于识别版本号）
	4.将该镜像push到docker测试环境私有仓库
	
## 1.6 NC57融合层镜像
	1.拉取 BOOTHR-NC-API 最新源码
	2.拉取 BOOTHR-NC-API-WRAPPER 最新源码
	3.拉取 BOOTHR-NC-HRSS-PATCH 最新源码
	4.通过 ant 对拉取到的源码进行编译
	5.编写 Dockerfile 将编译好的代码copy到nc57的基础镜像中
	6.通过 Dockerfile 制作nc57融合层镜像
	7.将制作好的镜像打上标签（用于识别版本号）
	8.将该镜像push到docker测试环境私有仓库
	9.通过 浏览器连接到 openshift平台
	10.找到 应用对应的 Deployments
	11.更改该应用的ymal文件（更改镜像的版本号）
	12.保存后自动触发更新该应用

# 2.生产环境-应用版本更新

## 2.1 测试环境测试OK后申请更新生产环境

## 2.2 BOOTHR-FRONT PC前端应用
	1.通过 浏览器连接到openshift平台
	2.找到 应用对应的Builds
	3.点击 Start Build 手动触发更新
	
## 2.3 BOOTHR-CTL 会话层
	1.通过 浏览器连接到openshift平台
	2.找到 应用对应的Builds
	3.点击 Start Build 手动触发更新

## 2.4 BOOTHR-HRTRAIN 培训模块微服务
	1.通过 浏览器连接到openshift平台
	2.找到 应用对应的Builds
	3.点击 Start Build 手动触发更新

## 2.5 BOOTHR-FS-STORE 文件存储微服务
	1.通过 浏览器连接到openshift平台
	2.找到 应用对应的Builds
	3.点击 Start Build 手动触发更新

## 2.6 NC57 融合层
	1.将通过测试的镜像版本重新打上标签 
	2.将该镜像push到docker生产环境私有仓库
	3.通过 浏览器连接到openshift
	4.找到 应用对应的 Deployments
	5.更改该应用的ymal文件（更改镜像的版本号）
	6.保存后自动触发更新该应用


