Request-log-analyzer
====================

RLA是一个简单的管道和过滤系统，这允许你方便的添加其他的报告、过滤器以及输出格式。其处理流程大体如下: 

                               -> Aggregator  (database)
    Source -> Filter -> Filter -> Aggregator  (summary report)  -> Output
                               -> Aggregator  (...)

管道建立完成后，开始生成大块的生产者，并通过管道推送请求。

    Controller.start

## Source

RequestLogAnalyzer::Source is an Object that pushes requests into the chain.
At the moment you can only use the log-parser as a source.
It accepts files or stdin and can parse then into request objects using a RequestLogAnalyzer::FileFormat definition.
In the future we want to be able to have a generated request database as source as this will make interactive
down drilling possible.

## Filter

The filters are all subclasses of the RequestLogAnalyzer::Filter class.
They accept a request object, manipulate or drop it, and then pass the request object on to the next filter
in the chain.
At the moment there are three types of filters available: Anonymize, Field and Timespan.

##  Aggregator

The Aggregators all inherit from the RequestLogAnalyzer::Aggregator class.
All the requests that come out of the Filterchain are fed into all the aggregators in parallel.
These aggregators can do anything what they want with the given request.
For example: the Database aggregator will just store all the requests into a SQLite database while the Summarizer will
generate a wide range of statistical reports from them.

##  Running the pipeline

All Aggregators are asked to report what they have done. For example the database will report: I stuffed x requests
into SQLite database Y. The Summarizer will output its reports.

    Controller.report

The output is pushed to a RequestLogAnalyzer::Output object, which takes care of the output.
It can generate either ASCII, UTF8 or even HTML output.
