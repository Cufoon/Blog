---
title: "MIUI 到底会在哪些地方恶心你"
slug: "miui-shit"
date: 2023-04-09T19:31:28+08:00
draft: false
author: "一位米粉"
tags: []
categories: []
---
<style>
    *:not(i){
        font-family: "MiSans", "SF Pro SC", "SF Pro Text", "SF Pro Icons",
            "PingFang SC", "HarmonyOS_Regular", "Helvetica Neue",
            "Microsoft YaHei", "Helvetica", "Arial", sans-serif !important;
    }
    *::-webkit-scrollbar {
        display: none;
    }
</style>

内容很多，一时不知道从哪里讲起，那就先从相册说起吧

# 一、MIUI相册

版本号：3.5.2.9(4197441) 小米相册编辑版本号：1.0.3.2.1(4197441)

## 1.1 人物识别问题

![相册](/images/2023/001.webp)

这两个页面看起来没有任何问题，但是事实上存在着两个问题。

问题一：即使我已经是小米云服务的会员，相册里面依然有相当一部分的照片没有正确的进行人物识别，这很烦，也很无语，且低一点的机型小米不给开放本地识别能力，但是如果你用过一款相册应用，时光相册，你把时光相册的联网权限关掉、开启手机的飞行模式，你再用时光相册的人物相册，你会发现时光相册就能很好的进行本地的人物识别，所以小米相册在这一点上就很恶心，它不是不行，它不是不搞不做摆烂。

问题二：那就是在智能相册的页面，它虽然会显示人物相册，但是这其实并不是人物相册，这也就意味着你如果不小心忽略错了人物，那么恭喜你，至少在这比较直观的智能相册页面，你无论如何也找不回你已经忽略的人物了。这一点很恶心，要不是我真的有找回已经忽略的人物的需求，我真的想不到还会存在这种问题。

# 1.2 还是TMD人物识别问题

![相册](/images/2023/002.webp)

### 曲线解决恢复已忽略人物的问题

如果在上一步你也有需要恢复已忽略人物的需求，那么事实上也是有办法的，那就是搜索，如果你在不经意间点到相册左上角的搜索按钮（当然前提是你开起了相册的云服务，是的，shitMIUI相册把本地搜索也给砍了，haha）。

那么你就会发现第一行显示的就是人物信息，点击最后一个更多就能进入人物主页（如果你逛小米社区，在小米社区提问，会有小米的员工回复告诉你要到人物主页去恢复已忽略的人物），没错，人物主页是这样进入的。然后你点击右上角的三个点就能查看已忽略的所有人物，点进去就能取消忽略了。

这样就解决了恢复已忽略人物的问题，但是在智能相册页面，你永远都做不到这一点，而一个正常用户知道人物相册，甚至你去忽略一个人物的时候，你的操作都是在智能相册页面完成的。很讽刺，明明在智能相册里面人物的右边对称位置增加一个文字按钮更多，或者增加一个类似与搜索时显示的更多的那样子的人物就能很好的解决进入人物首页的问题，但是shitMIUI相册团队就是不做。很无语，我只能想到一种理由，那就是MIUI相册的工程师、产品经理根本就不用小米手机或者就不用小米的相册，否则绝无可能做出来这么个东西。

### 你以为这就完了？太天真了

如果你有仔细看上面的两张图，你会发现无论我在智能相册里面，还是在人物主页里面看到的都只是两个人物，但是在搜索页面很明显还存在两个未命名的人物，甚至其实那个更多的图标里面还有其他的人物。

最最戏剧性的是，这几个未命名的人物你是无法管理的，你点进去就是显示那些识别的图片，你无法像其他人物一样可以执行忽略或者合并操作，对它就在那里，它不能管理，也不能合并，真的，这太糟糕了，可以说这个功能就是依托答辩。答辩到即使你是小米云服务的会员，从你的相册里面识别出来人物都是随缘的，你可能会有大量的照片没有进行人物识别，甚至有很多的照片进行了人物识别，也识别出了人物但是你管理不了，但是你搜索的页面又能看到，这又何尝不是一种PUA，折磨你，恶心你。

## 1.3 迷一样的时光功能以及摆烂的拼图功能

首先是时光功能

坦白说，应该没有人知道时光会在什么时候生成，什么条件下生成。

几年来，我的相册里面就生成了三个时光，然后有一个时光在我升级MIUI14之后还莫名其妙消失了😃

小米社区随便翻一翻都能知道这功能有多难用，且完全不可预测，鬼知道什么时候会生成什么时候又会突然消失。

然后是拼图功能

像本文中这种纵向的拼图，你使用相册的拼图功能是不能直接实现的，小米社区也有不少的同学反馈了这个问题，但是尽管相册圈有500多个入驻小米员工，但是连屁都没有一个好吧，什么是态度，我相信不言自明，毕竟相册圈还有不少20年就一直到现在还是开发中的提案。

**如何自救？** 最好的方法那就是使用第三方工具来进行这种拼图，别用答辩相册，真的答辩。
如果你不想下载使用第三方的拼图工具，那么你可以用一下几个步骤来完成，首先，把你所有的图片先通过编辑功能把它们横过去，然后再用拼图功能拼接，拼接完成之后，再把拼接的图片通过编辑功能横过来。🤗

# 二、笔记

版本号：5.5.3(553)

MIUI的笔记可以说是改版了好几次，但是笔记的一些问题依旧没有解决

**2.1** 比如，只要你点开就是默认编辑模式，你点开什么都没有改，你就看看，你再返回，它的最后编辑时间就会变成当前的时间。（文字笔记好像现在没有这个问题，但是思维笔记依然存在这个问题，且小米云服务的网页里面的笔记也还是有这个问题）

**2.2** 长按拖动排序笔记没了👍

**2.3** 然后我看最近好像又改成每篇笔记限制字数了，且字体不跟随系统主题设置了，且现在笔记行间距过大

**2.x** 之前我使用笔记的时候出现过数据丢失且连续几天都丢失，我无法判断现在还有没有这个问题，我现在是没有问题的，还是不建议在这里记不容忍丢失的内容，万一没了，美的库。

# 三、文件管理

版本号：4.4.7.6(4476)

文件管理能有什么问题呢？？

文件管理啥都好，现在还整合了小米云盘，但是死活不愿意适配Android/data和Android/obb目录，我不理解，很不理解，又是因为谷歌的政策不能做？

还有在有些情况下长按选中文件夹会选中不了，返回上级文件夹再回来就又行了。你大概率没遇到这个情况，等你遇到了，你就知道我说的是什么意思了。

# 四、应用商店

## 4.1 应用更新问题

小米的应用商店是真的慢，很多APP往往很早的就在其他的应用商店就能获取到最新的版本，但是小米应用商店就不一样，往往等应用开发者上新版本的一周左右之后才能在小米的应用商店收到更新。这种体验是相当差的，你可以解释为小米应用商店为了用户体验所以在应用更新方面没有那么积极。但是华为、OPPO、VIVO都比小米的快，都没有小米更注重用户体验。

当然你可以是一个不喜欢更新手机应用的人，那么这一点其实对于你而言，无所谓。

## 4.2 界面无比混乱且有开屏广告

先说开屏广告，尽管尽管你可以说所有应用商店在启动的时候都有开屏广告，你比如MIUI的钱包、小米视频、音乐APP，它都有开屏广告，但是最大的问题是钱包、小米视频、小米音乐都可以卸载或者说有更加完美的替代。（尽管MIUI14剃刀计划，剃掉老用户，只有新款手机可以卸载钱包、小米视频和音乐APP，明明就是开放个卸载，该几行代码甚至只是移除掉几个白名单的问题，但是就是不做，别扯什么工信部预装应用备案什么的，钱包能备案成手机功能必须且不可卸载应用本身就是纯扯淡的事，比烂更烂没有什么意义）应用商店可以说拥有真正系统级应用的意义，然而每一次打开都有开屏广告这很痛苦，甚至近期的更新还增加了退出应用商店时二次确认会弹广告。我实在不知道该说什么，要不咱还是首页多点广告吧，开屏广告去掉吧，或者你有点良心，把应用商店从名单里面去掉，这样也能方便的卸载掉应用商店而不会卡米。

然后是界面混乱问题，小米的应用商店的界面混乱程度，真的“混乱”这个词都自愧不如。榜单和软件界面还好，其他三个页面是真的依托答辩

### 首先看首页

![应用商店比较-首页信息流](/images/2023/003.webp)

上图左边是小米的应用商店，中间是OPPO的应用商店，右边是VIVO的应用商店

且小米的长截图有BUG，左边小米应用商店的截图没有截全

从图中应该也不难看出小米的布局是最差的，OPPO最佳，VIVO次之。

### “游戏”跟上图主页的情况十分类似，不再重复放图

### 再来看看“我的”页面

![应用商店比较-我的页面](/images/2023/004.webp)

很显然，我用高下立判来形容，不过分吧？

（且长截屏发挥稳定的会在最后加上一条黑线，真的离谱，且由于小米应用商店这个页面列表里面还有一个列表，所以导致无法截全，当然黑线也更粗）

# 五、个性美化

## 5.1 应用图标

MIUI的主题和各种自定义美化功能可以说是广受好评，尽管我是一个经典主题党，我不喜欢去用那些图标意义不明的主题，不熟悉手机的情况下找个应用都得翻来翻去。

MIUI的主题免费之后主题商店的主题质量有所下降，很多主题都是粗制滥造的，而且小米并不允许用户个人使用修改过的主题，想要换主题，要么root进行破解，要么只能是使用小米主题商店里面上架的主题。可是小米主题商店里面的主题质量实在是太差了，而且长期都是各种仿IOS类的主题或者是那种乱七八糟花里胡哨的主题占据着主题商店的大头，简约的主题也往往由于图标不够好看，且主题商店有一些奇怪的要求，最后也导致不够简约。

坦白说，主题这东西千人千面，萝卜青菜各有所爱，没有是与非。但是我想表达的是，我个人就非常喜欢MIUI默认经典主题的图标，精美好看简约规范，让我想要去更换图标的它其实只是那些鲨x第三方应用的图标，但是如果想保留默认的经典主题的图标，然后更改第三方应用的图标，这在现在的MIUI上面是无法实现的，因为首先小米就不允许主题设计师使用其经典主题提供的图标，要求主题设计师必须重新设计系统应用的图标。可是直到如今MIUI也没有提供任何一种方式来自主更换在桌面上应用的图标。而在这一点上，一个已经在天上的品牌在数年前就早已实现。

当然你会说现在MIUI桌面不是可以给应用编辑图标吗？编辑图标还有1x1 2x1 1x2 2x2几种大小可选吗？你为什么不用这个，对，我想说的是，这个功能是真的很垃圾，不论什么货色的图标都上架卖0.99米币不说，这也根本就不是更换图标，它就是桌面小组件那一套逻辑罢了，所以如果你的应用在一个文件夹里面，你必须把它移出文件夹才能编辑图标，这真的让我觉得1x1的图标就是依托答辩，你还要开心的往下咽。

综上，MIUI在自己已经不好好搞自己桌面的“完美图标”的情况下，还给不同机型就“完美图标”这个事情上进行了区分，尽管已经如此恶心不厚道的基础上，又推出了编辑图标这种收费的乐色，不是不让你收费，把东西做好，别说0.99米币，5米币该买还是会买的。

## 5.2 小组件

MIUI桌面的小组件的圆角问题，大家已经吐槽的很多了，基本上你随便搜一搜都有不少人在吐槽。
除了这些之后，小组件商店的页面也做的很混乱，真的混乱。超出文字表达了，可以看一下图，觉得不混乱也没事，因人而已。

<img src="/images/2023/005.webp" alt="添加小组件页面" style="width: 50%" />

# 六、云服务

小米的云服务可以说是MIUI一个十分重要的部分，但是长久使用下来，至少我7年多来的使用体验并不是那么的好，小米的云服务永远会存在一些让人很难受的问题。

## 6.1 同步不一致的问题

小米云服务一直以来的理念都是模仿iCloud的同步机制，而不是备份机制或者二者的糅合。

既然是同步机制，最大的问题就莫过于同步不一致的问题，

如果你曾经使用过相机的拍文档的功能，理应当在相册里面只有一张照片，而且你仍然可以对这张照片再次进行“文档编辑”调整效果，这很美好，因为在现在的相册里面就是这样的它只会有一张。但是当你通过i.mi.com上面来查看你的相册，你很有可能会看到每一个你利用拍文档拍的照片都实际上是一张原图和一张经过文档编辑处理后的图片。这似乎问题也不大，因为毕竟在手机上显示的就是一张，网页上只能说明前端工程师偷懒没有适配好。但是倘若你在手机上把一张文档的照片给删除了，经过同步之后，你很有可能会发现只是把“文档编辑”处理后的照片给删除了，而原来的那张原图还会留在云空间里，它只会在你访问i.mi.com上面的相册才能看得到，你在手机相册里面是看不见的。

还有一个典型的同步不一致的场景，那就是如果你习惯于截图并分享给好友，在分享截图时勾选分享之后删除这张截图的功能，那么当你打开你的相册，你发现截图里面确实没有那些你只用来分享之后就会被删除掉的截图，但是同样的，你在i.mi.com上面依然能够找到他们。

这就完了吗？其实还没有，你如果经常去清理自己的短信，你会发现有些时候手机上的短信已经删除了，但是云服务空间里面还是存在，当然如果你的手机里面有成千上万的短信，而你从来不管不问，这里面会不会有同步不一致的问题，你也完全无法察觉。

甚至前些天，我就出现过，云备份我已经删除了但是空间还一直被占用的问题，这个问题在几天之后就自然恢复了。云服务同步不一致的问题，会是一个比较大的问题，特别是我打开了快速同步，并且手动进行多次同步，还是会有不一致的情况下，这是很痛苦的，极其痛苦。这种不确定性会让你不断地怀疑自己同步的内容会不会突然消失，因为你删除的东西同步之后云端都还可能依然存在，那么你增加的内容也很有可能实现了假同步，当你信心满满的换到新设备之后，一段时间之后你发现你再也难以找回之前的数据了。

## 6.2 家人服务

家人服务有什么问题呢？家人服务的问题很多。

首先是存储共享的功能，事实上小米的云服务存储空间共享功能要早于现在“家人服务”出现，但是是在小米10周年之后才有的功能。这也就意味着，你很有可能除了你自己，你的家人的账号也给开通了小米云服务的会员，至少我的是这样。

然后按照小米现在共享空间的逻辑，你把你的空间共享给你的家人，你的家人如果也是小米云服务的会员，那么要么他还是使用他自己的空间（相当于共享了个寂寞），他如果选择使用你共享给他的空间，那么他自己的云服务会员就浪费了，他的自动续费会被关闭，但是他的会员时间还是一直在走的。希望就是说这方面能解决一下吧。不想让米粉的会员时间顺延，那就让会员的空间叠加也行啊。当然你可以说别人的也是这样，其实也没什么毛病，这也不是什么问题。

## 6.3 查找手机

本来查找也没有什么问题，我一直使用以来也没有什么问题，好巧不巧，这两天它出问题了。

是的，万万没想到这也有问题的。

问题就是我已经打开了查找手机，就像下面这样：

<img src="/images/2023/006.jpg" alt="查找设备设置" style="width: 50%" />

可是在i.mi.com上面或者在手机的查找设备页面，我的这个设备它就是一直显示的处于离线状态，真的让我觉得很无语，我甚至怀疑过是我的网络问题，我换过wifi尝试，用手机流量尝试，用手机一卡的流量尝试，用手机流量的二卡尝试，结果都还是这样。

于是乎，我怀疑是需要重新登录一下小米账号，于是我退出了小米账号，又重新登录，重新打开查找设备，结果还是一样，于是我又开始怀疑是不是我的小米云服务软件的版本有问题，于是我又卸载了小米云服务软件的更新，然后又进行了重新打开查找设备，依然不行。我进行了我可以进行的所有方法（除了重置手机恢复出厂设置，因为代价太大了要备份又要恢复，太浪费时间了），来尝试解决这个问题。但是无法得到解决，即使经历了至少三天的时候它依然没有恢复，尽管我一直连接着网络，打开了上面所有查找手机相关的开关，无论在i.mi.com上面还是手机设置里面的查找手机里面，它就是一直显示离线状态。

<img src="/images/2023/007.jpg" alt="查找设备-离线" style="width: 50%" />

# 七、总结

诚恳地讲，现在的MIUI已经很好了，从MIUI7开始往系统内增加广告到MIUI9快如闪电，再到MIUI12口碑崩盘，再到现在的MIUI14，MIUI好像又站起来了，又好像没有。绝大多数广告都能关，但是也一直在尝试增加新的广告。倒也无可厚非，把广告做漂亮一点就行。系统还是一如既往地不够稳定，你不知道哪一天它就出问题了，猝不及防。你也就只能想着理解万岁理解万岁。一个MIUI+beta了两年，最后变成了小米妙享，还各种设备都不支持，冲着小米妙享买的小米平板5的人不知道是何种感受，华为受制裁后，互联功能的宣传就没那么多了，小米妙享MIUI真的认真做了吗，这很难说，毕竟它还在做。很多开发版和之前内测版积累的很多好的东西无论如何也更新不到正式版/稳定版，比如手机管家（安全中心）里面的自动任务，何时才能等到开发版上功能丰富的自动任务？我不知道，我也无法知道。小米社区里依然有成吨的反馈需要解决，解决的过来吗？很难说，很明显解决不过来，但是社区里又在搞些什么呢？桌面下拉要不要改成搜索？相册首页的“全部-相机”要不要挪到右上角菜单？安全中心要不要改名叫手机管家（已经改了）？手机管家里面功能列表要不要精简点去掉几个，然后让用户去设置里翻那几个功能（已经删掉了）？我不理解也不清楚，精力究竟花在了哪里，工程师在忙些什么，用户的反馈能否真的被看见，产品每天在想什么，都难以预见，也都是打工人，也都喜欢摸鱼，这又有何不可呢？但是我又会有一些遗憾，这么多年我都一直很喜欢MIUI，它也一直有它的独到之处，有BUG那又能怎么样呢？又不是修不好又不是百分百会遇到，可是当我的年龄逐渐增加，我已经不太喜欢折腾了，遇到的这些问题，再也不是说我随便刷个机恢复出厂设置解决一下无所谓的，曾经的不是百分百遇到在这时就变成了百分之百。坦白说，我依然喜欢MIUI，我只是不相信了。
