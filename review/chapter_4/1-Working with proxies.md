## Working with proxies  
## 使用代理

The sequence diagram in figure 4.1 depicts the most common situation where the proxy instance receives a method call and forwards it to the target. Even this arrangement has a use; it hides the location of the target from the client. If you have used remote method invocation, you are familiar with proxies that are local substitutes for remote objects.  
图4-1所示的顺序图描述了代理最常用的一个场景：代理实例接收到一个方法调用，并简单地委托给目标对象。即便简单，这种设计也是有其作用的：它向客户端隐藏了真正的目标对象。如果你使用过远程方法调用（RMI），那么你对用于替换远端对象的本地代理应该不陌生。



[图4-1 一种常见的代理应用场景的时序图。代理将接受到的方法推送给目标对象，可能在方法调用的前/后做一些处理，也可能不做](./reference/figures/Figure4.1-Sequence diagram for the typical use of a proxy.png)



The Java reflection API contains a dynamic proxy-creation facility, ```java.lang.reflect.Proxy```. This class is part of Java reflection because ```Proxy``` is Java’s only way of approximating method invocation intercession. Let’s dissect the previous phrase. Intercession is any reflective ability that modifies the behavior of a program by directly taking control of that behavior. Method invocation interces- sion is the ability to intercept method calls. The intercepting code can determine the behavior that results from the method call.  
Java的反射API包含了对动态代理创建的支持：java.lang.reflect.Proxy。这个类是Java反射的一部分，因为Proxy是Java近似实现方法调用拦截的唯一方法。(because Proxy is Java’s only way of approximating method invocation intercession.)我们来斟酌一下这个词语(Let’s dissect the previous phrase.)。Intercession is any reflective ability that modifies the behavior of a program by directly taking control of that behavior.方法调用拦截指的即是可以拦截方法调用的能力。拦截代码can determine the behavior that results from the method call.




We say approximating because Java does not support reflective facilities for inter- ceding on method calls. Therefore, we must use proxies as an approximation. Referring to figure 4.1, we see that proxies also allow the ability to pre- and post- process method calls. Let’s examine the benefits achieved from doing this.  
我们称其为“近似实现”，是因为Java反射并不支持intercede方法调用。因此，我们必须使用代理来实现这个目标。再看一下图4-1，可以看到代理能够对方法调用进行前处理和后处理。我们来看一下使用代理的好处。



Programmers commonly discuss properties of classes. For example, a class that records its method calls is often referred to as a tracing class. A class that ensures that a failed operation does not leave an object in an intermediate state is often referred to as an atomic class.  
程序员通常对类的属性感兴趣。比如，一个能够记录其方法调用的类又被称为追踪类，而一个能够确保对象不会因失败的操作而处于中间状态的类又被称为原子类。



The code that implements such properties is usually spread among the defi- nitions of each of the methods of the class, almost always at the beginning and at the return points. The ability to intercede on method invocation permits the programmer to gather this property-implementing code together in one place. This property can later combine with classes, yielding the desired effect.  
实现这些属性的代码通常分布在类的每个方法的定义中，很多时候都是在方法的开头和返回处。有了拦截方法调用的能力，程序员就可以把这些属性的实现代码收集到一个地方。然后，这个属性就可以用来和类组合以产生需要的效果。



The case for this combination of classes and properties is more real for soft- ware projects than you would think. A colleague once observed that when an object-oriented database is first brought into a programming shop, the number of classes doubles. The shop has added one property, persistence, to their application. Each class now requires a persistent and a nonpersistent version [18].  
在软件项目开发中，需要组合类和特性的场景比你想象的可能要更常见。有位同事曾经观察到，when an object-oriented database is first brought into a programming shop, the number of classes doubles. The shop has added on property, persistence, to their application. Each class now requires a persistent and a nonpersistent version[18].



Developers get many key benefits from separating property-implementing code. One benefit of this separation is low maintenance cost for applications. Each such property can be modified by making a change in only one place in the code base. Another benefit of separating properties is improved reusability. The separated property can be used in many places in many applications.  
将属性实现的代码分离出来对开发者大有裨益。其中一个便是使应用的维护成本降低。每个属性可以只在代码库中的一个地方统一修改。另外一个好处是增强了属性的复用性。分离出来的属性在很多地方都能使用，也可以被许多应用软件使用。



There is also a compelling argument to present to management for such sepa- ration. Consider George’s employer, Wildlife Components, which sells a class library of n classes. There are p properties that they wish their classes to have in all combinations. Both the number of classes and the number of properties grow as the company evolves to meet the increasing business demands. WCI faces the possibility of having to support a class library of at least n2p classes if they must write new classes to implement and combine properties in their original classes.  
There is also a compelling argument to present to management for such separation. George的雇主Wildlife Components有一个产品，是一个包含了n个类的类库。同时还有p种属性可以被类所拥有，属性间还可以组合。随着公司业务需求的拓展，类和属性的数量都会随之增长。如果要为每种属性的组合重新编写一个新的类，那么WCI可能面临必须为类库支持$$n2p$$个类的局面。




This additional maintenance is a serious enough concern to win management over. Isolating properties into reusable components and composing them later, as can be done with Proxy, yields a much smaller library of size n+p. This represents an enormous savings to WCI or any other company. This effect may not be as pronounced in other organizations, but it does exist.  
这些额外的维护代价已经足够严重，值得我们考虑来管理它们。将每个属性隔离成为一些可复用的组件，在使用的时候再把它们组合起来——这是使用Proxy能够做到的——是一种不错的方案，可以把类库中类的数量降低到n+p。这对WCI或其他任何公司来说都节省了一笔巨大的开销。对于有些公司来说，这笔开销可能没有那么明显，但它是确实存在的。




Now that we have discussed the abstract benefits of Proxy, let’s pay a visit to George and look at a simple example.  
我们已经抽象地讨论了使用Proxy的好处，现在是时候来跟着George一起看个简单的例子了。