# Articles

## *MongoDB Aggregations*

* Pipeline
  * framework for data aggregation 
  * modeled on data processing pipelines
  * Stages:
    * 1st: `$match` filters documents by status field and passes to next stage - status must equal 'A'
    * 2nd: `$group` groups documents by `cust_id` - calculates sum of amount for each unique id
  * `db.collection.aggregate()` method and `aggregate` command run aggregation pipeline
* Pipeline Expressions
  * pipeline expressions can only operate on the current document in the pipeline
    * can't refer to data from other docs
  * expressions have a document structure and can contain other expression
  * expressions are stateless
    * except  accumulators (used in the $group stage) maintain their state
* Aggregation Pipeline Behavior
  * indexes can be used to improve pipeline performance
    * `$match` stage can use an index to filter documents if it occurs at the beginning of a pipeline
    * `$sort` stage can use an index as long as it is not preceded by a `$project`, `$unwind`, or `$group stage`
    * `$group` tage can sometimes use an index to find the first document in each group if all of the following criteria are met:
      * preceded by `$sort` stage
      * index on grouped field which matches sort order
      * only accumulator used in `$group` stage is `$first`
    * `$geoNear` pipeline operator takes advantage of a geospatial index
* Early Filtering
  * if your aggregation operation requires only a subset of the data in a collection, use the `$match`, `$limit`, and `$skip` stages to restrict the documents that enter at the beginning of the pipeline
  * placing `$match` pipeline stage before `$sort` stae at start of pipeline is equal to single query with sort and can use an index
  * when possible, place `$match` operators at beginning of pipeline
* Sharded Collections
  * aggregation pipeline supports operations
* Aggregation Pipeline vs Map-Reduce
  * aggregation pipeline provides better performance and a more coherent interface than `map-reduce`
  * `$group`, `$merge`, `$accumulator`, `$function`


## *Aggregations in MongoDB by Example*

* Aggregations are a set of functions that allow you to manipulate the data
* Steps:
  1) Call aggregate function on any collection
  1) Pipeline matches and filters out documents
  1) Group documents into subsets and perform operations across common fields