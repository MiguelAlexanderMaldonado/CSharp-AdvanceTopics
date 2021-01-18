## Delegates

A [Delegate](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/delegates/using-delegates) is a type that safely encapsulates a method, similar to a function pointer in C and C++. Unlike C function pointers, delegates are object-oriented, type safe, and secure. The type of a delegate is defined by the name of the delegate.

* [Variance](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates): When you assign a method to a delegate, _covariance_ and _contravariance_ provide flexibility for matching a delegate type with a method signature. Covariance permits a method to have return type that is more derived than that defined in the delegate. Contravariance permits a method that has parameter types that are less derived than those in the delegate type.

* **Example**: Photo processor.

```
	public class PhotoFilters
	{
	    public void ApplyBrightness(Photo photo)
	    {
	        Console.WriteLine("Apply brightness");
	    }

	    public void ApplyContrast(Photo photo)
	    {
	        Console.WriteLine("Apply contrast");
	    }

	    public void Resize(Photo photo)
	    {
	        Console.WriteLine("Resize photo");
	    }
	}
```
```
	public class PhotoProcessor
	{
	    public void Process(string path, Action<Photo> filterHandler)
	    {
	        var photo = Photo.Load(path);
	        filterHandler(photo);
	        photo.Save();
	    }
	}
```
```
	static void Main(string[] args)
	{
	    var processor = new PhotoProcessor();
	    var filters = new PhotoFilters();
	    
	    Action<Photo> filterHandler = filters.ApplyBrightness;
	    filterHandler += filters.ApplyContrast;
	    filterHandler += RemoveRedEyeFilter;

	    processor.Process("photo.jpg", filterHandler);
	}
```