!SLIDE

# Building Data Infrastructure

## Will Larson ([@lethain](https://twitter.com/Lethain))
## SocialCode ([@socialcodeinc](https://twitter.com/socialcodeinc))

!SLIDE largeimg

## When an increase...

![Showing teams, products and databases increasing over time.](imgs/when_an_increase.png)

!SLIDE left

## ...causes your tools or approach to break.

* Complex deployments.
* Tight coupling of components.
* Changes too complex to review.
* Team bottlenecks.


!SLIDE

## What about "big data" problems?

>> When an increase of data, in quantity or kind,
>> causes your tools or approach to fail.

!SLIDE left

## Monolithic data problems.

* Expensive schema changes.
* Data siloed by performance.
* Incompatible requirements.


!SLIDE left

## How to tame your data?

1. Embrace the silos?
2. Unify collection and storage?
3. Pipeline for sharing data?


!SLIDE largeimg

## A familiar monolith.

![Architecture diagram of monolithic architecture composed of a load balancer, Gunicorn web servers, MySQL, Redis and celery workers.](imgs/monolithic.png)


!SLIDE left

## One pipeline to facilitate them all.

1. Avoid datastore lock-in.
1. Decouple publishing and consumption.
2. Support cheap data exploration.
3. Fail rarely.
4. Fail loudly.
5. Facilitate schemas change.

!SLIDE largeimg

## Our solution today.

![A data pipeline, with services publishing into an input service, Kafka and Zooper between the input service and an output service, and datamarts subscribing to the output service.](imgs/pipeline_arch.png)


!SLIDE left

## Details on the components.

1. [Kafka](http://kafka.apache.org/)
2. [Zookeeper](http://zookeeper.apache.org/)
3. [JSON Schema](http://json-schema.org/)
4. HTTP servers
5. Datastore agnostic.


!SLIDE left

## Why Kafka?

1. Most important decision we made.
2. As easy as publish-subcribe,
3. With strong deliverability guarantees.
4. Data durability.
5. Horizontal scalability.


!SLIDE left

## Why Zookeeper?

1. It integrates well with Kafka out of the box.
2. It's fast.
3. It's simple to use.


!SLIDE left

## Why [JSON Schema](http://json-schema.org/) and HTTP?

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

## Why datastore agnostic?

1. Don't know what we don't know.
2. Variable access patterns and requirements.
3. Simple, dependable infrastructure.


!SLIDE left

## Learnings thus far

* Kafka bindings in Python are young.
* Don't plan ahead too far.
* Performance takes time, and perhaps Java.


!SLIDE

# Questions?
