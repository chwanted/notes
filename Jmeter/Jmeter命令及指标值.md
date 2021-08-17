####  Jmeter命令

非GUI模式命令，需要进入jmeter bin，运行命令

```shell
jmeter -n -t <testplan filename> -l result.jtl
```

运行并生成报告（必须没有result.jtl）

```shell
jmeter -n -t script.jmx -l result.jtl -e -o <report_file path>
```

如果已经存在结果文件（.jtl），运行如下命令生成报告

```shell
jmeter -g result.jtl -o <report_file path>
```

分布压测运行命令（脚本和参数文件存放到各台终端相同目录下，将每台终端的jmerter-server.bat打开等待主机发号施令）

```shell
jmeter.bat -n -t <testplan filename> -R host1:port1,host2:port2 -l <listener filename>
```

#### 指标值计算

- 平均并发用户数

  <img src="https://latex.codecogs.com/svg.image?c=\frac{nL}{T}" title="c=\frac{nL}{T}" />

  - C：平均用户并发数

  - n：平均每天访问用户数（login     session的数量）

  - L：一天内用户从登陆到退出的平均时间

  - T：考察的时间段长度（一天内多长时间有用户使用系统）

    

- 吞吐量（承压能力）

  <img src="https://latex.codecogs.com/svg.image?F=\frac{vuR}{T}" title="F=\frac{vuR}{T}" />

  - vu：虚拟用户个数

  - R：每个虚拟用户发出的请求

  - T：性能测试所用的时间

    

- TPS：每秒request/事务数量

  <img src="https://latex.codecogs.com/svg.image?TPS=\frac{concurements}{AverageResponseTime}" title="TPS=\frac{concurements}{AverageResponseTime}" />

  - concurements：并发数
  - AverageResponseTime：平均响应时间

- 高峰并发用户数

  <img src="https://latex.codecogs.com/svg.image?c=c&plus;3\sqrt{c}" title="c=c+3\sqrt{c}" />