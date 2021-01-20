# Asynchronous programming

[Asynchronous programming with Async / Await](https://docs.microsoft.com/es-es/dotnet/csharp/programming-guide/concepts/async/)

## **Example** 

* Windows Form Application

	```
	public partial class MainWindow : Window
    {
        public MainWindow()
        {
	        InitializaComponent();
		}
		
		private void Button_Click(object sender, RoutedEventArgs e)
		{
			DownloadHtmlAsync("http://msdn.microsoft.com");
		}
		
		public async Task DownloadHtmlAsync(string url)
		{
			var webClient = new WebClient();
			var html = await webClient.DownloadStringTaskAsync(url);
			
			using (var streamWriter = new StreamWriter(@"c:\projects\result.html"))
			{
				await streamWriter.WriteAsync(html);
			}
		}
    }
	```
	
[Back to index](../README.md)