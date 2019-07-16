# distributed systems

## distributed transactions

**Talk** [Life Beyond Distributed Transactions: An Apostate's Implementation - Jimmy Bogard](https://www.youtube.com/watch?v=1fjGPG-v76s&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=140)

Also https://developers.redhat.com/blog/2018/10/01/patterns-for-distributed-transactions-within-a-microservices-architecture/

### Two-phase commit (2pc) pattern
![2pc](https://technet.tmaxsoft.com/upload/download/online/tibero/pver-20170217-000001/tibero_dev/resources/tbdev_4.png)

### Saga pattern
![saga](https://i.imgur.com/9Z9X7PF.png)

## polly

**Talk** [Bulletproof Transient Error Handling with Polly - ​Carl Franklin](https://www.youtube.com/watch?v=2kfCXMoVCqM&list=PL03Lrmd9CiGe9QtFC8LRRqknzpKgcrWpe&index=72&t=0s)

https://github.com/App-vNext/Polly

.NET implementation of resilience policies:
- [retry](https://docs.microsoft.com/en-us/azure/architecture/patterns/retry)
- [circuit-breaker](https://docs.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker)
- timeout
- [bulkhead isolation](https://docs.microsoft.com/en-us/azure/architecture/patterns/bulkhead)
- cache
- fallback
- policy wrap (allows any of the above policies to be combined flexibly)