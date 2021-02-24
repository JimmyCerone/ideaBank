## Learning 
- The difference between the theory and the practice of services - what details to touch up on
- Break projects down feature by feature to simplify what services might be used where. 
	- Easy to compare alternatives - what if I made an Azure equivalent?

## Notes

- Went the Dynamo S3 route instead of the Aurora route. 
	- What's the difference here? 
- Dynamo DB connected to event bridge instead of mobile side
- Event bridge listener could be the first to break if there is a crazy amount of package updates in dynamo
	- Listener on every dynamo update. We'd probably throw that on a queue with an autoscaling pool of workers to pull stuff out of that queue. 
- We are fine on the VPC stuff because we don't use aurora serverless. Our setup does not require a VPC. 
	- One of the big tradeoffs in AWS is whether to use VPC. That adds a lot of overhead in terms of managing IP address. 
	- Downside is no sql
- Choice for Joe would depend on the team he was working worth. 
	- For Atoms, he'd do Dynamo because they could handle low level stuff w/ nosql
	- For non atoms, he'd do aurora because sql is more commonly known
	- Dynamo was used on Healthy Minds 
		- One user stuff and users aren't relating to each other so this can be used
		- Over time the business wanted more and more complex queries built, which started to add up
	- Fusion forced us to a VPC, which forced us to work with Amway's networking team to have to do networking stuff