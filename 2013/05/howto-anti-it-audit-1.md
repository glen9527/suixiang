<!DOCTYPE.md>
.md xmlns="http://www.w3.org/1999/...md" xml:lang="zh-CN">
<head>
<meta http-equiv="Content-Type" content="text.md; charset=utf-8" />
<meta name="generator" content="Python script by program.think@gmail.com" />
<meta name="provider" content="program-think.blogspot.com" />
<link type="text/css" rel="stylesheet" href="../../css/program-think.css" />
<title>如何对付公司的监控[1]：规避“网络行为审计” - 编程随想的博客</title>
</head>
<body>
<div id="main" style="width:100%;">
<h1><a href="../../index.md" title="回到首页">如何对付公司的监控[1]：规避“网络行为审计”</a></h1>
<div class="post-info"><span class="date-header">2013-05-09</span><a href="../../tags/IT.md" class="tag">IT</a> <a href="../../tags/IT.E4BFA1E681AFE5AE89E585A8.md" class="tag">IT.信息安全</a> </div>
<hr>
<div class="post">
&#12288;&#12288;这种监控手段最为常见，所以俺先多花点口水聊聊应对的招数。<br /><br /><h2>★原理介绍</h2><br />&#12288;&#12288;基于网络流量的监控，在安全界称为“上网行为审计”。<br />&#12288;&#12288;其原理，简单说就是：在公司的网络出口部署一个网络审计设备，这个设备会记录每一个员工的上网行为。比如：你在什么时间、上了什么网站、使用了什么应用层协议、传输流量多大、等等。示意图如下：<br /><img src="../../images/2013/05/OddVetbwSArvYUGDb9WXnrSQDSPb_JYaPIUT3T_yOBiGFPiT5ddyK3dMTMVou-ThyR46u-QuzcI19x8YmJ9hgD78mp-8SuFocr7Pg_nmrGpknACnRePn7r6haDM" alt="不见图 请翻墙"><!--program-think--><br /><br /><h2>★对于监控方的优缺点</h2><br /><h3>◇优点</h3><br />&#12288;&#12288;相对于另外两种方法，它的主要优点是：部署很容易。很多时候只需要部署一台设备就可以监控整个公司的上网行为。<br />&#12288;&#12288;而且这种监控设备通常都会附带历史记录查询的功能，如此一来，公司的管理层可以根据时间段，根据员工的内网IP，进行针对性的查询。<br /><br /><h3>◇缺点</h3><br />&#12288;&#12288;这种监控方式的主要缺点，主要有两个：<br />&#12288;&#12288;<b>1. 它会受限于<u>加密的</u>网络流量</b><br />&#12288;&#12288;一旦网络数据流是加密的，监控设备就很难（甚至不可能）分析出网络流量中的应用层数据。<br />&#12288;&#12288;<b>2. 太依赖于公司的网络出口</b><br />&#12288;&#12288;什么意思捏？就是说如果员工不通过公司的“公网出口”访问互联网，那监控设备自然就无法监控到。比如说，你把公司的笔记本电脑拿回家上网，公司的网络审计自然就监控不到。<br /><br />&#12288;&#12288;看完这个缺点分析，聪明的读者已经明白如何规避了。还不明白的同学，请看俺下面的具体介绍。<br /><br /><h2>★规避第1招——使用 HTTPS</h2><br />&#12288;&#12288;HTTPS 是访问 Web 页面的一种标准协议，而且是强加密的。当你使用 HTTPS 访问某个网站的时候，公司的网络审计设备无法对你的 HTTPS 数据流进行解密。因此也就无法知道你具体在干嘛。<br />&#12288;&#12288;最典型的例子就是 Google 搜索（之前在《<a href="../../2013/03/internet-resource-discovery-3.md">解答 Google 搜索的常见问题</a>》有详细介绍过）。<br />&#12288;&#12288;当你使用 <b>HTTPS</b> 的方式进行 Google 搜索，公司的网络审计设备是看不到你的搜索关键字，也看不到你的搜索结果。反之，如果你用明文的 <b>HTTP</b> 方式进行 Google 搜索，那么你的搜索关键字和搜索结果就会被公司的网络审计设备详细记录下来。<br />&#12288;&#12288;顺便说一下，其它知名的搜索引擎（比如：百度、Bing、等）目前还没支持 HTTPS，所以都存在被监控的风险。<br /><br />&#12288;&#12288;但是 HTTPS 有如下两个缺点，大伙儿需要注意。<br />&#12288;&#12288;<b>缺点1</b><br />&#12288;&#12288;网络审计设备虽然无法解密 HTTPS 的加密流量，但是还是可以看出来，你在访问哪个网站。<br />&#12288;&#12288;<b>缺点2</b><br />&#12288;&#12288;某些网站本身就不支持 HTTPS 协议。这时候你就无法使用 HTTPS 的方式访问了。<br /><br /><h2>★规避第2招——使用翻墙工具</h2><br />&#12288;&#12288;那么，如何解决 HTTPS 的上述两个缺点捏？俺不得不学一下祥林嫂，再次跟大伙儿啰嗦"翻墙"这个话题。<br />&#12288;&#12288;如果你对“翻墙”一无所知或者了解不多，请先看俺的扫盲教程《<a href="../../2009/05/how-to-break-through-gfw.md">如何翻墙</a>》（可惜这篇文章本身需要翻墙才能看到）。<br />&#12288;&#12288;另外，俺博客上有许多翻墙工具的使用教程。在俺博客页面上点“IT.翻墙”这个标签，就可以看到所有翻墙的相关博文。<br /><br />&#12288;&#12288;几乎所有的翻墙工具都有如下两个特点。这两个特点可以用来对抗公司的网络监控。<br />&#12288;&#12288;<b>特点1——翻墙工具都是加密的</b><br />如果你看完俺写的那篇扫盲——《<a href="../../2009/05/how-to-break-through-gfw.md">如何翻墙</a>》，应该就知道 GFW 的一大特色是敏感词过滤。为了对付 GFW 的敏感词过滤，<b>大部分</b>翻墙工具都会使用加密。一旦你使用翻墙方式上网，你的上网流量是加密的，公司的网络监控设备就无法知道你上网的内容。<br />&#12288;&#12288;提醒一下：少数翻墙工具（比如GoAgent）不是采用强加密的方式传输数据，不能确保规避网络监控。<br />&#12288;&#12288;<b>特点2——翻墙工具通常都有“中转服务器”</b><br />&#12288;&#12288;所谓的中转服务器，对于代理类翻墙就是代理服务器；对于 VPN 翻墙，就是 VPN 服务器。因为有了中转服务器，所以网络审计设备只能看到你访问了某个中转服务器，但是无法知道你<b>最终访问</b>的网站。<br />&#12288;&#12288;换句话说，网络监控设备，充其量<b>最多只能猜到你在使用翻墙工具</b>，但是你用翻墙工具上了那些网站，它是一概不知的。<br />&#12288;&#12288;那么有没有办法让网络审计设备<b>彻底无法知道</b>你的上网行为？当然有。后面的第4个招数会介绍。<br /><img src="../../images/2013/05/ym8NucMzyAcxYHA8sNfJa69rn6BeL5lDxriZnqz4gXDOmh5mZ9NKb7VYGibfmI19X174p9_IB4MW-HC4NamUizQLaA0UwNiTvx6xOw1FhvHEBum8NJSLPKXzokQ" alt="不见图 请翻墙"><br /><br />&#12288;&#12288;补充说明一下“公共代理”：<br />&#12288;&#12288;互联网上有很多公共代理，这些公共代理大部分是不加密的，仅仅只有转发的功能。这种情况下，你的上网流量依然会被监控的。所以，公共代理是不靠谱的，还是得用专门的翻墙工具，才能够确保加密。<br /><br /><h2>★规避第3招——使用翻墙工具+虚拟机</h2><br />&#12288;&#12288;一般情况下，使用翻墙工具对付公司的网络监控，是足够了。但如果你比较小心谨慎，还可以再考虑“翻墙工具+虚拟机”的方式。<br />&#12288;&#12288;翻墙工具搭配虚拟机，主要是考虑到如下情况：<br />&#12288;&#12288;你使用的是代理翻墙而不是VPN翻墙，并且你的浏览器装了插件（比如  Flash 插件、Java 插件）。<br />由于插件可以不经过浏览器代理设置，直接联网。潜在风险就是：插件发起的网络请求可能是直连（不经代理），这就有可能被监控到。<br />&#12288;&#12288;请注意：浏览器<b>扩展</b>（extension）和浏览器<b>插件</b>（plugin）是两码事，别搞混了。两者的区别请看“<a href="../../2012/08/howto-prevent-hacker-attack-5.md">这篇博文</a>”<br /><br />&#12288;&#12288;对于浏览器插件直接联网的风险，示意图如下。<br /><img src="../../images/2013/05/fYzQ4MlJFO819D4eW4E5aA7bs8iTTvWamfnp3u65E9pGUGDAwUAjxm4TLitAjZV2dOX5ctSsRr9-tzXEQc4-MI7Zg9bskuktKFhoI8_Pap9ZFvcZvG6l6RyHIcg" alt="不见图 请翻墙"><br /><br />&#12288;&#12288;那么，如何用虚拟机来防止浏览器插件直接联网捏？请看俺之前的博文《<a href="../../2012/10/system-vm-0.md">扫盲操作系统虚拟机</a>》和《用虚拟机隐匿公网IP》（<a href="../../2013/01/howto-cover-your-tracks-6.md">原理介绍</a>，<a href="../../2013/01/howto-cover-your-tracks-7.md">配置图解</a>）——里面有详细介绍和配置教程，这里就不再啰嗦了。<br /><br />&#12288;&#12288;提醒一下：<br />&#12288;&#12288;这里介绍用虚拟机不是为了隐匿自己的公网IP，而是为了隐匿<b>目标网站</b>的IP。但配置方法是一样的。<br /><br /><h2>★规避第4招——使用另外的物理线路上网</h2><br />&#12288;&#12288;前面分析了网络审计设备的一个缺点是——太依赖于公司的网络出口。也就是说，你如果不通过公司的网络出口，那它是一点办法都没有。<br />&#12288;&#12288;如今网络越来越发达，各种上网手段越来越多。大伙儿很容易就能做到：不通过公司的线路，照样接入互联网。<br />&#12288;&#12288;常见的方法有如下几种<br /><br /><h3>◇使用手机上网（PC机通过手机上网）</h3><br />&#12288;&#12288;如今智能手机很普及，完全可以用手机作为中介，让电脑联网。如果你的手机支持 3G 移动网络，速度应该不成问题（看视频都可以）。<br />&#12288;&#12288;方法至少有两种：通过 USB 线，通过 WIFI（手机作 AP 热点）。Android 或 iOS 系统都可以用这两招搞定。俺个人倾向于用 USB 线，安全性比较好。<br />&#12288;&#12288;具体怎么玩，大伙儿自己去 Google 一下。俺就不浪费口水了。<br /><br /><h3>◇使用 3G 上网卡</h3><br />&#12288;&#12288;如今 3G 越来越普及了，3G 上网卡也很常见了。你可以额外花点银子，买个上网卡。具体的费用，自己去运营商的官网查询。<br /><br /><h2>★小结</h2><br />&#12288;&#12288;刚才聊了4种方式，用来对付“基于网络的监控”。HTTPS 虽然最简单，但是安全性最差；第4个招数最安全，但是有额外的经济成本。所以比较折中的办法，就是用第2招和第3招——基于翻墙工具。<br />&#12288;&#12288;如果列位看官还有啥补充或者有啥疑问，欢迎<a href="../../2013/05/howto-anti-it-audit-1.md">到本文留言</a>。<br /><br /><a href="../../2013/05/howto-anti-it-audit-0.md#index">回到本系列的目录</a>。<br /><div class="blogger-post-footer">
</div>
<hr>
<div class="copyright">
<h4>版权声明</h4>
本博客所有的原创文章，作者皆保留版权。转载必须包含本声明，保持本文完整，并以超链接形式注明作者<a href="mailto:program.think@gmail.com">编程随想</a>和本文原始网址：<br>
<a href="2013/05/howto-anti-it-audit-1.md">2013/05/howto-anti-it-audit-1.md</a>
</div>
</div>
</body>
<.md>