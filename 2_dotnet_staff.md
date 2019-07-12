# .net staff

## .NET Core 3

**AWESOOOOME talk** [Hidden gems in .NET Core 3 - David Fowler & Damian Edwards](https://www.youtube.com/watch?v=xdSSH63IZZc&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=14&t=1225s)

>.NET Core 3.0 GA (General Availability) scheduled for September 2019

CLR:
- GC limits, new good defaults
- AssemblyLoadContext: logical successor to AppDomains (load/unload assemblies)
- Startup hooks: regietr code to execute before Main
- dotnet diagnostics tools: counters, trace, dump
- publish options: PublishSingleFile, PublishTrimmed

BCL:
- IAsyncDisposable: C# 8 await using, call async methods in  
- https://www.w3.org/TR/trace-context/ support
- ThreadPool: [UnsafeQueueUserWorkItem](https://docs.microsoft.com/en-us/dotnet/api/system.threading.threadpool.unsafequeueuserworkitem?view=netcore-3.0) (no current [ExecutionContext](https://docs.microsoft.com/en-us/dotnet/api/system.threading.executioncontext?view=netframework-4.8), i.e. no security context, call context, and synchronization context), [IThreadPoolWorkItem](https://docs.microsoft.com/en-us/dotnet/api/system.threading.ithreadpoolworkitem.execute?view=netcore-3.0) (implement your own type that get queue to the ThreadPool)
- new networking abstractions: implement your own servers and clients based on Kestrel's networking stack

## C# 8 features

**Talk** [C# 8 and Beyond - Filip Ekberg](https://www.youtube.com/watch?v=aw1UQJcwDcc&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=18&t=0s)

[Language feature status](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md)

C# 7
- tuple deconstruction
- pattern matching (switch "improvement")

C# 8
- more pattern matching + object deconstruction
- ranges
- nullable refernces
- using declarations
- static local functions
- async enumerables
- target type new expression
```
Triangle triangle = new();
```
- defaut in deconstruction
```
(int a, string b) = default;
```
- generic attributes
```
public class CustomAttribute<T> : Attribute { }
```
- default interface methods

## async await mistakes

**Talk** [Correcting Common Async/Await Mistakes in .NET - Brandon Minnick](https://www.youtube.com/watch?v=J0mcYVxJEl0&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=172)

- async await internals (state machine etc.)
- ```.ConfigureAwaits(false)```
- blocking calls (`.Reslt`, `.Wait()`)
- `.GetAwaiter().GetResult()`
- just `Task SomeMethod() => GetAsync();` insted of `async Task SomeMethod() => await GetAsync();`
- `ValueTask` in case of hot path
- async void, SafeFireAndForget