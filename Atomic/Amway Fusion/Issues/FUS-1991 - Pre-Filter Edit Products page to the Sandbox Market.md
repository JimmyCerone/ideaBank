## Goal

When viewing the Manage > Edit Products page in the context of sandbox, pre-filter the list of products to match the sandbox market.

## Requirements
When viewing the Manage > Edit Products page through the lens of a sandbox (any status),

-   Set the Geography Filter to have the Sandbox's Market selected
-   List only the products that match the sandbox market (per the filter)
-   Disable making changes to the geography filter
	-   Looks like we will have to update line 496 of `modules/client/components/collapsible-filter-sidebar/index.tsx` for this. Doesn't seem impossible, we would just check if there is a sandbox selected. 
-   Update the results count to match the number of the products shown


## Questions
- What precursors do we have for setting the geography filter on navigation? 
	- How do we handle it when navigating from Price Edit to Report page? 
- Are there any precursors for disabling a segment of a geography filter? 
- Can we port over the changes Nick and Mike made to update the number of products shown? 