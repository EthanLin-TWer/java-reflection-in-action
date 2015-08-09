## Java Reflection in Action - Java反射实战(翻译稿)

#### 林从羽, Linesh.                                      08 Aug, 2015

Java反射，本质上是Java程序能够对自身程序要素（类名、方法、注解等）进行自我检查及自我修改的能力，是Java虚拟机必须从底层支持的一项特性，也从语言层面上支持了应用层面的解耦。这本书是我大四做“Java反射机制研究与应用”毕业设计时候接触的书，书中讲解了Java反射的基本要素以及实际的应用场合，涉及代理、调用栈信息、类加载器等方面，虽然写于2004年，但其中使用方式及思想仍大有可借鉴之处。

这本书和周志明的《深入理解Java虚拟机：JVM高级特性与最佳实践（第2版）》，分别提供了应用层面和虚拟机层面上Java反射涉及以及实现范围的参考。若要深入了解反射的具体理论及实现，可以参阅本书作者之一Ira R.Forman的另一本著作"Putting Metaclasses to Work"，以及JVM底层的实现源码。具体的链接我再补上，现在只是把自动生成的这个丑哭了的README.md替换掉。

#### 翻译进度
本书目前翻译了第1章，第2章翻译了一部分，不过仍需做一次小校正才能发出。目前主要进行的是第4章的翻译工作，会陆续发出。

#### 本书目录
[Contents](SUMMARY.md)

#### 感谢
之前一直在本地进行翻译工作，感谢jimmylv同学让我看到gitbook这个写作工具，给我带来新的有关前端的在线协作的工作方式，以及为我介绍了一大波提高工作效率及改善工作环境的插件及软件。

感谢所有有缘来与这本译书相遇的读者。

#### 致辞
欢迎也期望任何人都能为本书翻译不足的地方提出建议，以及你对于本书与这项翻译的任何观点与看法。翻译本书目前仅是自己的业余爱好，在翻译过程我力求通畅并忠于原文，并希望能够让读者从其中得到原书要传达的内容。完善并对本书的翻译精益求精当是自己的追求，然而这个步骤将在全书的大略翻译完成以后进行。

