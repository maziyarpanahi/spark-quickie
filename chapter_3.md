# Chapter 3: Creating Spark DataFrames

Creating Spark DataFrames is a fundamental skill, as they serve as the primary data structure for data manipulation and analysis in Spark. This chapter covers creating DataFrames from collections and reading data from files.

## Creating DataFrames from Collections

DataFrames can be created from existing collections in Scala or Python, which is useful for testing and experimentation.

### Scala Example

```scala
import spark.implicits._

// Creating a DataFrame from a Seq
val df = Seq(
  ("Alice", 1),
  ("Bob", 2),
  ("Cathy", 3)
).toDF("name", "id")

df.show()
```

### Python (PySpark) Example

```python
# Creating a DataFrame from a list
df = spark.createDataFrame(
  [("Alice", 1), ("Bob", 2), ("Cathy", 3)],
  ["name", "id"]
)

df.show()
```

In these examples, we create DataFrames from collections with specified column names.

## Reading Data from Files

Spark supports reading data from various file formats, including CSV, JSON, and Parquet. Below are examples of how to read these formats into DataFrames.

### Reading CSV Files

#### Scala Example

```scala
val dfCsv = spark.read
  .option("header", "true")
  .option("inferSchema", "true")
  .csv("path/to/your/csvfile.csv")

dfCsv.show()
```

#### Python (PySpark) Example

```python
dfCsv = spark.read \
  .option("header", "true") \
  .option("inferSchema", "true") \
  .csv("path/to/your/csvfile.csv")

dfCsv.show()
```

### Reading JSON Files

#### Scala Example

```scala
val dfJson = spark.read
  .option("multiline", "true")
  .json("path/to/your/jsonfile.json")

dfJson.show()
```

#### Python (PySpark) Example

```python
dfJson = spark.read \
  .option("multiline", "true") \
  .json("path/to/your/jsonfile.json")

dfJson.show()
```

### Reading Parquet Files

#### Scala Example

```scala
val dfParquet = spark.read.parquet("path/to/your/parquetfile.parquet")

dfParquet.show()
```

#### Python (PySpark) Example

```python
dfParquet = spark.read.parquet("path/to/your/parquetfile.parquet")

dfParquet.show()
```

In these examples, we use `spark.read` followed by an `option` method to specify reading parameters such as `header` and `inferSchema` for CSV files, or `multiline` for JSON files. The `csv`, `json`, and `parquet` methods are used to read data from files in the respective formats.

Creating and reading DataFrames are foundational skills in Spark. With these capabilities, you can begin to perform more complex data manipulation and analysis tasks.

---

This chapter introduces the basics of creating and initializing DataFrames from both collections and external data sources, providing a solid foundation for exploring more advanced DataFrame operations and transformations.
