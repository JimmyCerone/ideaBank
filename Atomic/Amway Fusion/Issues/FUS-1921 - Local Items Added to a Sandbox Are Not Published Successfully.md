## TODO
- [ ] Write a test to cover where we have something in master and in overlay table
	- In the file `market-item-revision-report-refresher`
		- Report refresher test only does product, but it should have a good example to get started with
- [x] Test deleting the overlay table and see if that fixes the issue
	- Does not fix the issue

## Reflection
- So we did a few things here. First, we dropped the foreign key constraint on the snapshot table so that we can add things that don't yet have MIRs (which is what we end up doing as the mir isn't created yet). Second, we set the context to be the sandbox context before we take the snapshot, which gives us the local sales item. Previously, we were just using master and updating already existing stuff without adding old. 
- We only saw the issue of the Mirs after we focused on the sandbox instead of master. 
- The main query we had the issue with was grabbing which mirs to update. It was using the lens, which was set to master, which is why we missed those. 

### Questions about Solution
- Why do we have the cache function we do? 
	- Gives us memoization on the front end. Going to change the caching function to avoid us getting something that has the same id but is a different mir. We use the data pool and the effective date time to ensure uniqueness. 
- What attempts didn't work and why? 
	- First thought was a caching issue because we were able to find the id after it was published. 
	- Good that we wrote a test right away which sped up our iteration. 

## Notes
- Edit Product page shouldn't show things that aren't currently effective for today's date. 
- So we are finding these things on master, just not on the report. 

## Questions
- Are we running the report refresher after publication? 
	- We ran `yarn db:migrate:latest` which runs this and it didn't update. So it's probably not this. 
- Are all the pieces (p, pv, mpv, mir) getting connected together and being created on the replay? 
	- What do we expect to happen if not? 
- Is there something about the MPV or Mir created that would make us exclude it from the Report page? 
	- We find them on master so why not on the report page?
- Could it be that since we still have this on the Overlay table that we aren't selecting from the master table? 
- How does the refresher even work? What is it for? What's the difference between the test for the report and the mir test? Is it just different it's? 
- Why does the price review effective snapshot not have anything in it?

WITH "latest\_import" AS ( SELECT fi.id, fi."dataImportedFromForecastingToRawAt", date\_part('month', fi."dataImportedFromForecastingToRawAt") :: INT AS month, date\_part('year', fi."dataImportedFromForecastingToRawAt") :: INT AS year FROM "ForecastImport" fi ORDER BY fi."dataImportedFromRawToPublicAt" DESC LIMIT 1 ), "mir" AS ( -- overlay and master SELECT overlay. "dp\_dataPoolId" AS "dataPoolId", TRUE AS "isOverridden", overlay. "id" AS "id", overlay. "legacy\_AMWAY\_SKU\_PFX" AS "legacy\_AMWAY\_SKU\_PFX", overlay. "legacy\_AMWAY\_SKU\_BASE" AS "legacy\_AMWAY\_SKU\_BASE", overlay. "legacy\_AMWAY\_SKU\_SFX" AS "legacy\_AMWAY\_SKU\_SFX", overlay. "skuRevision" AS "skuRevision", overlay. "marketProductVariantId" AS "marketProductVariantId", overlay. "skuRevisionPrefix" AS "skuRevisionPrefix", overlay. "hybridCostUsd" AS "hybridCostUsd", overlay. "forecastedUnitSale…

[client.c42dd4144e0f8e31392c.js:1:456372](https://review.fusion.corp.amway.net/client.c42dd4144e0f8e31392c.js)  