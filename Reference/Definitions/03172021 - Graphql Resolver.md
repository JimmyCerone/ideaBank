From: https://www.apollographql.com/docs/apollo-server/data/resolvers/

> A #Resolver is a #Function that's responsible for population the data for a single field in your #Schema

The schema of a graphql #API is the structure of the API. The resolver goes and grabs the data, using the schema as a guide. 

The Resolver Map is like the schema for the resolver, letting you know where everything is. In a fun twist, you can even have #Arguments thrown into a resolver (which have to be included in the schema as well) when you write the #Code. 

## Connections
- We use resolvers often at #AtomicObject and in a way, they are like #Atomic #Ideas from the [[The Atomic Web Note Taking Strategy - Zettelkasten]] method. Each resolver defines an #Idea in the schema. 
- Connecting to [[03062021 - Levers]], you can chain these resolvers together to get lots of data at once. 