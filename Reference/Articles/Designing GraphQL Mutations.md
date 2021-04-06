An excellent article sent over by Andy to help me as I reviewed the PR from [[FUS-1646 A User can override a price record while price editing backend]]. 

Source: https://www.apollographql.com/blog/designing-graphql-mutations-e09de826ed97/

## Reflections
- The admonition to be specific reminds me of the concept of #Atomic from the [[Head First SQL]] book I've been reading. 
- Love the naming convention of verb first then noun. Simple, clear, and effective.


## Summary
- Naming
	- Verb then noun
- Specificity
	- Represent specific actions
- Input Object
	- Single input 
- Payload
	- Must be unique for each mutation
- Nesting
	- Helps you be versionless? Not sure quite how
		- Refactors are easier to do this way. 