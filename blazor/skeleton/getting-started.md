---
layout: post
title: Getting Started with Blazor Skeleton Component | Syncfusion
description: Checkout and learn about getting started with Blazor Skeleton component in Blazor Server App and Blazor WebAssembly App.
platform: Blazor
control: Skeleton
documentation: ug
---

# Getting Started with Blazor Skeleton Component

This section briefly explains about how to include Blazor Skeleton component in your Blazor Server App and Blazor WebAssembly App using Visual Studio.

To get start quickly with Skeleton Component using Blazor, you can check on this video or [GitHub](https://github.com/SyncfusionExamples/Blazor-Getting-Started-Examples/tree/main/Skeleton) sample.

{% youtube
"youtube:https://www.youtube.com/watch?v=Zd6gzsjunYM"%}

## Prerequisites

* [System requirements for Blazor components](https://blazor.syncfusion.com/documentation/system-requirements)

## Create a new Blazor App in Visual Studio

You can create a **Blazor Server App** or **Blazor WebAssembly App** using Visual Studio via [Microsoft Templates](https://learn.microsoft.com/en-us/aspnet/core/blazor/tooling?view=aspnetcore-7.0) or the [Syncfusion Blazor Extension](https://blazor.syncfusion.com/documentation/visual-studio-integration/template-studio).

## Install Syncfusion Blazor Notifications and Themes NuGet in the App

To add **Blazor Skeleton** component in the app, open the NuGet package manager in Visual Studio (*Tools → NuGet Package Manager → Manage NuGet Packages for Solution*), search and install [Syncfusion.Blazor.Notifications](https://www.nuget.org/packages/Syncfusion.Blazor.Notifications/) and [Syncfusion.Blazor.Themes](https://www.nuget.org/packages/Syncfusion.Blazor.Themes/). Alternatively, you can utilize the following package manager command to achieve the same.

{% tabs %}
{% highlight C# tabtitle="Package Manager" %}

Install-Package Syncfusion.Blazor.Notifications -Version {{ site.releaseversion }}
Install-Package Syncfusion.Blazor.Themes -Version {{ site.releaseversion }}

{% endhighlight %}
{% endtabs %}

N> Syncfusion Blazor components are available in [nuget.org](https://www.nuget.org/packages?q=syncfusion.blazor). Refer to [NuGet packages](https://blazor.syncfusion.com/documentation/nuget-packages) topic for available NuGet packages list with component details.

## Register Syncfusion Blazor Service

Open **~/_Imports.razor** file and import the `Syncfusion.Blazor` and `Syncfusion.Blazor.Notifications` namespace.

{% tabs %}
{% highlight razor tabtitle="~/_Imports.razor" %}

@using Syncfusion.Blazor
@using Syncfusion.Blazor.Notifications

{% endhighlight %}
{% endtabs %}

Now, register the Syncfusion Blazor Service in the **~/Program.cs** file of your Blazor Server App or Blazor WebAssembly App.

{% tabs %}
{% highlight C# tabtitle="Blazor Server App" hl_lines="3 10" %}

using Microsoft.AspNetCore.Components;
using Microsoft.AspNetCore.Components.Web;
using Syncfusion.Blazor;

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();
builder.Services.AddSyncfusionBlazor();

var app = builder.Build();
....

{% endhighlight %}
{% highlight C# tabtitle="Blazor WebAssembly App" hl_lines="3 11" %}

using Microsoft.AspNetCore.Components.Web;
using Microsoft.AspNetCore.Components.WebAssembly.Hosting;
using Syncfusion.Blazor;

var builder = WebAssemblyHostBuilder.CreateDefault(args);
builder.RootComponents.Add<App>("#app");
builder.RootComponents.Add<HeadOutlet>("head::after");

builder.Services.AddScoped(sp => new HttpClient { BaseAddress = new Uri(builder.HostEnvironment.BaseAddress) });

builder.Services.AddSyncfusionBlazor();
await builder.Build().RunAsync();
....

{% endhighlight %}
{% endtabs %}

## Add stylesheet

The theme stylesheet can be accessed from NuGet through [Static Web Assets](https://blazor.syncfusion.com/documentation/appearance/themes#static-web-assets). Reference the stylesheet in the `<head>` of the main page as follows:

* For **.NET 6** Blazor Server app, include it in **~/Pages/_Layout.cshtml** file.

* For **.NET 7** Blazor Server app, include it in the **~/Pages/_Host.cshtml** file.

* For Blazor WebAssembly app, include it in the **~/index.html** file.

```html
<head>
    ....
    <link href="_content/Syncfusion.Blazor.Themes/bootstrap5.css" rel="stylesheet" />
</head>
```
N> Check out the [Blazor Themes](https://blazor.syncfusion.com/documentation/appearance/themes) topic to discover various methods ([Static Web Assets](https://blazor.syncfusion.com/documentation/appearance/themes#static-web-assets), [CDN](https://blazor.syncfusion.com/documentation/appearance/themes#cdn-reference), and [CRG](https://blazor.syncfusion.com/documentation/common/custom-resource-generator)) for referencing themes in your Blazor application.

## Add Blazor Skeleton component

Add the Syncfusion Blazor Skeleton component in the **~/Pages/Index.razor** file.

{% tabs %}
{% highlight razor %}

<SfSkeleton Height="15px" Width="200px"></SfSkeleton><br/>
<SfSkeleton Height="15px" Width="100px"></SfSkeleton>

{% endhighlight %}
{% endtabs %}

* Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> (Windows) or <kbd>⌘</kbd>+<kbd>F5</kbd> (macOS) to launch the application. This will render the Syncfusion Blazor Skeleton component in your default web browser.

{% previewsample "https://blazorplayground.syncfusion.com/embed/BDhfXCjOBcbNWOHl?appbar=false&editor=false&result=true&errorlist=false&theme=bootstrap5" backgroundimage "[Blazor Skeleton Component](./images/blazor-skeleton-component.png)" %}

## Blazor Skeleton Shapes

The [`Shape`](https://help.syncfusion.com/cr/blazor/Syncfusion.Blazor.Notifications.SfSkeleton.html#Syncfusion_Blazor_Notifications_SfSkeleton_Shape) property can be used to display skeleton in different shapes like circle, square, rectangle and text.

{% tabs %}
{% highlight razor %}

<div style="width: 200px">
    <SfSkeleton Shape="SkeletonType.Circle" Width="48px" CssClass="custom-css"></SfSkeleton>
    <SfSkeleton Shape="SkeletonType.Square" Width="48px"></SfSkeleton>
    <br/><br/>
    <SfSkeleton Shape="SkeletonType.Text" Height="15px"></SfSkeleton>
    <br/><br/>
    <SfSkeleton Shape="SkeletonType.Rectangle" Height="50px" Width="100%" ></SfSkeleton>
</div>
<style>
    .custom-css {
        margin-right: 30px;
    }
</style>

{% endhighlight %}
{% endtabs %}

{% previewsample "https://blazorplayground.syncfusion.com/embed/LXBpDCNOLlUkQdXp?appbar=false&editor=false&result=true&errorlist=false&theme=bootstrap5" backgroundimage "[Blazor Skeleton Component](./images/blazor-skeleton-shape-sample.png)" %}

N> You can also explore our [Blazor Skeleton example](https://blazor.syncfusion.com/demos/skeleton/defaultfunctionalities) that shows how to render and configure the skeleton.

