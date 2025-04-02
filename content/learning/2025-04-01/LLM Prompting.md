## Basic Prompting approaches
- Zero shot - Ask a question, get an answer
- One shot - Given an example interaction, given an input mirror the single example
- Multi shot - Given multiple examples, match the final input to the pattern past examples provide
- Chain of thought - Ask the model to think step by step - this gives a longer answer that is more likely to be correct for concepts like math that may need multiple steps to avoid short circuiting to an incorrect answer.


### Example of high complexity prompt
[[NASA-BIDARA-prompt]]
[Analysis of the BIDARA prompt](https://www.thepromptwarrior.com/p/dissecting-nasa-megaprompt)
### Prompt techniques

#### RTF
R - Role  
T - Task  
F - Format

Example
```
"Act like a life coach with 30 years of experience in mentoring. Give me a plan to improve my work-life balance in table format."
```
#### Chain of thought
Ask for the solution to be "step by step"

Example:
```
"How do I improve my sales calls? I've only got a 15% close rate right now, and I think it's because I'm not selling the dream enough.

Let's think through it step-by-step."
```
#### RISEN

R - Role  
I - Instructions  
S - Steps  
E - End goal  
N - Narrowing

Example:
```
"Role: You are an expert digital course builder who has sold millions in online courses.

Main Task: Please give me a list of EVERYTHING important that I should include in my AI course and tell me all the different methods of growth I can implement to maximise revenue.

Steps to complete the task:

1. First start by covering all the things that ANY digital course should include. 

2. Then proceed by giving your thoughts on what AI courses should include. 

3. End with covering the best growth marketing tactics and strategies for digital courses.

Goal: The goal is to give me a concise list of everything I should include within the course, as well as give me ideas on how I can maximize the revenue from my course. 

Constraints: Maximum of 500 words. - Avoid technical jargon. - Make it actionable - Make it clear"
```

#### RODES

R - Role  
O - Objective  
D - Details  
E - Examples  
S - Sense Check

#### Chain of density
Asking the LLM to write increasingly better versions of the prompted content by critiquing its attempts and making improvements based on its critiques.

#### Tree of thought
Example
```
Imagine three different experts are answering this question.All experts will write down 1 step of their thinking,then share it with the group.Then all experts will go on to the next step, etc.If any expert realises they're wrong at any point then they leave.The question is...
```

https://www.thepromptwarrior.com/p/5-prompt-frameworks-level-prompts
https://www.promptingguide.ai/techniques