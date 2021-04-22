https://jira.amway.com:8443/browse/FUS-1951

https://jira.amway.com:8443/browse/FUS-1948

https://amwayawr.slack.com/archives/G01PRE1A27M/p1617290009145900
- Turned into issue: https://jira.amway.com:8443/browse/FUS-1958 

https://jira.amway.com:8443/browse/FUS-1960

https://jira.amway.com:8443/browse/FUS-1961


## Crashes on Review
- Editing multiple costs at once failed
- Page crashes on editing but the changes are saved
- Failure when searching on the filter
	- Reminds me of the [[Tech Time]] task that Jordan and I worked on in the SKU Search box
	- May not have been this - couldn't reproduce
- When changing sandboxes the only changed toggle persists and we don't return to default
	- Tied to an expectation to all filters going away when you change sandboxes
- Errors when switching from Price Edit page to Report page. 
	- Fetch errors
	- Gateway timeout (when running multiple queries)
	- Saw a failure when switching while things were still loading
		- Lends a bit of credence to the idea that things might be hiding in the background. Saw the old requests pop in and then the last one failed.
			- Got an error from cloudfront that said forbidden error.
			- Seems like random things pop in later than would be expected.
		- Seem to especially have errors when opening a filter while things are still loading or switching while a filter is loading
			- If doing it before data is loaded you might have errors
		- Could it be that multiple users working at the same time causes trouble?
		- Seems to crash when going from Sandbox Management page to Report page. 
			- Database has to scale up which causes a lack of response

## Jason Sync
- Errors in last 3 hours
	- [ ] Permission error on GetBundleItems
		- Determined that the user didn't have correct permission to retrieve one of these included items
		- User Id: AIU2576
	- [ ] Deadlock
		- Update MPV SKU Suffix
	- [x] GetLocalCurrency
		- Sandbox Id was null

Theory 
- Race conditions on the front end which wouldn't show up on back end
	- We could have something that tries to resolve but can't because of a lack of data which would cause an error

- [ ] Look into Sandbox Selector vs. rest of page
	- Is that causing conflicts?
		- Could put in a sleep to try to show race conditions (must be an async sleep so it doesn't block the process)


## Switching Crashes
- Variables / [[03062021 - Levers]]
	- Access
	- Loading State
	- # of edits ongoing
	- Time waited