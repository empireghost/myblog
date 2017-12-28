---
title: RPC
date: 2017-12-22 11:02:55
categories:
    RPC thrift grpc
tags:
    RPC thrift grpc
---

#### [thrift](http://thrift.apache.org/)

thrift 注册多个服务

```

    TBinaryProtocol.Factory proFactory = new TBinaryProtocol.Factory();

    TProcessor myServiceProcessor = new MyService.Processor<MyService.Iface>(
            new MyServiceImpl());

    TProcessor personServiceProcessor = new PersonService.Processor<PersonService.Iface>(
            new PersonServiceImpl());

    TMultiplexedProcessor multiProcessor = new TMultiplexedProcessor();
    multiProcessor.registerProcessor("myService", myServiceProcessor);
    multiProcessor.registerProcessor("personService", personServiceProcessor);
```
---

#### [grpc](http://grpc.io/)
