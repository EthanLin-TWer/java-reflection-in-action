# Using Java's dynamic proxy  
# 使用Java的动态代理


The dictionary [68] tells us that a proxy is an “agency, function, or office of a deputy who acts as a substitute for another.” When this idea is applied to object-oriented programming, the result is an object, a proxy, that supports the interface of another object, its target, so that the proxy can substitute for the target for all practical purposes.  
词典[68]对代理的定义是，代理是一个“中介【这里难翻】。”这个概念应用到面向对象编程上时，就产生了一类称为代理的对象。一个代理对象可以去实现另一个对象——称为目标对象——所实现的接口，这样在任何场合下，代理都可以替换其目标对象以实现对应功能。



The keys to this arrangement are implementation and delegation. The proxy implements the same interface as the target so that it can be used in exactly the same way. The proxy delegates some or all of the calls that it receives to its target and thus acts as either an intermediary or a substitute. In its role as an intermediary, the proxy may add functionality either before or after the method is forwarded to the target. This gives the reflective programmer the capability to add behavior to objects. This chapter discusses this and other uses of proxies.  
这种arrangement的思想在于实现和委托。代理与其目标对象均实现了相同的接口，因此使用它们的方式也是完全相同的。对代理的调用，可能部分或全部地被委托给其目标对象。因此，代理扮演的是一个中介和substitute的角色，它可以在方法调用被委托给目标对象之前或之后多做一些事情。这使得反射编程具备为对象添加行为的能力。本章将讨论这个话题以及代理的其他用途。
