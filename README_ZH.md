# Evmongoose

![](https://img.shields.io/badge/license-GPLV3-brightgreen.svg?style=plastic "License")

Evmongoose是一个API接口友好和可伸缩的HTTP服务器库，它基于mongoose和libev实现。Evmongoose支持高度的可定制化
来扩展你的应用程序。在开始这个项目之前，我一直都没有找到一个令我满意的基于事件框架的HTTP服务器库。那些HTTP
服务器库只能loop它自己的对象，不能添加我自己的对象。比如我想基于事件框架监视某个信号（比如SIGINT）或者某个文件。

# 特性
* 高度的可定制化
* 支持HTTPS
* SSL库可选：OpenSSL和mbedtls，对于存储苛刻的系统可选择mbedtls
* 支持Lua（开发中）

## [示例程序](https://github.com/zhaojh329/evmongoose/blob/master/example/simplest_web.c)

# 编译
## 在Ubuntu上运行
### 安装依赖库
    sudo apt install libev-dev libssl-dev
    
### 安装evmongoose（默认支持HTTPS）
    git clone https://github.com/zhaojh329/evmongoose.git
    cd evmongoose
    mkdir build
    cd build
    cmake ..
    make

### 安装evmongoose（禁止HTTPS）
    git clone https://github.com/zhaojh329/evmongoose.git
    cd evmongoose
    mkdir build
    cd build
    cmake .. -DHTTPS_SUPPORT=OFF
    make

## OpenWRT/LEDE
	git clone https://github.com/zhaojh329/evmongoose.git
	cp evmongoose/openwrt/ openwrt_dir/package/evmongoose -r
	cd openwrt_dir
	make menuconfig
	Libraries  --->
	    Networking  --->
	        <*> evmongoose
	            Configuration  --->
	                SSl (mbedtls)  --->
	
	make package/evmongoose/compile V=s
	
# API参考手册
Evmongoose并没有改变mongoose和libev的API用法，所以请参考
[mongoose](https://docs.cesanta.com/mongoose/master)
和libev的API参考手册。只有一点需要注意，使用evmongoose时不再调用mg_mgr_poll。
	
## 感谢以下项目提供帮助
* [mongoose](https://github.com/cesanta/mongoose)
* [libev](https://github.com/kindy/libev)