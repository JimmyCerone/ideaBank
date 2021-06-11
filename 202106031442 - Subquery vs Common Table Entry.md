## Comparison
- On [[2021-06-03]] I was working on a query at work as part of [[FUS-2026 - Fix the Fulfilled Report]]. We fixed it up but it was still very slow because we were using [[202106031332 - Common Table Entry (CTE)]] instead of [[202106031440 - Subquery]]. In [[Head First SQL]] I learned that [[202106031440 - Subquery]] are slow, but apparently [[202106031332 - Common Table Entry (CTE)]] are even slower. 
- So a [[202106031440 - Subquery]] is a query within a query while a [[202106031332 - Common Table Entry (CTE)]] is a table you create before the rest of your query. Both allow you to break off chunks of #SQL into more understandable bits and both are slow but [[202106031332 - Common Table Entry (CTE)]] is slower because it requires creating a whole new table that is then queried. 

## Differences
1. CTEs can be recursive
	- Allows your CTE to call itself until a specified ending condition is met. 
2. CTEs are reusable
	- You can reuse this multiple times within a query and even alias it.


## Interoperability
- How can I swap out a common table entry for a subquery?
	- Seems to be the only direction things can go (i.e. you can't always swap a subquery out for a CTE)


Source: https://learnsql.com/blog/sql-subquery-cte-difference/