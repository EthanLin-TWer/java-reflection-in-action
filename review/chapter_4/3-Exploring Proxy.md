# Exploring Proxy

> As stated previously, the two important tasks for any proxy are interface imple- mentation and delegation. The Java Proxy class accomplishes implementation of interfaces by dynamically creating a class that implements a set of given interfaces. This dynamic class creation is accomplished with the static getProxyClass and newProxyInstance factory methods, shown in listing 4.1.

> Listing 4.1 Partial declaration for `java.lang.reflect.Proxy`

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

> Each class constructed by these factory methods is a public final subclass of Proxy, referred to as a proxy class. We refer to an instance of one of these dynamically constructed proxies as a proxy instance. We call the interfaces that the proxy class implements in this way proxied interfaces. A proxy instance is assignment- compatible with all of its proxied interfaces.

> The getProxyClass method retrieves the proxy class specified by a class loader and an array of interfaces. If such a proxy class does not exist, it is dynamically constructed. Because each Java class object is associated with a class loader, in order to dynamically create a proxy class, getProxyClass must have a class loader parameter (the reason for this requirement is explained in chapter 6). The name of each proxy class begins with $Proxy followed by a number, which is the value of an index that is increased each time a proxy class is created.

> All proxy classes have a constructor that takes an InvocationHandler parame- ter. InvocationHandler is an interface for objects that handle methods received by proxy instances through their proxied interfaces. We discuss invocation han- dlers further after we finish with the methods of Proxy. A combination of getCon- structor and newInstance may be used to construct proxy instances, as in the following lines

```
   Proxy cl = getProxyClass( SomeInterface.getClassLoader(), 
                           Class[]{SomeInterface.class} );
   Constructor cons = cl.getConstructor( new Class[]{InvocationHandler.class} );
   Object proxy = cons.newInstance( new Object[] { new SomeIH( obj ) } );
```

> where SomeIH is a class that implements InvocationHandler. Alternatively, this sequence can be accomplished with a single call to newProxyInstance:

```
   Object proxy = Proxy.newProxyInstance( SomeInterface.getClassLoader(),
                                          Class[]{SomeInterface.class},
                                          new SomeIH( obj ) );
```
> This call implicitly creates the proxy class, which can be retrieved with getProxy- Class.

> The static method isProxyClass is used to determine if a class object repre- sents a proxy class. The line

```Proxy.isProxyClass(obj.getClass())```

> may be use to determine if obj refers to a proxy instance. If p refers to a proxy
instance,

```Proxy.getInvocationHandler(p)```

> returns the InvocationHandler that was used to construct p.

