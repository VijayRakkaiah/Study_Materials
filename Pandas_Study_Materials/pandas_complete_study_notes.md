# Python Pandas – Complete Study Notes with Code & Interview Q&A 📘

---

## 1. Importing Data

### Functions & Examples

```python
import pandas as pd

df = pd.read_csv('data.csv')
df = pd.read_table('data.txt')
df = pd.read_excel('data.xlsx')
df = pd.read_sql('SELECT * FROM table', conn)
df = pd.read_json('data.json')
df = pd.read_html('https://example.com')[0]
df = pd.read_clipboard()

df = pd.DataFrame({'A':[1,2], 'B':[3,4]})
```

### Interview Questions & Answers

**Q1. Difference between `read_csv()` and `read_table()`?**  
`read_csv()` is optimized for comma-separated files by default, while `read_table()` is more generic and expects tab-separated data unless specified.

**Q2. How do you read multiple Excel sheets?**  
Using `pd.read_excel('file.xlsx', sheet_name=None)` which returns a dictionary of DataFrames.

**Q3. How does `read_sql()` work internally?**  
It executes SQL queries through a database connection and converts the result into a Pandas DataFrame.

---

## 2. Exploring Data

### Attributes
```python
df.shape
df.size
df.dtypes
df.index
df.columns
```

### Viewing Data
```python
df.head()
df.tail()
df.sample(3)
df.info()
```

### Statistics
```python
df.describe()
df.mean()
df.median()
df.mode()
df.std()
df.var()
df.count()
df['col'].value_counts()
df['col'].nunique()
df['col'].unique()
```

### Interview Questions & Answers

**Q1. Difference between `shape` and `size`?**  
`shape` returns (rows, columns), while `size` returns total number of elements.

**Q2. What does `info()` show that `describe()` doesn’t?**  
`info()` shows data types, non-null counts, and memory usage.

**Q3. When do you use `value_counts()`?**  
To understand frequency distribution of categorical values.

---

## 3. Selecting Data

```python
df.loc[0:5, ['A','B']]
df.iloc[0:5, 0:2]
df[df['Age'] > 30]
df.select_dtypes(include='number')
```

### Interview Questions & Answers

**Q1. Difference between `loc` and `iloc`?**  
`loc` is label-based, `iloc` is position-based.

**Q2. What is boolean indexing?**  
Filtering data using conditions that return True/False.

**Q3. Can `iloc` accept column names?**  
No, it only works with integer positions.

---

## 4. Modifying Data

### Creating
```python
s = pd.Series([1,2,3])
df = pd.DataFrame({'A':[1,2]})
```

### Adding / Removing
```python
df.drop('A', axis=1)
df.pop('A')
df.assign(C=df['B']*2)
df.insert(1, 'D', [5,6])
```

### Combining
```python
pd.merge(df1, df2, on='id')
df1.join(df2)
pd.concat([df1, df2])
```

### Interview Questions & Answers

**Q1. Difference between `merge()` and `join()`?**  
`merge()` works like SQL joins on columns, `join()` joins on index by default.

**Q2. What happens if axis is not specified in `drop()`?**  
By default, rows are dropped (`axis=0`).

---

## 5. Cleaning Data

### Type & Value Handling
```python
df['Age'] = df['Age'].astype(int)
df.replace('NA', 0)
df.rename(columns={'old':'new'})
```

### Handling Missing Values
```python
df.isnull()
df.fillna(0)
df.dropna()
df.ffill()
df.bfill()
```

### Duplicates
```python
df.drop_duplicates()
```

### Interview Questions & Answers

**Q1. Difference between `fillna()` and `dropna()`?**  
`fillna()` replaces missing values, `dropna()` removes them.

**Q2. When is forward fill useful?**  
In time-series data where previous value is meaningful.

---

## 6. Analyzing Data

```python
df.sort_values('Age')
df.groupby('Dept')['Salary'].mean()
df.pivot_table(values='Sales', index='Year', columns='Region')
pd.melt(df, id_vars=['ID'])
df.query('Age > 30')
```

### Interview Questions & Answers

**Q1. Difference between `pivot()` and `pivot_table()`?**  
`pivot()` fails on duplicates; `pivot_table()` handles aggregation.

**Q2. Why is `groupby()` called split-apply-combine?**  
Data is split into groups, function applied, results combined.

---

## 7. Date-Time Management

```python
df['date'] = pd.to_datetime(df['date'])
df['year'] = df['date'].dt.year
pd.date_range('2024-01-01', periods=5)
df['date'] + pd.Timedelta(days=5)
```

### Interview Questions & Answers

**Q1. What is `.dt` accessor?**  
Used to extract datetime properties from datetime columns.

**Q2. Difference between `Timestamp` and `Timedelta`?**  
Timestamp represents a point in time; Timedelta represents duration.

---

## 8. Output & Saving

```python
df.to_csv('out.csv', index=False)
df.to_excel('out.xlsx')
df.to_json('out.json')
df.to_sql('table', conn)
```

### Interview Questions & Answers

**Q1. How do you avoid index while saving CSV?**  
Use `index=False`.

**Q2. Can Pandas write to databases?**  
Yes, using `to_sql()` with SQLAlchemy.

---

## 9. Special Features

```python
df['name'].str.lower()
df.plot()
df.style.highlight_max()
```

### Interview Questions & Answers

**Q1. What is `.str` accessor?**  
Provides vectorized string operations on Series.

**Q2. Does Pandas plotting require Matplotlib?**  
Yes, Pandas uses Matplotlib internally.

---

## 10. Final Interview Tips

- Focus on `groupby`, `merge`, `loc/iloc`, missing values
- Be ready to explain logic, not just syntax
- Practice EDA on real datasets

---

