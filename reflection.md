# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| | | | | The New Game button does not reset the record/data and it does not restart the game either.
| | | | | The State Bug exist because there is a section of code which converting the secret number from integer into string when it is an even attempt.
| | | | | The Hint is incorrect. When the guess is smaller than the secret number, the Hint says Go LOWER and when the guess is bigger than the secret number, the Hint says Go HIGHER.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? Copilot
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). 
Most of the suggestions were correct.
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.
I forgot which suggestion that I rejected. Next time I will document it when I reject a suggestion from Copilot.

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
By testing the app through various different scenarios.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
I did pytest and 6 passed in 0.02s (I added several new tests into test_game_logic.py file.
- Did AI help you design or understand any tests? How?
Yes, Copilot definitely helps me design and understand all the tests. I did not know much about code testing (through pytest), but now I have a better knowledge on how to test my code.
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
It is interesting that I do not have to refresh my web browser after code changes. I just start a new game and the new code is reflected/applied in the new game.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
I learned a lot from this project. I know more about Git/GitHub. I improve my Python knowledge/skill.
- What is one thing you would do differently next time you work with AI on a coding task?
I definitely will utilize AI for my next coding task. The challenge is that I do not know whether a company will allow the utilization of AI in the enterprise coding environment.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
I am amazed on the progress of AI. I learned various programming languages in the past. Through the help of AI, I can debug easier and faster.
