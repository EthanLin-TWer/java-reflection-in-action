# 了解Proxy类

> As stated previously, the two important tasks for any proxy are interface imple- mentation and delegation. The Java `Proxy` class accomplishes implementation of interfaces by dynamically creating a class that implements a set of given interfaces. This dynamic class creation is accomplished with the static `getProxyClass` and `newProxyInstance` factory methods, shown in listing 4.1.

如前所述，代理的两个重要工作分别是接口实现和调用委托。Java的`Proxy`类是这样完成接口实现的任务的，它动态地创建一个类，并让这个类去实现目标对象的接口。这个类的动态创建过程是由静态的`getProxyClass`方法以及工厂方法`newProxyInstance`来实现的，如代码清单4.1所示。

> Listing 4.1 Partial declaration for `java.lang.reflect.Proxy`

代码清单4.1 `java.lang.reflect.Proxy`类的部分定义

```
public class Proxy implements java.io.Serializable { 
   ...
   public static Class getProxyClass( ClassLoader loader, Class[] interfaces )
      throws IllegalArgumentException ...

   public static Object newProxyInstance( ClassLoader loader, Class[] interfaces,
      InvocationHandler h ) throws IllegalArgumentException ...

   public static boolean isProxyClass( Class cl ) ...

   public static InvocationHandler getInvocationHandler( Object proxy ) 
      throws IllegalArgumentException ...
}
```

> Each class constructed by these factory methods is a public final subclass of `Proxy`, referred to as a __proxy class__. We refer to an instance of one of these dynamically constructed proxies as a __proxy instance__. We call the interfaces that the proxy class implements in this way __proxied interfaces__. A proxy instance is assignment-compatible with all of its proxied interfaces.

由这些工厂方法构造出来的每个类都是Proxy的一个公有final子类，也称为__代理类__。这些被动态创建的代理的实例称为__代理实例__。代理类通过这种方式实现的接口称为__代理接口(proxied interfaces)__。_一个代理实例对其实现的所有代理接口是赋值兼容的_。

> The `getProxyClass` method retrieves the proxy class specified by a class loader and an array of interfaces. If such a proxy class does not exist, it is dynamically constructed. Because each Java class object is associated with a class loader, in order to dynamically create a proxy class, `getProxyClass` must have a class loader parameter (the reason for this requirement is explained in chapter 6). The name of each proxy class begins with `$Proxy` followed by a number, which is the value of an index that is increased each time a proxy class is created.

> All proxy classes have a constructor that takes an `InvocationHandler` parameter. `InvocationHandler` is an interface for objects that handle methods received by proxy instances through their proxied interfaces. We discuss invocation handlers further after we finish with the methods of `Proxy`. A combination of `getConstructor` and `newInstance` may be used to construct proxy instances, as in the following lines

```
   Proxy cl = getProxyClass( SomeInterface.getClassLoader(), 
                           Class[]{SomeInterface.class} );
   Constructor cons = cl.getConstructor( new Class[]{InvocationHandler.class} );
   Object proxy = cons.newInstance( new Object[] { new SomeIH( obj ) } );
```

> where `SomeIH` is a class that implements `InvocationHandler`. Alternatively, this sequence can be accomplished with a single call to `newProxyInstance`:

```
   Object proxy = Proxy.newProxyInstance( SomeInterface.getClassLoader(),
                                          Class[]{SomeInterface.class},
                                          new SomeIH( obj ) );
```
> This call implicitly creates the proxy class, which can be retrieved with `getProxyClass`.

> The static method `isProxyClass` is used to determine if a class object repre- sents a proxy class. The line

```Proxy.isProxyClass(obj.getClass())```

> may be use to determine if `obj` refers to a proxy instance. If `p` refers to a proxy
instance,

```Proxy.getInvocationHandler(p)```

> returns the `InvocationHandler` that was used to construct `p`.

