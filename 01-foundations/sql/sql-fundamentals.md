# SQL Fundamentals

SQL is a must-have skill for data engineers. They use the querying language to perform essential tasks like modeling data, extracting performance metrics, and developing reusable data structures.

Data engineer SQL questions tend to mirror the work that engineers do.

Therefore, data engineers need to be proficient not just in querying data and pulling metrics, but also in data structures, manipulation and security within SQL. Broadly, a data engineer may face SQL questions in these categories:

- SQL queries - Using SQL data query language (DQL) statements to pull metrics and analyze data. Commands to know: SELECT
- Data modeling - Using DDL commands to create database schema and define data structures. Commands to know: CREATE, ALTER, DROP, RENAME, TRUNCATE, COMMENT
- Data manipulation - Using DML statements to retrieve and manipulate data. Commands to know: INSERT, UPDATE, DELETE, MERGE, CALL, EXPLAIN PLAN, LOCK TABLE
- Data security - Using DCL (data control language) commands to manage database security. Commands to know: GRANT, REVOKE

This data engineering SQL questions guide provides an overview of the types of questions you might face, as well as an example data engineer interview questions to help you prepare for your interview.

Watch this video: https://www.youtube.com/embed/AK7_m-aThfw

[This](https://techtfq.com/blog/top-20-sql-interview-questions) is the blog link for the above video.

## Basics

### SQL SELECT

There are two required ingredients in any SQL query: `SELECT` and `FROM`---and they have to be in that order. `SELECT` indicates which columns you'd like to view, and `FROM` identifies the table that they live in.

### SQL LIMIT

As you might expect, the limit restricts how many rows the SQL query returns.

**Why should you limit your results?**

Many analysts use limits as a simple way to keep their queries from taking too long to return. The aim of many of your queries will simply be to see what a particular table looks like—you'll want to scan the first few rows of data to get an idea of which fields you care about and how you want to manipulate them. If you query a very large table (such as one with hundreds of thousands or millions of rows) and don't use a limit, you could end up waiting a long time for all of your results to be displayed, which doesn't make sense if you only care about the first few.

### SQL WHERE

Once you know how to view some data using SELECT and FROM, the next step is filtering the data using the WHERE clause.

### SQL Comparison Operators

**Comparison operators on numerical data**

The most basic way to filter data is using comparison operators. The easiest way to understand them is to start by looking at a list of them:

| Equal to                 | `=`              |
| ------------------------ | ------------------ |
| Not equal to             | `<>` or `!=` |
| Greater than             | `>`              |
| Less than                | `<`              |
| Greater than or equal to | `>=`             |
| Less than or equal to    | `<=`             |

These comparison operators make the most sense when applied to numerical columns.

**Comparison operators on non-numerical data**

All of the above operators work on non-numerical data as well. `=` and `!=` make perfect sense—they allow you to select rows that match or don't match any value, respectively.

There are some important rules when using these operators, though. If you're using an operator with values that are non-numeric, you need to put the value in single quotes: 'value'.

You can use `>`, `<`, and the rest of the comparison operators on non-numeric columns as well---they filter based on alphabetical order.

If you're using `>`, `<`, `>=`, or `<=`, you don't necessarily need to be too specific about how you filter.

**Arithmetic in SQL**

You can perform arithmetic in SQL using the same operators you would in Excel: `+`, `-`, `*`, `/`. However, in SQL you can only perform arithmetic across columns on values in a given row. To clarify, you can only add values in multiple columns *from the same row* together using `+`---if you want to add values across multiple rows, you'll need to use aggregate functions.

The columns that contain the arithmetic functions are called "derived columns" because they are generated by modifying the information that exists in the underlying data.

As in Excel, you can use parentheses to manage the order of operations.

It occasionally makes sense to use parentheses even when it's not absolutely necessary just to make your query easier to read.

### SQL Logical Operators

You'll likely also want to filter data using several conditions---possibly more often than you'll want to filter by only one condition. Logical operators allow you to use multiple comparison operators in one query.

Each logical operator is a special snowflake, so we'll go through them individually in the following lessons. Here's a quick preview:

- `LIKE` allows you to match similar values, instead of exact values.
- `IN` allows you to specify a list of values you'd like to include.
- `BETWEEN` allows you to select only rows within a certain range.
- `IS NULL` allows you to select rows that contain no data in a given column.
- `AND` allows you to select only rows that satisfy two conditions.
- `OR` allows you to select rows that satisfy either of two conditions.
- `NOT` allows you to select rows that do not match a certain condition.

### SQL LIKE

LIKE is a logical operator in SQL that allows you to match on similar values rather than exact ones.

### SQL IN

IN is a logical operator in SQL that allows you to specify a list of values that you'd like to include in the results.

As with comparison operators, you can use non-numerical values, but they need to go inside single quotes. Regardless of the data type, the values in the list must be separated by commas.

### SQL BETWEEN

BETWEEN is a logical operator in SQL that allows you to select only rows that are within a specific range.

### SQL IS NULL

IS NULL is a logical operator in SQL that allows you to exclude rows with missing data from your results.

Some tables contain null values—cells with no data in them at all. This can be confusing for heavy Excel users, because the difference between a cell having no data and a cell containing a space isn't meaningful in Excel. In SQL, the implications can be pretty serious.

You can select rows that contain no data in a given column by using IS NULL.

### SQL AND

AND is a logical operator in SQL that allows you to select only rows that satisfy two conditions.

You can use SQL's AND operator with additional AND statements or any other comparison operator, as many times as you want.

### SQL OR

OR is a logical operator in SQL that allows you to select rows that satisfy either of two conditions. It works the same way as AND, which selects the rows that satisfy both of two conditions.

You can combine AND with OR using parenthesis.

### SQL NOT

NOT is a logical operator in SQL that you can put before any conditional statement to select rows for which that statement is false.

NOT is commonly used with LIKE.

NOT is also frequently used to identify non-null rows, but the syntax is somewhat special—you need to include IS beforehand.

### SQL ORDER BY

The ORDER BY clause allows you to reorder your results based on the data in one or more columns.

You can also order by mutiple columns. This is particularly useful if your data falls into categories and you'd like to organize rows by date, for example, but keep all of the results within a given category together.

When using ORDER BY with a row limit (either through the check box on the query editor or by typing in LIMIT), the ordering clause is executed first. This means that the results are ordered before limiting to only a few rows.

### Comments

You can "comment out" pieces of code by adding combinations of characters. In other words, you can specify parts of your query that will not actually be treated like SQL code. It can be helpful to include comments that explain your thinking so that you can easily remember what you intended to do if you ever want to revisit your work. Commenting can also be useful if you want to test variations on your query while keeping all of your code intact.

You can use-- (two dashes) to comment out everything to the right of them on a given line.

You can also leave comments across multiple lines using /* to begin the comment and */ to close it.

## Intermediate

### SQL Aggregate Functions

SQL is excellent at aggregating data the way you might in a pivot table in Excel. You will use aggregate functions all the time, so it's important to get comfortable with them. The functions themselves are the same ones you will find in Excel or any other analytics program.

- COUNT counts how many rows are in a particular column.
- SUM adds together all the values in a particular column.
- MIN and MAX return the lowest and highest values in a particular column, respectively.
- AVG calculates the average of a group of selected values.

### SQL COUNT

COUNT is a SQL aggregate function for counting the number of rows in a particular column. COUNT is the easiest aggregate function to begin with because verifying your results is extremely simple.

Things start to get a little bit tricky when you want to count individual columns.

One nice thing about COUNT is that you can use it on non-numerical columns.

### SQL SUM

SUM is a SQL aggregate function. that totals the values in a given column. Unlike COUNT, you can only use SUM on columns containing numerical values.

### SQL MIN/MAX

MIN and MAX are SQL aggregation functions that return the lowest and highest values in a particular column.

They're similar to COUNT in that they can be used on non-numerical columns. Depending on the column type, MIN will return the lowest number, earliest date, or non-numerical value as close alphabetically to "A" as possible. As you might suspect, MAX does the opposite—it returns the highest number, the latest date, or the non-numerical value closest alphabetically to "Z."

### SQL AVG

AVG is a SQL aggregate function that calculates the average of a selected group of values. It's very useful, but has some limitations. First, it can only be used on numerical columns. Second, it ignores nulls completely.

### SQL GROUP BY

SQL aggregate function like COUNT, AVG, and SUM have something in common: they all aggregate across the entire table. But what if you want to aggregate only part of a table? For example, you might want to count the number of entries for each year.

In situations like this, you'd need to use the GROUP BY clause. GROUP BY allows you to separate data into groups, which can be aggregated independently of one another.

You can group by multiple columns, but you have to separate column names with commas—just as with ORDER BY).

As with ORDER BY, you can substitute numbers for column names in the GROUP BY clause. It's generally recommended to do this only when you're grouping many columns, or if something else is causing the text in the GROUP BY clause to be excessively long.

The order of column names in your GROUP BY clause doesn't matter—the results will be the same regardless. If you want to control how the aggregations are grouped together, use ORDER BY.

### SQL HAVING

You'll often encounter datasets where GROUP BY isn't enough to get what you're looking for. Let's say that it's not enough just to know aggregated stats by month. After all, there are a lot of months in this dataset. Instead, you might want to find every month during which AAPL stock worked its way over $400/share. The WHERE clause won't work for this because it doesn't allow you to filter on aggregate columns—that's where the HAVING clause comes in.

### Query clause order

The order in which you write the clauses is important. Here's the order for everything you've learned so far:

1. SELECT
2. FROM
3. WHERE
4. GROUP BY
5. HAVING
6. ORDER BY
7. LIMIT

### SQL CASE

The CASE statement is SQL's way of handling if/then logic. The CASE statement is followed by at least one pair of WHEN and THEN statements—SQL's equivalent of IF/THEN in Excel. Because of this pairing, you might be tempted to call this SQL CASE WHEN, but CASE is the accepted term.

Every CASE statement must end with the END statement. The ELSE statement is optional, and provides a way to capture values not specified in the WHEN/THEN statements.

You can also define a number of outcomes in a CASE statement by including as many WHEN/THEN statements as you'd like.

You can also string together multiple conditional statements with AND and OR the same way you might in a WHERE clause.

CASE's slightly more complicated and substantially more useful functionality comes from pairing it with aggregate functions. For example, let's say you want to only count rows that fulfill a certain condition. Since COUNT ignores nulls, you could use a CASE statement to evaluate the condition and produce null or non-null values depending on the outcome.

Combining CASE statements with aggregations can be tricky at first. It's often helpful to write a query containing the CASE statement first and run it on its own.

### SQL DISTINCT

You'll occasionally want to look at only the unique values in a particular column. You can do this using SELECT DISTINCT syntax.

DISTINCT can be particularly helpful when exploring a new data set. In many real-world scenarios, you will generally end up writing several preliminary queries in order to figure out the best approach to answering your initial question. Looking at the unique values on each column can help identify how you might want to group or filter the data.

You can use DISTINCT when performing an aggregation. You'll probably use it most commonly with the COUNT function.

It's worth noting that using DISTINCT, particularly in aggregations, can slow your queries down quite a bit.

### SQL Joins

It might be helpful to refer to this JOIN visualization by Patrik Spathon.

[![](https://user-images.githubusercontent.com/62965911/213920018-c8eece0a-b772-40f6-85bd-f6c0159f903e.png)](https://joins.spathon.com/)

Let's say we want to figure out which conference has the highest average weight. Given that information is in two separate tables, how do you do that? A join!

```sql
SELECT teams.conference AS conference,
    AVG(players.weight) AS average_weight
FROM college_football_players players
    JOIN college_football_teams teams ON teams.school_name = players.school_name
GROUP BY teams.conference
ORDER BY AVG(players.weight) DESC
```

### SQL INNER JOIN

Returns only the rows from both the dataframes that have matching values in both columns specified as the join keys. In mathematical terms, an inner join is the intersection of the two tables.

### SQL LEFT/LEFT OUTER JOIN

Returns all the rows from the left dataframe and the matching rows from the right dataframe. If there are no matching values in the right dataframe, then it returns a null.

### SQL RIGHT/RIGHT OUTER JOIN

Returns all the rows from the right dataframe and the matching rows from the left dataframe. If there are no matching values in the left dataframe, then it returns a null.

### SQL OUTER/FULL JOIN

Returns all the rows from both the dataframes, including the matching and non-matching rows. If there are no matching values, then the result will contain a NULL value in place of the missing data.

### SQL CROSS JOIN

Returns all possible combinations of rows from both the dataframes. In other words, it takes every row from one dataframe and matches it with every row in the other dataframe. The result is a new dataframe with all possible combinations of the rows from the two input dataframes.

A cross-join is used when we want to perform a full outer join but in a more computationally efficient manner. Cross joins are not recommended for large datasets as they can produce a very large number of records, leading to memory issues and poor performance.

### SQL LEFT ANTI JOIN

A left anti join is a type of left join operation that returns only the rows from the left dataframe that do not have matching values in the right dataframe. It is used to find the rows in one dataframe that do not have corresponding values in another dataframe.

The result of a left anti join is a dataframe that contains only the rows from the left dataframe that do not have matching values in the right dataframe. If a row from the left dataframe has matching values in the right dataframe, it will not be included in the result.

### SQL SELF JOIN

A self join is a join operation in which a dataframe is joined with itself. It is used to compare the values within a single dataframe and return the rows that match specified criteria.

For example, a self join could be used to find all pairs of rows in a dataframe where the values in two columns are equal. The result would be a new dataframe that contains only the rows that meet the specified criteria.

### SQL UNION

SQL joins allow you to combine two datasets side-by-side, but UNION allows you to stack one dataset on top of the other. Put differently, UNION allows you to write two separate SELECT statements, and to have the results of one statement display in the same table as the results from the other statement.

SQL has strict rules for appending data:

- Both tables must have the same number of columns
- The columns must have the same data types in the same order as the first table

While the column names don't necessarily have to be the same, you will find that they typically are. This is because most of the instances in which you'd want to use UNION involve stitching together different parts of the same dataset.

## Advanced

### SQL Date Format

Assuming you've got some dates properly stored as a date or time data type, you can do some pretty powerful things. Maybe you'd like to calculate a field of dates a week after an existing field. Or maybe you'd like to create a field that indicates how many days apart the values in two other date fields are. These are trivially simple, but it's important to keep in mind that the data type of your results will depend on exactly what you are doing to the dates.

When you perform arithmetic on dates (such as subtracting one date from another), the results are often stored as the interval data type—a series of integers that represent a period of time.

### Using SQL String Functions to Clean Data

**LEFT, RIGHT, and LENGTH**

You can use LEFT to pull a certain number of characters from the left side of a string and present them as a separate string. The syntax is LEFT(string, number of characters).

When using functions within other functions, it's important to remember that the innermost functions will be evaluated first, followed by the functions that encapsulate them.

**TRIM**

The TRIM function is used to remove characters from the beginning and end of a string.

The TRIM function takes 3 arguments. First, you have to specify whether you want to remove characters from the beginning ('leading'), the end ('trailing'), or both ('both', as used above). Next you must specify all characters to be trimmed. Any characters included in the single quotes will be removed from both beginning, end, or both sides of the string. Finally, you must specify the text you want to trim using FROM.

**POSITION**

POSITION allows you to specify a substring, then returns a numerical value equal to the character number (counting from left) where that substring first appears in the target string.

Importantly, POSITION function is case-sensitive. If you want to look for a character regardless of its case, you can make your entire string a single by using the UPPER or LOWER functions.

**SUBSTR**

LEFT and RIGHT both create substrings of a specified length, but they only do so starting from the sides of an existing string. If you want to start in the middle of a string, you can use SUBSTR. The syntax is SUBSTR(*string*, *starting character position*, *# of characters*):

**CONCAT**

You can combine strings from several columns together (and with hard-coded values) using CONCAT. Simply order the values you want to concatenate and separate them with commas. If you want to hard-code values, enclose them in single quotes.

**Changing case with UPPER and LOWER**

Sometimes, you just don't want your data to look like it's screaming at you. You can use LOWER to force every character in a string to become lower-case. Similarly, you can use UPPER to make all the letters appear in upper-case:

**Turning strings into dates**

Dates are some of the most commonly screwed-up formats in SQL. This can be the result of a few things:

- The data was manipulated in Excel at some point, and the dates were changed to MM/DD/YYYY format or another format that is not compliant with SQL's strict standards.
- The data was manually entered by someone who use whatever formatting convention he/she was most familiar with.
- The date uses text (Jan, Feb, etc.) instead of numbers to record months.

In order to take advantage of all of the great date functionality, you need to have your date field formatted appropriately. This often involves some text manipulation, followed by a CAST.

**Turning dates into more useful dates**

Once you've got a well-formatted date field, you can manipulate in all sorts of interesting ways.

What if you want to include today's date or time? You can instruct your query to pull the local date and time at the time the query is run using any number of functions. Interestingly, you can run them without a FROM clause:

**COALESCE**

Occasionally, you will end up with a dataset that has some nulls that you'd prefer to contain actual values. This happens frequently in numerical data (displaying nulls as 0 is often preferable), and when performing outer joins that result in some unmatched rows. In cases like this, you can use COALESCE to replace the null values:

### SQL Subqueries

Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps. For example, if you wanted to take the sums of several columns, then average all of those values, you'd need to do each aggregation in a distinct step.

Subqueries can be used in several places within a query, but it's easiest to start with the FROM statement.

Subqueries are required to have names, which are added after parentheses the same way you would add an alias to a normal table.

A quick note on formatting: The important thing to remember when using subqueries is to provide some way for the reader to easily determine which parts of the query will be executed together. Most people do this by indenting the subquery in some way.

### SQL Window Functions

A window function performs a calculation across a set of table rows that are somehow related to the current row. This is comparable to the type of calculation that can be done with an aggregate function. But unlike regular aggregate functions, use of a window function does not cause rows to become grouped into a single output row — the rows retain their separate identities. Behind the scenes, the window function is able to access more than just the current row of the query result.

If you'd like to narrow the window from the entire dataset to individual groups within the dataset, you can use PARTITION BY to do so.

Note: You can't use window functions and standard aggregations in the same query. More specifically, you can't include window functions in a GROUP BY clause.

**The usual suspects: SUM, COUNT, and AVG**

When using window functions, you can apply the same aggregates that you would under normal circumstances—SUM, COUNT, and AVG.

**ROW_NUMBER()**

ROW_NUMBER() does just what it sounds like—displays the number of a given row. It starts with 1 and numbers the rows according to the ORDER BY part of the window statement. ROW_NUMBER() does not require you to specify a variable within the parentheses.

Using the PARTITION BY clause will allow you to begin counting 1 again in each partition. The following query starts the count over again for each terminal:

**RANK() and DENSE_RANK()**

RANK() is slightly different from ROW_NUMBER().

You can also use DENSE_RANK() instead of RANK() depending on your application. Imagine a situation in which three entries have the same value. Using either command, they will all get the same rank.

**NTILE**

You can use window functions to identify what percentile (or quartile, or any other subdivision) a given row falls into. The syntax is NTILE(*# of buckets*). In this case, ORDER BY determines which column to use to determine the quartiles (or whatever number of 'tiles you specify). For example:

**LAG and LEAD**

It can often be useful to compare rows to preceding or following rows, especially if you've got the data in an order that makes sense. You can use LAG or LEAD to create columns that pull values from other rows—all you need to do is enter which column to pull from and how many rows away you'd like to do the pull. LAG pulls from previous rows and LEAD pulls from following rows.

This is especially useful if you want to calculate differences between rows.

**Defining a window alias**

If you're planning to write several window functions in to the same query, using the same window, you can create an alias.

The WINDOW clause, if included, should always come after the WHERE clause.

### Performance Tuning SQL Queries

SQL tuning is the process of improving SQL queries to accelerate your servers performance. It's general purpose is to reduce the amount of time it takes a user to receive a result after issuing a query, and to reduce the amount of resources used to process a query.

A database is a piece of software that runs on a computer, and is subject to the same limitations as all software---it can only process as much information as its hardware is capable of handling. The way to make a query run faster is to reduce the number of calculations that the software (and therefore hardware) must perform. To do this, you'll need some understanding of how SQL actually makes calculations. First, let's address some of the high-level things that will affect the number of calculations you need to make, and therefore your querys runtime:

- Table size: If your query hits one or more tables with millions of rows or more, it could affect performance.
- Joins: If your query joins two tables in a way that substantially increases the row count of the result set, your query is likely to be slow.
- Aggregations: Combining multiple rows to produce a result requires more computation than simply retrieving those rows.

Query runtime is also dependent on some things that you can't really control related to the database itself:

- Other users running queries: The more queries running concurrently on a database, the more the database must process at a given time and the slower everything will run. It can be especially bad if others are running particularly resource-intensive queries that fulfill some of the above criteria.
- Database software and optimization: This is something you probably can't control, but if you know the system you're using, you can work within its bounds to make your queries more efficient.

**Reducing table size**

Filtering the data to include only the observations you need can dramatically improve query speed. How you do this will depend entirely on the problem you're trying to solve. For example, if you've got time series data, limiting to a small time window can make your queries run much more quickly:

```sql
SELECT *
  FROM sample_event_table
 WHERE event_date >= '2014-03-01'
   AND event_date <  '2014-04-01'
```

Keep in mind that you can always perform exploratory analysis on a subset of data, refine your work into a final query, then remove the limitation and run your work across the entire dataset. The final query might take a long time to run, but at least you can run the intermediate steps quickly.

This is why we enforces a LIMIT clause by default—100 rows is often more than you need to determine the next step in your analysis, and it's a small enough dataset that it will return quickly.

It's worth noting that LIMIT doesn't quite work the same way with aggregations—the aggregation is performed, then the results are limited to the specified number of rows. So if you're aggregating into one row as below, LIMIT 100 will do nothing to speed up your query:

```sql
SELECT COUNT(*)
  FROM sample_event_table
 LIMIT 100
```

If you want to limit the dataset before performing the count (to speed things up), try doing it in a subquery:

```sql
SELECT COUNT(*)
  FROM (
    SELECT *
      FROM sample_event_table
     LIMIT 100
       ) sub
```

Note: Using LIMIT this will dramatically alter your results, so you should use it to test query logic, but not to get actual results.

In general, when working with subqueries, you should make sure to limit the amount of data you're working with in the place where it will be executed first. This means putting the LIMIT in the subquery, not the outer query. Again, this is for making the query run fast so that you can test—NOT for producing good results.

**EXPLAIN**

You can add EXPLAIN at the beginning of any (working) query to get a sense of how long it will take. It's not perfectly accurate, but it's a useful tool.

Congratulations!
