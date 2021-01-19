## Lambda expressions

A [Lambda expression](https://docs.microsoft.com/es-es/dotnet/csharp/language-reference/operators/lambda-expressions) is an expression of any of the following two forms:

* [Expression lambda](https://docs.microsoft.com/es-es/dotnet/csharp/language-reference/operators/lambda-expressions#expression-lambdas) that has an expression as its body:

	```
	(input-parameters) => expression
	```

* [Statement lambda](https://docs.microsoft.com/es-es/dotnet/csharp/language-reference/operators/lambda-expressions#statement-lambdas) that has a statement block as its body:

	```
	(input-parameters) => { <sequence-of-statements> }
	```

Use the  [lambda declaration operator  `=>`](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/lambda-operator)  to separate the lambda's parameter list from its body. To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.

Any lambda expression can be converted to a  [delegate](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/reference-types#the-delegate-type)  type. The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value. If a lambda expression doesn't return a value, it can be converted to one of the  `Action`  delegate types; otherwise, it can be converted to one of the  `Func`  delegate types. For example, a lambda expression that has two parameters and returns no value can be converted to an  [Action<T1,T2>](https://docs.microsoft.com/en-us/dotnet/api/system.action-2)  delegate. A lambda expression that has one parameter and returns a value can be converted to a  [Func<T,TResult>](https://docs.microsoft.com/en-us/dotnet/api/system.func-2)  delegate. In the following example, the lambda expression  `x => x * x`, which specifies a parameter that's named  `x`  and returns the value of  `x`  squared, is assigned to a variable of a delegate type:

```
Func<int, int> square = x => x * x; 
Console.WriteLine(square(5)); 
// Output:  
// 25
```

## Types
	
```
args => expression
```

* No argument
	```
	() => ...
	```
* One argument
	```
	x => ...
	```
* Multiple arguments
	```
	(x, y, z) => ...
	```

## Examples

* Multipler
	```
	static void Main(string[] args)
	{
		const int factor = 5;
		
		// Delegate
		Funct<int, int> multipler = nu => n*factor;
		
		var result = multipler(10);
		Console.WriteLine(result);
	}
	```

*	Books
	```
	public class Book
    {
        public string Isbn { get; set; }
        public string Title { get; set; }
        public float Price { get; set; }
    }
	```
	```
	public class BookRepository
    {
        public List<Book> GetBooks()
        {
            return new List<Book>
            {
                new Book() {Title = "Title 1", Price = 5},
                new Book() {Title = "Title 2", Price = 7},
                new Book() {Title = "Title 3", Price = 17}
            };
        }
    }
	```
	```
	static void Main(string[] args)
    {
        var books = new BookRepository().GetBooks();

        var cheapBooks = books.FindAll(b => b.Price < 10);

        foreach (var book in cheapBooks)
        {
            Console.WriteLine(book.Title);
        }
    }
	```

[Back to index](../README.md)