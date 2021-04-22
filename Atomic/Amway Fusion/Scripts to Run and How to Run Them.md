When running against #ReviewEnvironments, you chave to run `source .env.post-deploy`

## Deploying to Review
1.  Run down\_for\_maintenance
2.  Restore Snapshot from Production RDS Snapshot.
3.  Configure cluster, rename old review DB and give previous name to the new Review DB.
4.  Run \`source .env.affiliate-data-review && okta-auth && source .env.post-deploy && echo $DATABASE\_URL\`
5.  Run make deploy\_lambdas
6.  Migrate db.
7.  Run export LAST\_SUCCESSFUL\_MAIN\_DMS\_RUN="2021-04-14T18:04:26.562000-04:00"
8.  Run node dist/scripts/load-data-from-dbo-to-public.js
9.  Run  ./scripts/shared/import-market-categories
10.  Run ./scripts/shared/load-geography-hierarchy
11.  Run ./scripts/shared/price-record-editing-setup
12.  Run ./scripts/shared/populate-market-pricing-configuration-table
13.  Run download-and-unzip-raw-jde-data
14.  Run ./scripts/shared/load-csv-to-raw-jde-schema raw-jde-data/LocalReport.csv raw-jde-data/GlobalReport.csv raw-jde-data/80658.csv
15.  Run ./scripts/shared/insert-jde-load-record
16.  Run ./scripts/shared/load-data-from-jde-to-public
17.  Run ./scripts/shared/load-data-from-forecasting-to-public
18.  Run make deploy\_react\_app

## Deploying to Personal Review Environment
1. SSH into review environment
 	- `Review 2`
		- `ssh -L 54320:fus-tf-shared-postgres-db.cluster-creogmmhut8d.us-east-1.rds.amazonaws.com:5432 -o ExitOnForwardFailure=yes -o ServerAliveCountMax=3 -o ServerAliveInterval=15 -p 2222 jimmy@127.0.0.1`
2. Run `source .env.review2 && okta-auth && source .env.post-deploy`