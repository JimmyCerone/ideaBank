## [[2021-05-25]]

Testing Instructions:

1.  Navigate to the Change Access page.
2.  Select the Affiliate User Role and the India Market.
3.  Verify that the User does not have access to the Edit Product page.
4.  Navigate to the Change Access page.
5.  Select the Global User Role.
6.  Verify that the User does not have access to the Edit Product page.
7.  Navigate to the Change Access page. 
8.  Select the Affiliate User & Portfolio Manager User Roles and the India Market.
9.  Navigate to the Edit Product page while on Master.
10. Verify that Product Attribute, Product Status, Market Product Variant Editing, Add Markets, Edit Pricing are all disabled.
12. Select an In Progress Sandbox with the Market of India from the drop down menu.
13.  Verify that Product Attribute, Product Status, Market Product Variant Editing, Add Markets, Edit Pricing are all enabled enabled for the Sandbox Market.
14.  Navigate to the Edit Product page and select a Sales Bundle product. 
15.  Verify that Bundle Add Products is enabled based on Product's Status (Draft = Enabled, Established = Disabled) and the Bundle Add Variant is enabled only for the Sandbox Market.
16.  Navigate to the Change Access page.
17.  Change your Market to China.
18.  Navigate to the Edit Product page for an In Progress Sandbox with a Market that is not China. 
20.  Verify that Product Attribute, Product Status, Market Product Variant Editing, Add Markets, Edit Pricing are all disabled.
21.  Navigate to the Edit Product page and select a Sales Bundle product.
22.  Verify that Bundle Add Products is disabled based on Product's Status (Draft = Enabled, Established = Disabled) and the Bundle Add Variant is disabled.
23.  Navigate to the Change Access page.
24.  Change your Role to Global Portfolio Hierarchy & Attribute Assigner.
25.  Navigate to the Edit Product page for an In Progress Sandbox. 
26.  Verify that Product Attribute, Product Status, Market Product Variant Editing, Add Markets, Edit Pricing are all enabled enabled for the Sandbox Market.
27.  Navigate to the Edit Product page and select a Sales Bundle product in the Sandbox Market. 
28.  Verify that Bundle Add Products is enabled based on Product's Status (Draft = Enabled, Established = Disabled) and the Bundle Add Variant is enabled only for the Sandbox Market.
29.  In the Sandbox drop down, select an 'Awaiting Approval' Sandbox.
30.  Verify that all editing is disabled.

## [[2021-05-20]]
- [x] Fix 2 other tests
	- [x] These were flaky
- [ ] Add role to page
	- [ ] Check and see if that test passes
	- [ ] Make the role selected by default
- [ ] Update cypress tests to include testing for:
	- [ ] New role
	- [ ] global products

## [[2021-05-19]]

- [x] Fix cypress tests
	- Weird failure. It seems that the whole left panel is disabled when a user is in the Sandbox and has all the permissions. Not sure that is in the scope of our story? Is that product attributes? Seems like they should not be disabled...![[Screen Shot 2021-05-19 at 12.37.54 PM.png]]
- [ ] Fix 2 other tests
- [ ] Add role to page
	- [ ] Check and see if that test passes
- [ ] Update cypress tests to include testing for:
	- [ ] New role
	- [ ] global products

## Tests
- [ ] modules/client/pages/create-product/__tests__/add-sales-bundle-mutation.test.ts
	- Updated the test to include sandbox support but fails on a unique key error which makes me think it's trying to insert something on master, which makes me think we need andy's changes for this to pass. 
	- ![[Screen Shot 2021-05-13 at 11.51.31 AM.png]]
	- CONFIRMED ANDY PROBLEM - there is no `ProductSalesBundleEntry_DPOverlay` table as of yet.
- [ ] 

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