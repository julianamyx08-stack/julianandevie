<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You, Always ❤️</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
  body {
    font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    background: linear-gradient(to bottom, #ffd6e8, #fcbad3);
    margin: 0;
    padding: 20px;
    text-align: center;
    color: #5a2a44;
    overflow-x: hidden;
  }

  h1 {
    font-size: 2em;
    margin-bottom: 5px;
  }

  p {
    opacity: 0.85;
    margin-top: 0;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(110px, 1fr));
    gap: 15px;
    margin-top: 30px;
  }

  .card {
    background: white;
    border-radius: 18px;
    padding: 20px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.15);
    font-weight: 600;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .card.today {
    box-shadow: 0 0 15px rgba(255,105,180,0.8);
  }

  .card:hover {
    transform: scale(1.05);
  }

  .locked {
    opacity: 0.4;
  }

  .note {
    display: none;
    background: white;
    margin-top: 35px;
    padding: 30px;
    border-radius: 22px;
    box-shadow: 0 12px 30px rgba(0,0,0,0.25);
    font-size: 1.1em;
    line-height: 1.6;
    animation: fadeIn 0.6s ease;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .heart {
    position: fixed;
    bottom: -20px;
    font-size: 20px;
    animation: floatUp 6s linear infinite;
    opacity: 0.6;
  }

  @keyframes floatUp {
    from { transform: translateY(0); opacity: 0.6; }
    to { transform: translateY(-110vh); opacity: 0; }
  }
</style>
</head>

<body>

<h1>For You, My Love ❤️</h1>
<p>One note each day — no skipping ahead.</p>

<div class="grid" id="cards"></div>
<div class="note" id="noteBox"></div>

<script>
/* ==============================
   ✏️ SET YOUR START DATE HERE
   Format: YYYY-MM-DD
   ============================== */
const startDate = "2026-02-14";

/* ==============================
   💌 WRITE YOUR 54 NOTES HERE
   Replace the text inside quotes
   ============================== */
const notes = [
  "Day 1: Write your note here 💖",
  "Day 2: Write your note here 💖",
  "Day 3: Write your note here 💖",
  "Day 4: Write your note here 💖",
  "Day 5: Write your note here 💖",
  "Day 6: Write your note here 💖",
  "Day 7: Write your note here 💖",
  "Day 8: Write your note here 💖",
  "Day 9: Write your note here 💖",
  "Day 10: Write your note here 💖",
  "Day 11: Write your note here 💖",
  "Day 12: Write your note here 💖",
  "Day 13: Write your note here 💖",
  "Day 14: Write your note here 💖",
  "Day 15: Write your note here 💖",
  "Day 16: Write your note here 💖",
  "Day 17: Write your note here 💖",
  "Day 18: Write your note here 💖",
  "Day 19: Write your note here 💖",
  "Day 20: Write your note here 💖",
  "Day 21: Write your note here 💖",
  "Day 22: Write your note here 💖",
  "Day 23: Write your note here 💖",
  "Day 24: Write your note here 💖",
  "Day 25: Write your note here 💖",
  "Day 26: Write your note here 💖",
  "Day 27: Write your note here 💖",
  "Day 28: Write your note here 💖",
  "Day 29: Write your note here 💖",
  "Day 30: Write your note here 💖",
  "Day 31: Write your note here 💖",
  "Day 32: Write your note here 💖",
  "Day 33: Write your note here 💖",
  "Day 34: Write your note here 💖",
  "Day 35: Write your note here 💖",
  "Day 36: Write your note here 💖",
  "Day 37: Write your note here 💖",
  "Day 38: Write your note here 💖",
  "Day 39: Write your note here 💖",
  "Day 40: Write your note here 💖",
  "Day 41: Write your note here 💖",
  "Day 42: Write your note here 💖",
  "Day 43: Write your note here 💖",
  "Day 44: Write your note here 💖",
  "Day 45: Write your note here 💖",
  "Day 46: Write your note here 💖",
  "Day 47: Write your note here 💖",
  "Day 48: Write your note here 💖",
  "Day 49: Write your note here 💖",
  "Day 50: Write your note here 💖",
  "Day 51: Write your note here 💖",
  "Day 52: Write your note here 💖",
  "Day 53: Write your note here 💖",
  "Day 54: Write your note here 💖"
];

// --- New Zealand time logic ---
const nzToday = new Date(
  new Date().toLocaleString("en-US", { timeZone: "Pacific/Auckland" })
);

const start = new Date(startDate + "T00:00:00");
const dayNumber = Math.floor((nzToday - start) / (1000 * 60 * 60 * 24));

const cards = document.getElementById("cards");
const noteBox = document.getElementById("noteBox");

notes.forEach((note, index) => {
  const card = document.createElement("div");
  card.className = "card";
  card.textContent = index <= dayNumber ? `Day ${index + 1}` : "🔒";

  if (index === dayNumber) card.classList.add("today");

  if (index <= dayNumber) {
    card.onclick = () => {
      noteBox.style.display = "block";
      noteBox.textContent = note;
      noteBox.scrollIntoView({ behavior: "smooth" });
    };
  } else {
    card.classList.add("locked");
  }

  cards.appendChild(card);
});

// floating hearts
setInterval(() => {
  const heart = document.createElement("div");
  heart.className = "heart";
  heart.textContent = "❤️";
  heart.style.left = Math.random() * 100 + "vw";
  document.body.appendChild(heart);
  setTimeout(() => heart.remove(), 6000);
}, 700);
</script>

</body>
</html>
