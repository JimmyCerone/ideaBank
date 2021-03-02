#PriceEditing #Fusion #Amway

Add Changed By/Date to Sandbox Price Edit Table

## Next Steps
- [x] Mention questions about "System" and lastModifiedBy at standup
- [x] Tackle the UI stuff

- [ ] Run queries against Joe database to see if there are problems with the query on price edit report. 

Problems:
- The query is hard to write alone in tableplus
	- I worked with Jordan to try to get the query from the terminal by running the Joe environment from my terminal. The database seems weird and/or it's not connecting (stuck on the terms & conditions screen)

Ran remotely: yarn dev & docker-compose up. Also tried to run db:migrate:latest but it said the "pool" was full.

What else can I try? I'm stumped af. Do it locally. 

## Wednesday Jan 27
- [x] Fix errors described in notes from the day before
- [x] turn on / change correct feature flags
- [ ] Write tests for multiple sandboxes with changes to mirs.
- [ ] Add a couple of sandboxes
- [ ] Run remote script to update the #Database
	- [ ] Insert mpv and mir for all markets for just one sandbox
- [ ] Update testing instructions to match these below:

Testing Instructions:

\* Make sure you have access to the Australia Market as the Sandbox will be configured for that market.

1.  Navigate to the Price Edit Page
2.  Choose the "Unchanged" Sandbox
3.  Visually confirm that the 2 new columns, "Changed By" and "Changed At" are present.
4.  Verify in the background color and borders of the 2 columns match the designs.
5.  Verify that all the entries are empty.
6.  Choose the "Changed" Sandbox
7.  Confirm that each row has data for both "Changed By" and "Changed At".

Note:

\- The story which implements editable price fields is not present in this story (not yet in develop).

## Tuesday Jan 26
![[Screen Shot 2021-01-26 at 4.28.25 PM.png]]
- Sandboxes / other options aren't loaded on the remote. 
- Attempted another push to the remote branch 
	- This failed... ![[Screen Shot 2021-01-26 at 4.50.19 PM.png]]

![[Screen Shot 2021-01-26 at 4.32.20 PM.png]]
- The insert script failed for a reason I'm not sure of
- I'm fairly sure that it was the DATABASE_URL - I wasn't sure where to find this and the one in the command didn't work for reasons seen above. 

#SshTunnel to get to a #RemoteDatabase for updating. Works for any development database.

First, run the following command:

`ssh -L 54320:fus-tf-shared-postgres-db.cluster-creogmmhut8d.us-east-1.rds.amazonaws.com:5432 -o ExitOnForwardFailure=yes -o ServerAliveCountMax=3 -o ServerAliveInterval=15 -p 2222 jason@127.0.0.1`

Then in another #Terminal tab, run the following command, prefixed with the DATABASE_URL for the remote db: 

`DATABASE_URL=``[postgres://db_access](postgres://db_access)``:xcAeQN4FgxvepL6cQaK3JNBJiXE4xsUV9ULgxQCtqwD8E37KvxUv7vsRmFZTezG2@localhost:54320/joe?ssl=true insert-mpv-dp-overlay-record-for-all-products-in-market --marketid 979f0814-8185-46c0-92fd-1d3525046a08 --sandboxid b5e7ba6c-09d6-475d-bdb6-3fcde9bb7a8c --abopriceltax 33`

More generally the command is this (with any script specified): 

`DATABASE_URL=``[postgres://db_access](postgres://db_access)``:xcAeQN4FgxvepL6cQaK3JNBJiXE4xsUV9ULgxQCtqwD8E37KvxUv7vsRmFZTezG2@localhost:54320/grace?ssl=true <script>`

Todos: 
 - [X] Rendering issues (the cells appear out of order)
 - [X] Blank case testing
	 - There needs to be handling for the case where the file hasn't been changed at all and nothing comes back from the query
	 - We should return an empty string...
	 - Would we change this in the #getPriceEditReportQuery?


## Questions
- Is there any case in which a user's change will be marked as a change by "System"?
- Are the lastModifiedBy and lastModifiedAt fields updated in the mutation?
- How can we set this up for review? 

#Error: 

- #Norwex-with-silver should run yarn build before it runs migrations. Right now, it doesn't, so I should have done that manually. Since I didn't, the compiled JS was out of date and expecting things that weren't in the updated norwex.

#Terminal:

- insert-mpv-dp-overlay-record --marketproductvariantid 00151829-a01c-45b1-9137-9ecede43c783 --sandboxid 3c106a0f-1f7a-43e5-b6e9-a8e235d0b899 --abopriceltax 50


**Blank Case Testing**
	- I think I need to tweak the query below: 
		```
		 CASE
           WHEN mpv."lastModifiedAt" > mir."lastModifiedAt" then mpv."lastModifiedAt"
	         ELSE mir."lastModifiedAt"
          END as "changedAt",
          CASE
           WHEN mpv."lastModifiedAt" > mir."lastModifiedAt" then mpv."lastModifiedBy"
	         ELSE mir."lastModifiedBy"
		      END as "changedBy" 
			  ```
			  
My guess is that I need to add a case where if there is neither a date for MPV nor MIR, then I I return an empty string. I'm not sure how to do that. I'm going to use tableplus to work that out.

Here's my attempt at an improved query: `SELECT
	CASE WHEN "MarketProductVariant"."lastModifiedBy" = "System" THEN
		CASE WHEN "MarketItemRevision"."lastModifiedBy" = "System" THEN
			''
		ELSE
		ELSE
			CASE WHEN "MarketProductVariant"."lastModifiedAt" > "MarketItemRevision"."lastModifiedAt" THEN
				"MarketProductVariant"."lastModifiedAt"
			ELSE
				"MarketItemRevision"."lastModifiedAt"
			END AS "changedAt",
			CASE WHEN "MarketProductVariant"."lastModifiedAt" > "MarketItemRevision"."lastModifiedAt" THEN
				"MarketProductVariant"."lastModifiedBy"
			ELSE
				"MarketItemRevision"."lastModifiedBy"
			END AS "changedBy"
		FROM
			"MarketProductVariant",
			"MarketItemRevision"; `
			
			
	