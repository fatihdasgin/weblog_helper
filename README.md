# Weblog Helper

A python application for filtering standart HTTP access logs by a single source IP Address or IP CIDR network.

## Installation

### Requirements

Please make sure that `ipaddress` python3 module is installed on your system. If you don't have `ipaddress` installed, you can install with:

```bash
$ pip3 install ipaddress
```

### Install

```bash
$ git clone https://github.com/fatihdasgin/weblog_helper
```

## Quick Usage

You can filter standart HTTP access logs by providing a single IP address or CIDR network.


The options to use weblog_helper are as follows:

```
./weblog_helper --file <HTTP access log file>

./weblog_helper --ip <IP Address or CIDR>
```


Filtering a single source IP logs:

```
$ ./weblog_helper --ip 180.76.15.135
180.76.15.135 - - [02/Jun/2015:17:05:23 -0700] "GET /logs/access_140730.log HTTP/1.1" 200 979626 "-" "Mozilla/5.0 (compatible;Baiduspider/2.0; +http://www.baidu.com/search/spider.html)" "www.redlug.com"
180.76.15.135 - - [02/Jun/2015:19:50:23 -0700] "GET /War/?C=N;O=A HTTP/1.1" 200 733 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)" "www.redlug.com"
```


To provide a different access log file, use `--file` option.

```
$ ./weblog_helper --ip 106.208.0.17 --file /path/to/file/access_log
106.208.0.17 - - [03/Jun/2015:08:26:52 -0700] "GET /pdf/che_sos.pdf HTTP/1.1" 200 207560 "https://www.google.co.in/" "Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.95 Safari/537.36" "redlug.com"
106.208.0.17 - - [03/Jun/2015:08:26:58 -0700] "GET /pdf/che_sos.pdf HTTP/1.1" 206 32768 "http://redlug.com/pdf/che_sos.pdf" "Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/39.0.2171.95 Safari/537.36" "redlug.com"
```


CIDR network filtering:

```
./weblog_helper --ip 180.76.15.0/24
180.76.15.135 - - [02/Jun/2015:17:05:23 -0700] "GET /logs/access_140730.log HTTP/1.1" 200 979626 "-" "Mozilla/5.0 (compatible;Baiduspider/2.0; +http://www.baidu.com/search/spider.html)" "www.redlug.com"
180.76.15.137 - - [02/Jun/2015:17:05:28 -0700] "GET /logs/access_140730.log HTTP/1.1" 200 7849856 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)" "www.redlug.com"
180.76.15.17 - - [02/Jun/2015:17:20:23 -0700] "GET /logs/access_141026.log HTTP/1.1" 200 45768 "-" "Mozilla/5.0 (compatible; Baiduspider/2.0; +http://www.baidu.com/search/spider.html)" "www.redlug.com"
```