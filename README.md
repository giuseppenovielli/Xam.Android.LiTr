# Xam.Android.LiTr
Xamarin.Android Binding of linkedin.LiTr library https://github.com/linkedin/LiTr by Giuseppe Novielli

LiTr v1.5.0

Documentation Available https://github.com/linkedin/LiTr

Available NuGet TODO

# How To use
1.  Add nuget package https://www.nuget.org/packages/Xam.Android.LiTr/
2.  Copy and paste follow code
3.  Compile <> tag

```
var name = <name_video>.mp4
var fileOutputPath = System.IO.Path.Combine(Android.App.Application.Context.GetExternalFilesDir(Android.OS.Environment.DirectoryMovies).AbsolutePath, name);

var videoFormat = MediaFormat.CreateVideoFormat(MediaFormat.MimetypeVideoAvc, <width>, <height>);
videoFormat.SetInteger(MediaFormat.KeyBitRate, <bitrate>);
videoFormat.SetInteger(MediaFormat.KeyFrameRate, <framerate>);
videoFormat.SetInteger(MediaFormat.KeyIFrameInterval, <iframeinterval>);

var audioFormat = MediaFormat.CreateAudioFormat(MediaFormat.MimetypeAudioAac, 44100, 2);
audioFormat.SetInteger(MediaFormat.KeyBitRate, 128000);

var UUID = Guid.NewGuid().ToString();
                
var mediaTransformer = new MediaTransformer(context);
var listener = new TransformationListener();
mediaTransformer.Transform(
               UUID,
               <inputUri>,
               fileOutputPath,
               videoFormat,
               audioFormat,
               listener,
               null);
                  
public class TransformationListener : Java.Lang.Object, ITransformationListener
{
    public TransformationListener()
    {
    }
    
    public void OnCancelled(string id, IList<TrackTransformationInfo> trackTransformationInfos)
    {
        System.Diagnostics.Debug.WriteLine("\n\n");
        System.Diagnostics.Debug.WriteLine("OnCancelled");
        System.Diagnostics.Debug.WriteLine(id);
    }

    public async void OnCompleted(string id, IList<TrackTransformationInfo> trackTransformationInfos)
    {
        System.Diagnostics.Debug.WriteLine("\n\n");
        System.Diagnostics.Debug.WriteLine("OnCompleted");
        System.Diagnostics.Debug.WriteLine(id);
    }

    public void OnError(string id, Java.Lang.Throwable cause, IList<TrackTransformationInfo> trackTransformationInfos)
    {
        System.Diagnostics.Debug.WriteLine("\n\n");
        System.Diagnostics.Debug.WriteLine("OnError");
        System.Diagnostics.Debug.WriteLine(id);
        System.Diagnostics.Debug.WriteLine(cause.ToString());
    }

    public void OnProgress(string id, float progress)
    {
        System.Diagnostics.Debug.WriteLine("\n\n");
        System.Diagnostics.Debug.WriteLine("OnProgress");
        System.Diagnostics.Debug.WriteLine(id);
        System.Diagnostics.Debug.WriteLine(progress.ToString());
    }

    public void OnStarted(string id)
    {
        System.Diagnostics.Debug.WriteLine("\n\n");
        System.Diagnostics.Debug.WriteLine("OnStarted");
        System.Diagnostics.Debug.WriteLine(id);
    }
}              
``` 
              
                  

