# Articles

## *Redis*

* Remote Dictionary Server
* Fast, open-source, in-memory key-value data store for use as a database, cache, message broker, and queue
* Delivers sub-millisecond response times enabling millions of requests per second for real-time applications
* All Redis data resides in-memory - not disk or SSD
* Avoid seek time delays and can access data in microseconds
* Data types include:
  * Strings
  * Lists
  * Sets
  * Sorted sets
  * Hashes
  * Bitmaps
  * HyperLogLogs
* Simplifies code by enabling you to write fewer lines of code to store, access, and use data in applications
* Storage used for:
  * Caching
  * Messaging
  * Game leaderboards
  * Session data
  * Media streaming
  * Geospatial
  * Machine learning
  * Real-time analytics


## *Queue*

* Common data structure that places elements in a sequence
* Uses FIFO method - First In First Out
* Basic operations
  * Enqueue() - inserts element to the end of the queue
  * Dequeue() - removes element from start of queue
  * isEmpty() - returns true if queue is empty
  * Top() - returns first element of queue


## *Bull*

* Node library that implements a fast and robust queue system based on Redis
* Public npm package:
  * `npm install bull --save`
  * Redis server must be running on localhost
*  Queue is created by instantiating a Bull instance:
  * `const myFirstQueue = new Bull('my-first-queue');`
* A queue instance can normally have 3 main different roles:
  * job producer
  * job consumer
  * events listener
* Queue can have many producers, many consumers, and many listeners 
* Producers can add jobs to a queue even if there are no consumers available at that moment
  * Provide asynchronous communication
* Workers consume jobs in a given order:
  * FIFO (default)
  * LIFO
### * Producers:
  * Node program that adds jobs to a queue
  * `const myFirstQueue = new Bull('my-first-queue'); 
  const job = await myFirstQueue.add({
  foo: 'bar'});`
### * Consumers (workers):
  *  Node program that defines a process function
  * `const myFirstQueue = new Bull('my-first-queue');
myFirstQueue.process(async (job) => {
  return doSomething(job.data);
});`
### * Listeners:
  * Listen to events that happen in the queue
    * Local:
      * will receive notifications produced in the given queue instance
    * Global:
      *  listen to all the events for a given queue
    * `const myFirstQueue = new Bull('my-first-queue');
// Define a local completed event
myFirstQueue.on('completed', (job, result) => {
  console.log(\`Job completed with result ${result}\`);})`
* Lifecycle of a Job:
  1) Job Added
  1) Wait or Delay
  1) Active
  1) Completed or Failed
  1) Job Finished
* Stalled Jobs
  * Job that is being processed but where process function has hanged
  * Can be retried by another idle worker or it can just move to the failed status
  * Avoid by making sure the process function does not keep Node event loop busy for too long
* Events:
  * Local:
    * queue instance (worker)
  * Global:
    * listen to all events
* Queue Options:
  * Rate Limiter
    * Create queues that limit the number of jobs processed in a unit of time
  * Named Jobs
    * Give names to jobs
    * Doesn't change mechanics of queue
  * Sandboxed Processors
    * Allows the worker to process several jobs in parallel
    * To avoid Bull stalling job when jobs are CPU intensive, run process functions in separate Node processes
* Job Types
  * FIFO - first in first out
    * Jobs are processed in the same order they are coming into the queue
  * LIFO - last in first out
    * Jobs are added to the beginning of the queue and will be processed as soon as the worker is idle
  * Delayed
    * Delay parameter means the minimum amount of time the job will wait before being processed
  * Prioritized
    * Added to a queue with a priority value
    * High priority (1) before low priority processed
  * Repeatable
    * Repeat themselves indefinitely or until a given maximum date or the number of repetitions has been reached
    * Important:
      * Won't add the same repeatable job if options are the same
      * If there are no workers running, repeatable jobs will not accumulate next time a worker is online
      * Can be removed using the removeRepeatable method
