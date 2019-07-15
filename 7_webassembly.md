# webassembly

## webassembly

**Talk** [An Introduction to WebAssembly - Guy Royse](https://www.youtube.com/watch?v=jxf8uaOOu48&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=70&t=0s)

>WebAssembly (abbreviated Wasm) is a binary instruction format for a stack-based virtual machine. Wasm is designed as a portable target for compilation of high-level languages like C/C++/Rust, enabling deployment on the web for client and server applications.

## blazor

**Talk** [Blazor, a new framework for browser-based .NET apps - Steve Sanderson](https://www.youtube.com/watch?v=uW-Kk7Qpv5U&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=167&t=0s)

[Blazor](https://docs.microsoft.com/en-us/aspnet/core/blazor/?view=aspnetcore-3.0)


```
<div>
    <h1>@Title</h1>

    @ChildContent

    <button @onclick="@OnYes">Yes!</button>
</div>

@code {
    [Parameter]
    private string Title { get; set; }

    [Parameter]
    private RenderFragment ChildContent { get; set; }

    private void OnYes()
    {
        Console.WriteLine("Write to the console in C#! 'Yes' button was selected.");
    }
}
```

