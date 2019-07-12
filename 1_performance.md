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

- [System.ValueTuple](https://docs.microsoft.com/en-us/dotnet/api/system.valuetuple?view=netframework-4.8) vs [System.Tuple](https://docs.microsoft.com/en-us/dotnet/api/system.tuple?view=netframework-4.8)
- ref structs, readonly structs, ref readonly structs, in method parameter
- [Span<T>](https://docs.microsoft.com/en-us/dotnet/api/system.span-1?view=netstandard-2.1) slicing vs String.Substring
- object pooling, [ArrayPool<T>](https://docs.microsoft.com/en-us/dotnet/api/system.buffers.arraypool-1?view=netstandard-2.1)
- [StringBuilder](https://docs.microsoft.com/en-us/dotnet/api/system.text.stringbuilder?view=netframework-4.8)
- params: [Array.Empty<T>](https://docs.microsoft.com/en-us/dotnet/api/system.array.empty?view=netframework-4.8), [Enumerable.Empty<T>](https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.empty?view=netframework-4.8), generic overloads
- boxing: `Console.WriteLine($"data {integer_var}");` - boxing, `Console.WriteLine($"data {integer_var.ToString()}");` - no boxing
- [ValueTask](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.valuetask-1?view=netstandard-2.1), [Task.CompletedTask](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task.completedtask?view=netframework-4.8)