- Problem when running server
	- Problem with type checking
		- TS_NODE_FAST=1 flag before command
	- Problems running out of memory
		- https://atomicobject.slack.com/archives/C03G0RE2R/p1617806674086100
	- Run yarn build
		- Fix build errors
	- Run yarn db:migrate:latest
		- Norwex-with-silver
	- Run yarn
	- Rm -rf node_modules
		- yarn
	- rm -rf dist
		- yarn build
	- Things to do when stuck
		- What did I do to get here?
		- What can I do next? 
		- How can I help others?
			- Catch up on email
			- Catch up on Slack
		- Check Twitter (if nothing else can be done)
		- Remember [[202104081532 - Value as a consultant is unevenly distributed]]
	- Long Running Processes
		- Start at the end of the day (if possible)
	- Errors out on review
		- Check lambdas error

## Deployment to Review
1. `source .env.affiliate-data-review && okta-auth && source .env.post-deploy && echo $DATABASE_URL`
2. Make sure infrastrure is in sync  `apply $DEPLOY_CONFIGURATION $DEPLOY_WORKSPACE` (only run once)
3. run `down-for-maintenance`
4. Reply server code
	1. `Make deploy lambdas`
5. Migrate db
	- ssh into db and prefix with DB Url
6. Deploy client code
	1. `Make deploy react app`


## Memory Errors
1. Check RAM usage with the Activity Monitor / Task Manager
	- ![[Screen Shot 2021-04-14 at 10.11.01 AM.png]]
2. Quit unnecessary apps that are using lots of RAM (quitting docker if running `yarn build` or `yarn dev` is often helpful)
3. Run the command with the following prefix: `NODE_OPTIONS=--max-old-space-size=4096`
4. If that fails, attempt again with `NODE_OPTIONS=--max-old-space-size=8192`
5. Alternatives if none of the above work
	- `yarn build` and `yarn dev` run many node processes concurrently. Consider running these sequentially and manually to lower the RAM usage. 
	- Run `rm -rf node_modules` then `yarn` to confirm that all packages are correctly installed. Rerun command with prefix above.


## Memory Issue Fix
- Building the server is what runs out of memory
	- `server.config.js`
		- `scriptentry`
		- `lambdaentry`
		- Build all scripts
- Problem probably lies with the shared scripts
	- when doing a `yarn build` we don't have to build every single script
		- split scripts directory into two camps
			1. Essential scripts
				- `post-migrate` is essential
			2. Useful scripts (db-setup stuff)
				- These are in a separate command called `yarn build scripts`


## Domain vs. Record
- Usually we have these mirror each other. 
- Records layer is how we model things in the db
	- Has to reflect the database
	- Data loaders would go here - it worries about caching and stuff
- Domain entity is how we model these things for the business team. 
	- Does not have to reflect the database
	- Changes to business language would happen first here. 
	- Start here, then move to the record layer