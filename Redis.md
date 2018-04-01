Remote Dictionay server

message broker
key value pair data base

key is prinable ASCII value :512 MB
Values : Strings ,hashes, list ,sets sorted sets

# Commands
 SET key value
This command sets the value at the specified key.

 GET key
Gets the value of a key.

 DEL key
This command deletes the key, if it exists.

 FLUSHALL 
Delete all the keys of all the existing databases, not just the currently selected one.

 KEYS pattern
Returns all keys matching patter

SETEX key seconds value
Sets the value with the expiry of a key

SETNX key value
Sets the value of a key, only if the key does not exist

SETRANGE key offset value
Overwrites the part of a string at the key starting at the specified offset

STRLEN key
Gets the length of the value stored in a key

MSET key value [key value ...]
Sets multiple keys to multiple values

MSETNX key value [key value ...]
Sets multiple keys to multiple values, only if none of the keys exist

PSETEX key milliseconds value
Sets the value and expiration in milliseconds of a key

INCR key
Increments the integer value of a key by one

INCRBY key increment
Increments the integer value of a key by the given amount

INCRBYFLOAT key increment
Increments the float value of a key by the given amount

DECR key
Decrements the integer value of a key by one

DECRBY key decrement
Decrements the integer value of a key by the given number

APPEND key value
Appends a value to a key



HDEL key field [field ...]
Delete one or more hash fields

HEXISTS key field
Determine if a hash field exists

HGET key field
Get the value of a hash field

HGETALL key
Get all the fields and values in a hash

HINCRBY key field increment
Increment the integer value of a hash field by the given number

HINCRBYFLOAT key field increment
Increment the float value of a hash field by the given amount

HKEYS key
Get all the fields in a hash

HLEN key
Get the number of fields in a hash

HMGET key field [field ...]
Get the values of all the given hash fields

HMSET key field value [field value ...]
Set multiple hash fields to multiple values

HSET key field value
Set the string value of a hash field

HSETNX key field value
Set the value of a hash field, only if the field does not exist

HSTRLEN key field
Get the length of the value of a hash field

HVALS key
Get all the values in a hash

HSCAN key cursor [MATCH pattern] [COUNT count]
Incrementally iterate hash fields and associated values



BLPOP key [key ...] timeout
Remove and get the first element in a list, or block until one is available

BRPOP key [key ...] timeout
Remove and get the last element in a list, or block until one is available

BRPOPLPUSH source destination timeout
Pop a value from a list, push it to another list and return it; or block until one is available

LINDEX key index
Get an element from a list by its index

LINSERT key BEFORE|AFTER pivot value
Insert an element before or after another element in a list

LLEN key
Get the length of a list

LPOP key
Remove and get the first element in a list

LPUSH key value [value ...]
Prepend one or multiple values to a list

LPUSHX key value
Prepend a value to a list, only if the list exists

LRANGE key start stop
Get a range of elements from a list

LREM key count value
Remove elements from a list

LSET key index value
Set the value of an element in a list by its index

LTRIM key start stop
Trim a list to the specified range

RPOP key
Remove and get the last element in a list

RPOPLPUSH source destination
Remove the last element in a list, prepend it to another list and return it

RPUSH key value [value ...]
Append one or multiple values to a list

RPUSHX key value
Append a value to a list, only if the list exists



SADD key member [member ...]
Add one or more members to a set

SCARD key
Get the number of members in a set

SDIFF key [key ...]
Subtract multiple sets

SDIFFSTORE destination key [key ...]
Subtract multiple sets and store the resulting set in a key

SINTER key [key ...]
Intersect multiple sets

SINTERSTORE destination key [key ...]
Intersect multiple sets and store the resulting set in a key

SISMEMBER key member
Determine if a given value is a member of a set

SMEMBERS key
Get all the members in a set

SMOVE source destination member
Move a member from one set to another

SPOP key [count]
Remove and return one or multiple random members from a set

SRANDMEMBER key [count]
Get one or multiple random members from a set

SREM key member [member ...]
Remove one or more members from a set

SUNION key [key ...]
Add multiple sets

SUNIONSTORE destination key [key ...]
Add multiple sets and store the resulting set in a key

SSCAN key cursor [MATCH pattern] [COUNT count]
Incrementally iterate Set elements



ZREVRANGEBYLEX key max min [LIMIT offset count]
Return a range of members in a sorted set, by lexicographical range, ordered from higher to lower strings.

ZRANGEBYSCORE key min max [WITHSCORES] [LIMIT offset count]
Return a range of members in a sorted set, by score

ZRANK key member
Determine the index of a member in a sorted set

ZREM key member [member ...]
Remove one or more members from a sorted set

ZREMRANGEBYLEX key min max
Remove all members in a sorted set between the given lexicographical range

ZREMRANGEBYRANK key start stop
Remove all members in a sorted set within the given indexes

ZREMRANGEBYSCORE key min max
Remove all members in a sorted set within the given scores

ZREVRANGE key start stop [WITHSCORES]
Return a range of members in a sorted set, by index, with scores ordered from high to low

ZREVRANGEBYSCORE key max min [WITHSCORES] [LIMIT offset count]
Return a range of members in a sorted set, by score, with scores ordered from high to low

ZREVRANK key member
Determine the index of a member in a sorted set, with scores ordered from high to low

ZSCORE key member
Get the score associated with the given member in a sorted set

ZUNIONSTORE destination numkeys key [key ...] [WEIGHTS weight [weight ...]] [AGGREGATE SUM|MIN|MAX]
Add multiple sorted sets and store the resulting sorted set in a new key

ZSCAN key cursor [MATCH pattern] [COUNT count]
Incrementally iterate sorted sets elements and associated scores


SUBSCRIBE, UNSUBSCRIBE and PUBLISH implement the Publish/Subscribe messaging paradigm where senders (publishers) are not programmed to send their messages to specific receivers (subscribers).

PSUBSCRIBE pattern [pattern ...]
Listen for messages published to channels matching the given patterns

PUBSUB subcommand [argument [argument ...]]
Inspect the state of the Pub/Sub subsystem

PUBLISH channel message
Post a message to a channel

PUNSUBSCRIBE [pattern [pattern ...]]
Stop listening for messages posted to channels matching the given patterns

SUBSCRIBE channel [channel ...]
Listen for messages published to the given channels

UNSUBSCRIBE [channel [channel ...]]
Stop listening for messages posted to the given channels

# Redis Cluster  [Working on it]
https://redis.io/topics/cluster-tutorial 

What you get :
	High availablity  : 
	Data Shrading : Data is spread across multiple nodes 

Redis Ports:
	Allow firewall access to Any client port + 10000 (used by Redis cluster bus to communicate with other nodes)

Redis Data Shrading:
	Every key is part of hash slots 
	Node contains hash slots
	Hash slot for give key is computed by CRC16 Modulo 16384
	You can force multiple keys to be part of the same hash slot by using a concept called hash tags.

Redis Cluster master-slave model
	suggested Cluster setup : A,B,C Master nodes A1,B1,C1 are slave nodes 6 node cluster .
	Hash Slots are disributed among masters.
	B fails B1 gets pormoted as master .
	But Both B and B1 fails cluster stops working . 

Redis Cluster consistency guarantees
	Strong consistency is not possible

	client writes to Master B
	Master B returns ok
	Master B triggers replication on B1 B2 B3 .
	if master waits for B1,B2,B3 ack it will be performance overhead

Redis Cluster configuration parameters

	cluster-enabled
	cluster-config-file :read only  client can`t use this
	cluster-node-timeout :If a master node is not reachable for more than the specified amount of time, it will be failed over by its slaves.
	cluster-slave-validity-factor
	cluster-migration-barrier
	cluster-require-full-coverage
	 



