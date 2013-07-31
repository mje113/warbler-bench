WARBLER BENCHMARK
=================

```
$ rake assets:precompile
$ warble executable compiled war
$ mv warbler-bench.war warbler-bench-compiled.war
$ warble executable war
```

SHOWDOWN
--------

## Puma

```
$ rails s -e production -p 8080
```

After 5 runs of:

```
$ ab -n 2000 -c 20 http://localhost:8080/

Finished 2000 requests


Server Software:        
Server Hostname:        localhost
Server Port:            8080

Document Path:          /
Document Length:        438 bytes

Concurrency Level:      20
Time taken for tests:   1.925 seconds
Complete requests:      2000
Failed requests:        0
Write errors:           0
Total transferred:      2392000 bytes
HTML transferred:       876000 bytes
Requests per second:    1039.00 [#/sec] (mean)
Time per request:       19.249 [ms] (mean)
Time per request:       0.962 [ms] (mean, across all concurrent requests)
Transfer rate:          1213.52 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    0   0.5      0       7
Processing:     5   19   8.0     17      74
Waiting:        5   18   7.9     17      74
Total:          5   19   8.0     18      75

Percentage of the requests served within a certain time (ms)
  50%     18
  66%     21
  75%     23
  80%     24
  90%     28
  95%     33
  98%     42
  99%     51
 100%     75 (longest request)
```

## WAR (non compiled)

```
$ java -jar warbler-bench.war
```

After 5 runs of:

```
$ ab -n 2000 -c 20 http://localhost:8080/

Finished 2000 requests


Server Software:        
Server Hostname:        localhost
Server Port:            8080

Document Path:          /
Document Length:        382 bytes

Concurrency Level:      20
Time taken for tests:   3.151 seconds
Complete requests:      2000
Failed requests:        0
Write errors:           0
Total transferred:      2442000 bytes
HTML transferred:       764000 bytes
Requests per second:    634.78 [#/sec] (mean)
Time per request:       31.507 [ms] (mean)
Time per request:       1.575 [ms] (mean, across all concurrent requests)
Transfer rate:          756.91 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    1   1.1      0      16
Processing:     7   30  13.2     29     106
Waiting:        7   30  13.2     28     104
Total:          8   31  13.4     29     106

Percentage of the requests served within a certain time (ms)
  50%     29
  66%     34
  75%     38
  80%     40
  90%     49
  95%     56
  98%     67
  99%     75
 100%    106 (longest request)
```

## WAR (compiled)

```
$ java -jar warbler-bench-compiled.war
```

After 5 runs of:

```
$ ab -n 2000 -c 20 http://localhost:8080/

Finished 2000 requests


Server Software:        
Server Hostname:        localhost
Server Port:            8080

Document Path:          /
Document Length:        382 bytes

Concurrency Level:      20
Time taken for tests:   2.824 seconds
Complete requests:      2000
Failed requests:        0
Write errors:           0
Total transferred:      2442000 bytes
HTML transferred:       764000 bytes
Requests per second:    708.30 [#/sec] (mean)
Time per request:       28.237 [ms] (mean)
Time per request:       1.412 [ms] (mean, across all concurrent requests)
Transfer rate:          844.57 [Kbytes/sec] received

Connection Times (ms)
              min  mean[+/-sd] median   max
Connect:        0    1   0.7      0       8
Processing:     7   27  11.9     26     119
Waiting:        7   27  11.9     26     119
Total:          7   28  12.0     26     120
WARNING: The median and mean for the initial connection time are not within a normal deviation
        These results are probably not that reliable.

Percentage of the requests served within a certain time (ms)
  50%     26
  66%     30
  75%     33
  80%     35
  90%     40
  95%     49
  98%     64
  99%     75
 100%    120 (longest request)
```
