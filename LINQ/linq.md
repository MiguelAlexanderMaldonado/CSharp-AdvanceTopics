# LINQ

All [LINQ](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) query operations consist of three distinct actions:

1.  Obtain the data source.
    
2.  Create the query.
    
3.  Execute the query.

```
class IntroToLINQ
{
    static void Main()
    {
        // The Three Parts of a LINQ Query:
        // 1. Data source.
        int[] numbers = new int[7] { 0, 1, 2, 3, 4, 5, 6 };

        // 2. Query creation.
        // numQuery is an IEnumerable<int>
        var numQuery =
            from num in numbers
            where (num % 2) == 0
            select num;

        // 3. Query execution.
        foreach (int num in numQuery)
        {
            Console.Write("{0,1} ", num);
        }
    }
}
```
The following illustration shows the complete query operation. In LINQ, the execution of the query is distinct from the query itself. In other words, you have not retrieved any data just by creating a query variable.

![Diagram of the complete LINQ query operation.](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/media/introduction-to-linq-queries/linq-query-complete-operation.png)

* **LINQ Extension Methods**

	```
	.Where();
	.Single();
	.SingleOrDefault();

	.First();
	.FirstOrDefault();

	.Last();
	.LastOrDefault();

	.Min();
	.Max();
	.Count();
	.Sum();
	.Average();

	.Skip(n);
	.Take(n);
	```


## **Example** 

* Cheaper

	```
	class Program
    {
        static void Main(string[] args)
        {
            var books = new BookRepository().GetBooks();

			// 2 Options
			
			// LINQ Query Operatos
			var cheapeBooks =
				from b in books
				where b.Price < 10
				orderby b.Title
				select b.Title;
	
			// LINQ Extension Methods
			cheapeBooks = books
							.Where(b => b.Price < 10)
							.OrderBy(b => b.Title)
							.Select(b => b.Title)

			foreach (var book in cheapBooks)
				Console.WriteLine(book.Title)
        }
    }
	```
 
 
[Back to index](../README.md)