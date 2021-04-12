`updateProduct` mutation is not using the event services so it isn't getting replayed correctly on publish. So before publish, we see all the correct information but on publish we don't because there is no connection to events. 

- [x] Convert `updateProduct` to use `applyDomainMutation` helper
	- Will we still do this with the mutation? 
- [x] Make sure tests still pass
- [x] Add a test for publishing to prevent regression
	- [x] Test new test
- [x] Fix `yarn db:do-over:test` problem
- [x] Check on `review2`
- [x] Add validator 
- [x] Migrate to mutation logic

## What to Try Next
- [ ] Try adding the refresher to the update product mutation
	- Was going to try this but it seems to work find (locally at least) without this. 
- [x] Update db of review2 env
- [ ] Get cypress to pass
	- Seems to be failing because the filtering isn't working properly

## Troubleshooting
- yarn db:migrate:latest
- merged develop
- yarn
- kill-node
- killall node
- Remove dist folder
- Restart computer
- Beg for help from Andy

## Questions
- Should I add replayable to the other Product mutations?
- How does this connection to 1944?
- Why is addLocalSalesItem broken? how is that related to this change? Is it?
	- Are tests failing somewhere?

## Problem
- UI supports updating hierarchies but the back end does not support this. 


## Connections

Might have interesting connections to [[FUS-1944 - Edit Products page geography filter not filtering new local products]]. 

Seems to connect a decision made in [[FUS-1706 - Add Datapool Support for Product and Product Variant]] to exclude the hierarchies from the version table even as they were included in the overlay table. 