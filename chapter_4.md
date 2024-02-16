# Chapter 4: Understanding DataFrame Operations

DataFrame operations can be categorized into transformations and actions. Transformations create a new DataFrame from an existing one, while actions trigger computation and return results. Let's explore some basic operations to manipulate and understand our data better.

## Displaying Data and Schema

To inspect our data and understand its structure, we can display the contents of a DataFrame and view its schema.

### Scala Example

```scala
// Assuming df is an existing DataFrame
df.show()
df.printSchema()
```

### Python (PySpark) Example

```python
# Assuming df is an existing DataFrame
df.show()
df.printSchema()
```

`show()` action displays the top rows of the DataFrame, and `printSchema()` prints the schema, showing the column names and data types.

## Basic DataFrame Transformations

### Selecting Columns

You can select specific columns from a DataFrame.

#### Scala Example

```scala
df.select("name", "age").show()
```

#### Python (PySpark) Example

```python
df.select("name", "age").show()
```

### Filtering Rows

Filtering allows you to select rows that meet certain criteria.

#### Scala Example

```scala
df.filter($"age" > 18).show()
```

#### Python (PySpark) Example

```python
df.filter(df.age > 18).show()
```

### Adding Columns

You can add new columns to a DataFrame.

#### Scala Example

```scala
df.withColumn("agePlusOne", $"age" + 1).show()
```

#### Python (PySpark) Example

```python
df.withColumn("agePlusOne", df.age + 1).show()
```

### Renaming Columns

Renaming columns can help in making DataFrame more readable.

#### Scala Example

```scala
df.withColumnRenamed("age", "userAge").show()
```

#### Python (PySpark) Example

```python
df.withColumnRenamed("age", "userAge").show()
```

## Aggregations and Grouping Data

Aggregations are used to compute summary statistics for groups of data.

### Scala Example

```scala
df.groupBy("department").agg(avg("salary"), max("age")).show()
```

### Python (PySpark) Example

```python
from pyspark.sql import functions as F
df.groupBy("department").agg(F.avg("salary"), F.max("age")).show()
```

In these examples, we've seen how to perform basic DataFrame operations such as selecting, filtering, adding, and renaming columns, as well as performing aggregations on groups of data. These operations form the building blocks for data analysis and manipulation in Spark.

---

This chapter provides a foundation for working with DataFrames in Spark, demonstrating how to inspect, transform, and summarize data. The examples illustrate essential operations that are applicable to a wide range of data processing tasks.
