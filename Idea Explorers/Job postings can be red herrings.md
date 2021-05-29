#Problem: Job postings can be red herrings

## Solution:

- Web page watcher that checks how long a job has been posted and the turnover rate of job postings
	- Rates the job posting

- If the posting has been up for more than 4-6 weeks they are looking for Superjane

- If the average posting time is 1-2 weeks it's a fake posting (insider hire probably)

Two Approaches: 

- Chrome Extension
	- Rates the job based on the above criteria to give you an idea of how viable it is
- Website
	- The website could crawl opportunities on like Indeed and spit back a list of the highest rated jobs
- Directory
	- Rate companies based on the quality of their job postings
		- Goes a level beyond rating how good a company is. The most important thing when job searching isn't the quality of the company, it's the availability of the job. So you could have a high quality company but fake job postings and that doesn't help you.


- There are a few [[03062021 - Levers]] that determine what makes a good job posting
	- Length of time listed
		- If time is long, job is impossible to hire for
		- If time is short (on average), job is already taken
	- Based on these levers you can rate the quality of a job posting
		- Part of the reason job hunting is so hard is you end up in a situation like [[What's that mystery in your inbox costing you?]]. You see 100 job postings but you have way to rate the quality of the posting. Seeing if you fit the job is time consuming and you should only do that for high quality postings. 

## Risk
- Not all industries need this. How do we determine which industries would find this useful? 
- Does this affirm the broken job search model outlined in [[Designing Your Life]] or is this legitimately helping people? 
	- Chicken and egg question. Does the interview people model work because the job application model doesn't? 

## MVP
- How can we limit scope? 
	- By company / website we monitor
		- Would give us the chance to do #WizardOfOz 
	- By complexity of criteria
		- Simple time at first

#Lab #OneHundredIdeas - [[Jimmy]]