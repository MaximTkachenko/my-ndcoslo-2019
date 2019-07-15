# architecture

## ddd

**Talk** [Getting to DDD: Pragmatic or Principled? - Julie Lerman](https://www.youtube.com/watch?v=3AAzySH3A88&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=20&t=0s)

[Clean architecture article](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)

**Talk** [Clean Architecture with ASP.NET Core 2.2 - Jason Taylor](https://www.youtube.com/watch?v=Zygw4UAxCdg)

## kill monolith

**Talk** [Monolith Decomposition Patterns - Sam Newman](https://www.youtube.com/watch?v=64w1zbpHGTg&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=140&t=0s)

- single process monolith
- modular monolith
- distributed monolith (can't deploy independently) - put all back into monolith and split propely with [bounded contexts](https://martinfowler.com/bliki/BoundedContext.html) (DDD)
- [strangler pattern](https://docs.microsoft.com/en-us/azure/architecture/patterns/strangler)
- [branch by abstraction](https://martinfowler.com/bliki/BranchByAbstraction.html)
- database per microservice, avoid sharing databases
- no joins, no foreign keys

**Talk** [10 years of microservices at FINN.no - and we still haven’t slain that dragon! - Henning Spjelkavi](https://www.youtube.com/watch?v=8f7bg5YAdds&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=43&t=2589s)

