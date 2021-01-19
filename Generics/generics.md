# Generics

[Generics](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/generics/) introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.

- [Constraints](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters) inform the compiler about the capabilities a type argument must have. Without any constraints, the type argument could be any type. The compiler can only assume the members of System.Object, which is the ultimate base class for any .NET type.

![Constraints type](./images/constraintsTypes.png)

- [Generic Classes](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/generics/generic-classes)

- [Generic Interfaces](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/generics/generic-interfaces)

- [Generic Methods](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/generics/generic-methods)

- [Generic Delegates](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/generics/generic-delegates)

- **Example**: Make int nullable 

	```
    public class Nullable<T> where T : struct
    {
        private object _value;

        public Nullable()
        {
        }

        public Nullable(T value)
        {
            _value = value;
        }

        public bool HasValue
        {
            get { return _value != null; }
        }

        public T GetValueOrDefault()
        {
            if (HasValue)
                return (T)_value;
            return default(T);
        }
    }
	```

	```
    static void Main(string[] args)
    {
	    var number = new Nullable<int>();
	    Console.WriteLine("Has Value ?" + number.HasValue);
	    Console.WriteLine("Value: " + number.GetValueOrDefault());
    }
	```
 
 
[Back to index](../README.md)