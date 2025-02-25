---
title: "Interfaces - C# Programming Guide"
description: An interface in C# contains definitions for a group of related functionalities that a non-abstract class or a struct must implement.
ms.date: 02/20/2020
helpviewer_keywords: 
  - "interfaces [C#]"
  - "C# language, interfaces"
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
---
# Interfaces (C# Programming Guide)

An interface contains definitions for a group of related functionalities that a non-abstract [class](../../language-reference/keywords/class.md) or a [struct](../../language-reference/builtin-types/struct.md) must implement. An interface may define `static` methods, which must have an implementation. Beginning with C# 8.0, an interface may define a default implementation for members. An interface may not declare instance data such as fields, auto-implemented properties, or property-like events.

By using interfaces, you can, for example, include behavior from multiple sources in a class. That capability is important in C# because the language doesn't support multiple inheritance of classes. In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.

You define an interface by using the [interface](../../language-reference/keywords/interface.md) keyword as the following example shows.

[!code-csharp[Equatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#Equatable)]

The name of an interface must be a valid C# [identifier name](../inside-a-program/identifier-names.md). By convention, interface names begin with a capital `I`.

Any class or struct that implements the <xref:System.IEquatable%601> interface must contain a definition for an <xref:System.IEquatable%601.Equals%2A> method that matches the signature that the interface specifies. As a result, you can count on a class that implements `IEquatable<T>` to contain an `Equals` method with which an instance of the class can determine whether it's equal to another instance of the same class.

The definition of `IEquatable<T>` doesn't provide an implementation for `Equals`. A class or struct can implement multiple interfaces, but a class can only inherit from a single class.

For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

Interfaces can contain instance methods, properties, events, indexers, or any combination of those four member types. Interfaces may contain static constructors, fields, constants, or operators. For links to examples, see [Related Sections](./index.md#BKMK_RelatedSections). An interface can't contain instance fields, instance constructors, or finalizers. Interface members are public by default, and you can explicitly specify accessibility modifiers, such as `public`, `protected`, `internal`, `private`, `protected internal`, or `private protected`. A `private` member must have a default implementation.

To implement an interface member, the corresponding member of the implementing class must be public, non-static, and have the same name and signature as the interface member.

When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface declares but doesn't provide a default implementation for. However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.

The following example shows an implementation of the <xref:System.IEquatable%601> interface. The implementing class, `Car`, must provide an implementation of the <xref:System.IEquatable%601.Equals%2A> method.

[!code-csharp[ImplementEquatable](~/samples/snippets/csharp/objectoriented/interfaces.cs#ImplementEquatable)]

Properties and indexers of a class can define extra accessors for a property or indexer that's defined in an interface. For example, an interface might declare a property that has a [get](../../language-reference/keywords/get.md) accessor. The class that implements the interface can declare the same property with both a `get` and [set](../../language-reference/keywords/set.md) accessor. However, if the property or indexer uses explicit implementation, the accessors must match. For more information about explicit implementation, see [Explicit Interface Implementation](explicit-interface-implementation.md) and [Interface Properties](../classes-and-structs/interface-properties.md).

Interfaces can inherit from one or more interfaces. The derived interface inherits the members from its base interfaces. A class that implements a derived interface must implement all members in the derived interface, including all members of the derived interface's base interfaces. That class may be implicitly converted to the derived interface or any of its base interfaces. A class might include an interface multiple times through base classes that it inherits or through interfaces that other interfaces inherit. However, the class can provide an implementation of an interface only one time and only if the class declares the interface as part of the definition of the class (`class ClassName : InterfaceName`). If the interface is inherited because you inherited a base class that implements the interface, the base class provides the implementation of the members of the interface. However, the derived class can reimplement any virtual interface members instead of using the inherited implementation. When interfaces declare a default implementation of a method, any class implementing that interface inherits that implementation. Implementations defined in interfaces are virtual and the implementing class may override that implementation.

A base class can also implement interface members by using virtual members. In that case, a derived class can change the interface behavior by overriding the virtual members. For more information about virtual members, see [Polymorphism](../classes-and-structs/polymorphism.md).

## Interfaces summary

An interface has the following properties:

- An interface is typically like an abstract base class with only abstract members. Any class or struct that implements the interface must implement all its members. Optionally, an interface may define default implementations for some or all of its members. For more information, see [default interface methods](../../tutorials/default-interface-methods-versions.md).
- An interface can't be instantiated directly. Its members are implemented by any class or struct that implements the interface.
- A class or struct can implement multiple interfaces. A class can inherit a base class and also implement one or more interfaces.

## <a name="BKMK_RelatedSections"></a> Related Sections

- [Interface Properties](../classes-and-structs/interface-properties.md)  
- [Indexers in Interfaces](../indexers/indexers-in-interfaces.md)  
- [How to implement interface events](../events/how-to-implement-interface-events.md)
- [Classes and Structs](../classes-and-structs/index.md)  
- [Inheritance](../classes-and-structs/inheritance.md)  
- [Interfaces](../../language-reference/keywords/interface.md)
- [Methods](../classes-and-structs/methods.md)  
- [Polymorphism](../classes-and-structs/polymorphism.md)  
- [Abstract and Sealed Classes and Class Members](../classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Properties](../classes-and-structs/properties.md)  
- [Events](../events/index.md)  
- [Indexers](../indexers/index.md)
  
## See also

- [C# Programming Guide](../index.md)
- [Inheritance](../classes-and-structs/inheritance.md)
- [Identifier names](../inside-a-program/identifier-names.md)
