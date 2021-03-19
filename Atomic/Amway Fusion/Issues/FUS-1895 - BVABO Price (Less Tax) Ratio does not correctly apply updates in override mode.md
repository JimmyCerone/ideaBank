Steps to Reproduce: 
1. Enter the override mode for an item
2. Change the BV value for that item
3. See that BV/ABO Price (less tax) turns into an input and contains the resulting calculation
4. Enter a new value into BV/ABO Price (Less Tax) and save that change
5. See that the value you entered is divided by 100


Notes:
- Works correctly for other ratios, but not for BV/ABO ratio. 
	- Verified that this is what I'm seeing on the front end. 


Questions:
- Could this be connected to [[FUS-1892 - BVABO Price (Less Tax) Ratio is not a dropdown for new local items]]? - that seems to be an issue for override status. May not be connected but could be near the same place in the #Code. 
- Is this a front end or backend issue? Is it related to the updates made to percentage handling? 
- ~~Is this an issue with the type of the cell? ~~
	- Doesn't seem to be. The type is the same as all the others. 
- How does this cell differ from the other ones? 
	- Visually there is no difference. Same type and everything - makes me think this is on the backend? 
	- The two components in play are the:
		- `CombinedLoadingNumberCell`
		- `InputDropDownCell`