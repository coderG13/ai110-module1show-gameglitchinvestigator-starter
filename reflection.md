# 💭 Reflection: Game Glitch Investigator

## 1. What was broken when you started?

Bug 1 (hints backwards): When my guess was higher than the secret, the game told me “Go HIGHER!” instead of “Go LOWER.” I expected a “Too High → go lower” hint, but it gave the opposite.

Bug 2 (type/glitchy comparisons): The game behaves inconsistently across attempts because the secret number sometimes gets treated like a string instead of an integer. This caused wrong outcomes/hints even when I used the debug tab to see the secret.

Bug 3 (difficulty/range mismatch): The UI difficulty shows a range (ex: Easy 1–20), but the game text and/or New Game logic doesn’t consistently use that range (it still acts like 1–100).

---

## 2. How did you use AI as a teammate?

I used the Claude AI extension in VS Code while debugging the game logic. I asked Claude to look at the check_guess function because the hints in the game seemed wrong when I played it. Claude pointed out that the hint messages were reversed, so guesses higher than the secret should return “Too High” and guesses lower should return “Too Low”. After applying that change, I ran the tests and the Streamlit app to confirm that the hints were now correct.

One suggestion from Claude that was not very helpful was keeping extra logic to handle string comparisons inside the function. Since I fixed the bug where the secret number was sometimes converted to a string, that extra code was unnecessary. I removed it and confirmed the simpler logic still worked by running the tests again.

---

## 3. Debugging and testing your fixes

To check if the bug was really fixed, I used both automated tests and manual testing. I ran pytest in the terminal and confirmed that all the provided tests passed successfully. After that, I ran the Streamlit game and used the developer debug panel to see the secret number while making guesses. This helped me confirm that the hints matched the correct outcomes when the guess was too high or too low. AI helped me understand what scenarios to test and guided me toward verifying the fix properly.

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
