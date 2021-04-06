## Context
- Learned this from Lydia at #Work at #AtomicObject 

## Idea
- The apollo cache can automatically be updated during a mutation by specifying a "return" that uses the useMutation hook to update the item by id. 

Source: https://www.apollographql.com/docs/react/data/mutations/

## Connections
- This happens almost a level "above" or "before" [[03172021 - Graphql Resolver]]. The server doesn't know about this stuff - lives on the browser. So it's a whole different layer. 