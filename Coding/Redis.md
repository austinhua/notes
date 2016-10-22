# Redis
```
GET/SET key value
SET server:name "fido"
GET server:name => "fido"
```
```
DEL key
SETNX -- set if not exists
INCR key -- *atomically* increment a number (if doesn't exist increment from 0)
```
```
EXPIRE key [time(sec)] -- set the key to expire (disappear) after a certain amount of time
TTL key -- test how long a key will exist - -2: doesn't exist, -1: never expires - if you set a key again, it's TTL will be reset to -1
```

### Data Structures
##### Lists
>RPUSH, LPUSH, LLEN, LRANGE, LPOP, RPOP

```
RPUSH key value
LRANGE key [index of first element to retrieve] [index of last element to retrieve] -- use -1 to mean until end of list
```
##### Sets
Similar to lists, except no specific order and each element may only appear once
> SADD, SREM, SISMEMBER, SMEMBERS, SUNION
```
SISMEMBER set key
SADD set key
SMEMBERS set
```
