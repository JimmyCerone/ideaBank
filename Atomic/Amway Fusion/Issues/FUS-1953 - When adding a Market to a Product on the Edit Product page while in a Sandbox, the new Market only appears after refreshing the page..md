## What I Know
- The error doesn't occur on Master
- There are related errors when changing Sandboxes (things don't update correctly), which suggests caching
- Happens for Local Sales Items and existing products. 
- The side bar does not update either
- Running the Query in Apollo returns the correct number of markets
- When running `AddMarketsToProduct` I am getting back the correct stuff in the response. Yet when I run `GetMarketProductVariantsForProductMarkets` I get the `Master` data back. So somehow something is getting lost between those two steps. 
	- Looks like only the `productId` is getting passed into the `GetMarketProductVariantsForProductMarkets` query. Why is that? 
		- SandboxId can be passed in but isn't required. Is this the refreshing issue we see when we reload a page and the sandbox disappears? If so, why isn't that reflected in the UI? 

## What I Think 
- I think this is a caching issue. 

## What I Need to Know
- How do I know for sure this is caching? 
- How do I fix a caching issue? I've done this before but I forget... 
- Is there a way to test for this? 
- What's different about master? Are we not passing the sandboxId around correctly? 
	- Where else did we do this incorrectly? Why do I remember this? 
- What query is run in the AddMarketDrawer? Which query is grabbing the stuff we need? 
- Could the problem be with the EditProductReportRefresh??? 
- What is kicking off `GetMarketProductVariantsForProductMarkets`? What is it getting passed in? 

## What Happened
- Added sandboxId to the refetch query on the `add-markets-drawer/index.tsx` file. That updated the cache for when the `GetMarketProductVariantsForProductMarketsRan` later, grabbing the right data. Not sure though why that change improved the handling of changing sandboxes (though it did seem to).

## What New Things Came Up
- It looks like this change blew away the check boxes on the drawer.
	- The checkboxes work fine on the review environment.
	- Why did this change blow that functionality away? 
		- Turns out it didn't, this was an old environment. Worked just fine on Lydia's environment. 
- Looks like this test keeps failing remotely but not locally: `modules/client/pages/price-edit/\_\_tests\_\_/price-edit-report-refresh.test.ts`