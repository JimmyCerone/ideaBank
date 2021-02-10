### 1644
Quick Version: Price points can be calculated on the front end. 

Steps: 
1. Navigate to the price edit page
2. Change sandbox to a tester w/ India Market
3. Note that the PreferredPriceLessTax cell is editable
4. Enter a new value and note that all dependent price points are recalculated
	- Triggers the save animation on the top right
	- You will see gray loading cell in the dependent fields


### 1721
Quick Version: User can assign classifications while price editing. 

Steps:
1. Stay in the India Sandbox selected earlier.
2. Show new classification columns and their orders:
	- Consumption Tax Rate
	- Retail Price Markup
	- Trade Discount
	- BV/ABO Price Less Tax
	- Standard BV/PV
3. Click the dropdown for different classifications and choose new values.
4. Observe the recalculation


### 1564
Quick Version: On the Price Edit Page for the market product variant, we should see the correct ratio on the drop downs. **Only for the India Market**

1. Note that the first pass of this in 1721 used dummy data and this loaded everything up correctly. 

### 1669 
Quick Version: Changed by and date are added to the price edit table as columns. 

Steps: 
1. Navigate to the price edit page
2. Choose the unchanged sandbox
3. Verify that 2 new columns "Changed By" and "Changed At" are present
4. Verify that the columns are empty
5. Choose changed sandbox
6. Verify that columns are "full"

### 1707
Quick Version: Duplicate rows on the price edit page are fixed. 

Steps: 
1. Navigate to the price edit page and select sandbox
2. Check that no duplicate rows are present

### 1641
Quick Version: Fixed scroll bar on price edit page. 
 
 Steps: 
 1. Verify that only 1 vertical and horizontal scroll bars are present

### 1514 
Quick Version: Adds filtering to the sandbox for market item revisions to achieve parity with Report / Manage Products page. 

Steps: 
1. Navigate to the price edit page. 
2. Choose a sandbox 
3. Filter and demonstrate only 1 country is present

https://app.zeplin.io/project/5ddeb85d094def05edf80e2d/screen/5f75ee4a4abc7e84ec400701

### 1706
Quick Version: Allows you to view products created in a sandbox

Steps: 
1. Navigate to the edit products report page
2. Change the sandbox to the correct one
3. Verify that there is a product in the sandbox that does not exist on master

Author's Note: Check testing instructions for how to demo. 
### 1620 
Quick Version: Finished role enforcement for sandbox management.

Notes: 

Price Approver can change the status of a sandbox to: 
- "in Progress"
- "archived"
- "published"
Portfolio Manager can: 
- "awaiting approval"
- "archived"

Setup: 3 Sandboxes:
- In Progress
- Awaiting Approval
- Published

Steps: 
1. Go to access override and add super user then pick a market
2. Navigate to the sandbox page
3. Click on the sandbox to edit the status. See that all status options are disabled. 
4. Go to access override and add portfolio manager role and remove the price approver role
5. Go back to the sandbox and see that you can change the status to awaiting approval
6. Return to access overrides to give yourself the price approver role
7. Publish the sandbox
8. See that you can now archive the sandbox

Author's note: 
>Yeah that is worth a mention - I think that was one of the last roles we needed for the india release and it lets the user submit sandboxes to review (and the price approvers can publish).There are more specifics in the story but that is just what I recall

### 1648
Quick Version: Users can navigate to market rates & rules page.

Steps: 
1. Change access to "affiliate user"
2. Verify the page is hidden
3. Change access to Fusion COE
4. Go to market rates and rules page 
5. Confirm the content for roles and abilities of "ManageAffiliateMarketRates" or "ReadAffiliateMarketRates"


### 1649
Quick Version: When a user navigates to the market rates & rules page, they see a list of markets.

Steps: 
1. Check assigned markets
2. Go to manage market rates page
3. See the list of markets selected in change access
4. Change to the India sandbox
5. Verify that only India is now listed







## Helpers

## Questions
- Ask Lydia about where to demo from
	- Local develop branch? 
	- Staging?

People have had issues running off of develop. Lydia has demoed off of her review environment. Getting data in order can be hard.

On the Lydia review environment there is a good amount of work on there (with some work on there). 
There is another review environment (Review1) that is a possibility. 
Either deploy develop onto another review environment and fix price editing. 

## High Priority Stories

## Action Items
- Update price record editing data with 3 scripts: 
	`import-market-price-ratios  
import-market-rates-and-ratios import-market-consumption-tax-configuration-and-classification`
- The issue I might run into after I run these is that AITS is working on fixing the ratio assignment to a marketproductvariant
- When test data is needed and it doesn't matter what assignment it is, you can run this SQL query to update it
- If an MPV doesn't have a classification assigned to it, it will throw an error when you try to edit it (as it tries to go fetch that)
		- Ensure that all MPVVersions in that market have a classification set


SQL Script to make sure all MPVs in a MPVV have a ratio assigned to them: 

``` select \* from "MarketProductVariant" mpv   
join "MarketProductVariantVersion" mpvv on mpvv."headerId" = mpv.id  
where mpv."marketId" = (select id from "Market" where name = 'India')   
and mpvv."retailMarkupRatioClassificationId" IS NOT NULL;select class.id, \* from "MarketConsumptionTaxClassification"  class  
join "MarketConsumptionTaxConfiguration" conf on conf.id = class."marketConsumptionTaxConfigurationId"  
where conf."marketId" = (select id from "Market" where name = 'India');update "MarketConsumptionTaxClassification"  
set "isDefault" = true  
where id = '9e1d1cee-e3dd-48ef-8db4-01c474d3c287';update "MarketProductVariantVersion"  
set "retailMarkupRatioClassificationId" = '6ab83a81-bc2e-4987-ae8d-101dc4d14d79'  
where "retailMarkupRatioClassificationId"  IS NULL;update "MarketProductVariantVersion"  
set "bvPvRatioClassificationId" = 'fb3c5f21-edc1-4327-a99a-853644199726'  
where "bvPvRatioClassificationId"  IS NULL;update "MarketProductVariantVersion"  
set "bvAboRatioClassificationId" = 'b71dfdc9-5819-493a-bb39-c7ec726fcf5c'  
where "bvAboRatioClassificationId"   IS NULL;update "MarketProductVariantVersion"  
set "preferredPriceDiscountRatioClassificationId" = '358e0198-c94c-4eb4-abbc-3aa5c3689d4d'  
where "preferredPriceDiscountRatioClassificationId" IS NULL;update "MarketProductVariantVersion"  
set "marketConsumptionTaxClassificationId" = '9e1d1cee-e3dd-48ef-8db4-01c474d3c287';  
where "marketConsumptionTaxClassificationId" IS NULL;