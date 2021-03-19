{panel:title=Goal}
{panel}
{panel:title=Design}
[https://zpl.io/adg6jZn] - Initial view of the table
 [https://zpl.io/VKeO5yJ] - Editing a price point
 [https://zpl.io/VqNjgv4] - Cells with a change
 [https://zpl.io/VqNjgv4] - Differences between current & changed price points
{panel}
{panel:title=Requirements}
 * Make the #PreferredPriceLessTax cell editable
 * When the user enters a new value for PreferredPriceLessTax and focuses out of the cell, the entire price record is recalculated
 ** This triggers the save animation on the 'Save' button in the top right
 ** While the dependent price points are being recalculated, show the standard data loading state (gray bar in the cell)
 ** Prioritize performance of recalculations (<1s from change to update as an initial benchmark)

 * The user sees the calculated values for changed fields in the "Changed" row. Those cells have a yellow background (see design){panel}
{panel:title=Out of Scope}
The mutation to re-calculate price points (completed in https://jira.amway.com:8443/browse/FUS-1516)
{panel}
{panel:title=Implementation Hypothesis}
 * The mutation to update price points returns the market item revision data with the updated price points to the client, thus refreshing the apollo cache and allowing the user to see re-calculated price points
 * Look at the sales bundle price editing component for ideas on how to show a data loading state on the frontend while the mutation is doing the re-calculations in the background
 * As part of https://jira.amway.com:8443/browse/FUS-1628 added a disabled property on the changed row.  The PreferredPriceLessTax cell should only be editable if disabled is false.{panel}
{panel:title=Feature Flag}
{panel}
{panel:title=Requires Audit?}
{panel}
{panel:title=Questions for Planning Team}
{panel}
{panel:title=Questions for Delivery Team}
{panel}

#Fusion