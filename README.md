Not updated...


# Bullet Line: Scripture Pursuit (KJV)

**Bullet Line: Scripture Pursuit** is an engaging, high-speed King James Version (KJV) Bible trivia game built as a self-contained web application. Test your knowledge of the Old and New Testaments, build your silver treasury, and outrun the incoming derailment!

---

## 🚀 Core Features

* **KJV Scripture Integration:** Every trivia question is paired with a direct King James Bible reference and scripture quote to deepen your study and understanding of the Word.
* **The Cash Builder Round:** A fast-paced 60-second opening round where you bank 1,000 Shekels of Silver for every correct answer.
* **Dynamic Chase Mechanics:** Navigate the 7-step train board as you try to outrun an approaching Derailment. Correct answers move your Bullet Train toward the station while incorrect answers let the chaser close the gap.
* **Procedural Web Audio API Sound Effects:** Fully self-contained sound effects and train ambient audio generated programmatically via JavaScript—no external audio assets required.
* **Responsive & Immersive UI:** Features a custom neon train CSS layout, animated fog background, mobile-optimized scripture viewing drawers, and dynamic game statistics tracking.
* **The Jerusalem Herald News Ticker:** A two-line LED marquee on the title screen delivers scrolling local weather and a rotating feed of KJV-inspired "breaking news" headlines — see below for details.

---

## 🎮 How to Play

1. **Start the Game:** Click the **START GAME** button on the main screen.
2. **The Builder Round:** Answer as many KJV Bible questions as you can within 60 seconds to stack up your starting Shekels of Silver.
3. **Choose Your Head Start:** Select your track position based on your accumulated bank (Lower Track, Current Bank, or Express Line).
4. **The Chase:** Answer difficulty-scaled questions (Easy, Medium, Hard) to advance your Bullet Train to the station (Step 0) while keeping ahead of the Derailment!

---

## 💰 Treasury Management System

The game tracks your biblical wealth across three distinct metrics:

### **TREASURY** (Current Game Bank)
* **What it is:** The amount of Shekels you've earned in the current game session.
* **When it updates:** Increases by 1,000 Shekels for each correct answer during the Builder Round.
* **When it resets:** Resets to 0 Shekels when you start a new game or finish the current one.
* **Display:** Shows at the top-left of the screen during gameplay.

### **TOTAL TREASURY** (Running Tally)
* **What it is:** The cumulative total of all Shekels earned across every won game, ever.
* **When it updates:** Only increases when you **win** a game (reach the Train Station). Losses don't add to this total.
* **When it resets:** Never resets automatically — it's a persistent running tally saved in browser localStorage under the key `totalTreasuryAccount`, and it carries forward across page reloads and browser sessions. You can manually clear it only by clearing your browser's localStorage.
* **Display:** Shows at the top-right of the screen during gameplay.
* **Purpose:** Tracks your all-time success across every game you've ever played on this device/browser.

### **🏆 HIGH SCORE TREASURY** (Persistent Record)
* **What it is:** The single highest TREASURY amount you've ever earned in a game.
* **When it updates:** Automatically updates whenever you complete a game with more Shekels than your previous high score.
* **When it resets:** Never resets automatically—persists forever until you beat it. You can manually clear it only by clearing your browser's localStorage.
* **Storage:** Saved in browser localStorage under the key `treasuryHighScore`.
* **Display:** Shows above the train board during the Chase Round (only during active gameplay, not on the title screen).
* **Purpose:** Gives you a challenge to beat across sessions—a personal record to surpass.

### **Example Scenario**
```
Starting Point (from previous play):
  - HIGH SCORE: 5,000 Shekels
  - TOTAL TREASURY: 12,000 Shekels

Game 1 (Win with 3,000):
  - TREASURY: 3,000 Shekels → game ends, resets to 0
  - TOTAL TREASURY: 15,000 Shekels (12,000 + 3,000, saved to localStorage)
  - HIGH SCORE: Still 5,000 (didn't beat it)

Game 2 (Win with 6,000):
  - TREASURY: 6,000 Shekels → game ends, resets to 0
  - TOTAL TREASURY: 21,000 Shekels (15,000 + 6,000)
  - HIGH SCORE: 6,000 Shekels 🎉 (NEW HIGH SCORE!)

Game 3 (Lose, earn 0):
  - TREASURY: 0 Shekels (crashed before banking)
  - TOTAL TREASURY: 21,000 Shekels (losses don't add)
  - HIGH SCORE: Still 6,000 Shekels

Page reload/new browser session:
  - TOTAL TREASURY: Still 21,000 Shekels (persists, does not reset)
```

---

## 📊 Game Summary Report

After each game concludes (win or loss), a detailed **Game Summary Report** is displayed showing:

* **Question-by-Question Breakdown:** Every question you answered during the game, listed in order with:
  * Your choice vs. the correct answer
  * Result badge (✓ CORRECT or ✗ INCORRECT)
  * The KJV scripture reference paired with each question
  * The full scripture text for deeper study
* **High Score Comparison:** 
  * If you set a **new high score:** A trophy banner celebrates your achievement with the new record amount
  * If you didn't beat it: Shows your final score, the high score to beat, and how many Shekels away you were
* **Game Statistics:** A running total at the bottom tracks:
  * Total games played
  * Games won
  * Games lost
* **Print Report:** Click the **🖨️ Print** button next to the report title to:
  * Open a print-friendly version of your game summary
  * Save it as a PDF for future reference
  * Print it to a physical printer if desired
  * The printed report includes all questions, answers, scripture references, and formatting—perfect for personal record-keeping or sharing your performance
* **Share & Restart Options:** Copy your results or start a fresh game immediately.

This report helps reinforce biblical knowledge, track your progress over multiple play sessions, see how close you came to beating your personal high score, and generate a printable record of your gameplay.

---

## 🔄 Question Deck Shuffle Logic

The game uses a **smart deck shuffling system** to ensure a fresh experience while preventing question fatigue:

* **Session Persistence:** Used question IDs are tracked in browser localStorage (`bulletline_used_questions`), preventing the same question from appearing twice in a single session.
* **Automatic Reshuffling:** When all questions in the master deck have been asked, a shuffle modal appears notifying you that the deck is being reset. The used question log is cleared, and all 400+ questions become available again.
* **Graceful Fallback:** If localStorage is unavailable (e.g., private browsing mode or embedded browsers), the question deck still tracks usage in-memory for that session only—you won't replay questions until you reload the page.
* **Randomized Draw:** Active questions are randomly shuffled on each reset to ensure varied game experiences.

---

## 🔀 Reshuffle Deck Button

The **🔀 Reshuffle Deck** button appears on the main title screen and allows you to manually reset the question deck at any time:

* **What it does:** Clears your used question history and reshuffles all 400+ questions back into the active deck, regenerating a fresh randomized order.
* **When to use it:** If you've gone through many questions and want to reset the deck before the automatic reshuffle modal appears, or if you simply want a fresh randomized question order for variety.
* **Storage:** Clears the `bulletline_used_questions` localStorage entry and resets the in-memory tracking.
* **Note:** This button only appears on the title screen (not during active gameplay). Pressing it does not affect any current game in progress.

---

## 📡 The Jerusalem Herald News Ticker

The title screen features a two-line scrolling LED ticker themed as a fictional news network, "The Jerusalem Herald":

* **Line 1** cycles through welcome and promotional messages.
* **Line 2** alternates between a local weather readout ("YOUR LOCAL WEATHER IN THE HOLY LAND") and batches of KJV-inspired news headlines, each labeled with the "JERUSALEM HERALD" masthead (styled gold) and a status tag (styled red — normally "BREAKING NEWS," see below).

**Randomized playback:** Every time Line 2 finishes a pass — including each time it loops — the news headlines are freshly shuffled into a new random order, and are broken into randomly-sized batches of 1 to 5 stories between each weather segment (rather than a fixed count), so the sequence and grouping is different every time.

**Weather audio:** Background weather music fades out automatically the moment a news headline begins, whenever that headline appears in the rotation.

**Headline library:** Line 2 currently draws from 45+ headlines spanning both Old and New Testament events (Creation, the Flood, the Exodus, the judges and kings, the exile, the life and ministry of Jesus, and the early church), written in a tabloid "breaking news" voice. A number of headlines involving Jesus explicitly proclaim His identity — as the Christ, the Son of God, and the Savior of the world who came to save mankind from sin — in addition to reporting the event itself.

* **Status tags:** Most headlines run under the default **"BREAKING NEWS"** tag. A headline can instead carry a custom tag when "breaking news" wouldn't make sense for it — for example, the Noah's Ark headline is framed as a retrospective, first-person recollection from an aged Noah rather than same-day coverage (since only his family of eight would have survived to report it), and runs under a **"SPECIAL REPORT"** tag instead.

---

## 📂 Project Structure

The project is organized into a handful of files rather than a single monolithic one, separating the question data and styling from the application logic:

* `index.html` — The core application: HTML structure, SVG graphics, audio synthesis logic, and game logic.
* `styles.css` — All CSS styling, including the neon train layout, animated fog background, mobile-optimized scripture drawers, and news ticker styling.
* `questions.json` — The complete 400+ question bank, including scripture references, quotes, and answer choices.
* `store.html` — A standalone merchandise/store page sharing the game's branding, fog background, and visual style.
* `logo.png` — The game's logo image.
* `License.pdf` — Project license documentation.

---

## 📜 License

This work is licensed under the **Apache License 2.0**. 

© 2026 William Monti. See the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) for more details.
