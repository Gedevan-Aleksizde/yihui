---
title: 新手教程：建立网站的全套流程与详细解释
date: '2009-06-19'
slug: how-to-build-a-website-as-a-dummy
---

你要是Google这个话题，得到的结果八成都是广告——他们都会告诉你，“嘿，我（或某公司）这里可以建网站，傻瓜式的哟，快来投奔我吧！”新手一般都觉得建网站是一件超级复杂的事情，于是很天真很无邪地进了圈套，到最后还乐呵呵帮人数钱。傻瓜式的东西就如它的名字一样，只是为傻瓜准备的，要格外小心。

我正式接触计算机在2002年，接触网站建设在2003年，想想时日也不短了，虽然不是什么高手，但还是有一定发言权滴。数月前，鼓动[江堂兄](http://li-and-jiang.com/blog/)从Live Space逃脱、建立了自己的窝，而近日又把自己的网站和“[统计之都](http://cos.name)”网站都搬了家，然后也帮“[贝吉塔行星](http://www.bjt.name)”逃离了那抽风的Live Space，后来有朋友问起关于如何建立个人网站的事情，所以干脆写篇教程，把这建网站的来龙去脉讲清楚。


# 一、建网站的准备材料：域名和空间


一个网站通常由域名和一堆网页文件构成：

- 域名：就是“三达不溜什么什么点坑”这样的东西（如www.yihui.name，不严格，见后话），它由一家非营利组织ICANN管理，但它授权给了若干注册商（registrar）去卖域名，你可以在这些域名经销商那里注册**顶级域名**，所谓顶级域名就是“字母或数字组合+顶级域名后缀”，这些后缀包括常见的com/org/net，也包括不常见的name/info/biz等，各家允许注册的域名后缀可能有所不同，这就看个人喜好了；关于域名后缀，本来它是有含义的，比如com是company，org是organization，name是个人域名，等等，但我个人觉得这些东西已经没太大意义了，域名只要好记、看着像模像样就可以了，管它是公司还是组织呢（有例外：如gov等特殊后缀一般人不能注册），那著名的del.icio.us网站就是个很好的例子，它不一定非得是美国网站，但这个域名就是注册得很巧妙。顶级域名下面可以设置子域名，如二级三级域名，严格来说，www.yihui.name只是yihui.name的二级子域名，只是www太盛行，以至于人们干脆把`www.***.***`当作顶级域名了。animation.yihui.name就是本站的一个子域名/子站。说了半天，域名怎么注册啊？你Google一下“域名注册”或“domain name registration”，顶上的Sponsored link中都是有实力的注册商，但我作为过来人要严重提醒的是，尽量**不要在国内注册**（尤其不要相信那个万网的鬼话）。据说GoDaddy还可以，我没试过，只知道它似乎不能注册.name域名，我自己是在name.com注册的域名（需要付美元，我用的PayPal，双币种的信用卡也可以）。
- 网站空间：想得简单一些，空间和你的硬盘没啥区别，只不过是空间服务商卖给你的一块服务器硬盘位置而已，性能可能比你的PC机好一点，网站空间就是放网页文件的地方，网页文件你可以简单想象为你硬盘里的文件，它们也是按路径访问的，网址的路径就对应着硬盘里的文件夹。网页文件通常分为：
  - 静态网页：其内容是固定不变的，里面放着HTML代码（网页的一种语言），不管谁、不管什么时间访问，内容都一样，通常以.html/.htm为文件名
  - 动态网页：我估计现在大多数网站都是动态的了，所谓动态就是网页文件会根据不同的条件**解析**生成不同的HTML代码，例如：某动态页面根据时间和用户ID向访问者问好，早上访问就说早上好，晚上访问就说晚上好，路人甲来了就说路人甲你好……动态页面通常和数据库挂钩，用户在访问网页的时候，网页程序就存取数据库，所以页面内容会不断更新。动态页面可能采取不同的语言编写，如古老的微软的ASP、盛行的开源的PHP。现在网络上有无数的网站系统，我当然推崇PHP+MySQL的系统了，目前尤其看好WordPress系统。
- 注意有些国外空间是几乎可以当做自己的电脑使用的，包括编译安装程序（如Python），SSH登录，MySQL可以在命令行中执行，等等，国内似乎没见过能给空间这么大自由的

域名和空间没有必然联系，域名的作用就是作为一个字符串映射到一个IP地址上，因为（1）IP地址太难记了（2）IP地址数目有限（同一个IP上可以放N个域名）所以才需要域名这么个东西。这就意味着，你有换空间的**自由**。哪天对空间服务商不高兴了，可以直接把他踹了，把域名解析到别家去，用另一家空间。哎哎，等会儿，啥叫**域名解析**？

# 二、关于网站的配置

## 1、域名的设置

注册域名交完银子之后，域名就是你的了，如果你在国内注册的，你花钱买的域名**不一定**真的是你的。一定要看你是否有以下权利：

- 修改注册联系人、管理联系人、技术联系人和付费联系人信息，如果你在后台找不到修改的地方，那么恭喜你，这域名好像不是你的，而是某奸商的，用WHOIS查一下域名信息吧；
- 拿到授权码（Auth Code），国内也有叫域名转移密码的，这个码很重要，如果你不知道或奸商不告诉你，那再次恭喜你，这个域名仍然不是你的，想搬家到别家注册商都搬不了，万一不行遇到这种情况，那么就去ICANN投诉奸商，每天投诉三遍，如果某注册商总是遭到投诉，ICANN会修理它的，总之你一定要知道自己作为消费者有什么权利

如果域名真的属于你，那么你哪天对注册商不高兴了，也可以把它踹掉，转移到别的注册商下。

域名的设置主要是一些解析工作，包括：

- 域名服务器（name server）：通常是`ns*.***.***`之类的网址，这个服务器负责解析下面的各种设置，也就是说，它是域名各项设置的Boss。国内一些域名注册商通常以这一点为手段，卡住用户，比如限制你只能使用它的域名服务器，然后再限制你最多只能设置10项A记录或MX记录等，多了要另外收费，这种规矩实在是很扯淡；尤其是对于那些需要多个子域名的用户，这一点很不方便，国外情况好一些，至少我还没见过有哪家限制你使用特定域名服务器的；
  - 要特别提及的一点是，有些空间服务商只需要你把域名服务器设置为他们的域名服务器，剩下的所有解析问题你基本上都不用管了，你可以自由创建子域名，而不必添加A记录
- A记录：就是将域名指向主机IP，可以将顶级域名或子域名指向特定的IP，所以你的子域名和顶级域名可以不在同一台服务器上，比如我可以将www.yihui.name指向66.147.240.177，将test.yihui.name指向127.0.0.1，等等。
- MX记录：就是邮件服务器，大家知道邮箱是`***@***.***`的形式，当你发邮件点“发送”之后，首先你的邮件服务商要根据你的收件人邮箱的域名去找它的MX记录，然后再把邮件发给相应的（另一家）邮件服务商，比如我的域名yihui.name的MX记录是ASPMX.L.GOOGLE.COM，也就是Google Apps的邮件服务地址，当你给xie@yihui.name发邮件的时候，系统先去找一下yihui.name的MX记录，一看，哦，是Google啊，那就投递到Google家去，Google收到邮件，一看，哦，要发给xie用户啊，那就发给xie的收件箱中吧；我记得以前搜狗似乎也提供过免费的邮件服务，不知现在还在不在，我已经用Google Apps很久了。
- CNAME：即别名，这玩意儿就是个域名“面具”，比如我把google.yihui.name的CNAME设置为google.com，那么你们访问前者的时候实际上就在访问Google，域名中包含的任何路径都会原封不动传递给google.com，比如google.yihui.name/services/就是在访问google.com/services/，但你的浏览器地址栏中的地址不会显示后者，而是显示那个“伪装”的地址。所以只要我高兴，我可以随意制造消息，比如“Google换网址了，新网址是<http://google.xiexie.name>”。
- 其它设置：不说了，理论上一个A记录就够用了，别的都不用管。

## 2、主机的设置

域名设置好了之后，主机上也需要一些呼应工作。要是域名设置了A记录，但主机上不“接收”，那网站也没法使用。主机如何接收取决于它安装的网站服务程序，现在流行的是Apache，当然也有少数网站依旧抱着Windows IIS大腿（用ASP语言+Access数据库），据说近段时间又出现了一款新软件，有取代Apache的可能，名字忘记了。以Apache为例吧，主机上会创建一个虚拟主机（Virtual Host）配置文件，告诉服务器，“嘿，有个网站指向了你，你要为这个网站服务，这个网站放在某某目录下，如果用户访问某个网址，你要负责把该目录下的文件拿出来给用户看。”大致原理就是这样，细节不多说了。

对用户来说，不用管那么多细节，以上原理的实现对你来说就是在后台把域名绑定到主机的目录下（以及子域名绑定到子目录下）。一般来说，网站还需要两个辅助工具才能让主人随心所欲地配置自己的网站，即FTP和数据库。

### （1）用FTP传输网页文件

FTP就是用来传文件到某一台服务器的，只要你购买了虚拟主机服务，一般就会给你一个FTP帐号，你可以利用这个帐号登录你的主机，把网页文件传上去，然后用户就可以访问了。一点常识是，index.htm/index.php之类的网页文件通常是你在访问一个目录时主机会自动为你查找的文件，比如你访问yihui.name，主机会自动查找有没有index.php，如果有，就执行这个文件，生成HTML给你的浏览器。这个文件的文件名也许是可以配置的，但建议不要在这上面特立独行。

现在又很多成熟的建站系统，从网上下载下来然后传到服务器上，访问你的网址，按照提示一步步配置即可，跟装软件没两样。

### （2）网站数据库

动态网站大多数需要数据库（即使是文本文件“数据库”），如果你的网站用PHP语言，那么MySQL就是绝配了。若是PHP+MySQL空间（一般Linux主机都是这样），主机服务商会给你分配MySQL数据库帐号，包括：数据库主机（多为localhost）、数据库名、用户名、密码。这四项将会在你安装网页程序的过程中要求你填写。

# 三、网站的运行

对于那些程序员来说，第一个例子通常都是hello world，如果你愿意看hello world的话，就把“hello world”用任何文本编辑工具写在一个文本文件中，命名为index.htm（注意Windows会默认隐藏文件扩展名！你自己保证文件名不是index.htm.txt吧，我不管了），传到网站根目录下，然后访问你的网站，你就能欣喜地看到这个老得不能再老的hello world了。

一个像样的网站当然不是hello world这么简单，它的运行就像一个复杂的程序，可能存在文件之间的函数调用以及数据库的存取等等。世上真正开发网站程序的人肯定是少数，所以不用担心，你就用别人的程序吧，典型的网站系统有：

- 博客系统（Blog）：推荐WordPress，理由是程序写得简洁，扩展性强，我以前用国产的Bo-blog系统，后来没经得住诱惑投奔WP了
- 内容管理系统（CMS）：新闻八卦站、教程站等等，顾名思义就是填充内容的，这种网站八成是互相抄，没几个正儿八经写的，所以为了缓解大家的阅读压力，请各位客官珍爱生命，远离这种网站，也不要再重复建设
- 论坛系统（BBS）：网民对此应该非常熟悉了，国内常见的系统有PHPWind、Discuz等，国外盛极一时的有phpBB，我个人推荐的是一款相对新出道的bbPress，理由同WordPress，在大家拼命增加功能的今天（搞得用户面对一大堆选项焦头烂额），难得见到一款拼命减功能的论坛系统
- 维基系统（Wiki）：Wikipedia采用的是MediaWiki系统，如果你不想让维基和数据库交互的话，DokuWiki将是不错的选择，它不需要数据库支持，全部都是文本文件操作

网站的安装都没啥说的，一般都是把网页文件整锅端上服务器，然后访问你的网址，按提示走。该设定网站名称设名称，该输密码输密码。然后你会意识到，原来一个小小的个人也可以创造一个看似吓人的大网站。

但网站的维护并非一件简单的事情，当你有权利面对所有的选项时，你也会觉得痛苦。像我这种业余玩了几年网站的人都快有职业病了，什么地方没对齐就会觉得不舒服，什么地方少了个空格一眼就看出来了，段首空格缩进2字符还是1.9字符感觉就是不一样。所有的东西你都可以改，你愿意怎么布置就怎么布置。只需一个文本编辑器和FTP，你就可以改了传，传了看，看了改。俨然永劫不复了。所以建网站也要有好心态，千万别完美心态，不然这辈子都要不断改。现在网站系统更新也快，隔三差五就有新功能，看得你心痒痒：我是不是该装个A插件/换个B主题啊？张三家有个功能特别酷，我要不要琢磨一下是怎么弄的啊？……

所以，我是建议各位看官学习HTML和CSS以及PHP+MySQL呢，还是不建议呢？我也不知道。

还有搜索引擎优化（SEO），采取一些策略让搜索引擎喜欢你的网站，使得你的搜索排名靠前，你又得学习什么是网页Meta信息（关键词、描述），什么是301重定向，什么是404错误，什么是Apache的Rewrite模块什么是伪静态网址；……

# 四、摘要

头一次见到把摘要写到最后的吧？

1. 买域名，避开奸商，建议通过你熟悉的朋友介绍，不行就Google；若在国外买，可用支持美元的信用卡或PayPal付款；域名每年都要交钱的。
2. 买虚拟主机空间，避开奸商，建议通过你熟悉的朋友介绍，不行也不要随意Google，因为空间性能很重要，不试不知道；根据你的建站需求买相应的空间（静态？动态？需要多大？），国内分不同种类的空间，可能按大小收费，国外据我了解的HostMonster是没有大小限制的，一口价，敞开让你随便用，当然，总会受硬盘大小限制
3. 设置域名服务器或者A记录，指向主机
4. 通过FTP把网页文件传上去，然后访问你的新网站
5. 配置你的网站，通常可以登录网站后台作设置，平时做一些日常更新，看到眼红的功能也可以自己DIY出来
6. 如果你不得不在我英明神武的天朝购买虚拟主机，那么恭喜你还有最重要的一步，就是去英明神武的公衅部那里去备个鸟案，备案网址自己搜吧，能否备得上你自己烧香，我不管，一日不备案，一日网站不得运行，主机服务商会把你卡得死死的

有什么不清楚的请在下面穷追猛问，我会随时修改更新本文内容。本文叙述有诸多不严格的地方，但对新手来说不需了解那么多，因此没加说明。本文谢绝IT类网站转载。
