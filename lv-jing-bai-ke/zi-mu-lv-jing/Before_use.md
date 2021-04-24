# 用前须知

字幕滤镜的用前须知！

## 字幕滤镜分类

主流的字幕滤镜有四种，分别是：

* [`Subtext`](http://www.vapoursynth.com/doc/plugins/subtext.html)：VapourSynth默认自带的字幕滤镜，拥有最基础的添加字幕功能。
* [`VSFilter`](https://github.com/HomeOfVapourSynthEvolution/VSFilter)：Windows Media Player里的一个字幕加载工具，后续被添加了VapourSynth的接口，使其可以在VapourSynth中使用。
* [`VSFilterMod`](https://code.google.com/archive/p/vsfiltermod/)：VSFilter的另一个分支，在VSFilter原本的基础上大幅提高效率，改善了字幕渲染效果。
* [`xy-vsfilter`](https://code.google.com/archive/p/xy-vsfilter/)：VSFilter的一个分支，在VSFilter原本的基础上新增了各种特效代码。

上述字幕滤镜由于最初版已年久失修，目前推荐使用[`VSFilterMod`](https://github.com/sorayuki/VSFilterMod/)和[`xy-vsfilter`](https://github.com/HomeOfVapourSynthEvolution/xy-VSFilter)

## 如何选择字幕滤镜？

首先需要确定你的字幕文件是什么格式，目前主流的格式有三种，分别是：

* `srt`：最简单的文本格式，仅包含每段字幕出现的时间和内容，无字形、字体格式设定；通常用于在线播放或者本地加载播放，具体的字形、字体可以手动在播放界面更改。
* `ass`：srt的升级版，可以详细的设定每一段字幕的字形、字体、位置等各类高级信息，一些复杂的动态文本特效都可以用它来编写；通常用于本地制作特效字幕。
* `sub`：图片格式字幕，每一段字幕都是有一张图片构成，字形、字体和内容都不支持更改；通常用于DVD、BD等光盘中。


若字幕中仅有最基础的字幕时间以及内容信息，则可以选择任意一款字幕滤镜；

若字幕中包含[`mocha跟踪字幕`](https://www.bilibili.com/video/BV1eW41177bK)，则必须使用`xy-vsfilter`；  

若字幕中包含`特效代码`，则必须使用`VSFilterMod`；

请尽量避免字幕中同时出现`mocha跟踪字幕`和`特效代码`两种情况；

**原因如下：**

1.部分特效代码仅有VSFilterMod支持，例如在字幕中插入图片，如果在这种字幕里使用了非VSFilterMod滤镜，它则会直接忽略所不支持的信息，有些辛苦制作出来的特效可能就根本无法显示；

2.同时因为用mocha制作的跟踪字幕通常每一帧的坐标都会包含小数点位，但是VSFilterMod却会舍去字幕文件中字幕位置信息的部分小数点位，编码出来的效果就会导致跟踪字幕在播放的过程中因为出现坐标的不准确而异常抖动