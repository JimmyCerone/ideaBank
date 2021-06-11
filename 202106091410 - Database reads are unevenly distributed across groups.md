## Idea
- In the past I've assumed there is an equal chance you need everything in a database. So then more data = harder to read. In reality that's more logorathmic or arithmetic growth than exponential because you don't read the whole database everytime. Often you can filter by something like recency, which changes the [[03062021 - Levers]] and makes reads much easier because you don't have to look over the whole database. 
- Also, since [[202106091445 - Reads and writes are not always done by the same person]], you can end up with a "filtered" view of the database because your responsibility may be for reads but not for writes or vice versa. So everything you write you don't have to read. 

## Connections
- Connects deeply with my work at [[Atomic Object]] because a product backlog is basically a database. Surprised that [[Agile Estimation and Planning by Mike Cohn]] did not touch on this. 

## Example
- You should input as many bugs as possible because you won't be doing all the reads. 

### Source: [[Jimmy]] & [[Jason Porritt]]