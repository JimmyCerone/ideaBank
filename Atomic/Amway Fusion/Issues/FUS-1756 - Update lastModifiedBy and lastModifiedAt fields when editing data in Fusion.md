## TODO 
- [ ] Make sure there are test cases for each story requirement

## Tests
- [ ] `modules/client/pages/specific-market-rates-and-rules/market-price-ratio/get-market-price-ratio-classification.test.ts`
	- Fails in the canvas, which is quite odd
- [x] `get-price-edit-report.test.ts`
	- Fails on lines 127-132 seems to fail on the update which is part of the `effective-date-time.ts` file. Not sure what is going on with that... 
	- Fails in the 'Can Query' test specifically
-  [x] `forecasting-integrator.test.ts`
	- Why is the forecasting integrator implicated? 
	- The problem seems to be that there is nothing being returned. 
	- Seems unrelated... Weird and will skip
	- Failing tests:
		- 'ignores zero dcost items'
		- 'sums up multiple variants for the India market and applies it to variant most recently updated from Appraise'
		- After merging in develop, there are now more failing tests:
			- ![[Screen Shot 2021-03-18 at 10.45.52 AM.png]]
			- ![[Screen Shot 2021-03-18 at 10.46.53 AM.png]]
			- ![[Screen Shot 2021-03-18 at 10.50.31 AM.png]]
- [x] `modules/appraise-to-fusion-change-processor/__tests__/appraise-to-fusion-change-processor.test.ts`
	- Problem seems to be with the `processAppraiseChanges` we saw earlier, this time with the Product segment
		- No idea what this function does. Am also going to skip this again. 
	- Failing test is:
		- 'handles creates'
- [x] `modules/domain-services/product/\_\_tests\_\_/product-repository.test.ts`
	- Test fails on the `returns products that match` test
	- Running a bisect we get that the `add a couple more test expectations` is the source of our error yet we didn't update the product-repo tests nor anything related to the product repo in that commit
	- Lots of type errors
- [x] `modules/client/pages/price-edit/\_\_tests\_\_/update-mir-last-modified.test.ts`
	- Fails on `correctly updates the last modified at and by fields` where the nativeId is not what is expected (system instead of custom user)
	- Still failing after pulling in develop[]
- [x] `modules/import-export/dbo-integrator/importers/tests/product-variant-importer.test.ts`
	- Diagram of failure here: https://letsboard.co/boards/OfXtPfNqGuVo3A6mufoMrwXOTy6bVtiaAQt6
	- Fails on:
		- 'determines the suffix from dbo'
		- 'imports 1 variant for 2 sku master records if they share the first part of the suffix'
		- ![[Screen Shot 2021-03-18 at 12.27.46 PM.png]]
- [x] `modules/import-export/dbo-integrator/importers/tests/product-importer.test.ts`
	- Fails on:
		- 'upserts the products from DBO'
			- We worked on the upsert, so this makes some sense. Doesn't seem too bad to fix.
			- ![[Screen Shot 2021-03-18 at 12.29.06 PM.png]]
	- Problem is that we are running the following query in the `findOneBy` function in `knex`:
		- `select * from "Product_DPLens"(?::uuid, ?::timestamptz ) as "Product" where "skuRoot" in (?)`
			- We should not be looking to the Overlay table here. For some reason the table in `knex` is looking there...
- [x] `modules/client/graphql/\_\_tests\_\_/get-product-by-sku-root.test.ts`
	- Fails on:
		- 'returns a product with its brand Hierarchy'
			- Believe we updated this as well, can't remember quite what we did. 
			- ![[Screen Shot 2021-03-18 at 12.31.16 PM.png]]
- [x] `modules/client/components/product-form/tests/is-sku-unique-to-product.query.test.ts`
	- Fails on: 
		- 'is sku unique query > returns false if there is an existing product root on another product'
		- ![[Screen Shot 2021-03-18 at 12.32.44 PM.png]]
- [x] `modules/client/pages/price-edit/\_\_tests\_\_/check-for-existing-product-with-sku-root.test.ts`


#Fusion