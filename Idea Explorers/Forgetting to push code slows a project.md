#Problem: Forgetting to push code slows down a project

Solution: 
- Joe's transit command but automated

[[03062021 - Levers]] involved in pushing to a branch: 
- Completeness
- Quality of Code

Some would argue [[Extreme Programming by Kent Beck]] that you should push all the time, even if something is incomplete. I worry I will forget stuff ([[Humans have limited memories]]) and so I wait to push. It'd be nice for my system to just do it for me, or remind me / ask me if I want to. 

```#!/usr/bin/env bash

git add . && git commit -m "transit commit" && git push
