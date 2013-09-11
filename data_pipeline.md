!SLIDE

# Building Data Infrastructure

## Will Larson ([@lethain](https://twitter.com/Lethain))
## SocialCode ([@socialcodeinc](https://twitter.com/socialcodeinc))

!SLIDE largeimg

## Growth problems.

![Showing teams, products and databases increasing over time.](imgs/when_an_increase.png)


!SLIDE largeimg

## A familiar monolith.

![Architecture diagram of monolithic architecture composed of a load balancer, Gunicorn web servers, MySQL, Redis and celery workers.](imgs/monolithic.png)


!SLIDE left

## Monolithic data problems.

* Expensive schema changes.
* Data siloed by performance.
* Explosion of access patterns.


!SLIDE left

## Our requirements.

1. Decouple publishing and consumption.
2. Support cheap data exploration.
4. Facilitate schemas change.
3. Fail rarely, fail loudly.
4. Avoid datastore lock-in.


!SLIDE largeimg

## Our solution today.

![A data pipeline, with services publishing into an input service, Kafka and Zooper between the input service and an output service, and datamarts subscribing to the output service.](imgs/pipeline_arch.png)


!SLIDE left

## What is Kafka?

1. ....


!SLIDE left

## Why Kafka?

1. Does pub-sub right.
2. Data durability.
3. Horizontal scalability.
4. [Zookeeper](http://zookeeper.apache.org/).


!SLIDE left

## Why [JSON Schema](http://json-schema.org/)? Why HTTP?

~~~~{json}
{
   "title": "Example Schema",
   "type": "object",
   "properties": {
   "firstName": {"type": "string"},
   "lastName": {"type": "string"},
   "age": {
       "description": "Age in years",
       "type": "integer",
       "minimum": 0
    },
    "required": ["firstName", "lastName"]
}
~~~~


!SLIDE left

## Have our lives improved?

1. A time and database for all things.
2. Allowed us to bring up a datawarehouse with minimal coordination.
3. Easy experimentation with data streams.
4. (What else??)


!SLIDE left

## Learnings thus far

* Kafka bindings in Python are young.
* Don't plan ahead too far.
* Performance takes time, and perhaps Java.


!SLIDE

# Questions?


!SLIDE

## Rejected slides


!SLIDE

## What about "big data" problems?

>> When an increase of data, in quantity or kind,
>> causes your tools or approach to fail.


!SLIDE left

## Details on the components.

1. Simple HTTP interface.
2. [JSON Schema](http://json-schema.org/)
3. [Kafka](http://kafka.apache.org/)

