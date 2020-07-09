# MongoDB CLI

## Getting Started

The prompts below each ask for you to write the query in MongoDB for performing
some action (described in the prompt). Your response should be a valid query and
it should be property formatted in Markdown. For example:

**Prompt:** Find all burgers in the `burgers` collection.

```
db.burgers.find({})
```

### Instructions

* Start your `mongo` server
* Connect to the `mongo` shell

### Prompts

**Prompt:** What is the command to start the `mongo` server?

**Prompt:** What is the command to connect to the `mongo` shell?

**Prompt:** What is the command for listing all `mongo` databases?

**Prompt:** What command would you use to create a database called `burgers`?

**Prompt:** What command would you use to add the collection `burger` to your
`burgers` database?

**Prompt:** What is the command for listing all collections in a database?

## Inserting

### Prompts

**Prompt:** Insert a single burger into the `burgers` collection with the
following:

* a `patty` property set to `beef`
* a `cheese` property set to `false`
* a `toppings` set to an array with `ketchup`, `onions`, and `pickles`
```
db.burgers_db.insert([
        {
            "patty": "beef",
            "cheese": false, 
            "toppings": ["ketchup", "onions", "pickles"]
            }
        ]) 
``` 
**Prompt:** Insert 10 burgers into the `burgers` collection with the following:

* a `patty` property that is set to one of: `beef`, `turkey`, or `veggie`
* a `cheese` property that is either `true` or `false`
* a `toppings` property that is either one of `ketchup`, `onions`, `pickles`,
  `mustard`, and `mayonnaise`
```
db.burgers_db.insert([
            {
            "patty": "beef",
            "cheese": 'false', 
            "toppings": "mustard",
            },
            {
            "patty": "turkey",
            "cheese": 'true', 
            "toppings": "mayonnaise"
            }, 
            {
            "patty": "veggie",
            "cheese": 'false', 
            "toppings": "onions"
            },
            {
            "patty": "beef",
            "cheese": 'true', 
            "toppings": "ketchup",
            },
            {
            "patty": "beef",
            "cheese": 'false', 
            "toppings": "pickles",
            }, 
            {
            "patty": "turkey",
            "cheese": 'true', 
            "toppings": "pickles",
            }, 
            {
            "patty": "beef",
            "cheese": 'false', 
            "toppings": "onions",
            },
            {
            "patty": "beef",
            "cheese": 'false', 
            "toppings": "ketchup",
            },
            {
            "patty": "veggie",
            "cheese": 'false', 
            "toppings": "ketchup",
            },
            {
            "patty": "turkey",
            "cheese": 'false', 
            "toppings": "ketchup",
            }
        ]) 

``` 
## Reading

The following prompts will have you querying (reading) from your `burger`
collection. If you don't have burgers in your database that match the query
criteria described below, you wont get any results back. So, add one or two that
match that criteria before running the query.

### Prompts

**Prompt:** What query would find all burgers with a `beef` patty?
```
db.burgers_db.find({"patty": "beef"})
``` 
**Prompt:** What query would find all burgers with cheese on them?
```
db.burgers_db.find({"cheese": 'true'})
```
**Prompt:** What query would find a burger by it's ObjectId?
```
db.burgers_db.find({"_id": ObjectId("5f065254655a3699e46a7bc6")})
``` 
**Prompt:** What query would find all burgers with `ketchup` as a topping?
```
db.burgers_db.find({"toppings":"ketchup"})
```
**Prompt:** What query would find all burgers with either a turkey or veggie
patty?
```
db.burgers_db.find({ $or: [{"patty": "turkey"}, {"patty": "veggie"}]})
```
**Prompt:** What query would find all burgers with a beef patty and cheese?
```
db.burgers_db.find({ $and: [{"patty": "beef"}, {"cheese": "true"}]})
```
**Prompt:** What query would find all burgers with a beef patty and ketchup as
a topping?
```
db.burgers_db.find({ $and: [{"patty": "beef"}, {"toppings": "ketchup"}]})
```
**Prompt:** What query would find all burgers with a beef patty and both onions
and pickles as toppings?
```
db.burgers_db.find({ $and: [{"patty": "beef"}, {"toppings": "onions"}, {"toppings": "pickles"}]})
```
**Prompt:** What query would find burgers with either a turkey patty or cheese?
```
db.burgers_db.find({ $or: [{"patty": "turkey"}, {"cheese": "true"}]})
```
## Update

### Prompts

**Prompt:** What query would update one burger by it's ObjectId, setting it's
"patty" to "pork"?
```
db.burgers_db.updateOne({"_id": ObjectId("5f065254655a3699e46a7bc6")}, {$set: {"patty": "pork"}})
```

**Prompt:** What query would update all burgers with beef paddies to have
cheese? (i.e. set "cheese" to true)
```
db.burgers_db.updateMany({"patty": "beef"}, {$set: {"cheese": "true"}})
```
## Delete

### Prompts

**Prompt:** What query would delete a burger by it's ObjectId?
```
db.burgers_db.deleteOne({"_id": ObjectId("5f065254655a3699e46a7bc6")})
```
**Prompt:** What query would delete all veggie burgers?
```
db.burgers_db.deleteMany({"patty":"veggie"})
```
**Prompt:** What query would delete all burgers with pickles on them?
```
db.burgers_db.deleteMany({"toppings": "pickles"})
```