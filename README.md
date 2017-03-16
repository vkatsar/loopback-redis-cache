# loopback-redis-cache
Redis cache mixin for loopback.io

# Features

  - Cache every GET request using only one get option
  - Different redis server for each model

### Installation

loopback-redis-cache requires [Node.js](https://nodejs.org/) v4+ to run.

 Install using npm

```sh
$ npm install loopback-redis-cache --save
```
Edit /server/config.json and add 
```
  "redis": {
    "host": "127.0.0.1",
    "password": "your-redis-password"
  }
```  
### Plugins

loopback-redis-cache is currently extended with the following plugins.

| Plugin | README |
| ------ | ------ |
| redis | [https://github.com/NodeRedis/node_redis/blob/master/README.md] [PlDb] |

### How to use it
At your model (using config.json settings)
```
  "mixins": {
     "Rediscache": {}      
  }
```  
At your model (using external redis server)
```
  "mixins": {
     "Rediscache": {
       "client": {
         "host": "redis.server.ip.address",
         "password": "redis-password"
       }
     }    
  }
  ```
