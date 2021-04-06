`updateProduct` mutation is not using the event services so it isn't getting replayed correctly on publish. So before publish, we see all the correct information but on publish we don't because there is no connection to events. 

- [x] Convert `updateProduct` to use `applyDomainMutation` helper
	- Will we still do this with the mutation? 
- [ ] Make sure tests still pass
- [ ] Add a test for publishing to prevent regression
- [x] Add validator 
- [x] Migrate to mutation logic

## Troubleshooting
- Remove dist folder
- Restart computer
- Beg for help from Andy

## Questions
- Should I add replayable to the other Product mutations?
- How does this connection to 1944?
- Why is addLocalSalesItem broken? how is that related to this change? Is it?
	- Are tests failing somewhere?

Might have interesting connections to [[FUS-1944 - Edit Products page geography filter not filtering new local products]]. 