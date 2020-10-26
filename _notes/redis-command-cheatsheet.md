---
layout: collection_item
title:  "Redis Cheatsheet"
category: Programning
tags: redis key value store nosql session web
---

## General commands
### Set a new key 
```redis
SET server:name = "fido"
```
### Get a key value
```
GET server:name
```
### Check if a key exists
```redis
EXISTS server:name
```
### Detete a given key
```redis
DEL server:name
```
### Increment & Decrement a given key value
```redis
SET connections 10
INCR connections
DECR connections
```
#### Increment & Decrement by a specific value
```redis
INCRBY connections 100
DECRBY connctions 10
```

### Expire Value and TTL
#### Seting time limit
```redis
SET key = 10
EXPIRE key 100 
PEXPIRE key 100000
```
Here, 
`EXPIRE` calculates in second
`PEXPIRE` calculates in milisecond

We can also define expire time at the time of declaration
```redis
SET key "Hello World" EX 5
```
#### View current time limit
```redis
TTL key
PTTL key
```

`TTL` shows timelimit in second
`PTTL` shows timelimit in milisecond

#### Cancel timelimit
```redis
PERSIST key
```

## List Commands
 `RPUSH`, `LPUSH`, `LLEN`, `LRANGE`, `LPOP`, and `RPOP`
### Description
#### `RPUSH` Pushes an item/ items to the end of the list
#### `LPUSH` Pushes an item/ items to the start of the list
```
RPUSH friends "Liam"
RPUSH friends "Steve" "Diponkor" "Mahim"
LPUSH friends "Rafi"
RPUSH friends "Abid" "Samin" "Joyanta"
```
#### `LRANGE` Retrive items from a list in specific range 0 is starting index and if we count from last -1 is the first index, -2 is the second index and so one. Example. lists all friends

```redis 
lrange friends 0 -1
```

#### `LPOP` Removes the first element from the list
#### `RPOP` Removes the last element from the list
#### `LLEN` Gets the length of the list

## Set Commands 
`SADD`, `SREM`, `SISMEMBER`, `SMEMBERS`, `SUNION`

#### `SADD` add an item/ items to set
#### `SREM` remove an item/ items from set
#### `SISMEMBER` check if an items exists
#### `SUNION` Returns the union of two sets
```redis
SUNION set1 set2
```
#### `SPOP` removes and return single or specific number of item from last
##### Removing on item from last
```redis
SPOP friends
```
##### Removing specific number of items from the list
```redis 
SPOP friends 3
```

## Sorted sets
All commands and working priniciple are same to sets but each element has a score which is used to short the set items

`ZADD`, `ZRANGE`

```redis
ZADD hackers 1940 "Alan Kay"
ZADD hackers 1906 "Grace Hopper"
ZADD hackers 1953 "Richard Stallman"
ZADD hackers 1965 "Yukihiro Matsumoto"
ZADD hackers 1916 "Claude Shannon"
ZADD hackers 1969 "Linus Torvalds"
ZADD hackers 1957 "Sophie Wilson"
ZADD hackers 1912 "Alan Turing"
```

### Hash field
```redis
HSET user:1000 visits 10
HINCRBY user:1000 visits 1 => 11
HINCRBY user:1000 visits 10 => 21
HDEL user:1000 visits
HINCRBY user:1000 visits 1 => 1
```


