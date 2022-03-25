# wordle-solver

**What is Wordle?**

I’m sure you’ve heard of the popular game - Wordle. There’s a new 5 letter word released everyday, and players have 6 tries to guess it. At each guess, the game tells you which letters are ‘green’ (you guessed correctly and in the right position), which letters are ‘yellow’ (guessed correctly but in the wrong position) and ‘grey’ (not in the word at all). Based on these clues, you must make your next guess.

I’m obsessed with the game and haven’t missed a day since I started playing it. I always wondered what the best starting word, or best possible word to guess at any given stage of the game, was. Hence, this project!

**How the Solver works:**

1. The player first enters a word for the solver to guess.
2. The solver uses the list of possible 5-letter-word solutions scraped from Wordle’s website.
3. It calculates the frequency distribution of each letter across the list of solutions.
4. It then loops through all the possible 5-letter words and ‘scores’ them based on the frequency of their letters.
5. The above two steps are cached so that we don’t have to calculate it over and over again.
6. It then guesses the word with the highest score - “LATER” for the first guess.
7. It then checks its guess against the player’s word and ‘learns’ what letters are green, yellow and grey.
8. Based on these hints, it eliminates words that don’t fit this pattern from its scored list of words.
9. It then guesses the next word with the highest score, and so on until it guesses the word.

**Limitations/Further Improvements:**

- When scoring the words, the solver could also take into account the position of letters and not just their presence.
- Maybe another strategy could be to guess words that eliminate the most words, instead of just the highest ranked word. So from the top 5 highly ranked words, checking which words eliminate the most options (using backpropagation maybe?) and trying that one instead.
- Based on the previous point, having some sort of explore vs exploit metric, i.e. in the earlier tries, trying words that eliminate more possible options while in later tries, going with safer options.
- The only words I have tried that the solver fails to guess so far are “Grave” and “Graze” - since there are so many words that fit the “GRA-E” structure like grace, grade, grate, grape - which are all more “likely guesses” than grave or graze. Instead of trying ‘grade’, ‘grape’ or ‘grate’ separately, it could try ‘depth’ instead which would eliminate ‘d’, ‘p’ and ‘t’ in a single try, leaving it with more chances to try other words.
