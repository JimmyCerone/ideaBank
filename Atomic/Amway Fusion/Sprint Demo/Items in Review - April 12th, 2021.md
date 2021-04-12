#### Outline


#### 1949
##### Quick Version
- Users are now able to view the details of a new local sales item on the report table without crashing

##### Steps
1. Add new local sales item to sandbox  
2. Go to Report page in the context of the sandbox.  
3. Switch the effective date time to after the effective date of the sandbox  
4. Try to view the details of the new sales item  
5. See that Fusion doesn't crash.

#### 1948
##### Quick Version
- Sandbox status updates in the UI after publication without a refresh (used to require a refresh)


##### Steps
1.  Create a sandbox
2.  Publish sandbox and see that the status changes when the publish completes successfully

#### 1888
##### Quick Version
- Users can now publish a sandbox with a local sales item (crashed previously)

##### Steps
1. Create a new sandbox
2. Add a local sales item
3. Publish the sandbox

#### 1910
##### Quick Version
- Users can now change the Market Product Variant suffix on the Edit Product page (previously caused a crash)


##### Steps
-  Create a sandbox and add a local sales item
-   Go to the Edit Product page and Add Market
-   Select a market and see that it is successful
-   Change the suffix of the new product to any acceptable input
-   See that the update is successful and the app does not crash

#### 1960 
##### Quick Version
- Hierarchy assignments for new local sales items publish with the publication of a sandbox.

##### Steps
1.  Create a new Sandbox
2.  Add a new Local Sales Item to the Sandbox
3.  Set the new Product's Product Hierarchy, Brand Hierarchy, and Attributes
4.  Verify the Product Root is established and the MPV is active.
5.  Publish the Sandbox
6.  Visit the Report page (after the Sandbox effective date) and search for the new Local Sales Item
7.  See that the product root hierarchies and attributes are all correctly assigned