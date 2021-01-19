# Events

The [event](https://docs.microsoft.com/es-es/dotnet/csharp/language-reference/keywords/event) keyword is used to declare an event in a publisher class.

## Example

* Video
	```
	public class Video
	{
		public string Title {get; set;}
	}
	```
* VideoEventArgs
	```
	public class VideoEventArgs: EventArgs
	{
		public Video Video {get; set;}
	}
	```
* VideoEncoder
	```
	public class VideoEncoder
	{
		// Define a delegate
		//public delegate void VideoEncodedEventHandler(object source, VideoEventArgs args);
		// Define an event based on that delegate
		//public event VideoEncodedEventHandler VideoEncoded;
		
		// or use the delegate EventHandler<TEventArgs>
		public event EventHandler<VideoEventArgs> VideoEcoded;
		
		// Raise the event
		protected virtual void OnVideoEncoded(Video video) //C# syntax
		{
			if(VideoEncoded != null)
				VideoEncoded(this, new VideoEventArgs() { Video = video });
		}
		public void Encode (Video video)
		{
			Console.WriteLine("Encoding Video... " + video.Title);
			Thread.Sleep(3000);
			OnVideoEncoded(video);
		} 
	}
	```
* MailService
	```
	public class MailService
	{
		public void OnVideoEncoded(object source, VideoEventArgs e)
		{
			Console.WriteLine("MailService: Sending an email... " + e.Video.Title);
		}
	}
	```
* MessageService
	```
	public class MessageService
	{
		public void OnVideoEncoded(object source, VideoEventArgs e)
		{
			Console.WriteLine("MessageService: Sending a text message... " + e.Video.Title);
		}
	}
	```
* Program
	```
	class Program
	{
		static void Main(string[] args)
		{
			var video = new Video() {Title = "Video 1"};
			// Publisher
			var videoEncoder = new VideoEncoder();
			// Subscriber
			var mailService = new MailService();
			// Subscriber
			var messageService = new MessageService();
			
			videoEncoder.VideoEncoded += mailService.OnVideoEncoded;
			videoEncoder.VideoEncoded += messageService.OnVideoEncoded;
			
			videoEncoder.Encode(video);
		}
	}
	```
* Output
	```
	Encoding Video... Video 1
	MailService: Sending an email... Video 1
	MessageService: Sending a text message... Video 1	 
	```

[Back to index](../README.md)