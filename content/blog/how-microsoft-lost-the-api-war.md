---
title: Review | How Microsoft Lost the API War
date: "2020-03-21 19:11:00"
description: "Joel Spolsky 关于 Windows API 的看法"
---
上周在看 [Hyrum's Law](https://www.hyrumslaw.com) 这篇文章看到作者有提到 Joel 的 [Law of Leaky Abstractions](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/)，于是我又顺藤摸瓜浏览了一下 Joel 的其他文章，其中有一篇是 [How Microsoft Lost the API War](https://www.joelonsoftware.com/2004/06/13/how-microsoft-lost-the-api-war/)，也就是今天要 review 的文章。

在正式开始之前先介绍一下 Joel，Joel 是一位影响力很大的软件工程师和创业者，在 Joel 的博客 Joel on Software 里有很多思考非常深刻的文章（建议每位软件工程师都经常去翻阅一下），除此之外还写有一本书[《More Joel on Software》](https://book.douban.com/subject/4163938/)，当然，作为一位软件工程师，肯定不只是会写文章，Joel 在 91 年从耶鲁大学毕业后加入微软 Excel 团队，在 94 年创办了 Fog Creek Software，这些离我们都有点远了，但是作为一位在全球都有很强影响力的人，肯定不只是这些古老的成就，程序员每天都访问的网站 Stack Overflow 以及项目管理工具 Trello 也是 Joel 的作品。

如果想了解关于 Joel 的更多的信息，你可以访问 Joel 的博客 [Joel on Software](https://www.joelonsoftware.com) 和 [Wikipedia](https://en.wikipedia.org/wiki/Joel_Spolsky)。接下来正式进入主题。

这是一篇 Joel 写于 2004 年的[文章](https://www.joelonsoftware.com/2004/06/13/how-microsoft-lost-the-api-war/)，距今天已经过去 16 年，软件开发和开发工具发生了翻天覆地的变化，也正是互联网高速发展的时期， 这个行业也发生了翻天覆地的变化， 在 2004 年，Apple 还没东山再起，Google 还是一家小公司，Zuckerberg 刚在哈佛宿舍开发出来 TheFacebook，腾讯也才刚刚在香港交易所上市。那时候大家是怎样看待微软的呢？

> “Microsoft is finished. As soon as Linux makes some inroads on the desktop and web applications replace desktop applications, the mighty empire will topple.”

这就是当时大家对微软的看法。

虽然有很多事实表明 Linux 是对微软的一个巨大威胁，但是预测微软的结束还是非常不成熟的，微软在银行有让人难以置信的现金，而且现在依然创造着让人难以置信的利润。在 90 年代每个人都在想 IBM 会结束，mainframe 会成为历史，但是现在来看，mainframe 依然存在，而且 IBM 摇身一变成为了一家大型咨询公司。所以，通过片面的数据来判断微软已经结束了是非常的夸张的。

然而，有一个很少人注意到的现象正在发生：作为微软最宝贵的东西，Windows API，已经输了。作为微软的基石，开发者已经对其失去了兴趣。

操作系统是一个管理计算机资源，让应用运行起来的东西。人们不关心操作系统个，人们只关心应用，文字处理、即时通讯以及有 Paris Hilton 照片的网站，操作系统自身并没有什么用处，因此，拥有最有用的应用的操作系统才是最有用的。所以，如果你想卖操作系统，最重要的事情是让软件开发者为你的操作系统开发软件。

在开发软件时，要做的很多事情都需要操作系统过来做，比如显示一个菜单、写入一个文件，而且在每个操作系统中这些函数都是不一样的，这些函数叫做 API。如果你想让 Windows 应用跑在 Linux 上你就需要重新实现 Windows 的 API，包含成千上万的函数，工作量和重新实现一个 Windows 差不多。这就是为什么 API 是微软重要的资产。

在微软有两股相反的力量，「Raymond Chen 阵营」和「MSDN Magazine 阵营」。

Raymond Chen 是 Windows 团队的一位开发者，他的博客[The Old New Thing](https://devblogs.microsoft.com/oldnewthing/) 里塞满了有关 Windows 中某些事物的技术故事。其中一个故事是 Windows 为了做向后兼容所做出的巨大努力：

> 从顾客角度来看，你买了 X, Y 和 Z 三款应用，然后升级到 Windows XP，你的电脑开始偶发性崩溃，Z 应用无法正常工作。你会去告诉你的朋友「不要升级到 Windows XP，会经常崩溃，而且和 Z 应用不兼容」。你会去调试系统去发现是因为 X 应用导致崩溃、是 Z 应用因为使用了未公开的窗口消息吗？当然不会，你会去把 Windows XP 退掉。

类似这样的问题，这里还有[一篇吐槽](https://devblogs.microsoft.com/oldnewthing/20031015-00/?p=42163)。

很多开发者不同意这种向后兼容的开发方式，比如 Macintosh。但是相反，1983 年在 IBM PC 上开发的 DOS 应用现在还可以正常的执行，这要归功于核心 Windows API 团队。

另一个阵营是 MSDN Magazine 阵营，这个阵营的人总是在说服你使用像 COM+,MSXML,DirectX 这类新技术，但是当你把用了这些充满了让人头痛的外部依赖的应用发布给你的顾客时他却无法正常运行。这叫做「DLL 地狱」，明明在这里可以正常运行的，为什么到了那里却不行了呢？

Raymond Chen 阵营的人坚信通过让 write once and run anywhere 更简单来方便开发者。MSDN Magazine 阵营的人坚信通过提供强大的代码库来方便开发者，只要他们能接受巨大的部署和安装成本，以及学习曲线。

Raymond Chen 阵营的一切都是整合，不要让事情变得更差，让已经有的保持依然可以使用。MSDN Magazine 阵营一直在搅动绝大的技术碎片，以至于没人能跟得上。

在微软，MSDN Magazine 阵营赢得了这场战争，第一次大胜利是让  Visual Basic.NET 不兼容  VB 6.0，然后是 IIS 6.0 用了一个完全不一样的线程模型，然后是 .NET 1.1 不兼容 .NET 1.0，现在，OS 团队决定放弃 Win32，开始用 WinFX。于是，[越来越多的开发者开始转向 web 开发](http://www.paulgraham.com/road.html)。

微软实在是太大了，有太多的开发者，他们过于追求收入的增长以至于突然决定重写一切不是一个大项目。Raymond Chen 的微软本来是可以用一系列的 DLL 来实现 Avalon 这个新的图形系统来运行在任何版本的 Windows 上的，但是微软要给你一个买 Longhorn 的理由，他们想实现的是一个巨大的改变，就像 Windows 替代了 DOS 那样，但是 Longhorn 跟 Windows XP 对比并不像 Windows 和 DOS 之间那样改变巨大，它不足以让人们去为了使用它而买新的电脑。微软做了很多这种错误的角色，就像 WinFS，通过将文件系统变成一个关系型数据库来让搜索更简单，但是让搜索更简单的真正方法应该是让「搜索」更简单，不要让我去输入用于搜索语言的文件元信息，用诞生于 1973 年的全文搜索技术就可以。

当然，.NET 和 XAML 都是非常好的技术，但是，没有一个专职工作的开发人员有时间去跟上这些新的开发工具，仅仅是因为微软有过多员工在开发开发工具！

越来越多的的开发者开始转向 web 开发，web 应用和富客户端应用都有非常明显的优缺点，web 应用更容易部署，而富客户端应用有更快的响应速度。现在有 80% 的 UI 是基于 web 的技术开发的，即使没有新的浏览器出现，也会达到 95%，这对大部分人来说都很好，当然，对开发者更好，所以，突然间微软的 API 就不再重要了，web 应用不需要微软的 API。

HTML 是新的 API，那些让 HTML 「唱歌」的人是新的赢家。

以上便是 Joel 在 2003 年发表的关于微软的观点。在很多年以来，微软给人留下的都是一个封闭的形象，站在开源社区的对立面，而现在，微软成为了开源社区里最厉害的商业公司，先是收购了开源社区广泛使用的开发协作工具 Github，最近又收购了 Node 包管理工具 NPM。同时，微软开发的 Visual Code 也成为了最流行的代码编辑器，而 Visual Code 正是用 web 技术开发，当年微软把 eclipse 作者、设计模式四人帮之一的 Erich Gamma 挖到微软时给 Erich 的目标就是开发一款基于 web 的开发工具。现在，做 windows 开发的开发者越来越少了，客户端的使用场景也越来越少了，我前几天买了台新的工作电脑，除了开发工具外，基本上没有安装其他软件，而那些被广泛使用的客户端软件，也越来越多的是用 Electron 这种基于 web 的技术来开发。

The new API is HTML.