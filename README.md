# Pandas Pivot and Pivot Table

This repository provides an overview and explanation of the `pivot()` and `pivot_table()` functions in **pandas** for reshaping and organizing data. These functions are commonly used to transform data into a more convenient format for analysis.

## Table of Contents
- [pivot()](#pivot)
- [pivot_table()](#pivot_table)
- [Differences Between pivot() and pivot_table()](#differences-between-pivot-and-pivot_table)

## pivot()

The `pivot()` function is used to reshape data in pandas by turning unique values from one column into multiple columns in the new DataFrame. This is particularly useful when you want to "unstack" or reorganize your data into a more readable or usable format.

### Parameters:
- **`index`**: The column to use as the new row labels.
- **`columns`**: The column to use as the new column labels.
- **`values`**: The column whose values will be used to populate the new table.

### Key Points:
- `pivot()` is simple and works well when there are no duplicate combinations of the `index` and `columns`. 
- It cannot handle duplicate data and will raise an error if multiple rows exist for the same combination of index and column.

### Use Case:
If you have a DataFrame with columns for "Date", "City", and "Temperature", and you want to create a table where each city becomes a column and each date becomes a row, you can use `pivot()`. It will spread out the temperature values across the cities for each date.

---

## pivot_table()

The `pivot_table()` function is an extension of `pivot()` with more advanced functionality. It is useful when you have duplicate values and need to aggregate them. The `pivot_table()` function allows you to specify an aggregation function such as `mean`, `sum`, `count`, `max`, `min`, etc., to handle the data when duplicates are present.

### Parameters:
- **`values`**: The column whose values will be used to populate the new table.
- **`index`**: The column to use as the new row labels.
- **`columns`**: The column to use as the new column labels.
- **`aggfunc`**: The aggregation function to apply when there are duplicate values. By default, it is set to `'mean'`, but other options include `'sum'`, `'count'`, `'max'`, `'min'`, and more.
- **`fill_value`**: Optionally, you can set a value to replace missing values in the table (NaN).

### Key Points:
- `pivot_table()` can handle duplicates by applying an aggregation function, which makes it more flexible than `pivot()`.
- It is ideal for cases where you have multiple entries for the same combination of `index` and `columns` and need to calculate a summary statistic (e.g., average, sum, etc.).

### Use Case:
If you have data about the "Temperature" and "Humidity" for different cities and dates, you can use `pivot_table()` to calculate the average temperature and humidity for each city on each date. This will help you summarize the data without worrying about duplicate entries.

---

## Differences Between pivot() and pivot_table()

| Feature                     | `pivot()`                                  | `pivot_table()`                           |
|-----------------------------|--------------------------------------------|-------------------------------------------|
| **Handling Duplicates**      | Does not handle duplicates. Raises an error if there are duplicate combinations of index and columns. | Handles duplicates by applying an aggregation function (e.g., `mean`, `sum`, etc.). |
| **Aggregation**              | No aggregation capabilities.               | Supports aggregation functions to summarize duplicate data. |
| **Use Case**                 | Best for reshaping data with unique index-column combinations. | Best for reshaping data with possible duplicates that need aggregation. |
| **Flexibility**              | Less flexible in handling complex scenarios. | More flexible due to aggregation options. |

---

## Conclusion

Both `pivot()` and `pivot_table()` are powerful tools in pandas for reshaping data, but they serve different purposes. Use `pivot()` when your data is clean and does not have duplicates, and use `pivot_table()` when you need to handle duplicates and aggregate data effectively.
