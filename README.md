# FFImageLoading.ForbiddenSample
Recently I ran into an this issue, were images from sum sources resulted in the below error message, when showin in an Xamarin.Forms app using FFImageLoading CachedImage control.

The result was: 
- Image was never shown 
- Error "You don't have permission to access [IMAGE_PATH] on this server." in the Output window.

Output:
```
Image loading failed: https://politirapporten.nu/wp-content/uploads/2019/04/AKA05311-e1555667573457.jpg
Image loading failed: https://politirapporten.nu/wp-content/uploads/2019/04/AKA05311-e1555667573457.jpg
FFImageLoading.Exceptions.DownloadHttpStatusCodeException: Forbidden <!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">06-20 22:03:51.578 I/mono-stdout( 7488): FFImageLoading.Exceptions.DownloadHttpStatusCodeException: Forbidden <!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">

<html><head>
<title>403 Forbidden</title>
</head><body>06-20 22:03:51.578 I/mono-stdout( 7488): <html><head>

<h1>Forbidden</h1>
<p>You don't have permission to access /wp-content/uploads/2019/04/AKA05311-e1555667573457.jpg
on this server.<br />
</p>06-20 22:03:51.579 I/mono-stdout( 7488): <title>403 Forbidden</title>

<p>Additionally, a 403 Forbidden
error was encountered while trying to use an ErrorDocument to handle the request.</p>06-20 22:03:51.579 I/mono-stdout( 7488): </head><body>

</body></html>

  at FFImageLoading.Cache.DownloadCache.DownloadAsync (System.String url, System.Threading.CancellationToken token, System.Net.Http.HttpClient client, FFImageLoading.Work.TaskParameter parameters, FFImageLoading.DownloadInformation downloadInformation) [0x0027a] in C:\projects\ffimageloading\source\FFImageLoading.Common\Cache\DownloadCache.cs:119 
  at FFImageLoading.Cache.DownloadCache+<>c__DisplayClass15_0.<DownloadAndCacheIfNeededAsync>b__0 () [0x00050] in C:\projects\ffimageloading\source\FFImageLoading.Common\Cache\DownloadCache.cs:58 06-20 22:03:51.580 I/mono-stdout( 7488): <h1>Forbidden</h1>

06-20 22:03:51.580 I/mono-stdout( 7488): <p>You don't have permission to access /wp-content/uploads/2019/04/AKA05311-e1555667573457.jpg
  at FFImageLoading.Retry.DoAsync[T] (System.Func`1[TResult] action, System.TimeSpan retryInterval, System.Int32 retryCount, System.Action onRetry) [0x00189] in C:\projects\ffimageloading\source\FFImageLoading.Common\Helpers\Retry.cs:51 
  at FFImageLoading.Cache.DownloadCache.DownloadAndCacheIfNeededAsync (System.String url, FFImageLoading.Work.TaskParameter parameters, FFImageLoading.Config.Configuration configuration, System.Threading.CancellationToken token) [0x00401] in C:\projects\ffimageloading\source\FFImageLoading.Common\Cache\DownloadCache.cs:57 
  at FFImageLoading.DataResolvers.UrlDataResolver.Resolve (System.String identifier, FFImageLoading.Work.TaskParameter parameters, System.Threading.CancellationToken token) [0x00045] in C:\projects\ffimageloading\source\FFImageLoading.Common\DataResolvers\UrlDataResolver.cs:22 06-20 22:03:51.580 I/mono-stdout( 7488): on this server.<br />

06-20 22:03:51.580 I/mono-stdout( 7488): </p>
06-20 22:03:51.581 I/mono-stdout( 7488): <p>Additionally, a 403 Forbidden
  at FFImageLoading.DataResolvers.WrappedDataResolver.Resolve (System.String identifier, FFImageLoading.Work.TaskParameter parameters, System.Threading.CancellationToken token) [0x0004e] in C:\projects\ffimageloading\source\FFImageLoading.Common\DataResolvers\WrappedDataResolver.cs:21 
  at FFImageLoading.Work.ImageLoaderTask`3[TDecoderContainer,TImageContainer,TImageView].RunAsync () [0x00300] in C:\projects\ffimageloading\source\FFImageLoading.Common\Work\ImageLoaderTask.cs:618 06-20 22:03:51.581 I/mono-stdout( 7488): error was encountered while trying to use an ErrorDocument to handle the request.</p>

06-20 22:03:51.581 I/mono-stdout( 7488): </body></html>
06-20 22:03:51.582 I/mono-stdout( 7488): 
06-20 22:03:51.582 I/mono-stdout( 7488):   at FFImageLoading.Cache.DownloadCache.DownloadAsync (System.String url, System.Threading.CancellationToken token, System.Net.Http.HttpClient client, FFImageLoading.Work.TaskParameter parameters, FFImageLoading.DownloadInformation downloadInformation) [0x0027a] in C:\projects\ffimageloading\source\FFImageLoading.Common\Cache\DownloadCache.cs:119 
06-20 22:03:51.582 I/mono-stdout( 7488):   at FFImageLoading.Cache.DownloadCache+<>c__DisplayClass15_0.<DownloadAndCacheIfNeededAsync>b__0 () [0x00050] in C:\projects\ffimageloading\source\FFImageLoading.Common\Cache\DownloadCache.cs:58 
06-20 22:03:51.583 I/mono-stdout( 7488):   at FFImageLoading.Retry.DoAsync[T] (System.Func`1[TResult] action, System.TimeSpan retryInterval, System.Int32 retryCount, System.Action onRetry) [0x00189] in C:\projects\ffimageloading\source\FFImageLoading.Common\Helpers\Retry.cs:51 
06-20 22:03:51.583 I/mono-stdout( 7488):   at FFImageLoading.Cache.DownloadCache.DownloadAndCacheIfNeededAsync (System.String url, FFImageLoading.Work.TaskParameter parameters, FFImageLoading.Config.Configuration configuration, System.Threading.CancellationToken token) [0x00401] in C:\projects\ffimageloading\source\FFImageLoading.Common\Cache\DownloadCache.cs:57 
06-20 22:03:51.583 I/mono-stdout( 7488):   at FFImageLoading.DataResolvers.UrlDataResolver.Resolve (System.String identifier, FFImageLoading.Work.TaskParameter parameters, System.Threading.CancellationToken token) [0x00045] in C:\projects\ffimageloading\source\FFImageLoading.Common\DataResolvers\UrlDataResolver.cs:22 
06-20 22:03:51.583 I/mono-stdout( 7488):   at FFImageLoading.DataResolvers.WrappedDataResolver.Resolve (System.String identifier, FFImageLoading.Work.TaskParameter parameters, System.Threading.CancellationToken token) [0x0004e] in C:\projects\ffimageloading\source\FFImageLoading.Common\DataResolvers\WrappedDataResolver.cs:21 
06-20 22:03:51.584 I/mono-stdout( 7488):   at FFImageLoading.Work.ImageLoaderTask`3[TDecoderContainer,TImageContainer,TImageView].RunAsync () [0x00300] in C:\projects\ffimageloading\source\FFImageLoading.Common\Work\ImageLoaderTask.cs:618
```

This is the result I get when running this solution on my machine.
![alt text](Assets/Screenshot.png "You don't have permission to access [IMAGE_PATH] on this server.")

See the [ItemsPage.xaml](https://github.com/Laumania/FFImageLoading.ForbiddenSample/blob/76468e2477d3ef5b303ffbb0ebcd79b0af20efa7/ForbiddenImageSample/Views/ItemsPage.xaml#L21) where both an <Image> and a CachedImage is used.

```
<StackLayout>
        <Label Text="Normal Image" />
        <Image Source="https://politirapporten.nu/wp-content/uploads/2019/04/AKA05311-e1555667573457.jpg" />

        <Label Text="FFImageLoading Image" />
        <ffimageloading:CachedImage 
                                Grid.Row="2"
                                Grid.Column="0"
                                Grid.ColumnSpan="2"                                
                                Margin="-20,10"
								FadeAnimationEnabled="true"
                                Aspect="AspectFill"
	            				Source="https://politirapporten.nu/wp-content/uploads/2019/04/AKA05311-e1555667573457.jpg">
        </ffimageloading:CachedImage>
    </StackLayout>
```

The funny thing is, as you can see in the sample, that the same image loads fine using the normal <Image> control.

I googled it and could find anything, so I created a this repo, which is a totally new Xamarin.Forms Solution that illustrates the issue.

[Created issue over at FFImageLoading here](https://github.com/luberda-molinet/FFImageLoading/issues/1306)
