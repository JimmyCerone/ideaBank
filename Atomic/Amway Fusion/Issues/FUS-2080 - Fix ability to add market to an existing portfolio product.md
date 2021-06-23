## Tasks
- [ ] Check if a new local sales item is being created as affiliate sourced
- [ ] Are we doing a JDE check for cost and sourcing when the product is preexisting?
	- If so, no changes
	- If not, pull that out into another story
- [ ] Do we check for a unique variant? 
- [ ] Remove constraint so that anyone can add a market if they have that market
	- [ ] Update drop down so that you can only select your own markets

## Note
- Open questions have all been answered

## Requirements
- When someone adds a market, the market item revision corresponding to that new item is locally sourced
- We don't have to be in the market of the product to add my market
	- "Any Sandbox Editor can add any of their markets to any product, regardless of sourcing. That new product they add will be affiliate sourced."

## Testing Instructions
1 Navigate to the Review environment. 
2 Ensure that the roles you have are 'Sandbox Editor' and 'Affiliate User' with the 'India' Market.
3 Navigate to the Edit Products page. 
4 Select an Inactive Product outside of the India Market. 
5 Observe that the 'Add Markets' button is enabled.
6 Click the 'Add Markets' button and select the 'India' Market. 
7 Observe the Status of the Product change from 'Inactive' to 'Established'


## Problems
- [ ] Weird that the product isn't changing from `inactive` to `established` because it is technically supposed to on line `623` of `addMarketsToProduct` in `modules/domain-services/product/mutations.ts`.
	- This was a front end caching issue that was resolved by refetching the `GetProductRows` query.
- [ ] Add Markets button is disabled for Products that do no contain your market.
	- Updated the permissions to `ManageLocalProducts` and `ManageGlobalProducts` from `ManageProducts`, which is no longer used. 