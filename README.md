#zimg#


zimg is a light image storage and processing system. It's written by C and it has high performance in image field. There is a benchmark test report with more infomation: [Benchmark](http://zimg.buaa.us/benchmark.html). zimg is designed for high concurrency image server. It supports many features for uploading and downloading images.  

Homepage: [zimg.buaa.us](http://zimg.buaa.us/)  
Author: [@招牌疯子](http://weibo.com/819880808)  
Contact me: zp@buaa.us  


### Versions:
- 04/26/2014 - zimg 2.0.0 Beta Release. *Important milestone for zimg.*
- 03/10/2014 - zimg 1.1.0 Release.
- 08/01/2013 - zimg 1.0.0 Release.

### Dependence:
> We stand on the shoulders of giants.  

[libevent](https://github.com/libevent/libevent): Provides a sophisticated framework for buffered network IO.  
[imagemagick](http://www.imagemagick.org/script/magick-wand.php): A software suite to create, edit, compose, or convert bitmap images.  
[libmemcached](https://github.com/trondn/libmemcached): LibMemcached is designed to provide the greatest number of options to use Memcached.  
[lua](http://www.lua.org/): Lua is a lightweight multi-paradigm programming language designed as a scripting language with extensible semantics as a primary goal.  
#### [Optional] For Storage:  
[memcached](https://github.com/memcached/memcached): A distributed memory object caching system.  
[beansdb](https://github.com/douban/beansdb): Beansdb is a distributed key-value storage system designed for large scale online system, aiming for high avaliablility and easy management.  
[beanseye](https://github.com/douban/beanseye): Beanseye is proxy and monitor for beansdb, written in Go.  
[SSDB](https://github.com/ideawu/ssdb): SSDB is a high performace key-value(key-string, key-zset, key-hashmap) NoSQL database, an alternative to Redis.  
[twemproxy](https://github.com/twitter/twemproxy): Twemproxy is a fast and lightweight proxy for memcached and redis protocol.  

#### Thanks to:  
> zimg contains libevhtp and libhiredis. You needn't install them now.

[libevhtp](https://github.com/ellzey/libevhtp): A more flexible replacement for libevent's httpd API.  
[hiredis](https://github.com/redis/hiredis): Hiredis is a minimalistic C client library for the Redis database.  

### Supplying:
Receive and storage users' upload images.  
Transfer image through HTTP protocol.  
Process resized and grayed image by request parameter.  
Use memcached to improve performance.  
Multi-thread support for multi-core processor server.  
Use lua for conf and other functions.  
**Support beansdb/SSDB mode to save images into distributed storage backends.**

### In Planning:
Performance optimization.  
Security measures.  

### Documentation:
A guide book of zimg:  
[Guide Book of zimg](http://zimg.buaa.us/guidebook.html)  
There is an architecture design document of zimg v1.0. It is written in Chinese.  
[Architecture Design of zimg](http://zimg.buaa.us/arch_design.html)  
And this document is to introduce zimg v2.0.  
[Distributed Image Storage Server: zimg](http://blog.buaa.us/?p=215)  
The architecture of zimg's storage:  

![architecture_of_zimg_v2](http://ww2.sinaimg.cn/large/4c422e03gw1efpmngazc0j21ik1e6dnk.jpg)

### Download:
The source code is licensed under a BSD-like License.  
All versions on [Github](https://github.com/buaazp/zimg).  

### Build:

You should build dependences above and make sure the beansdb, beanseye or ssdb backend is working well.   
 
````
git clone https://github.com/buaazp/zimg
cd zimg   
make  
cd bin  
./zimg conf/zimg.lua
````
### Config:

````
--zimg server config

--server config
is_daemon=1
port=4869
thread_num=4
backlog_num=1024
max_keepalives=1

--cache config
cache=1
mc_ip='127.0.0.1'
mc_port=11211

--log config
log=1
log_name='./log/zimg.log'

--htdoc config
root_path='./www/index.html'

--storage config
--zimg support 3 ways for storage images
mode=1

--mode[1]: local disk mode
img_path='./img'

--mode[2]: beansdb mode
beansdb_ip='127.0.0.1'
beansdb_port='7900'

--mode[3]: ssdb mode
ssdb_ip='127.0.0.1'
ssdb_port='8888'

````

### Feedback:
If you have any question, please submit comment here or mention me on [Weibo](http://weibo.com/819880808).  
Technical issues are also welcomed to be submitted on [GitHub](https://github.com/buaazp/zimg/issues).


