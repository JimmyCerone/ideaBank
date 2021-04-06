## Background
- We discovered this during our [[Items in Review - March 23rd, 2021]] demo. The downstream problem this issue causes is that the MPVs you add via local sales item don't show up in the report page. The report page only shows active MPVs and when you add a local sales item it is in progress. The question here is whether we should change the status when publishing or not. 

## Implementation Hypothesis
- Write a failing test
- Update the add local sales item implementation to ensure that MPV is set to `active` and Product is set to `established`


## Questions
- What behavior do we want? 
	- We want to set the MPV status to active and the product status to established on creating a local sales item. 
- What are the consequences of changing this default behavior? 
	- None, other than we will now see these new local sales items on the report page
- How do we make sure we grab only local items here? 
	- Since we are only changing the creation process of local sales items, nothing else should be affected. 
- Where could we go to make a test fail? 
	- Add local sales item mutation test?