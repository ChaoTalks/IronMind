# IQ Challenge — Reference

Urges peak at 3–7 minutes then naturally subside. A genuine cognitive challenge occupies exactly that window. This is not distraction for distraction's sake — it is a targeted use of the prefrontal cortex to dampen the limbic pull.

**Rule:** Challenge difficulty should feel like *just* enough effort to require focus. Too easy = mind wanders back. Too hard = frustration, user disengages. Default to medium.

**Rotation rule:** Track every question delivered by its index. Never repeat a question until the entire difficulty tier for that topic is exhausted. Shuffle on reset. This ensures the user never sees the same question twice in a typical month of usage.

---

## Topic Selection

Read `challenge_topics` from user config (see `config.yaml`). If multiple topics are configured, rotate — never repeat the same topic two challenges in a row. If no preference is set, default to `math`.

- `leetcode` — algorithm and CS puzzles
- `history` — historical events, dates, figures
- `math` — mental math, logic, sequences
- `entertainment` — trivia, pop culture, film, music

---

## Delivery Format

### `active_urge` state
```
{one-line physical command}

While you're up — solve this:

**[{TOPIC} Challenge]**
{challenge question}

Come back with your answer.
```

### `warning` state
```
You caught it early. Here's something to chew on:

**[{TOPIC} Challenge]**
{challenge question}

Take your time.
```

---

## After the User Answers

- **Correct:** One-line acknowledgment. Check state. Offer another if they want.
- **Wrong:** Give the answer, no shame, move on. Offer a follow-up.
- **Partial/close:** Credit it, give the full answer.
- **"I don't know" / gives up:** Give the answer anyway. Engagement was the goal, not the score.

> Got it — [answer]. How are you feeling now?

> Close — [answer]. Want another, or are you good?

> That took focus. State check: still elevated or coming down?

> Answer is [X]. The effort counts. How's your head?

---

## Challenge Bank

---

### LEETCODE

#### Easy (15 questions)

1. You have an array `[2, 7, 11, 15]` and a target of `9`. Which two numbers add up to the target? What are their indices?
   **Answer:** Indices 0 and 1 (values 2 and 7).

2. What does `"racecar"[::-1]` return in Python?
   **Answer:** `"racecar"` — it's a palindrome, unchanged.

3. FizzBuzz: what does the number 15 print?
   **Answer:** FizzBuzz.

4. What is the time complexity of looking up an element in a hash map?
   **Answer:** O(1) average case.

5. What does `sum(range(1, 6))` return?
   **Answer:** 15.

6. What does `len([1, [2, 3], 4])` return?
   **Answer:** 3 — nested list counts as one element.

7. What does `list(range(0, 10, 2))` return?
   **Answer:** `[0, 2, 4, 6, 8]`.

8. What does `"hello"[1:3]` return?
   **Answer:** `"el"`.

9. How many times does this loop run: `for i in range(3, 9, 2)`?
   **Answer:** 3 times (i = 3, 5, 7).

10. What does `max([3, 1, 4, 1, 5, 9, 2, 6])` return?
    **Answer:** 9.

11. What is the output of `print(2 ** 10)`?
    **Answer:** 1024.

12. What does `bool(0) or bool(1)` evaluate to?
    **Answer:** True.

13. What is the index of the last element in `arr = [10, 20, 30, 40]`?
    **Answer:** 3.

14. Is an empty string `""` truthy or falsy in Python?
    **Answer:** Falsy.

15. What does `sorted([5, 2, 8, 1])` return?
    **Answer:** `[1, 2, 5, 8]`.

---

#### Medium (12 questions)

1. You have a string `"()[]{}"`. Is it valid (all brackets properly closed and nested)? Answer yes or no, then explain why in one sentence.
   **Answer:** Yes — each opening bracket is immediately closed in the correct order.

2. A sorted array `[1, 3, 5, 7, 9]` has had one element removed and replaced with a duplicate. The array is now `[1, 3, 3, 7, 9]`. What is the missing number?
   **Answer:** 5.

3. What data structure would you use to find the most frequently occurring word in a document in O(n) time? Why?
   **Answer:** A hash map (dictionary) — map each word to its count in one pass.

4. What is the output: `print([x**2 for x in range(5) if x % 2 == 0])`?
   **Answer:** `[0, 4, 16]`.

5. You push 1, 2, 3 onto a stack, then pop twice. What value is now on top?
   **Answer:** 1.

6. What is the output of `sorted([3,1,4,1,5,9], reverse=True)[:3]`?
   **Answer:** `[9, 5, 4]`.

7. Given `nums = [1,2,3,4,5]`, what does `nums[::2]` return?
   **Answer:** `[1, 3, 5]`.

8. What does `d = {'a':1,'b':2}; print(d.get('c', 0))` output?
   **Answer:** `0`.

9. You have "anagram" and "nagaram" — are they anagrams?
   **Answer:** Yes — same letters, different order.

10. What is memoization and why is it useful? Answer in one sentence.
    **Answer:** Memoization stores results of expensive function calls so they aren't recomputed — it trades memory for speed.

11. In a binary search of array `[1,3,5,7,9,11,13]`, how many comparisons does it take to find `7`?
    **Answer:** 2 comparisons (check 7 at index 3 after narrowing from middle).

12. Describe the two-pointer technique in one sentence.
    **Answer:** Two pointers start at opposite ends (or both at the start) and move toward each other or forward to solve array problems in O(n) instead of O(n²).

---

#### Hard (8 questions)

1. Explain in one sentence why merge sort is O(n log n) but not O(n²).
   **Answer:** It splits the array log n times and merges in O(n) at each level, so total work is n × log n.

2. Given an unlimited supply of coins `[1, 5, 10, 25]`, what is the minimum number of coins to make `41` cents?
   **Answer:** 4 coins (25 + 10 + 5 + 1).

3. What is the difference between BFS and DFS? When would you use each?
   **Answer:** BFS explores level by level (shortest path, uses a queue); DFS goes deep first (cycle detection, topological sort, uses a stack/recursion).

4. What is the time and space complexity of quicksort in the worst case?
   **Answer:** Time O(n²), space O(n) — worst case is an already sorted array with a bad pivot choice.

5. What does it mean for a problem to be NP-complete?
   **Answer:** It can be verified in polynomial time, cannot be solved in polynomial time by any known algorithm, and every NP problem reduces to it.

6. How many distinct ways can you climb 6 stairs if you can take 1 or 2 steps at a time?
   **Answer:** 13 ways (Fibonacci: 1,2,3,5,8,13).

7. What is a deadlock, and name two necessary conditions for it to occur.
   **Answer:** A deadlock is when two or more processes each wait for a resource held by the other. Two conditions: mutual exclusion and circular wait.

8. Why is a balanced BST preferred over an unbalanced one for search operations?
   **Answer:** A balanced BST guarantees O(log n) search; an unbalanced BST can degrade to O(n) — equivalent to a linked list.

---

### HISTORY

#### Easy (15 questions)

1. In what year did World War II end?
   **Answer:** 1945.

2. Who was the first person to walk on the moon, and in what year?
   **Answer:** Neil Armstrong, 1969.

3. Which ancient wonder of the world was located in Alexandria, Egypt?
   **Answer:** The Lighthouse of Alexandria.

4. Name the three countries that formed the Axis powers in WWII.
   **Answer:** Germany, Italy, Japan.

5. What empire built the Colosseum?
   **Answer:** The Roman Empire.

6. In what year did the Berlin Wall fall?
   **Answer:** 1989.

7. Who was the first President of the United States?
   **Answer:** George Washington.

8. What country did Columbus sail for when he reached the Americas in 1492?
   **Answer:** Spain.

9. In what year did the Titanic sink?
   **Answer:** 1912.

10. Who was the first woman to win a Nobel Prize?
    **Answer:** Marie Curie (Physics, 1903).

11. In which city was Julius Caesar assassinated?
    **Answer:** Rome.

12. How many wives did King Henry VIII have?
    **Answer:** Six.

13. What war was fought between the Northern and Southern states of the US?
    **Answer:** The American Civil War (1861–1865).

14. Who invented the telephone?
    **Answer:** Alexander Graham Bell (credited, 1876).

15. What was the name of the ship that carried the Pilgrims to America in 1620?
    **Answer:** The Mayflower.

---

#### Medium (12 questions)

1. Put these in chronological order: the French Revolution, the American Declaration of Independence, the fall of the Berlin Wall, the invention of the printing press.
   **Answer:** Printing press (~1440) → American Declaration (1776) → French Revolution (1789) → Berlin Wall (1989).

2. What was the Marshall Plan, and which country funded it?
   **Answer:** A US economic recovery program to rebuild Western Europe after WWII, funded by the United States.

3. The Silk Road connected which two major regions of the ancient world?
   **Answer:** China (East Asia) and the Mediterranean / Europe.

4. In which century did the Renaissance begin, and in which country?
   **Answer:** 14th century, Italy.

5. What triggered the start of World War I?
   **Answer:** The assassination of Archduke Franz Ferdinand of Austria-Hungary in Sarajevo (1914).

6. What was the Black Death, and roughly what fraction of Europe's population did it kill?
   **Answer:** A bubonic plague pandemic in the 14th century; killed roughly one-third of Europe's population.

7. Who was the last pharaoh of ancient Egypt?
   **Answer:** Cleopatra VII.

8. What was the Louisiana Purchase, and when did it happen?
   **Answer:** The 1803 purchase of approximately 828,000 square miles of territory from France, which doubled the size of the US.

9. Which empire was the largest by land area in history?
   **Answer:** The Mongol Empire (13th–14th centuries).

10. Name three ancient civilizations that developed along major river systems.
    **Answer:** Any three of: Egypt (Nile), Mesopotamia (Tigris & Euphrates), Indus Valley (Indus), China (Yellow River/Yangtze).

11. What revolution occurred in Russia in 1917?
    **Answer:** The Bolshevik Revolution (October Revolution), which overthrew the provisional government and brought the Communists to power.

12. What was the significance of the Battle of Hastings (1066)?
    **Answer:** It marked the Norman conquest of England — William the Conqueror defeated King Harold II, changing English language, culture, and governance permanently.

---

#### Hard (8 questions)

1. What was the Meiji Restoration, and roughly when did it occur?
   **Answer:** A period beginning in 1868 when Japan abolished the shogunate, restored imperial rule, and rapidly modernized its military, economy, and institutions.

2. Name two consequences of the Treaty of Versailles that directly contributed to WWII.
   **Answer:** Any two of: massive war reparations humiliating Germany, the "war guilt" clause, loss of German territory, limits on the German military.

3. The Byzantine Empire was the eastern continuation of which earlier empire, and approximately how long did it last?
   **Answer:** The Roman Empire; it lasted roughly 1,000 years (330 CE – 1453 CE).

4. What was the Scramble for Africa, and when did it occur?
   **Answer:** The rapid colonization of Africa by European powers, primarily between 1881 and 1914, formalized at the Berlin Conference of 1884–85.

5. What was the Opium War between Britain and China, and what were its key consequences?
   **Answer:** Two wars (1839–42, 1856–60) in which Britain forced China to open ports and allow opium trade; China ceded Hong Kong and signed unequal treaties.

6. What was the Thirty Years' War, and what treaty ended it?
   **Answer:** A series of wars in Central Europe (1618–1648) fought largely over religion and political power; ended by the Peace of Westphalia, which established the concept of national sovereignty.

7. What is the significance of the Magna Carta?
   **Answer:** Signed in 1215, it was the first document to limit the power of the English king and established that everyone — including the monarch — was subject to the rule of law. It is considered a foundation of constitutional governance.

8. Who was Tamerlane (Timur), and why was he historically significant?
   **Answer:** A 14th-century Turco-Mongol conqueror who built one of the largest empires of his era, stretching from Central Asia to Persia and into India; known for military genius and extreme brutality in conquered territories.

---

### MATH

#### Easy (15 questions)

1. What is 17 × 13?
   **Answer:** 221.

2. What is the next prime number after 29?
   **Answer:** 31.

3. A rectangle has sides of 7 and 12. What is its area? Its perimeter?
   **Answer:** Area = 84. Perimeter = 38.

4. If you have $240 and spend 35% of it, how much do you have left?
   **Answer:** $156.

5. What is the square root of 144?
   **Answer:** 12.

6. What is 23 × 7?
   **Answer:** 161.

7. What is 15% of 200?
   **Answer:** 30.

8. What is 3/4 + 1/3? Express as a simplified fraction.
   **Answer:** 13/12.

9. What is the LCM of 4 and 6?
   **Answer:** 12.

10. If x = 4, what is x³?
    **Answer:** 64.

11. What is 1000 ÷ 8?
    **Answer:** 125.

12. Convert 0.625 to a fraction.
    **Answer:** 5/8.

13. What is the mean of [4, 8, 6, 2, 10]?
    **Answer:** 6.

14. If a circle has radius 5, what is its area? (use π ≈ 3.14)
    **Answer:** 78.5.

15. How many degrees are in a right angle?
    **Answer:** 90.

---

#### Medium (12 questions)

1. Solve for x: `3x + 7 = 28`.
   **Answer:** x = 7.

2. A train travels at 80 km/h. How long does it take to cover 220 km? Give your answer in hours and minutes.
   **Answer:** 2 hours 45 minutes.

3. What is the sum of interior angles of a pentagon?
   **Answer:** 540°.

4. The Fibonacci sequence starts 1, 1, 2, 3, 5, 8... What are the next three numbers?
   **Answer:** 13, 21, 34.

5. If the probability of rain on any given day is 0.3, what is the probability it does NOT rain three days in a row?
   **Answer:** 0.7³ = 0.343.

6. Solve: 2x² - 8 = 0.
   **Answer:** x = 2 or x = -2.

7. A car travels 150 miles on 6 gallons of fuel. How far can it go on a full 15-gallon tank?
   **Answer:** 375 miles (25 mpg).

8. What is the sum of interior angles of a hexagon?
   **Answer:** 720°.

9. If a = 3 and b = 4, what is the hypotenuse of the right triangle?
   **Answer:** 5.

10. In how many ways can you arrange the letters in the word "CAT"?
    **Answer:** 6.

11. A store marks up prices 40%, then gives a 20% discount. Is the final price higher or lower than original, and by how much percent?
    **Answer:** Higher by 12% (1.4 × 0.8 = 1.12).

12. What is the GCD of 48 and 36?
    **Answer:** 12.

---

#### Hard (8 questions)

1. You have a 3-gallon jug and a 5-gallon jug. How do you measure exactly 4 gallons? Walk through the steps.
   **Answer:** Fill 5-gal → pour into 3-gal (5-gal has 2 left) → empty 3-gal → pour 2 gal into 3-gal → fill 5-gal again → pour from 5-gal into 3-gal until full (needs 1 gal) → 5-gal now has 4 gal.

2. What is the value of log₂(64)?
   **Answer:** 6 (since 2⁶ = 64).

3. A ball is dropped from 100m. Each bounce reaches half the previous height. What is the total distance the ball travels before coming to rest?
   **Answer:** 300m (100 down + 200 bouncing = geometric series: 100 + 2 × 100 × (1/2 + 1/4 + ...) = 100 + 200 = 300).

4. What is the derivative of f(x) = 3x⁴ - 2x² + 5x - 1?
   **Answer:** f'(x) = 12x³ - 4x + 5.

5. A geometric series has first term 2 and common ratio 1/3. What is the sum to infinity?
   **Answer:** 3 (formula: a/(1-r) = 2/(2/3) = 3).

6. How many ways can 5 people be seated at a round table?
   **Answer:** 24 (= (5-1)! = 4!).

7. What is the sum of the first 100 natural numbers?
   **Answer:** 5050 (= n(n+1)/2 = 100×101/2).

8. If f(x) = x² + 3x - 4, what are the roots of f(x) = 0?
   **Answer:** x = 1 and x = -4 (factor: (x+4)(x-1) = 0).

---

### ENTERTAINMENT

#### Easy (15 questions)

1. Name the actor who played Tony Stark / Iron Man in the MCU.
   **Answer:** Robert Downey Jr.

2. What year was the first iPhone released?
   **Answer:** 2007.

3. Which band sang "Bohemian Rhapsody"?
   **Answer:** Queen.

4. What is the highest-grossing film of all time (not adjusted for inflation)?
   **Answer:** Avatar (2009, re-releases included).

5. Name the author of the Harry Potter series.
   **Answer:** J.K. Rowling.

6. Name the superhero alter ego of Bruce Wayne.
   **Answer:** Batman.

7. In which sport is the Stanley Cup awarded?
   **Answer:** Ice hockey.

8. Who painted the Mona Lisa?
   **Answer:** Leonardo da Vinci.

9. Which artist released the album "Thriller"?
   **Answer:** Michael Jackson.

10. What video game franchise features a character named Master Chief?
    **Answer:** Halo.

11. Name the TV show in which Walter White is the main character.
    **Answer:** Breaking Bad.

12. What does "MCU" stand for?
    **Answer:** Marvel Cinematic Universe.

13. Name the actor who played Jack Sparrow in Pirates of the Caribbean.
    **Answer:** Johnny Depp.

14. What streaming service produces "Stranger Things"?
    **Answer:** Netflix.

15. Which country invented sushi?
    **Answer:** Japan.

---

#### Medium (12 questions)

1. Name three films directed by Christopher Nolan.
   **Answer:** Any three of: Memento, The Dark Knight, Inception, Interstellar, Dunkirk, Tenet, Oppenheimer.

2. What is the real name of the artist known as "The Weeknd"?
   **Answer:** Abel Tesfaye.

3. In which decade was hip-hop music generally considered to have originated?
   **Answer:** The 1970s (South Bronx, New York).

4. Which composer wrote The Four Seasons?
   **Answer:** Antonio Vivaldi.

5. Name three albums released by Kendrick Lamar.
   **Answer:** Any three of: Section.80, good kid m.A.A.d city, To Pimp a Butterfly, DAMN., Mr. Morale & The Big Steppers.

6. Which director made Pulp Fiction, Kill Bill, and Inglourious Basterds?
   **Answer:** Quentin Tarantino.

7. What year did the original Star Wars film (Episode IV: A New Hope) release?
   **Answer:** 1977.

8. What band was Beyoncé a member of before going solo?
   **Answer:** Destiny's Child.

9. Name three films in which Tom Hanks plays the lead role.
   **Answer:** Any three of: Forrest Gump, Cast Away, Philadelphia, Saving Private Ryan, The Green Mile, Captain Phillips.

10. What is the setting of the HBO series "The Wire"?
    **Answer:** Baltimore, Maryland.

11. Which video game is the best-selling of all time (over 300 million copies as of 2023)?
    **Answer:** Minecraft.

12. Name the four original members of Metallica.
    **Answer:** James Hetfield, Lars Ulrich, Dave Mustaine, Ron McGovney. (Current lineup: replace Mustaine with Kirk Hammett and McGovney with Cliff Burton.)

---

#### Hard (8 questions)

1. What was the first feature-length animated film ever released by Disney, and in what year?
   **Answer:** Snow White and the Seven Dwarfs, 1937.

2. Name the film that won Best Picture at the 2020 Oscars and why it was historically significant.
   **Answer:** Parasite (Bong Joon-ho) — first non-English-language film to win Best Picture.

3. What Radiohead album contains "Karma Police" and "No Surprises"?
   **Answer:** OK Computer (1997).

4. Who directed "2001: A Space Odyssey" and what studio released it?
   **Answer:** Stanley Kubrick; distributed by Metro-Goldwyn-Mayer (MGM).

5. What was the working title of the Beatles' "Yesterday" during its composition?
   **Answer:** "Scrambled Eggs."

6. Name three composers of the Baroque period other than Bach.
   **Answer:** Any three of: Handel, Vivaldi, Telemann, Purcell, Corelli, Monteverdi, Scarlatti.

7. What film is tied for the most Academy Award nominations of all time (14 nominations)?
   **Answer:** All About Eve (1950) and Titanic (1997) — both received 14 nominations.

8. In chess, what is the maximum number of queens one player can have on the board at the same time?
   **Answer:** 9 (the original queen plus 8 promoted pawns).

---

## Topic Rotation Logic

1. **Track used questions by index** within each topic + difficulty tier.
2. Never repeat a question until the entire tier is exhausted; shuffle on reset.
3. **Topic rotation:** exclude the last used topic; pick randomly from remaining configured topics.
4. **Difficulty cycle:** easy → medium → hard → medium → easy (repeating), unless `difficulty` is set to a fixed value.
5. If only one topic is configured, still rotate difficulty as above.

## Config Reference

```yaml
challenge:
  enabled: true
  topics:
    - math
    - leetcode
  difficulty: mixed        # easy | medium | hard | mixed
  in_active_urge: true
  in_warning: true
```
