
## Wednesday Jan 27
 - [x] Create a migration to add a column to the market item revision version & market item revision dp overlay
	- Everything on the #VersionTable is a field we expect to change over time. All the fields in the "main" table are expected to stay the same over time.
- [ ] Update DBO import, real time fusion sync, & JDE Importer
	- Write tests first for all 3 of these
	- Whenever any of the following 3 fields are changed, we want to update the columns we added
- [ ] Discuss how / if to test the date time on the [[Source to Market Item Revision Importer]] test.

- [x] Finish DBO importer 
	- [x] Make it so that unless Factory cost or hybrid cost aren't changed, then nothing gets changed
	- [x] Make updates to the margin importer


[[Add Cost Last Updated By And At To Market Item Revision]]