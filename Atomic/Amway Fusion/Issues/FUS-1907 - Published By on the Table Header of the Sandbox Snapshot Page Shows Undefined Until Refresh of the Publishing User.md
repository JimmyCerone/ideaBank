## TODOS
- [x] Update mutation to include publishedBy here: `modules/client/pages/sandbox/PublishSandbox.gql`
- [x] Create a PR
- [x] Request Lydia
- [x] Write up testing instructions
- [x] Let meredith know
- [x] Let Ryan know we need another story

## Questions
- Where is the source of the published by on the Sandbox Snapshot page? 
	- `GetSandbox` info, but that isn't the problem. The problem is that the cache isn't updated when `PublishSandbox` is run, so get sandbox runs and grabs data out of an old cache. 
- Am I right in assuming this is a front end issue?
	- I think so because the Last Edit columns are updating correctly on the Sandbox Management. So the data on the backend seems good. 
	- Not quite. This ended up being a backend issue in that the graphql queries weren't caching correctly. Specifically, `PublishSandbox` wasn't retaining any info about the sandbox, which left us with old data at the start, at least until we refreshed. 
- Should I write a test for the publish sandbox mutation?
	- Is that even the right mutation? Is the caching coming from somewhere else? Can I log this out? 

## Ideas
- [[202103231043 - Apollo cache can be updated by mutations]] - this seems to be the fix for us. We can update how the mutation is handled and thus keep better track of the #Cache. 