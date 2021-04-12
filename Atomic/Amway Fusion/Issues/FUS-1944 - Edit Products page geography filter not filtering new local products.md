c## Todo 
- [x] Can we replicate this?
	- [x] Replicated on `review2`
- [x] Grab the query that filters by market
	- [x] GetEditableProducts, which grabs the selectedMarketIds that is set at the Report Facet Hierarchy Filter level. Weird place to see an error because the mechanics of the market setting is simple and this works for other pages (like Report) that use similar setups. Meredith is adding testing
- [x] See if the filtering is bad for any other categories
	- [x] Good for all other categories
- [x] Check failing test on Github desktop
- [ ] Convert MPV to MPV Lens (mirror pattern from Product Lens). We basically aren't getting anything from sandbox.


![[IMG_6827.png]]


## Questions
- Is this an effective date issue on testing? 
	- No idea. 
- Is there a query I can check to see about this?


## What I Know
- So the `MarketProductVariant_DPOverlay` and `Product_DPOverlay` tables have it. So it's there and searchable by the market id. The query seems to grab the right market Id in its where clause. Not sure where things are going wrong here. 
- Is this a data problem? Are we inputting the local sales item wrong?  
- Local Sales Item has a NULL Active Market