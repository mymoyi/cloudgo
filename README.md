# Cloudgo

标签（空格分隔）： 服务计算

---

##1.Martini框架
本次实验选用Martini框架，因为Martini是一个强大为了编写模块化Web应用而生的GO语言框架，而且github上有详尽的中文文档，学习起来比较方便。

##2.Martini功能列表
1.无侵入式的设计.
2.很好的与其他的Go语言包协同使用.
3.超赞的路径匹配和路由.
4.模块化的设计 - 容易插入功能件，也容易将其拔出来.
5.已有很多的中间件可以直接使用.
6.框架内已拥有很好的开箱即用的功能支持.
7.完全兼容http.HandlerFunc接口.

##3.下载Martini
    go get github.com/go-martini/martini

##4.运行
    go run main.go -p8080
在浏览器中打开显示：

    hello moyi
##5.测试
###（1）curl
    curl  -v  http://localhost:8080/hello/moyi
结果：

    * Hostname was NOT found in DNS cache
    *   Trying 127.0.0.1...
    * Connected to localhost (127.0.0.1) port 8080 (#0)
    > GET /hello/moyi HTTP/1.1
    > User-Agent: curl/7.35.0
    > Host: localhost:8080
    > Accept: */*
    > 
    < HTTP/1.1 200 OK
    < Date: Wed, 15 Nov 2017 10:14:10 GMT
    < Content-Length: 16
    < Content-Type: text/plain; charset=utf-8
    < 
    * Connection #0 to host localhost left intact
    hello moyimoyi@ubantu：~$ 

###（2）压力测试
    ab -n 1000 -c 100 http://localhost:8080/hello/moyi
结果：
    
    This is ApacheBench, Version 2.3 <$Revision: 1706008 $>
    Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/ 

    Licensed to The Apache Software Foundation, http://www.apache.org/ 


    Benchmarking localhost (be patient)
    Completed 100 requests
    Completed 200 requests
    Completed 300 requests
    Completed 400 requests
    Completed 500 requests
    Completed 600 requests
    Completed 700 requests
    Completed 800 requests
    Completed 900 requests
    Completed 1000 requests
    Finished 1000 requests


    Server Software:        
    Server Hostname:        localhost
    Server Port:            8080

    Document Path:          /hello/moyi
    Document Length:        16 bytes

    Concurrency Level:      100
    Time taken for tests:   0.699 seconds
    Complete requests:      1000
    Failed requests:        0
    Total transferred:      133000 bytes
    HTML transferred:       16000 bytes
    Requests per second:    1430.94 [#/sec] (mean)
    Time per request:       69.884 [ms] (mean)
    Time per request:       0.699 [ms] (mean, across all concurrent requests)
    Transfer rate:          185.85 [Kbytes/sec] received

        Connection Times (ms)
              min  mean[+/-sd] median   max
        Connect:        0    2   6.8      0      45
    Processing:     1   62  13.6     60     113
    Waiting:        1   62  13.3     60     113
    Total:          1   64  17.9     61     158

    Percentage of the requests served within a certain time (ms)
    50%     61
    66%     65
    75%     68
    80%     71
    90%     77
    95%     91
    98%    138
    99%    152
    100%    158 (longest request)

