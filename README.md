YYDispatchQueuePool
==============

[![License MIT](https://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://raw.githubusercontent.com/ibireme/YYDispatchQueuePool/master/LICENSE)&nbsp;
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)&nbsp;
[![CocoaPods](http://img.shields.io/cocoapods/v/YYDispatchQueuePool.svg?style=flat)](http://cocoapods.org/?q=YYDispatchQueuePool)&nbsp;
[![CocoaPods](http://img.shields.io/cocoapods/p/YYDispatchQueuePool.svg?style=flat)](http://cocoapods.org/?q=YYDispatchQueuePool)&nbsp;
[![Support](https://img.shields.io/badge/support-iOS%206%2B%20-blue.svg?style=flat)](https://www.apple.com/nl/ios/)&nbsp;
[![Build Status](https://travis-ci.org/ibireme/YYDispatchQueuePool.svg?branch=master)](https://travis-ci.org/ibireme/YYDispatchQueuePool)

iOS utility class to manage global dispatch queue.<br/>
(It's a component of [YYKit](https://github.com/ibireme/YYKit))

When use a concurrent queue to execute lots of blocks, I met this problem in some situation:

<img src="https://raw.github.com/ibireme/YYDispatchQueuePool/master/Snapshots/CTRunDraw.png" width="320">
<img src="https://raw.github.com/ibireme/YYDispatchQueuePool/master/Snapshots/CTRunDrawLock.png" width="320">

When some block is locked, the concurrent queue may create lots of thread and may block the main thread.
Use a global serial queue pool to avoid it.

Usage
==============
	// Get a serial queue from global queue pool
	dispatch_queue_t queue = YYDispatchQueueGetForQOS(NSQualityOfServiceUtility);
	
	// Create a serial queue pool
	YYDispatchQueuePool *pool = [[YYDispatchQueuePool alloc] initWithName:@"file.read" queueCount:5 qos:NSQualityOfServiceBackground];
	dispatch_queue_t queue = [pool queue];


Installation
==============

### CocoaPods

1. Add `pod 'YYDispatchQueuePool'` to your Podfile.
2. Run `pod install` or `pod update`.
3. Import \<YYDispatchQueuePool/YYDispatchQueuePool.h\>.


### Carthage

1. Add `github "ibireme/YYDispatchQueuePool"` to your Cartfile.
2. Run `carthage update --platform ios` and add the framework to your project.
3. Import \<YYDispatchQueuePool/YYDispatchQueuePool.h\>.


### Manually

1. Download all the files in the YYDispatchQueuePool subdirectory.
2. Add the source files to your Xcode project.
3. Import `YYDispatchQueuePool.h`.


Documentation
==============
Full API documentation is available on [CocoaDocs](http://cocoadocs.org/docsets/YYDispatchQueuePool/).<br/>
You can also install documentation locally using [appledoc](https://github.com/tomaz/appledoc).


Requirements
==============
This library requires `iOS 6.0+` and `Xcode 7.0+`.


License
==============
YYDispatchQueuePool is provided under the MIT license. See LICENSE file for details.



<br/><br/>
---
中文介绍
==============
iOS 全局并发队列管理工具。<br/>
(该项目是 [YYKit](https://github.com/ibireme/YYKit) 组件之一)

当用 concurrent queue 来执行大量 block 时，有时会遇到下面这种情况：

<img src="https://raw.github.com/ibireme/YYDispatchQueuePool/master/Snapshots/CTRunDraw.png" width="320">
<img src="https://raw.github.com/ibireme/YYDispatchQueuePool/master/Snapshots/CTRunDrawLock.png" width="320">

当某个 block 所在线程被锁住时，concurrent queue 会创建大量线程以至于占用了过多资源而影响到主线程。这里可以用一个全局的 serial queue pool 来尽量控制全局线程数。

用法
==============
	// 从全局的 queue pool 中获取一个 queue
	dispatch_queue_t queue = YYDispatchQueueGetForQOS(NSQualityOfServiceUtility);
	
	// 创建一个新的 serial queue pool
	YYDispatchQueuePool *pool = [[YYDispatchQueuePool alloc] initWithName:@"file.read" queueCount:5 qos:NSQualityOfServiceBackground];
	dispatch_queue_t queue = [pool queue];
	
安装
==============

### CocoaPods

1. 在 Podfile 中添加 `pod 'YYDispatchQueuePool'`。
2. 执行 `pod install` 或 `pod update`。
3. 导入 \<YYDispatchQueuePool/YYDispatchQueuePool.h\>。


### Carthage

1. 在 Cartfile 中添加 `github "ibireme/YYDispatchQueuePool"`。
2. 执行 `carthage update --platform ios` 并将生成的 framework 添加到你的工程。
3. 导入 \<YYDispatchQueuePool/YYDispatchQueuePool.h\>。


### 手动安装

1. 下载 YYDispatchQueuePool 文件夹内的所有内容。
2. 将 YYDispatchQueuePool 内的源文件添加(拖放)到你的工程。
3. 导入 `YYDispatchQueuePool.h`。


文档
==============
你可以在 [CocoaDocs](http://cocoadocs.org/docsets/YYDispatchQueuePool/) 查看在线 API 文档，也可以用 [appledoc](https://github.com/tomaz/appledoc) 本地生成文档。


系统要求
==============
该项目最低支持 `iOS 6.0` 和 `Xcode 7.0`。


许可证
==============
YYDispatchQueuePool 使用 MIT 许可证，详情见 LICENSE 文件。


相关文章
==============
[iOS 保持界面流畅的技巧
](http://blog.ibireme.com/2015/11/12/smooth_user_interfaces_for_ios/) 

