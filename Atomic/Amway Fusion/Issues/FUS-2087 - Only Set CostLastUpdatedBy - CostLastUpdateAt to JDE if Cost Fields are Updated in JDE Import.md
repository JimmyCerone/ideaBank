# Fixing Future Imports
- Update Tests: 
	- `modules/import-export/jde-integrator/__tests__/source-to-market-item-revision-importer.test.ts`
	- Not sure how I want to update these, it's been a long time since I touched them...
		- https://github.com/AmwayEFS/fusion-platform/pull/1406/files

# Remediation of Old MIRS

## Steps
-  In the _source-to-market-item-revision-importer_ file, remove lines 67 and 68, which are as follows:

	- `costLastUpdatedBy: 'jde' as const, costLastUpdatedAt: DateTimeIso.now()`
- Correct the versions that were set with wrong sourcing information. For these two fields, find the latest version (v) that was not JDE and apply those two values to all versions after that version (v).
	- So far as I can tell, there are 88K rows of incorrectly set items. Not sure how to find the previous versions, maybe by checking effective date? To simply find entries with `costLastUpdatedBy` as `jde`, use the query below: 
		 ```
		 SELECT *	
	     FROM
			"MarketItemRevisionVersion" mirv
		 WHERE
			mirv. "costLastUpdatedBy" = 'jde';
		```
		
	## Next Steps
	- I think the next step is trying to discover the previous versions for a single product from the list above. What might it look like to do that? Then check out the SQL book b/c I imagine this might make use of a subquery or something
		- The query for a single market item revision is below: 
```
SELECT
	mirv."effectiveDateTimeRange", *
FROM
	"MarketItemRevision" mir
	JOIN "MarketItemRevisionVersion" mirv ON mirv. "headerId" = mir.id
WHERE
	mir.id = 'bebc088f-7165-43ee-9338-f3ee8ca3c795';
```

- The results of the query are: 
	- ![[Screen Shot 2021-06-24 at 9.13.15 AM.png]]
- So I think I could do some sort of search to find the first version that does not have JDE, then replace that anywhere there is JDE. Subqueries!
	- So this gets the most recent NON `jde` revision: 
``` 
SELECT
	mirv. "effectiveDateTimeRange",
	mirv. "costLastUpdatedBy",
	mirv. "costLastUpdatedAt",
	*
FROM
	"MarketItemRevision" mir
	JOIN "MarketItemRevisionVersion" mirv ON mirv. "headerId" = mir.id
WHERE
	mir.id = 'bebc088f-7165-43ee-9338-f3ee8ca3c795'
	AND mirv. "costLastUpdatedBy" <> 'jde'
ORDER BY
	mirv. "effectiveDateTimeRange" DESC
LIMIT 1;
```
- So I somehow need to use that to? Time to write on the [[Remarkable]]. 
- ![[Screen Shot 2021-06-24 at 9.56.20 AM.png]]


### Process
1. Grab all Mirv's with JDE
```
SELECT
	mirv. "headerId",
	*
FROM
	"MarketItemRevisionVersion" mirv
WHERE
	mirv. "costLastUpdatedBy" = 'jde'
GROUP BY
	mirv. "headerId",
	mirv.id;
```

2. Filter to their MIR
```
WITH "MirWithJde" (
	mirId
) AS (
	SELECT
		mirv. "headerId",
		*
	FROM
		"MarketItemRevisionVersion" mirv
	WHERE
		mirv. "costLastUpdatedBy" = 'jde'
	GROUP BY
		mirv. "headerId",
		mirv.id
)
SELECT
	mirId
FROM
	"MirWithJde"
GROUP BY
	mirId
ORDER BY
	mirId;
```

 3. Grab all Mirv's for said Mir's 

```
WITH "Mirs" (
	mirId
) AS (
WITH "MirWithJde" (
		mirId
) AS (
		SELECT
			mirv. "headerId",
			*
		FROM
			"MarketItemRevisionVersion" mirv
		WHERE
			mirv. "costLastUpdatedBy" = 'jde'
		GROUP BY
			mirv. "headerId",
			mirv.id
)
	SELECT
		mirId
	FROM
		"MirWithJde"
	GROUP BY
		mirId
	ORDER BY
		mirId
)
SELECT
	*
FROM
	"Mirs"
	JOIN "MarketItemRevisionVersion" mirv ON mirv. "headerId" = mirId
ORDER BY mirId;
```

4. Find most recent mirv with fusion

