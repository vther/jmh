这是我们的第一个BenchMark方法



JMH工作方式如下：

> - 使用@Benchmark注解于方法上

> - JMH生成执行这个基准的代码

我们可以把被'@Benchmark'标记的方法认为是基准测量的货物(payload),



一个类里面可以由多个@Benchmark方法，方法名无所谓。



JMH在编译期

> * 生成所有的基准测试代码，
> * 把方法注册在基准测试的清单里
> * 读出所有注解的默认值，准备好执行基准测试的环境



`@Benchmark`注解用于包裹测试的货物，JMH对于注解标注的方法提供了以下限制

> * 方法必须是public的
> * 参数仅仅能包含`@State`注解标注的类、`org.openjdk.jmh.infra.Control`、`org.openjdk.jmh.infra.Blackhole`
> * 方法只能是类被`@State`注解标注时候，才能被设为`synchronized`

`@Benchmark`方法允许抛出异常，但是任何抛出的异常都会被认为是基准测试失败



Mode 表示 JMH 进行 Benchmark 时所使用的模式。通常是测量的维度不同，或是测量的方式不同。目前 JMH 共有四种模式：

> 1. Throughput: 整体吞吐量，例如“1秒内可以执行多少次调用”。
> 2. AverageTime: 调用的平均时间，例如“每次调用平均耗时xxx毫秒”。
> 3. SampleTime: 随机取样，最后输出取样结果的分布，例如“99%的调用在xxx毫秒以内，99.99%的调用在xxx毫秒以内”
> 4. SingleShotTime: 以上模式都是默认一次 iteration 是 1s，唯有 SingleShotTime 是只运行一次。往往同时把 warmup 次数设为0，用于测试冷启动时的性能。






--------------------- 

