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
All data structures supported by Redis:
- Binary-safe strings.
- Lists: collections of string elements sorted according to the order of insertion. They are basically linked lists.
- Sets: collections of unique, unsorted string elements.
- Sorted sets, similar to Sets but where every string element is associated to a floating number value, called score. The elements are always taken - sorted by their score, so unlike Sets it is possible to retrieve a range of elements (for example you may ask: give me the top 10, or the bottom 10).
- Hashes, which are maps composed of fields associated with values. Both the field and the value are strings. This is very similar to Ruby or Python hashes.
- Bit arrays (or simply bitmaps): it is possible, using special commands, to handle String values like an array of bits: you can set and clear individual bits, count all the bits set to 1, find the first set or unset bit, and so forth.
- HyperLogLogs: this is a probabilistic data structure which is used in order to estimate the cardinality of a set. Don't be scared, it is simpler than it seems... See later in the HyperLogLog section of this tutorial.

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
SISMEMBER key member
SADD key member
SMEMBERS key
```

##### Sorted Sets
Redis 1.2 introduced Sorted Sets - each value has an associated score
> ZADD, ZRANGE
```
ZADD key score member
(ZADD hackers 1906 "Grace Hopper")
```

##### Hashes
Maps between string fields and string values - good way to represent objects (e. User w/ fields)
> HSET, HGET, HMSET, HMGET HDEL, HGETALL, HINCRBY, HEXISTS, HKEYS, HVALS
```
HSET key field value
HMSET key [field value ...]
HGET key field
HGETALL key -- returns 1)key1 2)value1 3)key2 4)value2...
HINCRBY key field [increment amount] -- value must be an integer
```



##### Scanning Elements
Consult redis documentation
