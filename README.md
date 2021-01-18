# CSharp-AdvanceTopics
 C# Advance topics: Events, Delegates, Lambda Expressions, LINQ, Async/Await, etc.

## Topics

* [Generics](generics.md)
* 

## Delegates

A [Delegate](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/delegates/using-delegates) is a type that safely encapsulates a method, similar to a function pointer in C and C++. Unlike C function pointers, delegates are object-oriented, type safe, and secure. The type of a delegate is defined by the name of the delegate.

* [Variance](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates): When you assign a method to a delegate, _covariance_ and _contravariance_ provide flexibility for matching a delegate type with a method signature. Covariance permits a method to have return type that is more derived than that defined in the delegate. Contravariance permits a method that has parameter types that are less derived than those in the delegate type.


