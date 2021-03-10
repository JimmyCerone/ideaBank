Instructions here: [[Chrysler Cloud Challenge]].

Brainstorming

Joe’s Advice

-   Approach: How does data move between the people, how does it move between the systems, Break down by service: ex we know we'll need object storage (probably #S3), we'll need some server thing ( #Lambda) , we'll need quick storage (DDB) 
    
-   Tap the brain trust (Jason, Rachael)
    

  
  
  
  
  

Jimmy’s Note: 

  

## Questions

-   What would your first step be?
    
-   What wouldn't you do?
    
-   What details can you get bogged down in?
    

-   "And then I will go to the web console and write some code"
    

-   NO SERVERS!
    

-   What does "some" packages mean?
    

-   Keeps track of a select number of packages you specify.
    

-   How do you stay out of the weeds?
    

-   He doesn't want to have to manage a server at all. If there is a server somewhere that somebody at Atomic needs to keep track of, this project is not built how I want it to be.
    
-   You probably will end up hating yourself at a certain point when you go to build it. Luckily we won't be building this and kind of can't. That's one restriction.
    
-   Think more whiteboard diagram and less weeds.
    

-   Are there any security restraints?
    

-   Data is accessible to all Atoms, but only atoms.
    
-   User management is a stretch goal.
    

-   What prior experience does the company have with AWS? Are there any support options we should keep in mind?
    

-   We get to benefit from the law of large numbers. There are at any time a couple of million Atoms who are working. Take the Atom you know with most experience in AWS and add a little bit.
    
-   No support options from Amazon.
    

-   Are there any resources for simple scanning?
    

-   Amazon services in English
    

-   What resources at Atomic are we going to mine?
    

-   Jason Porritt knows a bunch of amazon stuff
    
-   Rachael has done a bunch
    
-   Joe
    
-   Laura
    
-   Brian Vanderwall
    
-   Patrick Bacon
    
-   Lydia
    

## Brief

How can you leverage services instead of using traditional computers?

What are the things being shipped?

-   Monitors, keyboards, and hardware for different clients
    

-   As our client base grew, this became an important arm of our business. We are getting the sense that we are the company that moves stuff.
    
-   Needs a complete audit log of every package available for all time - doesn't have to be quickly accessible
    

-   Can take seconds to minutes to access historical data
    

The system should know where every package is, always. In 3D space.

## Approaches

In Amway, they broke down the people involved and then thought through how data would move between those people.

-   Then we wrote down the systems involved and how data would move between those systems
    
-   "Let's assume this is a single lambda web server"
    

-   What would happen if 20,000 people hit this all at once?
    

-   How do you do that?
    

Break it down by service

-   Picture of the package that's coming - S3
    
-   Going to need quick storage - Dynamo
    

Start in a bunch of ways and crunch on it till it breaks down into something that makes sense

## Process

-   Pairs
    

## Tools

-   Omnigraphl is best but expensive
    
-   Draw.io is free
    
-   MindNode can be used for diagramming
    
-   Graphiz and the syntax can be quite useful
    

-   Use whatever tools work the way your brain works to put together an architecture![](https://lh6.googleusercontent.com/ud5DHyfS5tWUA6wGbtlEygPNHr8UI1q_pJqx5mTnZiEISdqfROEBqbnSjjlSjOsVPKUEluF_zUtJRPdDGu6zLmyp-p2iRGOEvLQPodHNXWn6PAvQ8Xhn8bxmXru7U8VFsMAdYXkX)
    

Requirements: 

-   Serverless
    
-   Need to know where every package is in 3D space
    
-   Need a web interface that:
    

-   Shows location of both all and single packages
    

-   Need a management interface / dashboard that:
    

-   Allows you to track spend and monitor the system
    

-   Overall cost of shipping
    
-   Cost of average package shipping
    
-   Time / other metrics
    

-   Mobile app to track some packages
    
-   Minimize fixed cost - all marginal
    
-   6 months to build
    

  

Questions: 

-   Should the dashboard and web interface be intertwined?
    

-   One set of permissions gets you tracking, the other gets you dashboard access
    

-   Do we have to build a data entry system? Or can we assume all this data is already going to be there? 
    

-   Do we have to build an integration with UPS or something? 
    

-   What does the deliverable look like?
    

  

Reflections:

-   We can share backend architecture across all of these (web app - track all, track one, management & mobile app)
    

-   The difference will be how we arrange / display the data
    

-   One account that logs you into mobile, dashboard, and web app. 
    

  

Action Item: 

-   Ping Joe about data entry / collection
    
-   Rough draft for services for the backend, mobile app, web app, and infrastructure (AWS stuff - audit logs) organized by features by Friday
    

-   Mural board 
    

  

Feature List

## Project Wide Features:

-   Real time
    
-   Low fixed cost
    
-   Minimize ongoing costs
    
-   6 months of build time
    
-   Serverless
    

  
  

## Database: 

-   Tracking data for all packages
    

-   Location
    
-   Cost
    
-   Basic info
    

Questions: 

-   Should this be relational? 
    

-   If so, #RDS, if not #DynamoDB.
    
-   DynamoDB is likely the best option because the relationship between data shouldn’t be terribly complex (like Fusion); single-digit ms performance at any scale; automatic scaling while maintaining consistent performance
    

  

## API:

-   Retrieves many packages
    
-   Retrieves one package
    
-   User management
    
-   Service: API Gateway & Lambda
    

-   Allows you to filter out bad traffic (security)
    
-   Lambda - hold the business logic that connects backend/DB to our frontend; scales automatically, pay for compute time you consume (any type of backend service)
    

  

## Web Interface Features: 

-   Tracks all packages
    
-   Tracks one package
    
-   Login Feature
    

-   Cognito
    

-   Search feature
    
-   User management & roles
    
-   Portal to management if user has correct permissions
    

  

Service: Amazon S3 Standard for hosting and storage.

  

## Management Features: 

-   Dashboard
    

-   Track cost
    
-   Track time
    

-   Filtering capabilities
    

  

Amazon S3 Standard

  

## Mobile App Features: 

-   Tracks some packages
    
-   Login
    
-   Search feature to find packages
    

  

Amazon S3 Standard

  

## Data Entry: 

-   Bulk entry
    
-   Single entry
    

  

DynamoDB + API Gateway

## Logging:

-   Complete audit log of all packages for all time
    
-   Accessible in seconds to minutes
    

  

Service: Store data in an Amazon S3 Standard-IA

  
  
  

Additional Considerations:

-   Route 53 for CloudFront
    
-   IAM Policies
    
-   Certificate Manager
    
-   SNS (nice to have)
    
-   EventBridge (web hook to pull things in from - routes data to targets)
    
-   ![](https://lh3.googleusercontent.com/l5_gOaUr5vWq353ImxHbIjh7OeBGgSbhHS4NN4MUTd0dnF3_g8KdP4HzA4AmjBzA3AYml2iVaF-kveANdWDRJp26KVOlq4QI_JZkKnzxR6nP1XhH9M6u9iRHxx0KkwJUFMr-C0AY)