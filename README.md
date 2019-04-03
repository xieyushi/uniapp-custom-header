自己做的小程序项目中需要用到自定义导航栏,踩了几个坑以后,基本上满足了需求.现在回过头来.发现这个东西,在需求不复杂的情况下,还是可以写成组件的形式的.  
组件已经上传至uniapp插件市场,链接为[https://ext.dcloud.net.cn/plugin?id=281](https://ext.dcloud.net.cn/plugin?id=281)
具体的代码.已经上传到github:[https://github.com/xieyushi/uniapp-custom-header](https://github.com/xieyushi/uniapp-custom-header)<!--more-->  
直接是现成的uniapp项目.  
uniapp的custom-header也终于完成了.希望在这里给想用到自定义导航栏的同学能有所帮助:  
插件引入方法:  
```
import customHeader from '@/components/custom-header.vue';
```
页面标签中的写法:  

```
<custom-header></custom-header>
```
这是最简版的标签,会自动占位到微信小程序的胶囊下方的位置,如下图:  
![image](https://raw.githubusercontent.com/xieyushi/blog/master/blogimg/blogimg42.png)  
一般至少会设置几个参数:  

```
<custom-header :title="title" :backBtnClass="backBtnClass" :showBack="showBack" :containerStyle="containerStyle" :titleStyle="titleStyle" @backTap="backClick" ref="backTap"></custom-header>
```

插件的所有参数如下:  

```
导航文字:title,变量类型:String  
顶部导航容器样式字符串:containerStyle,变量类型:String  
标题导航样式字符串:headerStyle,变量类型:String  
左侧返回按钮样式类:backBtnClass,变量类型:String  
标题样式字符串:titleStyle,变量类型:String  
是否显示返回按钮:showBack,变量类型:Boolean  
点击返回事件调用的方法:showBack
```
下面说一下踩坑的问题:  
1.--status-bar-height 这个CSS变量,不可取,特别是在全面屏,刘海屏(如IPHONE X)的时候,这个高度是完全不够的.所以状态栏的高度.还是要用如下代码来获取:  

```
const res = uni.getSystemInfoSync();
return res.statusBarHeight + 'px';
```
2.导航的样式要用sticky.不要用fixed.  
3.其它的小程序中没有测试过(因为这个状态栏下方的标题栏,在小程序中,不管什么设备,都是固定的44px不会变化,不知道其它的是多少,如果有区别,请大家在插件中加上CSS的条件编译来区分)  
其它的注意事项:  
1.顶部的容器我没有给底色,因为自定义很可能一般都不是白底了.所以这里的底色大家请自行设置吧,在containerStyle中直接加上background的自定义样式就行了.  
2.自定义导航的页面,如果有分享.那么用户点了分享进来后,这个返回的按钮要不要显示的问题,以及如果显示,那么点了返回跳转到哪个页面的问题.大家一定要维护好,不然这个自定导航栏还不如不做...  
3.左上角的返回目前是用的uni.css中的uni-icon-back,其实这并不是一个很好的选项,样式上,大家要自己调一下.让返回的图标与文字能够居中对齐是对好(我目前的项目.是用了button,然后用了图片,有局限性,在这里的我用的是view,用户可以自定义这个view的class,大家可以给这个view 背景图片等来丰富这个元素)  
希望能对大家在uniapp或者是其它的小程序开发上有帮助!以后有时间.我也会不断完善更新的.

