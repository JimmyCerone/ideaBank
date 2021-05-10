## TODO
- [x] Clarify product status question with Taylor
- [x] Determine what level to write tests at
	- [x] Cypress? Unit tests? Where to put the tests?
		- GraphQL API tests because most of what we are doing here is on the back end in that things happen then get passed up to the UI as a simple "enabled" or "disabled"
		- Cypress wouldn't hurt in a couple of spots
- [x] Find where these roles are enforced in the code base
		- Goal is to decouple roles and abilities. So set someone's abilities up front based on their role and then use the abilities to determine what they can do. 
		- Seems to be all over the place. 
- [x] Ask about EmptyResult component (fixing translations)
- [ ] Write out tests on `modules/client/graphql/__tests__/get-product-report-row-query.test.ts`
- [ ] Write it.todo's for `modules/client/pages/edit-product/product-details/product-markets/__tests__/get-market-product-variants-for-product-markets.test.ts` 


## Questions
- What's the difference between ManageProductAttributes and ManageLocalProductAttributes?
- How much do I need to know about roles and abilities to do this work? How does my chart translate to abilities?
	- How much do I need to write tests? That's the answer to this question. 