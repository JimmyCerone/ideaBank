## TODO 
- Fix all tests that say override 

## Goal
Create the backend support for overriding a price record while price editing to adjust specific price points to exactly what is needed for Hybris. 

## Requirements
- Price record calculation is modified to only recalculate certain parts of the pricing chain. 
- New mutation for price changes that move "down" the chain in the diagram attached. Then tests are needed to make sure this _only_ changes things downstream. 
- Update the graphql query tests to ensure that the "isOverriden" field appears just fine. 


## Questions
- How much of this was already done? Where we changing something that already existed? 
- What's the difference between the forward and reverse directions? Is it that reverse is only for overwriting and forward is only for changing price points?
	- Not quite. Reverse changes the ratio when you override a price point. In the previous story we did multiple directions, but didn't change the ratios.
- What was the original story that started all the recalculation stuff? How long ago was it created? What were the critical decisions? Did it do the "forward" direction? 
	- 1644 [[FUS 1644 Can Calculate Price Points on a Market Item Revision]] was the original story that recalculated stuff. 

## Implementation Hypothesis
I'm struggling with this because I'm not sure I could have come up with it on my own. I suppose it's obvious that you need to have some way of knowing whether something has been overwritten or not, but I'm not sure I would have made that jump or known where to put that field. 

> Currently, editing a price point dispatches a mutation to re-calculate all price points for the sandbox price record ([https://jira.amway.com:8443/browse/FUS-1516](https://jira.amway.com:8443/browse/FUS-1516 "Follow link")). Make this mutation allow for the overriding of price points.

- What does it mean, "Make this mutation allow for the overriding of price points"? How is that any different than recalculating? Does it just mean we are now storing it somewhere? Were we changing nothing last time / not storing the changes?
	- We were always storing it before. Now if we overwrite something, we want to prevent it from being recalculated. If you change ABO, you want to make sure that changing Preferred Price doesn't blow away that change. 

> For each price point on the market product variant table, add an "is overridden" columns, for example for the bv column there should be a corresponding 'bvIsOverridden' column

- Why do we need this? Why not use the Overlay style? 
	- Because we need to make sure things don't change after they've been overwritten. 