Looks like the numbers are the same but the currency label is incorrect. Not sure if those are coming from different sources or what but that seems like the thread to pull on. 

![[Screen Shot 2021-04-12 at 2.42.43 PM.png]]

## Implementation Hypothesis
- Move away from selectedCurrencyState in `modules/client/pages/price-edit/report-and-sandbox-summary.tsx`
- On the Resolver level (`price-edit-report.ts`), utilize currency conversion

## TODO 
- [x] Write small query that takes sandbox and spits back currency
- [x] Fix summary data to adapt for currency like is already done on the Report page. 
- [x] Create a bug for summary sandbox
	- [x] Let Nora know after bug creation
	- [x] Figure out what to do with 2001 (do we want to call it done?)
	- Right now it is assuming one unit per product which puts it at odds with the Report page. We need the summary table to be based on the Annual Total Units from the Report page. 
	- So on the Summary table for the Price Edit page we are seeing average CMAB, not weighted average CMAB. 

## Questions
- Where is the currency label coming from? 
	- Is it the same as the numbers source? 
		- Looks like the data is coming from the sandbox with no respect to currency while the label is coming from selectedCurrencyState while it should probably be something different. So it might be as simple as updating that in `modules/client/pages/price-edit/report-and-sandbox-summary.tsx`
		- Would we have to set the `selectedCurrencyState` to something new on navigate or is there a different way to get the local currency? 