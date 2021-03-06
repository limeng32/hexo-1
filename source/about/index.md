---
layout: post
title: 开发 flying 的契机
description: 我所作的一切，其实就是以 pojo 对象和数据库交互。
category: about
date: 2017-04-03
list_number: false
---

## [程序员和数据库管理员的不同](#程序员和数据库管理员的不同)
为什么应用开发程序员和数据库管理员的思考方式大多时候不一样？为什么同一个需求 programmer 和 dba 会有不同的解决方法？实际上并非因为同行相轻，而是这两种人使用的工具体系不同：程序员使用的是计算机专家设计的语言，而数据库管理员使用的是数学家设计的语言，看，问题就在这里。

所以程序员会觉得和数据库打交道的代码很 <b>dirty</b>，很多开发了好几年数据库的人会觉得自己没学到啥，日复一日的再写一成不变的 sql。而 dba 们的怨言更多：“真有必要声明那么多对象类型？还有比 json 更好的格式？你们的 sql 基础为什么这么差？……”

然后，flying-初雪 即将到来。

## [flying 努力做的，其实就是以 pojo 对象和数据库交互](#flying-努力做的，其实就是以-pojo-对象和数据库交互)
flying 的本质，就是想把每一次与数据库交互都变为一次对象交互，而不是一次字符串交互。对象相对于字符串的好处不言而喻。

首先，计算机理解对象比字符串容易得多。比如我有一个子容器向父容器发送查询请求，然后按照业务，父容器要在这个查询请求上修改一个条件再追加一个条件。使用查询对象可以轻松做到这一点，因为它能被完全解析；但解析字符串就很麻烦了（试想一下拆分一个充满了 and 和 or 的 sql），估计只有数据库厂商才能提供可靠的工具。

其次，不同数据库的 sql 语法有区别，但它们的查询对象相同。

最后，查询对象可以跨语言甚至跨格式（JSON、XML），在传输和保存时可以压缩，这都是字符串所不具备的。

以上这些特性有的 flying 已经实现，有的正在实现，但它们最终都会实现。

## [合理的 orm 是团队成长的第一步](#合理的-orm-是团队成长的第一步)
互联网团队的成长实际上是信息处理能力的成长。第一步的瓶颈是存储层面，第二步的瓶颈是路由层面，第三步……别想太多。总之一个团队告别了冗长的 sql 语句后，它自然会达到一个新的层次。

乱语一番，请君见笑。