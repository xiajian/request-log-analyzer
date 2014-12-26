# Request-log-analyzer 

[<img src="https://secure.travis-ci.org/wvanbergen/request-log-analyzer.png" />](http://travis-ci.org/wvanbergen/request-log-analyzer)

Request-log-analyzer是用来分析多个格式的请求日志并生成性能报告的命令行工具，其目的是寻找需要优化的动作(action)。

* 分析日志文件: 当前支持 Amazon S3, Apache, Delayed::Job, Merb, Mysql, PostgreSQL, Rack, Rails等等.
* 组合多个文件，并解压压缩文件，这些在使用logrotate时，需要手动操作
* 使用多个度量指标，包括 累积请求时间，平均请求时间，处理块，数据库和渲染时间，HTTP方法和状态，Rails动作缓存统计等 (样例输出: http://github.com/wvanbergen/request-log-analyzer/wiki/sample-output)
* 可以运行兼容MRI 1.9+环境中，速度快、内存少，所以在生产服务器上运行很安全

更多信息，参考项目的[wiki]( http://github.com/wvanbergen/request-log-analyzer/wiki)

> [logrotate](https://fedorahosted.org/logrotate/) : 简化日志文件的管理任务，尤其是系统中生成大量的日志文件时。logrotate可以自动压缩、
> 删除或者将文件作为email发出。logrotate可以在日志文件达到一定大小的时候，处理日志文件，系统自带该命令。

## Installation & basic usage

request-log-analyzer可以当作Ruby gem包来安装(可能需要使用root权限来运行):

    $ gem install request-log-analyzer

可使用如下的命令分析Rails日志，并生成性能报告 : 

    $ request-log-analyzer log/production.log

更多细节，其他的文件格式的支持，以及可用的命令行选项，可以参考<http://github.com/wvanbergen/request-log-analyzer/wiki>

## Additional information

Request-log-analyzer由Willem van Bergen和Bart ten Brinke设计并实现。

如果，你的Rails应用程序性能表现不如人意。你可能需要一个专家来分析你的应用，别怕，有大神Willem van
Bergen (willem@railsdoctors.com)和Bart ten Brinke (bart@railsdoctors.com)。

* 项目wiki : http://github.com/wvanbergen/request-log-analyzer/wiki
* 议题追踪: http://github.com/wvanbergen/request-log-analyzer/issues
* 软件使用MIT协议，如果想要贡献项目，请查阅CONTRIBUTING.rdoc
