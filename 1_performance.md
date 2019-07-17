# performance

## benchmarkdotnet

**Talk** [Pragmatic Performance: When to care about perf, and what to do about it - David Wengier](https://www.youtube.com/watch?v=24qazsRnc40&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=71&t=1705s)
- [Book "Pro .NET Benchmarking. The Art of Performance Measurement"](https://www.apress.com/gp/book/9781484249406)
- [BenchmarkDotNet](https://github.com/dotnet/BenchmarkDotNet)

<details><summary>Example: StringBuilder vs Concat</summary>
<p>

```csharp
class Program
{
    static void Main()
    {
        var summary = BenchmarkRunner.Run<Test>();
    }
}

[MemoryDiagnoser]
public class Test
{
    private string[] _data;

    [GlobalSetup]
    public void GlobalSetup()
    {
        int count = 100;
        _data = new string[count];
        for (int i = 0; i < count; i++)
        {
            _data[i] = Guid.NewGuid().ToString();
        }
    }

    
    [Benchmark]
    public string Naive()
    {
        string result = string.Empty;
        for (int i = 0; i < _data.Length; i++)
        {
            result += _data[i];
        }

        return result;
    }

    [Benchmark]
    public string WithStringBuilder()
    {
        var result = new StringBuilder();
        for (int i = 0; i < _data.Length; i++)
        {
            result.Append(_data[i]);
        }

        return result.ToString();
    }
}
```

|            Method |      Mean |   Gen 0 | Gen 1 | Gen 2 | Allocated |
|------------------ |----------:|--------:|------:|------:|----------:|
|             Naive | 41.016 us | 87.3413 |     - |     - |  358.1 KB |
| WithStringBuilder |  2.911 us |  4.0703 |     - |     - |   16.7 KB |
>1 us - 1 Microsecond (0.000001 sec)

</p>
</details>

## zero allocation

**Talk** [Writing Allocation Free Code in C# - Matt Ellis](https://www.youtube.com/watch?v=nK54s84xRRs&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=17&t=0s)

https://sharplab.io

> Allocation is cheap, garbage collection is expensive.

>You should measure.

- [System.ValueTuple](https://docs.microsoft.com/en-us/dotnet/api/system.valuetuple?view=netframework-4.8) vs [System.Tuple](https://docs.microsoft.com/en-us/dotnet/api/system.tuple?view=netframework-4.8)
- [Span<T>](https://docs.microsoft.com/en-us/dotnet/api/system.span-1?view=netstandard-2.1) slicing vs String.Substring
- object pooling, [ArrayPool<T>](https://adamsitnik.com/Array-Pool/)
- [StringBuilder](https://docs.microsoft.com/en-us/dotnet/api/system.text.stringbuilder?view=netframework-4.8)
- params: [Array.Empty<T>](https://docs.microsoft.com/en-us/dotnet/api/system.array.empty?view=netframework-4.8), [Enumerable.Empty<T>](https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable.empty?view=netframework-4.8), overloads
- `Console.WriteLine($"data {integer_var}");` - boxing, `Console.WriteLine($"data {integer_var.ToString()}");` - no boxing
- [ValueTask](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.valuetask-1?view=netstandard-2.1), [Task.CompletedTask](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task.completedtask?view=netframework-4.8)
