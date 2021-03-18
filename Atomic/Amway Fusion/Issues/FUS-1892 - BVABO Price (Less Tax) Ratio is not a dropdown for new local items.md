Steps to Reproduce: 
1. Add a new local sales item in a sandbox
2. See that BV/ABO (Less Tax) Ratio is an input instead of a dropdown


Questions: 
- What would cause this? 
- Is this a front end handling issue or a backend creation issue?
	- Subquestion and probably the root is - what determines how this gets displayed? 
		- Could it be thinking it is in override mode?
			- So you can get into this state if you change BV while in override mode. So I'm betting this is it. Not sure why. 
			- Why would it think it's in override mode? 
- ~~Does it persist?~~
	- Yes this persists even after a reload