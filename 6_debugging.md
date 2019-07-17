# debugging

[Advanced .NET debugging techniques from real world investigations - Christophe Nasarre and Kevin Gos](https://www.youtube.com/watch?v=biDJkJ4L_K8&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=171&t=0s)

## windbg

https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugger-download-tools

## pefview

https://github.com/microsoft/perfview

## clrmd

https://github.com/microsoft/clrmd
```
using(var dt = DataTarget.LoadCrashDump(@"C:\temp\dump.dmp"))
{
    var rt = dt.ClrVersions.First().CreateRuntime();
    Console.WriteLine(rt.ThreadPool.TotalThreads);
}
```
