# .net staff

## .NET Core 3

**AWESOOOOME talk** [Hidden gems in .NET Core 3 - David Fowler & Damian Edwards](https://www.youtube.com/watch?v=xdSSH63IZZc&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=14&t=1225s)

>.NET Core 3.0 GA (General Availability) scheduled for September 2019

CLR:
- GC limits, new good defaults
- AssemblyLoadContext: logical successor to AppDomains (load/unload assemblies)
- Startup hooks: register code to execute before Main
- [dotnet diagnostics tools: counters, trace, dump](https://devblogs.microsoft.com/dotnet/introducing-diagnostics-improvements-in-net-core-3-0/)
- publish options: PublishSingleFile, PublishTrimmed

BCL:
- IAsyncDisposable: C# 8 await using, call async methods in  
- https://www.w3.org/TR/trace-context/ support
- ThreadPool: [UnsafeQueueUserWorkItem](https://docs.microsoft.com/en-us/dotnet/api/system.threading.threadpool.unsafequeueuserworkitem?view=netcore-3.0) (no current [ExecutionContext](https://docs.microsoft.com/en-us/dotnet/api/system.threading.executioncontext?view=netframework-4.8), i.e. no security context, call context, and synchronization context), [IThreadPoolWorkItem](https://docs.microsoft.com/en-us/dotnet/api/system.threading.ithreadpoolworkitem.execute?view=netcore-3.0) (implement your own type that get queue to the ThreadPool)
- new networking abstractions: implement your own servers and clients based on Kestrel's networking stack

## C# 8 features

**Talk** [C# 8 and Beyond - Filip Ekberg](https://www.youtube.com/watch?v=aw1UQJcwDcc&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=18&t=0s)

[Language feature status](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md)

C# 8
- more pattern matching + object deconstruction
```csharp
var whatFruit = fruit switch {
    Apple _ => "This is an apple",
    _ => "This is not an apple"
};
```
- new structs Indexe and Range
```csharp
var items = new[] { 1, 2, 3, 4, 5 };
items[^2] = 33; // 1, 2, 33, 4, 5
var subitems = items[0..2]; // 1, 2
```
- nullable refernces
```csharp
string? s = GetString();
var first = s[0]; //warning
```
- async enumerables
```csharp
await foreach(var dataPoint in SomeAsyncSource())
{
	Console.WriteLine(dataPoint);
}
```
- target type new expression
```csharp
Triangle triangle = new();
```
- defaut in deconstruction
```csharp
(int a, string b) = default;
```
- generic attributes
```csharp
public class CustomAttribute<T> : Attribute { }
```
- default interface methods
```csharp
public interface IHuman
{    
    public void Hi() => Console.WriteLine("Hi, you don't have to implement me");
}

public class Human : IHuman { }

((IHuman)new Human { … }).Hi();
```

## async await

**Talk** [Correcting Common Async/Await Mistakes in .NET - Brandon Minnick](https://www.youtube.com/watch?v=J0mcYVxJEl0&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=172)

- async await internals (state machine etc.)
- ```.ConfigureAwaits(false)```
- blocking calls (`.Reslt`, `.Wait()`)
- `.GetAwaiter().GetResult()`
- just `Task SomeMethod() => GetAsync();` insted of `async Task SomeMethod() => await GetAsync();`
- `ValueTask` in case of hot path
- async void, SafeFireAndForget
