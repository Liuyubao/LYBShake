# LYBShake

本博客包含了如何实现iOS摇一摇全步骤，包括了完整的代码。
先附上demo地址https://github.com/Liuyubao/LYBShake ，支持swift3.0+。

一、导包
----

![这里写图片描述](http://img.blog.csdn.net/20180201112252229?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

项目主要使用到了AVFoundation这个包。


二、继承代理，并实现协议方法
---------------
在要监听摇一摇的VC中继承AVAudioPlayerDelegate这个代理（为了播放音效），并实现以下3个代理方法。
![这里写图片描述](http://img.blog.csdn.net/20180201112953789?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
开始摇动的代理方法：
![这里写图片描述](http://img.blog.csdn.net/20180201113031521?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
取消摇动的代理方法（一般指的是中途摇动动作被打断）：
![这里写图片描述](http://img.blog.csdn.net/20180201113107183?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
结束摇动的代理方法：
![这里写图片描述](http://img.blog.csdn.net/20180201113116078?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

三、逻辑实现
------
【在监听摇动的VC中开启摇动感应：】

```
/**
开启摇动感应
*/
UIApplication.shared.applicationSupportsShakeToEdit = true
```
【定义摇动手势的上下两部分图：】

```
@IBOutlet weak var upImg: UIImageView!
@IBOutlet weak var downImg: UIImageView!
```
![这里写图片描述](http://img.blog.csdn.net/20180201113526593?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

【定义要播放的声音，分为摇动过程和摇动结束的声音：】

```
var player: AVAudioPlayer?
```
![这里写图片描述](http://img.blog.csdn.net/20180201113804629?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

【摇动开始的逻辑：】
1、开始的动画：图片上下移动60；
2、设置开始摇动的音效；
3、结束动画：还原上下两张图片；
![这里写图片描述](http://img.blog.csdn.net/20180201113835024?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

【摇动结束的逻辑：】
将所有摇动激发的事件都写在这里，包括音效及数据的更新。
![这里写图片描述](http://img.blog.csdn.net/20180201120429369?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvWXViYW9Mb3Vpc0xpdQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

四、github代码
----------

如果本博客对您有帮助，希望可以得到您的赞赏！
完整代码附上：https://github.com/Liuyubao/LYBShake
