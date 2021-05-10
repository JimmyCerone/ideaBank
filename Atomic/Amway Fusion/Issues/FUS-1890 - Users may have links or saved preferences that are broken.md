https://jira.amway.com:8443/browse/FUS-1890

## TODO 
- [x] Check feature flags on prod vs staging?
	- [ ] `SandboxSelection` is the culprit

## Problems
- We shouldn't be passing down an invalid UUID to the db level
	- Somehow things hidden behind the `SandboxSelection` magically take a care of this. This handling isn't present without the feature flag, which is part of why we get an error. What might be happening is that the sandbox selector component handles this case, which is why it breaks when it's hidden. 
	- Solution: Better URL handling in general. 
		- Risk: This makes what is going on a little opaque. Processing things that high up feels like it could cause confusion. Is there precedent for it? Do people know to look here? 
- The GraphQL queries on the Report page (`GetReportRows` & `GetReportSummary`) both still accept a Sandbox Id even when the Sandbox functionality is behind a feature flag. 
	- Solution: Hide this stuff behind a feature flag. 
		- Risk: This could be hard to do? 
			- Would not be hard. `state.ts` just could hide the sandboxId. 
				- Problem with this is that the feature flags are accessed via a hook, which can only be accessed in a React component. Thus we gotta either pass the flag in to the function or filter it before. This means that we won't have a centralized, future proof solution, which sucks. 
					- Is there a test we could write around this that would help prevent regression?
					- 

## Questions
- Why does the link listed on the story break prod but work fine locally? 
	- Will it work on review2?
- Is there a way to do bulk updates on the Dynamo DB instance? 
- Should the Sandbox functionality on the Report page GraphQL query be hidden behind a feature flag? 
- How do you see what's behind a feature flag? 
	- Search for the feature flag and see where you are using it. 