## TODO

- [x] Experiment with adding a test in the Record Repository's find method to see if it grabs a future product that has been published. 
	- [x] We should see that the version fields are not there, but that we have what we need.n

# Option 1 - ONE WE CHOSE
- Adjust base find method to return a skeleton of the record (just the header) that we don't expect to change over time. If there is versioned info, it will return that. Otherwise it will return blank. 
	- For items that are effective in the future, we will set their status to preliminary (hard coded in resolver)

# Option 2
- In the resolver set the effective date far into the future which will capture most every item we'd need. 

![[Screen Shot 2021-05-03 at 9.54.17 AM.png]]


## Questions
- Do we want to do this on the domain layer? 
- How would option 1 change the insert and update function on the records? 
	- We have been assuming that master always has a record.
- What does it mean to have a record with no version?
	- In our import process we'd bring something in that has no version because we wouldn't set the status which lives on the version table. 
	- Most of the times we'd create a product, we'd want to create on that isn't versioned. 
		- What happens when we do want to set the status? 
- What does our lens do if we see something with a future effective date in a sandbox?
	- If we have it for a future effective date for a sandbox and no record on master, we still want to return the attributes on the overlay record.


## Progress from [[2021-05-03]]
- Worked on the SQL code, couldn't get all of it to work but got some of it to work: 
	- `AND(overlay. "effectiveDateTimeRange" @> $2::timestamptz
		OR(NOT EXISTS (
				SELECT
					1 FROM "ProductVersion" version
				WHERE
					version. "headerId" = overlay.id)))`
	- The where exists part was particularly troublesome, TablePlus did not like the WHERE at all...
		- `AND(overlay. "effectiveDateTimeRange" @> $2::timestamptz
		OR(NOT EXISTS (
				SELECT
					1 FROM "ProductVersion" version
				WHERE
					version. "headerId" = overlay.id))
			AND(
WHERE
				EXISTS (selects 1 FROM "ProductVersion" version
				WHERE
					version. "headerId" = overlay.id)))`