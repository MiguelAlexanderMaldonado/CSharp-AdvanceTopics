# Extension methods

[Extension methods](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/classes-and-structs/extension-methods) enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type. Extension methods are static methods, but they're called as if they were instance methods on the extended type.

## **Example** 

* Shorten

	```
	namespace ExtensionMethods
	{
		public static class StringExtensions
	    {
	        public static string Shorten(this String str, int numberOfWords)
	        {
	            if (numberOfWords < 0)
	                throw new ArgumentOutOfRangeException("numberOfWords should be greater than or equal to 0.");

	            if (numberOfWords == 0)
	                return "";

	            var words = str.Split(' ');

	            if (words.Length <= numberOfWords)
	                return str;

	            return string.Join(" ", words.Take(numberOfWords)) + "...";
	        }
	    }
    }
	```

	```
	namespace ExtensionMethods
	{
		class Program
	    {
	        static void Main(string[] args)
	        {
	            string post = "This is supposed to be a very long blog post...";
	            var shortenedPost = post.Shorten(5);
	            Console.WriteLine(shortenedPost);
	         }
	    }
    }
	```
 
 
[Back to index](../README.md)