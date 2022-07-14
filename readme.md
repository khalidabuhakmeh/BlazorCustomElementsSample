# Blazor Custom Elements Sample

The purpose of this repository is to show **Blazor Custom Elements** in action
alongside ASP.NET Core Razor Pages. 

https://devblogs.microsoft.com/dotnet/asp-net-core-updates-in-dotnet-7-preview-6/#blazor-custom-elements-no-longer-experimental

1. The host is ASP.NET Core
2. The host framework is Razor Pages
3. The component framework is Blazor Web Assembly.

The purpose of custom elements is to allow you to build small islands of functionality without having to go **ALL IN** on blazor. You can write self-contained components that you can place anywhere on an HTML-output page (Razor Pages, MVC view, regular HTML).

The component is defined in [`./BlazorSolo.Components/Counter.razor`](BlazorSolo.Components/Counter.razor). It's also registered to be a custom component in [Program.cs](BlazorSolo.Components/Program.cs) of the same project.

To use the component, you need to add the following JavaScript script references to your host app in this specific order.

```html
<!-- Blazor -->
<script src="_content/Microsoft.AspNetCore.Components.CustomElements/BlazorCustomElements.js"></script>
<script src="_framework/blazor.webassembly.js"></script>
```

You also need the following middleware in your host application.

```c#
app.UseBlazorFrameworkFiles();
```

For debugging, you need to add the following middleware at the beginning of your request pipeline setup.

```c#
app.UseWebAssemblyDebugging();
```

Once you have all the other pieces in place, you just need to use the registered name of the component in your html. In this sample, the name is `my-counter`. Parameters are snake-case based on the camel case naming of parameters. `IncrementAmount` -> `increment-amount`. 

```html
<div class="text-center">
    <h1 class="display-4">Welcome</h1>
    
    <my-counter title="Khalid" increment-amount="2" />
    
</div>
```

## Prerequisites

- .NET 7 Preview 6+

## Debugging

If you'd like to debug your components, the infrastructure is set up for that. If you're a [JetBrains Rider](https://jetbrains.com/rider) user, you need to enable `with JavaScript Debugger` in your run configuration.

## Questions and Thoughts

Direct them at me, on Twitter at [@buhakmeh](https://twitter.com/buhakmeh).