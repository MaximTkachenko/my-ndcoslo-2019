# performance

## benchmarkdotnet

**Talk** [Pragmatic Performance: When to care about perf, and what to do about it - David Wengier](https://www.youtube.com/watch?v=24qazsRnc40&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=71&t=1705s)
- [Book "Pro .NET Benchmarking. The Art of Performance Measurement"](https://www.apress.com/gp/book/9781484249406)
- [BenchmarkDotNet](https://github.com/dotnet/BenchmarkDotNet)

## zero allocation

**Talk** [Writing Allocation Free Code in C# - Matt Ellis](https://www.youtube.com/watch?v=nK54s84xRRs&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=17&t=0s)

https://sharplab.io

> Allocation is cheap, garbage collection is expensive.

>You should measure.

- System.ValueTuple vs System.Tuple
- ref structs, readonly structs, ref readonly structs, in method parameter
- Span<T> slicing vs string.Substring
- object pooling, [ArrayPool<T>](https://docs.microsoft.com/en-us/dotnet/api/system.buffers.arraypool-1?view=netstandard-2.1)
- StringBuilder
- params: `Array.Empty<T>`, `Enumerable.Empty<T>`, generic overloads
- boxing: `Console.WriteLine($"data {r}");` - boxing, `Console.WriteLine($"data {r.ToString()}");` - no boxing
- ValueTask, Task.CompletedTask