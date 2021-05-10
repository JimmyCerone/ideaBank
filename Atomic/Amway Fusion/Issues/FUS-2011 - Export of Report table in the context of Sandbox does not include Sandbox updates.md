## TODO 
- [x] Find where this is in the code base. 
- [ ] Move test file `appraise-lite-xlsx-download.test.ts`
- [ ] Add the sandbox to the configureQuery method in `modules/records/appraise-lite-report/index.ts`
	- Why isn't sandboxId part of the where of the opts? And why isn't accounted for in the configureQuery? Where else is this broken without us knowing it?


## [[2021-05-05]]
- When we are updating a MPV on a sandbox, the activeMarketItemRevision is not copied over from the original record, meaning the new record doesn't show up on the revision refresher.
	- So should we copy over the original MIR or create a new one? 

## Implementation Hypothesis
Update the request to get the report to use the sandbox id and the current effective date time of the sandbox

## Questions
- Why isn't the sandbox being passed down as it is? The report state should be able to do this just fine. 
- Do we need to integrate effective date? What precedents are there for this? 
	- Is this the key missing link? Is sandbox id already working? Seems that even effective data appears to be accounted for. So not sure what's off base here. 
- How long does the download take? Is there any way to speed it up? 
- Why am I getting such weird errors? 
- Why aren't products getting added normally? 
- Why isn't the download working?


## Problems
- Items aren't adding correctly.
- The download is taking forever. 
- I can't tell if effective date or sandbox is the problem. 