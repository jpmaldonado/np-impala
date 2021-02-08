# Exercise

1. Create a new database, `stocks` and two tables from the `sp500` files. Import the date column as `timestamp`.
2. Generate a table that shows the following info (sample)>

| Symbol | Name | Max WClose | Min WClose  | Avg WClose |
|--------|--------|--------|--------|--------|--------|
| APPL | Apple | 12 | 8 | 10 |

WClose is the weighted average closing price `sum(Close*Volume)/Volume.`
3. Calculate the stocks that have "momentum" (10-day average close is higher than historical average).