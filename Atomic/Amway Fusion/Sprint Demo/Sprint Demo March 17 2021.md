# Price Editing
## 1886 - F - Lydia 
Quick Version: Price editing page reflects sandbox status saving users from incorrect states

Steps:
1. Start with an in progress sandbox and note the editable cell in preferred price less tax
2. Navigate to awaiting approval sandbox
3. Note that Preferred Price Less tax is now read only
- Same is true for published and archived sandboxes

## 1877 - B - Lydia
Quick Version: Cost fields are editable on the Price Edit Table

Steps: 
1. Select a sandbox and navigate to price edit page
2. View the cost fields and see they are editable (MC, Product Cost, and Other Affiliates COS)

## 1812 - F - Lydia
Quick Version: Users can enter any value they'd like to starting price points without rounding being applied

Steps: 
1. View the price edit page
2. Pick a sandbox
3. Change the preferred price less tax for a MIR to a price with 2 decimal points.
	- See the value entered for the preferred price tax does not round
	- See the difference row shows the incremental update

## 1851 - B - Meredith
Quick Version: Price edit updates occur without refresh once again. 

Steps: 
1. Navigate to the price edit page
2. Select a future sandbox
3. Edit a price
4. See it update without refreshing the page

Question: 
- What was the problem here? I don't quite remember. 

## 1852 - B - Lydia
Quick Version: The "Only Changed" toggle can now handle local sales items. 

Steps: 
1. Navigate to the price edit page. 
2. Select a sandbox
3. Add a local sales item
4. Click on the "Only Changed Items" toggle
5. See the page successfully load. 

## 1865 - B - Lydia
Quick Version: Summary totals now update when the only changed items toggle

Steps: 
1. Navigate to a sandbox and go to the price edit page
2. Make a price change
3. Toggle 'Only Changed Items'
4. See that the summary information at the bottom of the page now updates

## 1853 - B - Lydia
Quick Version: BV/ABO Price Less Tax Ratio is now displayed as a ratio on the price edit page as opposed to a percentage. 

Steps: 
1. Navigate to price edit page
2. Select a future sandbox
3. See that the BV/Abo Ratio is now a ratio instead of a percentage

## 1797 - F - Lydia
Quick Version: Users are no longer able to edit pricing on a sales bundle in the price edit page

Steps: 
1. View the price edit page
2. Select a valid sandbox
3. Filter by sales bundle
	- See that the rate/ratio drop down are disabled.
	- Right click to override and confirm the same. 

# Edit Product Page
## 1791 - F - AITS
Quick Version: When you navigate to the edit product page, it expands the row for the sandbox market. 

Steps: 
1. Navigate to the edit product page after selecting a sandbox
2. Search a product which has the market of the sandbox
3. Verify that the market is expanded while all other markets are collapsed. 

## 1882 - F - Lydia
Quick Version: MPVs can be added to finished goods and inactive products

Steps: 
1. Navigate to the product edit page
2. Select the In Progress Sandbox
3. View Sales Item w/ SKU 100000 and notice that it is established
- There is a bug prevent a full demo. When adding a market to a sales item, the page crashes due to a GraphQL timeout. 
- The bug can be found here: https://jira.amway.com:8443/browse/FUS-1898

# Report Page
## 1866 - B - Lydia
Quick Version: Restores the users ability to edit the price columns displayed on the report page.  

Steps: 
1. Navigate to the report page
2. Go to manage columns by selecting the gear icon on the top right
3. Select all pricing columns
4. See there is no error

# Sandbox
## 1804 - F - AITS
Quick Version: Users can change the name of a sandbox

Steps: 
1. Navigate to the sandbox page
2. Click on a sandbox that is in progress or awaiting approval
3. Edit the name on the sandbox drawer
4. Confirm the name has been changed
5. Note the edge cases
	- Cannot change name for published or archived sandboxes
	- Price approver role cannot change sandbox status
	
## 1864 - B - Lydia
Quick Version: The ratio values are visible to the user for the sandbox snapshot

Steps: 
1. Navigate to a published sandbox
2. Click "View Sandbox Snapshot"
3. See that the ratios are displayed as either the assigned or designated classification rates (all numbers, no "-")

# Developer Experience
## 1862 - B - Lydia
Quick Version: Import Market Consumption Tax Configuration and Classification script doesn't populate all MPVs 

Steps: None. Note as a DX. 

## 1854 - F - Lydia
Quick Version: Percentage points stored as decimals on the back end. 

Steps: None. Note as DX / back end.