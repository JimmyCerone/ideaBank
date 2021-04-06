## TODO
- [x] Write an event test (look at addLocalSalesItem test for setup info)
	- This will entail a test that checks the id's 
	- Will have to pass in an id
		- Check to make sure that id exists afterwards by grabbing from the repo. 
- [x] Create PR (as a draft)
- [x] Check failing tests
- [x] Merge
- [x] Update testing instructions & put into review
- [x] Let Meredith know

## Implementation Hypothesis
- Enforce ordering rules on replaying domain mutations. 

## Progress
- Adding `console.log` to view the order in which the actions are replayed. 
- `dispatch.ts` seems to be where we are adding things to the `EventLog`. So while the console.log might be helpful, it's probably in the dispatch where things go wrong. Probably? I suppose we could filter on the replay side... 
- The two events that are happening are:
	- `domain-event/add-local-sales-item`
		- Correctly adds a market product variant to the `MarketProductVariant_DPOverlay` table. 
	- `domain-event/market-product-variant-updated`
		- This is the real problem. It is looking in the `MarketProductVariant` table, which should be ok since technically we have already run the replay. Yet the reply doesn't seem to have been effective yet. Why? 
- The two events seem to be happening in the correct order.
- FIXED! By explicitly setting the id's on the `AddLocalSalesItem` we were able to persist those id's through the update (or at least make sure they match). 

## Theory
- This is the key question here: 
- Why does the replay not put the `MarketProductVariant` on the main table? Why is on the overlay even after replaying? 
	- Are we using the right context here? 
- Further, why does this work right for `AddLocalSalesItem` if we don't have a `market-product-variant-updated` right after? Why the delay?
- The updated theory is that the local sales item is getting added to the MPVV table, but with a different Id than it had in the overlay table. The update is searching for the id from the overlay table, which does not exist on the MPVV table. 

## Questions
- Where in the `replayDomainMutations` chain are we seeing things failing? We aren't getting much from the errors yet - future story. 
- What's the difference between a normal local item and one that has been edited? What order are we doing this in? Where do we find out what order this has been done in?
- Can I write a test for this first? 
	- Would it be crazy to write an AddLocalSalesItem action here: `modules/domain-services/market-product-variant/mutations.ts`? This seems to be the best way to get a test going. 
- ~~Could it be that we are trying to edit first, that we've reversed these two?~~
	- ~~What determines how these are loaded up? Is there a stack up there?~~
		- Things are added via the `dispatch.ts` - in the right order. Then played back sequentially.
		- All the events are stored on the `EventLog`. Not sure how they get on there.
		- Figured all this out - they are in order, just not working quite right.  
- Why does the replay not put the `MarketProductVariant` on the main table? Why is on the overlay even after replaying? 
	- Are we using the right context here? 


## Test
- The test is let's create a local sales item, observe it's MPV id in the overlay table and see if that remains the same once we publish it. 
	- Id in MPV Overlay: `219c4ec5-c922-4411-af70-d14855fcd944`
	- Id on Master: `335815c7-39bb-4681-913a-e6d294466dc3`
- Second test, this time with modifications to local sales item: 
	- Id in the MPV Overlay: `226243da-7757-4320-8d44-2a6e676c420e`
	- 