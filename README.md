# MongoDb-String-Opeartors

## This repository is about string opeartors in MongoDb.

### What are String Opeartors in MongoDB?

#### In MongoDB, string operators are used to perform various operations on string values within documents. These operators are primarily used in queries, updates, and aggregation pipelines. Below is an overview of the key string operators in MongoDB:

### 1) `$concat`

#### Combines multiple strings into a single string.

```
db.collection.aggregate([
  { $project: { fullName: { $concat: ["$firstName", " ", "$lastName"] } } }
])
```

### 2) `$substr`

#### Extracts a substring from a string.

```
db.collection.aggregate([
  { $project: { shortName: { $substr: ["$fullName", 0, 5] } } }
])
```

### 3) `$toLower`

#### Converts a string to lowercase.

```
db.collection.aggregate([
  { $project: { lowerName: { $toLower: "$fullName" } } }
])
```

### 4) `$toUpper `

#### Converts a string to uppercase.

```
db.collection.aggregate([
  { $project: { upperName: { $toUpper: "$fullName" } } }
])
```

### 5) `$strcasecmp `

#### Compares two strings in a case-insensitive manner.

```
db.collection.find({ $expr: { $eq: [{ $strcasecmp: ["$name", "alice"] }, 0] } })
```

### 6) `$regex`

#### Performs a regular expression match on string fields.

```
db.collection.find({ name: { $regex: "^A" } })
```

- You can also add flags like i for case-insensitive search:

```
db.collection.find({ name: { $regex: "^a", $options: "i" } })
```

### 7) `$trim`

#### Removes leading and trailing whitespace characters from a string.

```
db.collection.aggregate([
  { $project: { cleanedName: { $trim: { input: "$name" } } } }
])
```

### 8) `$ltrim`

#### Removes leading whitespace from a string.

```
db.collection.aggregate([
  { $project: { noLeadingWhitespace: { $ltrim: { input: "$name" } } } }
])
```

### 9) `$rtrim `

#### Removes trailing whitespace from a string.

```
db.collection.aggregate([
  { $project: { noTrailingWhitespace: { $rtrim: { input: "$name" } } } }
])
```

### 10) `$split `

#### Splits a string into an array of substrings based on a delimiter.

```
db.collection.aggregate([
  { $project: { nameParts: { $split: ["$fullName", " "] } } }
])
```

### 11) `$indexOfBytes`

#### Splits a string into an array of substrings based on a delimiter.

```
db.collection.aggregate([
  { $project: { index: { $indexOfBytes: ["$description", "mongodb"] } } }
])
```

### 12) `$replaceAll `

#### Replaces all occurrences of a substring with another string.

```
db.collection.aggregate([
  { $project: { modifiedText: { $replaceAll: { input: "$text", find: "old", replace: "new" } } } }
])
```
