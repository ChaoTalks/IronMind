# IQ Challenge — Reference

Urges peak at 3–7 minutes then naturally subside. A genuine cognitive challenge occupies exactly that window. This is not distraction for distraction's sake — it is a targeted use of the prefrontal cortex to dampen the limbic pull.

**Rule:** Challenge difficulty should feel like *just* enough effort to require focus. Too easy = mind wanders back. Too hard = frustration, user disengages. Default to medium.

---

## Topic Selection

Read `challenge_topics` from user config (see `config.yaml`). If multiple topics are configured, rotate — never repeat the same topic two challenges in a row. If no preference is set, default to `math`.

Configured under `challenge.topics` in `config.yaml`:
- `leetcode` — algorithm and CS puzzles
- `history` — historical events, dates, figures
- `math` — mental math, logic, sequences
- `entertainment` — trivia, pop culture, film, music

---

## Delivery Format

### `active_urge` state

Lead with the one-line physical command first. Then immediately follow with the challenge — give the brain something to land on before it drifts back.

```
{one-line physical command}

While you're up — solve this:

**[{TOPIC} Challenge]**
{challenge question}

Come back with your answer.
```

### `warning` state

Skip straight to the challenge. The drift hasn't become momentum yet — cognitive engagement alone is enough.

```
You caught it early. Here's something to chew on:

**[{TOPIC} Challenge]**
{challenge question}

Take your time.
```

---

## After the User Answers

- **Correct:** Brief acknowledgment, no over-praise. Then optionally offer another or check state.
- **Wrong:** Give the answer, keep it light, no shame. Offer a follow-up if they want.
- **Partial/close:** Credit the effort, give the full answer, move on.
- **"I don't know" / gives up:** Give the answer anyway. The goal was the engagement, not the result.

**Templates (after answer):**
> Got it. [correct/answer is X]. How are you feeling now?

> Close — [correct answer]. Want another, or are you good?

> Solid. That took focus. State check: still elevated or coming down?

---

## Challenge Bank

### LEETCODE

**Easy**

> You have an array `[2, 7, 11, 15]` and a target of `9`. Which two numbers add up to the target? What are their indices?

> What does this return: `"racecar"[::-1]` ?

> FizzBuzz: what does the number 15 print?

> What is the time complexity of looking up an element in a hash map?

> Given `n = 5`, what does this return: `sum(range(1, n+1))`?

**Medium**

> You have a string `"()[]{}"`. Is it valid (all brackets properly closed and nested)? Answer yes or no, then explain why in one sentence.

> A sorted array `[1, 3, 5, 7, 9]` has had one element removed and replaced with a duplicate. The array is now `[1, 3, 3, 7, 9]`. What is the missing number?

> What data structure would you use to find the most frequently occurring word in a document in O(n) time? Why?

> Reverse a linked list in your head: `1 → 2 → 3 → 4 → 5`. What does it look like reversed?

> What is the output: `print([x**2 for x in range(5) if x % 2 == 0])`?

**Hard**

> Explain in one sentence why merge sort is O(n log n) but not O(n²).

> You have a binary tree. Write the logic (in pseudocode or plain English) to check if it is a valid binary search tree.

> Given an unlimited supply of coins `[1, 5, 10, 25]`, what is the minimum number of coins to make `41` cents?

> What is the difference between BFS and DFS? When would you use each?

---

### HISTORY

**Easy**

> In what year did the Second World War end?

> Who was the first person to walk on the moon, and in what year?

> Which ancient wonder of the world was located in Alexandria, Egypt?

> Name the three countries that formed the Axis powers in WWII.

> What empire built the Colosseum?

**Medium**

> Put these events in chronological order: the French Revolution, the American Declaration of Independence, the fall of the Berlin Wall, the invention of the printing press.

> What was the name of the economic plan the United States used to help rebuild Western Europe after WWII?

> The Silk Road connected which two major regions of the ancient world?

> Which century did the Renaissance begin in, and in which country?

> What was the primary cause of the 1929 stock market crash?

**Hard**

> What was the Meiji Restoration, and roughly when did it occur? Answer in two sentences.

> Name two consequences of the Treaty of Versailles that directly contributed to WWII.

> The Byzantine Empire was the eastern continuation of which earlier empire, and approximately how long did it last?

> What is the significance of the year 1066 in English history?

---

### MATH

**Easy**

> What is 17 × 13?

> What is the next prime number after 29?

> A rectangle has sides of 7 and 12. What is its area? Its perimeter?

> If you have $240 and spend 35% of it, how much do you have left?

> What is the square root of 144?

**Medium**

> Solve for x: `3x + 7 = 28`

> A train travels at 80 km/h. How long does it take to cover 220 km? Give your answer in hours and minutes.

> What is the sum of angles in a pentagon?

> The Fibonacci sequence starts 1, 1, 2, 3, 5, 8... What are the next three numbers?

> If the probability of rain on any given day is 0.3, what is the probability it does NOT rain three days in a row?

**Hard**

> You have a 3-gallon jug and a 5-gallon jug. How do you measure exactly 4 gallons of water? Walk through the steps.

> What is the value of `log₂(64)`?

> A ball is dropped from 100m. Each bounce reaches half the height of the previous one. What is the total distance the ball travels before coming to rest?

> Prove (or explain) why the sum of any two odd numbers is always even.

> If `f(x) = x² + 3x − 4`, what are the roots of `f(x) = 0`?

---

### ENTERTAINMENT

**Easy**

> Name the actor who played Tony Stark / Iron Man in the MCU.

> What year was the first iPhone released?

> Which band sang "Bohemian Rhapsody"?

> What is the highest-grossing film of all time (not adjusted for inflation)?

> Name the author of the Harry Potter series.

**Medium**

> Name three films directed by Christopher Nolan.

> What is the real name of the artist known as "The Weeknd"?

> In which decade was hip-hop music generally considered to have originated?

> Which composer wrote The Four Seasons?

> Name the five original members of The Beatles. (Hint: there are five if you count Pete Best.)

**Hard**

> What was the first video game to be inducted into the World Video Game Hall of Fame?

> Name the film that won Best Picture at the 2020 Oscars — and why was it historically significant?

> What is the name of the musical mode most commonly used in blues music?

> Which author wrote both *Brave New World* and *Doors of Perception*?

> In what year did the last episode of *The Sopranos* air, and what is the final scene?

---

## Topic Rotation Logic

Track the last topic used per session. On next challenge:
1. If user has one topic configured → always use it
2. If multiple topics → exclude the last used, pick randomly from remaining
3. Vary difficulty: easy → medium → hard → medium → easy (cycle), unless user sets fixed difficulty

## Config Reference

```yaml
challenge:
  enabled: true
  topics:
    - math
    - leetcode
  difficulty: mixed        # easy | medium | hard | mixed
  in_active_urge: true     # send challenge during active_urge (after physical command)
  in_warning: true         # send challenge during warning (as primary redirect)
```
