# Convert

```
SELECT TOP 1 PickupDate, CONVERT(DATE, PickupDate) AS DateOnly
FROM table
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
