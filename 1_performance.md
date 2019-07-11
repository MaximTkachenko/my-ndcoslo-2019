# performance

## benchmarkdotnet

https://www.youtube.com/watch?v=24qazsRnc40&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=71&t=1705s
https://ndcoslo.com/talk/lowering-in-c-whats-really-going-on-in-your-code/
https://github.com/dotnet/BenchmarkDotNet

## zero allocation

https://www.youtube.com/watch?v=nK54s84xRRs&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=17&t=0s
https://sharplab.io

In GC runtimes allocation is cheap, garbage collection is expensive.
You should measure.

- System.ValueTuple vs System.Tuple
- Span<T> slicing vs string.Substring
- object pooling, [ArrayPool<T>](https://docs.microsoft.com/en-us/dotnet/api/system.buffers.arraypool-1?view=netstandard-2.1)
- StringBuilder
- params, `Array.Empty<T>`, `Enumerable.Empty<T>`, generic overloads
- boxing, `Console.WriteLine($"data {r}");` - boxing
- ValueTask, Task.CompletedTask

