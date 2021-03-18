![[Screen Shot 2021-01-29 at 2.03.29 PM.png]]

![[Screen Shot 2021-01-29 at 2.05.39 PM.png]]

![[Screen Shot 2021-01-29 at 2.05.58 PM.png]]

![[Screen Shot 2021-01-29 at 2.07.02 PM.png]]

![[Screen Shot 2021-01-29 at 2.13.22 PM.png]]

Questions: 
- What would your first step be? 
- What wouldn't you do? 
- What details can you get bogged down in? 
	- "And then I will go to the web console and write some code"
		- NO SERVERS!
- What does "some" packages mean?
	- Keeps track of a select number of packages you specify.
- How do you stay out of the weeds? 
	- He doesn't want to have to manage a server at all. If there is a server somewhere that somebody at Atomic needs to keep track of, this project is not built how I want it to be. 
	- You probably will end up hating yourself at a certain point when you go to build it. Luckily we won't be building this and kind of can't. That's one restriction. 
	- Think more whiteboard diagram and less weeds.

- Are there any security restraints?
	- Data is accessible to all Atoms, but only atoms. 
	- User management is a stretch goal. 
- What prior experience does the company have with AWS? Are there any support options we should keep in mind? 
	- We get to benefit from the law of large numbers. There are at any time a couple of million Atoms who are working. Take the Atom you know with most experience in AWS and add a little bit. 
	- No support options from Amazon. 
- Are there any resources for simple scanning?
	- Amazon services in English
- What resources at Atomic are we going to mine?
	- Jason Porritt knows a bunch of amazon stuff
	- Rachael has done a bunch
	- Joe
	- Laura
	- Brian Vanderwall
	- Patrick Bacon
	- Lydia 



## Brief
How can you leverage services instead of using traditional computers? 

What are the things being shipped? 
- Monitors, keyboards, and hardware for different clients
	- As our client base grew, this became an important arm of our business. We are getting the sense that we are the company that moves stuff. 
	- Needs a complete audit log of every package available for all time - doesn't have to be quickly accessible
		- Can take seconds to minutes to access historical data
	
The system should know where every package is, always. In 3D space. 


## Approaches

In Amway, they broke down the people involved and then thought through how data would move between those people. 
- Then we wrote down the systems involved and how data would move between those systems
- "Let's assume this is a single lambda web server"
	- What would happen if 20,000 people hit this all at once? 
		- How do you do that? 

Break it down by service
- Picture of the package that's coming - S3
- Going to need quick storage - Dynamo 

Start in a bunch of ways and crunch on it till it breaks down into something that makes sense

## Process
- Pairs 

## Tools
- Omnigraphl is best but expensive
- Draw.io is free
- MindNode can be used for diagramming
- Graphiz and the syntax can be quite useful
	- Use whatever tools work the way your brain works to put together an architecture