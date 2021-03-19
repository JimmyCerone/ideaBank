Steps to Reproduce: 
1. Add a new local sales item in a sandbox
2. See that BV/ABO (Less Tax) Ratio is an input instead of a dropdown

## TODO 
- [ ] Add to the `modules/client/pages/price-edit/__tests__/add-local-sales-item-to-sandbox.test.ts` a test to check which fields are designated (if possible) to check theory
	- No way to check if it's designated, but it does seem to be the default. Not sure if this is exactly what is happening on the front end. 
	- [ ] Test front end and check back end as you do. 


Questions: 
- What would cause this? 
- Is this a front end handling issue or a backend creation issue?
	- Subquestion and probably the root is - what determines how this gets displayed? 
		- Could it be thinking it is in override mode?
			- So you can get into this state if you change BV while in override mode. So I'm betting this is it. Not sure why. 
			- Why would it think it's in override mode? 
				- Seems to come from the `InputDropdownCell` Component
					- In there, if the row type is `Changed` and it isn't disabled AND if the field is `designated`, an input is shown. 
				- So. The cell must think the ratio is `designated`, which leads us to the question below. 
		- What is unique about a local item? How does it differ than a "normal" item? 
			- It seems like the ratio is showing up as `designated` for a new local sales item. Not sure why. 
			- Why is the ratio showing up as `designated` for a new local sales item? What is the process for creating one? 
				- The creation process happens in the `AddLocalSalesItemToSandbox` mutation. 
- ~~Does it persist?~~
	- Yes this persists even after a reload

#Fusion