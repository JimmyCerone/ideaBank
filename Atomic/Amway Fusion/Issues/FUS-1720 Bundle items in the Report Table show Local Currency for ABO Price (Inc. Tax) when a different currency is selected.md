1. Open the #ReportTable in #Production
2. Set the #Currency to USD
3. Set Geography Filter to Russia
4. Search for SKU 119522
5. Expand the #Bundle in the Report Table
6. See that #ABOPrice (Inc. Tax) for the Bundle Contents are not in USD

Desired Behavior
* All Report Entries, including Bundle Contents should respect the currency selected for the Report Table

### Tuesday February 2nd, 2021
Things that are "InCurrency": 
- [x] retail price including tax
- [x] retail price less tax
- [x] abo price including tax
- [x] abo price less tax
- [ ] CMAB
- [ ] CMAB%
- [ ] Hybrid Cost
- [ ] Transfer Price
- [ ] Measurement Credit

**We are skipping these for now**
- [ ] Projected Product Revenue?
- [ ] Cost Of Sales?
- [ ] Project Product CMAB? 

## Questions
- Could this be a problem with resolver?
	- It does seem to be a problem with the resolver. Specifically, the current resolver pulls the price from the market product variant, which is the wrong price since we are in a marketproductvariantsalesbundle. In a sales bundle, most mpv's have a discounted price, so you have to get the price from the salesbundleitem instead. We have two options:
			1. Rewrite the current inCurrency resolver to account for this (by getting the values from something other than the parent)
			2. Write a new resolver just for these values that we moved

## Progress
On Friday, I worked on updating tests. 

## TODOS
- Clean up types
- Show less tax
- Clean up comments
- Clean up the query 
- Run / find tests
- Run locally
- Push to review and check


## Problems
- This (`appriase-lite-report-query.test.ts`) test is failing in a flaky way when I went in and updated things, but only the last 2 tests are failing? 
- It's "fixed" in the sense that I can now build, but broken when I run the tests

![[Screen Shot 2021-01-29 at 4.40.21 PM.png]]

- #Migration - rollback from develop when you switch to a new, older branch

#Fusion