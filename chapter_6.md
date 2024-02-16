# Chapter 6: Joining and Merging DataFrames

Joining DataFrames is a common operation in data processing that combines rows from two or more DataFrames based on a common column or condition. Spark supports various types of joins: inner, outer, left, right, and cross joins.

## Inner Join

An inner join combines rows from two DataFrames where the join condition is met.

### Scala Example

```scala
val employees = spark.createDataFrame(Seq(
  (1, "John Doe"),
  (2, "Jane Doe"),
  (3, "Mike Jones")
)).toDF("id", "name")

val departments = spark.createDataFrame(Seq(
  (1, "Engineering"),
  (2, "HR"),
  (3, "Marketing")
)).toDF("id", "dept")

val innerJoinDf = employees.join(departments, "id")
innerJoinDf.show()
```

### Python (PySpark) Example

```python
employees = spark.createDataFrame([
  (1, "John Doe"),
  (2, "Jane Doe"),
  (3, "Mike Jones")
], ["id", "name"])

departments = spark.createDataFrame([
  (1, "Engineering"),
  (2, "HR"),
  (3, "Marketing")
], ["id", "dept"])

innerJoinDf = employees.join(departments, "id")
innerJoinDf.show()
```

## Left Outer Join

A left outer join returns all rows from the left DataFrame, and the matched rows from the right DataFrame. The result is NULL on the right side if there is no match.

### Scala Example

```scala
val leftJoinDf = employees.join(departments, Seq("id"), "left_outer")
leftJoinDf.show()
```

### Python (PySpark) Example

```python
leftJoinDf = employees.join(departments, ["id"], "left_outer")
leftJoinDf.show()
```

## Right Outer Join

A right outer join returns all rows from the right DataFrame, and the matched rows from the left DataFrame. The result is NULL on the left side if there is no match.

### Scala Example

```scala
val rightJoinDf = employees.join(departments, Seq("id"), "right_outer")
rightJoinDf.show()
```

### Python (PySpark) Example

```python
rightJoinDf = employees.join(departments, ["id"], "right_outer")
rightJoinDf.show()
```

## Full Outer Join

A full outer join returns all rows when there is a match in either left or right DataFrame.

### Scala Example

```scala
val fullJoinDf = employees.join(departments, Seq("id"), "outer")
fullJoinDf.show()
```

### Python (PySpark) Example

```python
fullJoinDf = employees.join(departments, ["id"], "outer")
fullJoinDf.show()
```

## Cross Join

A cross join returns the Cartesian product of the rows from the two DataFrames.

### Scala Example

```scala
val crossJoinDf = employees.crossJoin(departments)
crossJoinDf.show()
```

### Python (PySpark) Example

```python
crossJoinDf = employees.crossJoin(departments)
crossJoinDf.show()
```

Join operations are powerful tools in DataFrame manipulation, allowing for the combination of data from different sources based on logical relationships. Understanding how to apply different types of joins correctly is crucial for effective data analysis.

---

This chapter provides a comprehensive overview of joining and merging DataFrames in Spark, covering the most common types of joins and their applications. These techniques are fundamental for data integration and analysis tasks, enabling the combination of disparate data sources into a coherent dataset for further analysis or reporting.
