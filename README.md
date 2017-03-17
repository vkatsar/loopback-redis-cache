# loopback-redis-cache
Redis cache mixin for loopback.io

# Features

  - Cache every GET request using only one get option.
  - Different Redis server for each model with fallback to config.json Redis server.
  - Invalidate cache on every create, update or delete.

### Installation

loopback-redis-cache requires [Node.js](https://nodejs.org/) v4+ to run.

 Install using npm

```sh
$ npm install loopback-redis-cache --save
```
Add to /server/config.json
```
  "redis": {
    "host": "127.0.0.1",
    "password": "your-redis-password"
  }
```  
Add to /server/model-config.json
```
    "mixins": [
      ...
      "../node_modules/loopback-redis-cache"
      ...
    ]
```

### Plugins

loopback-redis-cache is currently extended with the following plugins.

| Plugin | README |
| ------ | ------ |
| redis | [https://github.com/NodeRedis/node_redis/blob/master/README.md] |
| redis-delete-pattern | [https://github.com/uber-archive/redis-delete-pattern/blob/master/README.md] |

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
  
  Example 
    ``
  http://0.0.0.0:3000/api/games?cache=120
    ``
  cache value in seconds
  
  ### AngularJS SDK example
  
  ```
    Category.findOne({
        filter: {
            where: {
                categoryId: $scope.Id
            }
        },
        cache: 123
    }, function (item) {
        console.log(item);
    }, function (err) {
        console.log(err);
    });
  ```
  
