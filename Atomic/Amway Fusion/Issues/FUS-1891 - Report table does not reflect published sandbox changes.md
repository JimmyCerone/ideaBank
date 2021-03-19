https://jira.amway.com:8443/browse/FUS-1891

[[2021-03-15]]

What We've Learned
- After publishing, the records look right on the master data pool, they just aren't showing up correctly on the front end
	- Less likely then that it is a problem with the replay domain mutations and more likely UI caching or the report not grabbing things correctly
	- [ ] Validate Effective Date


What We've Tried
- mir report refresher -> error once need to try again with logs this time
	- Could be a fix. Not super likely given the database looks good. 


#Fusion