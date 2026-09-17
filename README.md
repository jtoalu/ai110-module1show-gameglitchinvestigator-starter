# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
The game is to guess the secret number generated randomly between 1 and 100. Each round game has 8 attempts to guess the secret number. If the secret number
is guessed before all given attempts are used, then the player win the game. Otherwise, the player loose. 
- [ ] Detail which bugs you found.
1) The New Game button does not reset the record/data and it does not restart the game either.
2) The State Bug exist because there is a section of code which converting the secret number from integer into string when it is an even attempt.
3) The Hint is incorrect. When the guess is smaller than the secret number, the Hint says Go LOWER and when the guess is bigger than the secret number,
the Hint says Go HIGHER.
- [ ] Explain what fixes you applied.
1) The New Game bug was fixed by modifying the code in the "if new_game" section.
2) The State Bug was fixed by eliminating the "if st.session_state.attempts % 2 == 0" section.
3) The Hint bug was fixed by modifying the code in the "def check_guess(guess, secret)" function.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. # FIXME: Logic breaks here because the "New game started" is not displayed on the screen after clicking the New Game button.
   if new_game:
-    st.session_state.status = "playing"
-    st.session_state.score = 0
-    st.session_state.history = []
     st.session_state.attempts = 0
     st.session_state.secret = random.randint(1, 100)
     st.success("New game started.")

2. # The State Bug exist because there is a section of code which converting the secret number from integer into string when it is an even attemp.
@@ -158,7 +154,11 @@ if submit:
         st.error(err)
     else:
         st.session_state.history.append(guess_int)
-        secret = st.session_state.secret
+
+        if st.session_state.attempts % 2 == 0:
+            secret = str(st.session_state.secret)
+        else:
+            secret = st.session_state.secret

         outcome, message = check_guess(guess_int, secret)

3. # FIXME: Logic breaks here because the app says "Go LOWER!" when the guess is lower than the secret.
+
 def check_guess(guess, secret):
     if guess == secret:
         return "Win", "🎉 Correct!"

     try:
         if guess > secret:
-            return "Too High", "📉 Go LOWER!"
+            return "Too High", "📈 Go HIGHER!"
         else:
-            return "Too Low", "📈 Go HIGHER!"
+            return "Too Low", "📉 Go LOWER!"
     except TypeError:
         g = str(guess)
         if g == secret:
             return "Win", "🎉 Correct!"
         if g > secret:
-            return "Too High", "📉 Go LOWER!"
-        return "Too Low", "📈 Go HIGHER!"
+            return "Too High", "📈 Go HIGHER!"
+        return "Too Low", "📉 Go LOWER!"

4. <!-- Describe this step -->
5. <!-- Add more steps as needed -->

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
