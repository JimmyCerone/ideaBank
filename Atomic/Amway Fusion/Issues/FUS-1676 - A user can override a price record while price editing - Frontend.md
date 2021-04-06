## February 26th, 2021
### Questions
- ~~Do we need to add combined preferred price discount to all the tests? How do we determine which to have?~~
	- We don't need to add it. It automatically checks everything, all we have to specify is the ones that have changed. 
- ~~Events aren't getting the full typing from the events. The Field component can't do what needs to be done (I don't think).~~~
	- So we don't get full typing at the formik level and the field component doesn't have it. 
	- ![[Screen Shot 2021-02-26 at 12.44.21 PM.png]]
	- Doesn't work at the NumberFormatCellWithPrecision level either...
	- The problem was that I was explicitly typing... The type was built into the handler and if I had done something like (event) with no type, it would have worked just fine. 

## TODO

- [x] Make input-cell.tsx reload upon pressing enter
- [ ] Run commands on adjust-price-points.sql

## February 25th, 2021

### TODO
- [x] Add tests for the following cases to he `update-market-item-revision.test.ts` file
	- designatedBvAboRatio
	- designatedBvPvRatio
	- designatedPreferedPriceDiscount

### Testing Instructions
##### Requirements:

 * A user can right click on a product row while price editing to open a menu with the override option
 * A pop-up appears to confirm the user wants to override the price record
 * Once in override mode, additional fields appear editable

##### To test:

1.  Go to review environment
2.  Select the "1676 Testing" sandbox.
3.  Right click on a row
4.  Click the Override button
5.  Confirm that a popup appears. 
6.  Click cancel and confirm that the popup disappears and no changes are made
7.  Right click on a row, click the override button, click continue on the popup
8.  Confirm that the following fields are editable
 - Preferred Price Less Tax
 -  Abo Price Less Tax
 - Bonus Volume
 - Market Point Value
9. Edit a field and confirm that the difference is correct. Also confirm that the forward and reverse calculations were completed. 
10. Choose a new row and enter override mode. 
11. Edit a field and confirm that the ratios are now editable.
12. Change the ratio and notice that the fields become uneditable. 
- Can these change to editable? 

## February 23rd, 2021
- What I know so far. The mutation seems to be working. The record it's getting back looks fine. But for some reason the expected is wrong. 
- ~~Do we have to do the `designatedbvaboratio` as well? Or are we going to leave that off~~
	- Nope - we did this in a different way with the id instead.

### Todos
- [ ] Fix visual differences
	- Are the differences being exposed on the backend? How do I find that? Where do we start with this?
	- Are the tests done?
- [ ] Fix rounding rules on markups
- [x] Fix the fact that the changes aren't being made and reflected
	- Did we make an update that changed the resolver? Mutations don't seem to be working quite right. The only one being sent out is for the consumption tax. 
	- It seems that the only one that worked is the consumption tax, and it keeps getting sent out even when I change other things. 
	- Kind of stuck here. Not sure why the mutations aren't kicking off. No they do seem to be kicking off but things aren't updating correctly. Things aren't going downstream correctly. But things are being updated, so that's good.

## February 22, 2021

### Todos
- update tests to handle the rest of the mutations in the file `/Users/jrcii/Documents/Atomic Object/Amway/fusion-platform/modules/client/pages/price-edit/__tests__/new-update-market-item-revision.test.ts`
- ![[Screen Shot 2021-02-22 at 12.31.29 PM.png]]
	- Why did we remove this test from the file? was that an error? Are we replacing it with bvAboRatioClassificationId?

### Goal
- I think today's goal is to upgrade the tests to the point where we can be confident in the results on the frontend. 

## TODOS
- [x] Create a component that has access to the row because the row can tell us if it is overridden. If it's overridden, the component needs to display an editable cell instead of the drop down. ![[Screen Shot 2021-02-17 at 10.21.22 AM.png]]
	- Can we use the pattern from the override cell here? With the formik status?
	- This approach doesn't seem to be working, thought I'm not sure why the import isn't working. I know that the type on the props is wrong, but that shouldn't affect the import process.
	- No imports are working coming out of this file: `modules/client/components/price-edit-table/renderers/render-dropdown-cell.tsx`
	- My thought is that when we are overridden, we have the editable cell configuration, but otherwise we are in the dropdown configuration. I have a slight worry about the loading state.
	- Can we use the formik context already on the dropdown config and just add an alternative that pulls in the editable cell? Looks like it would be quite complicated to fit it in there. The easier path seems to figure out the import status.
- [ ] Test to make sure we are returning the difference correctly (update-market-item-revision.test.ts)
	- If we are overriding the retail market classification ID we want to make sure the difference is being calculated correctly. 
	- Borrow testing from calculation to improve these. 
	- Line 479
- [x] Check functionality of onClick
- [x] Change color of continue to blue (if possible)
- [x] Update style to match
	- [x] Add padding to override button
- [x] Connect state of the modal to the cells
- [x] Wire up mutation
- [x] Ask Ryan about questions
- [ ] Ask folks about consumption tax being null when running `import-market-price-ratios`. The error originates here: `modules/import-export/market-price-ratios-seeder/mpv-ratio-classification-mapper.ts`
- [x] Figure out why the price is showing from the other cell: ![[Screen Shot 2021-02-15 at 4.20.47 PM.png]]
	- All the cells are the same - they are all connected.
	- Gotta change stuff in this file (modules/client/components/price-edit-table/renderers/editable-cell-renderer.tsx) lines 75 on inside the `RenderFormikInputCell`
	- Why are they connected? Could it be the name column? Could we pass in custom objects to the name column to differentiate? 
	- Example of the behavior tied together live: ![[Screen Recording 2021-02-15 at 5.12.05 PM.mov]]

## Progress
- Override button is done (popup)
	- State still could use work
- Notification modal is up but not connected
	- Connect so that clicking continue results in editable cells
	- Move text to translations
	- Change color to blue
- State of the modal is connected to the cells via the formik context status. I've got it working for one cell, need to figure out what other cells I need to get hooked up. Then I've got to figure out the mutation. First comes fixing my db because I will need that to run dev and try all this stuff. 

## Questions
- ~~How do we do modals in React?~~
	- We are using popovers for the button and we have pre-built modals on the project. 
- ~~How do we capture a right click with accuracy?~~
	- OnContextMenu in a div takes care of this nicely. It wraps the whole row so the subrows are included. 
- ~~How much can we pull over from the old story?~~
	- Not sure what I was asking here, but not much. 
- ~~Do we need to be concerned about updates on the other fields / apollo caching?~~
	- We don't need to be concerned about updating other fields, at least I don't think so. These fields should be independent and shouldn't affect other fields. 
	- [x] Double check this.
	- This was wrong, the override will cause other fields to change. 
- ~~Will we have to create a new category on the price edit table page?~~
	- We did end up making a new cell type, which changes based on the status from the formik context. 
- Which fields can be overriden again? 
	- Still not 100% on this, but preferred price including tax is one of them. 
- ~~What level do we want to do this on?~~
	- Table (pass down)
	- Row (no passing)
	- Cell (pass up through handler)
	- We take care of this on the row level, via the row wrapper. 
- ~~Can we add an onClick prop to the Virtualized Table with Subrows?~~
	- Not necessary. 
- ~~Should we edit the row type to add an onclick method?~~
	- Not necessary
- ~~What do we do when you are finished overriding values?~~
	- Next time you load the page you should see the cells in the overridden state. The graphql "stores" the isOverridden state so that you can maintain that across reloads. 
	- According to Ryan, the above behavior works for us.
- Can you get back to a non-editing mode? Can you reset?
- ~~Can you override many rows at once?~~
	- Nope. According to Ryan you can only override one row at a time. 
		- How can we enforce this? Will it be on the price edit table level or lower down?
- What is the deal with the `cell-renderer` file? Are all of our renderers coming from there?

## Outline 
![[IMG_6660 2.heic]]

## Notes
- Almost seems like the right click ability is for the whole row, which then allows you to edit all available rows. That would be a simpler implementation. 
- Could we do something similar to line 190 with a prop? What level should this go on? Could we do it on the price-edit-table-container.tsx file? Detect which row is clicked and pass that down? 
- Doesn't seem like the cell is the best place as we have to pass in whether it is a drop down or editable on the row level. I'd advocate for the row level myself
- Looks like the best spot on a row is going to be on the virtualized table with subrows but I'm not sure that is going to be the right spot. 
- The variable size grid might be the right spot. Except it doesn't have an onClick method
- Whatever we do we will have to have the ability to make the cells editable. 
- The rows seem to live in the table.tsx, not sure if we can change that. 
- Looks like we actually should be in row.tsx? Damn this is so complicated.s
- Finally found where I need to be I think - in the row.tsx at the very bottom there is an onClick for the grid for each row - I can pass that down, probably will have to pass stuff back up so I can redo the rendering.
- The subrows complicates things because we need to make the whole row, including the subrow, clickable


## Goal 

Build out the frontend so that a user can override a price record while price editing to adjust specific price points to exactly what is needed for Hybris.

## Design 
[https://zpl.io/VYevxod]

## Requirements 
 * A user can right click on a product row while price editing to open a menu with the override option
 * A pop-up appears to confirm the user wants to override the price record
 * Once in override mode, additional fields appear

New ones from Ryan: 
-   The user can enter override mode for a row on the page
-   That row then allows the user to edit more than just the starting price
-   The user can continue to edit _other_ rows using the standard starting point and price calcs
-   The row that is in override mode will **always** be in override mode, until the Sandbox is published

## Implementation Hypothesis
* Use the "isOverriden" flag calculated on the backend when deciding to show a row in override mode
* Make sure the apollo client gets refreshed with a new value for the "isOverriden" flag whenever the first price point is overridden on a price edit record

#Fusion