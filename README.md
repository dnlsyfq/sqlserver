# Unicode Char

```
non‐standard characters like ♍? These are called Unicode characters


SELECT
  *
FROM User
WHERE Zodiac = N'♍';
```

# Introduction

```
SELECT TOP(10) *
FROM table

//restricting the percent of rows returned
SELECT TOP(10) PERCENT *
FROM table 
```

# LIKE 

```
SELECT
  *
FROM User
WHERE Name LIKE N'A%';
```

```
The underscore wildcard (_) replaces exactly one character. If a particular row has a Name of Catherine or Katherine, it will be returned by the query.

SELECT
  *
FROM User
WHERE Name LIKE N'_atherine';
```



# Convert




```
SELECT TOP 1 PickupDate, CONVERT(DATE, PickupDate) AS DateOnly
FROM table
```

```
SELECT
  -- Select the date portion of StartDate
  CONVERT(DATE, StartDate) as StartDate,
  -- Measure how many records exist for each StartDate
  COUNT(StartDate) as CountOfRows 
FROM CapitalBikeShare 
-- Group by the date portion of StartDate
GROUP BY CONVERT(DATE, StartDate)
-- Sort the results by the date portion of StartDate
ORDER BY CONVERT(DATE, StartDate);
```

# DatePart , Hours

```
SELECT
  TOP 3 COUNT(ID) AS NumberofRides,
  DATEPART(HOUR, PickupDate) AS Hour
FROM table
GROUP BY DATEPART(HOUR, PickupDate)
ORDER BY COUNT(ID) DESC
```



# DateName , Week

```
SELECT
  TOP 3 ROUND(
    SUM(FareAmount),
    0
  ) AS TotalFareAmt,
  DATENAME(WEEKDAY, PickupDate) AS DayofWeek
FROM table
GROUP BY DATENAME(WEEKDAY, PickupDate)
ORDER BY SUM(FareAmount) DESC;
```

# DateDiff

```
SELECT
  AVG(
    DATEDIFF(SECOND, PickupDate, DropOffDate)/60
  ) AS AvgRideLengthInMin
FROM table
WHERE DATENAME(WEEKDAY, PickupDate) = 'Sunday';
```
