# Outline
- Price Edit Improvements
	- Override Retail Price Including Tax on new Local Sales Item now works (1980)
	- Records are recalculated for the user when they: (1894) 
		-   Hits enter, OR
		-   Hits tab
		-   Anything that would unfocus the cell
	- Users now see a visual indication when a Product is in Price Override mode on the Price Edit page. (1946)
	- When a user toggles only changed, it updates the hierarchy filter counts. (1867)
	- User sees different starting price point for price editing based on their market (1971, 1970, 1969)
- Edit Product Page Improvements
	- Users can now change the Market Product Variant Suffix on the Edit Product page without crashing.  (1910)
	- Users are able to add a Market to a new Local Sales item without the page crashing. (1904)
- Report Page Improvements
	- Users can now view Item Details for a new Local Sales Item on the Report page (1949)
	- Market Consumption Tax Rate and Preferred Price Discount appear as expect on the Report page for India (1913)
- Publishing Improvements
	- Hierarchy assignments for new Local Sales Items now Publish successfully (1960)
	- Sandbox status updates in the UI after publication without a refresh (1948)
	- Local Sales Items are successfully published and viewable on Report and Edit Product pages (1926, 1921)
	- Users can now publish a sandbox with a local sales item (1888)
- Improved Testing by Adding System Tests
	- Cypress (1906)
	- Price Record Editing (1859)
	- Creating Local Sales Item (1860)
- Audited Product Root Validations (1881)



## 1980 - B - Lydia & Jordan
### Quick Version
- Users are now able to override the Retail Price Including Tax on a new Local Sales Item.

### Steps
1. Add new local sales item to sandbox
2. Go to Price Edit page and find new item
3. Override the Retail Price including tax
4. No crash!



## 1894 - B - Nick & Mike
### Quick Version
- Records are recalculated for the user when they: 
	-   Hits enter, OR
	-   Hits tab
	-   Anything that would unfocus the cell

### Steps
1. Navigate to the Price Edit page.
2. Edit a price and click enter
3. Edit a price and click tab
4. Edit a price and click away



## 1946 - F - Lydia & Jordan
### Quick Version
- Users now see a visual indication when a Product is in Price Override mode on the Price Edit page. 

### Steps
1. Navigate to the Price Edit page. 
2. Right click on a Product, click Override and select yes. 
3. Note the UI change. 


## 1867 - B - Nick & Mike
### Quick Version
- When a user toggles only changed, it updates the hierarchy filter counts.

### Steps
1. Navigate to the Price Edit page with a Sandbox selected.
2. Change the price of a Product.
3. Toggle Only Changed. 
4. See the the sidebar filter counts have been updated.



## 1971 - F - Lydia & Jordan
### Quick Version
- User sees different starting price point for price editing based on their market. 

### Steps
1. Navigate to the Price Edit page. 
2. Select US Sandbox from the selector. 
3. Note that the Retail Price Including Tax column is the starting price point and is editable. 
4. Select India Sandbox from the selector. 
5. Note that the Preferred Price Less Tax column is the starting price point instead of the Retail Price Including Tax. 



## 1970 - F - Lydia & Jordan
### Quick Version
- Support for different starting price points when doing pricing calculations is now supported. 
	- Added support for: 
		-   Preferred Price (Less Tax)
		-   Retail Price (Inc. Tax)
		-   ABO Price (Inc. Tax)
		-   ABO Price (Less Tax)

### Steps
- None - back end



## 1969 - F - Lydia & Jordan
### Quick Version
- Laid the groundwork for the price calculation updates of 1970

### Steps
- None - back end.


## 1910 - B - Meredith & Jimmy
### Quick Version
- Users can now change the Market Product Variant Suffix on the Edit Product page without crashing. 

### Steps
-   Create a sandbox and add a local sales item
-   Go to the Edit Product page and Add Market
-   Select a market and see that it is successful
-   Change the suffix of the new product to any acceptable input
-   See that the update is successful and the app does not crash


## 1904 - B - Meredith & Jimmy
### Quick Version
- Users are able to add a Market to a new Local Sales item without the page crashing. 

### Steps
-   Create a sandbox and add a local sales item
-   Go to the Edit Product page and Add Market
-   Select a market and see that it is successful



## 1949 - B - Meredith & Jimmy
### Quick Version
- Users are now able to view the details of a new local sales item on the report table without crashing

### Steps
1. Add new local sales item to sandbox  
2. Go to Report page in the context of the sandbox.  
3. Switch the effective date time to after the effective date of the sandbox  
4. Try to view the details of the new sales item  
5. See that Fusion doesn't crash.



## 1913 - B - Meredith & Jimmy
### Quick Version
- Market Consumption Tax Rate and Preferred Price Discount appear as expect on the Report page for India

### Steps
1. Navigate to the Report page. 
2. Observe that neither Market Consumption Tax Rate nor Preferred Price Discount are null. 



## 1960 - B - Jimmy & Meredith
### Quick Version
- Hierarchy assignments for new local sales items publish with the publication of a sandbox.

### Steps
1.  Create a new Sandbox
2.  Add a new Local Sales Item to the Sandbox
3.  Set the new Product's Product Hierarchy, Brand Hierarchy, and Attributes
4.  Verify the Product Root is established and the MPV is active.
5.  Publish the Sandbox
6.  Visit the Report page (after the Sandbox effective date) and search for the new Local Sales Item
7.  See that the product root hierarchies and attributes are all correctly assigned




## 1948 - B - Meredith & Jimmy
### Quick Version
- Sandbox status updates in the UI after publication without a refresh (used to require a refresh)

### Steps
1.  Create a sandbox
2.  Publish sandbox and see that the status changes when the publish completes successfully



## 1921 - B - Lydia & Jordan
### Quick Version
- Local Sales Items added to a Sandbox are now published successfully. 

### Steps
-   Navigate to the Sandbox Management page
-   Create a new Sandbox
-   Add a Local Sales Item to the Sandbox.
-   Navigate to the Sandbox Management page
-   Publish sandbox
-   Click to "View Sandbox Snapshot"
    -   Toggle to view by "only changed" item, see the local item is viewable
-   Navigate to the Report page and search by Sku Root
	-   See that the item is visible



## 1926 - F - Lydia & Jordan
### Quick Version
- When a Sandbox with a Local Sales Item is published, you can now see the Local Sales Item on the Report page. 

### Steps
-   Navigate to the Sandbox Management page.
-   Create a new Sandbox (or find an In Progress Sandbox with an Effective Date in the future)
-   Navigate to the Price Edit page and select the Sandbox created or found above.
-   Add a Local Sales Item to the Sandbox. (Take note of the Sku Root)
-   Navigate back to the Sandbox Management page.
-   Publish the In Progress Sandbox.
-   Navigate to the Report page.
-   Change the Effective Date to after the published Sandbox Effective Date
-   Filter by the Sku Root of your newly created Local Sales Item
-   Observe the newly created Local Sales Item



## 1888 - B - Meredith & Jimmy
### Quick Version
- Users can now publish a sandbox with a local sales item (crashed previously)

### Steps
1. Create a new sandbox
2. Add a local sales item
3. Publish the sandbox




## 1906 - F - Jordan & Lydia
### Quick Version
- Improved the developer experience for Cypress testing for System tests. 



## 1860 - F - Meredith
### Quick Version
- Created System Test for Creating Local Sales item



## 1859 - F - Lydia & Jordan
### Quick Version
- Created System Test for Price Record Editing



## 1881 - F - Lydia & Jordan
### Quick Version
- Product Root input validation aligns with expected rules across the application.
