# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  


HTML:

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Interactive Event Handling</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- 1. Event Handling -->
  <button id="clickBtn">Click Me</button>
  <button id="hoverBtn">Hover Over Me</button>
  <button id="keypressBtn">Press a Key</button>

  <!-- Bonus: Double click or Long press -->
  <button id="secretBtn">Double Click or Long Press</button>

  <!-- 2. Interactive Elements -->
  <div id="textChangerBtn">
    <button id="colorChangeBtn">Change My Color</button>
  </div>
  
  <!-- Image Gallery -->
  <div class="gallery">
    <img id="galleryImage" src="https://via.placeholder.com/200" alt="Image Gallery">
  </div>

  <!-- Tabs -->
  <div id="tabs">
    <button class="tabButton" data-target="tab1">Tab 1</button>
    <button class="tabButton" data-target="tab2">Tab 2</button>
    <div id="tab1" class="tabContent">Content for Tab 1</div>
    <div id="tab2" class="tabContent">Content for Tab 2</div>
  </div>

  <!-- 3. Form Validation -->
  <form id="form">
    <input type="text" id="name" placeholder="Enter Name" required><br>
    <input type="email" id="email" placeholder="Enter Email" required><br>
    <input type="password" id="password" placeholder="Enter Password" required><br>
    <button type="submit">Submit</button>
  </form>

  <script src="script.js"></script>
</body>
</html>

CSS
/* Basic Styling */
body {
  font-family: Arial, sans-serif;
  padding: 20px;
}

button {
  margin: 10px;
  padding: 10px 20px;
  cursor: pointer;
}

button:hover {
  background-color: lightblue;
}

/* Tabs and Content */
.tabContent {
  display: none;
  margin-top: 10px;
}

#tabs {
  margin-top: 20px;
}

/* Gallery */
.gallery {
  margin-top: 20px;
}

#galleryImage {
  width: 200px;
  height: auto;
  border: 2px solid black;
}

/* Real-time feedback (just a basic change of color) */
input:invalid {
  border: 2px solid red;
}

Script.js

// 1. Event Handling 🎈

// Button click event
document.getElementById("clickBtn").addEventListener("click", function() {
  alert("Button clicked!");
});

// Hover effect event
document.getElementById("hoverBtn").addEventListener("mouseover", function() {
  alert("Hovered over button!");
});

// Keypress detection
document.getElementById("keypressBtn").addEventListener("keydown", function(event) {
  alert(`You pressed the key: ${event.key}`);
});

// Bonus: Secret action on double click or long press
document.getElementById("secretBtn").addEventListener("dblclick", function() {
  alert("Double-click detected!");
});
let timer;
document.getElementById("secretBtn").addEventListener("mousedown", function() {
  timer = setTimeout(function() {
    alert("Long press detected!");
  }, 1000); // 1-second long press
});
document.getElementById("secretBtn").addEventListener("mouseup", function() {
  clearTimeout(timer); // Cancel long press if mouse is released before 1 second
});

// 2. Interactive Elements 🎮

// Change text or color
document.getElementById("colorChangeBtn").addEventListener("click", function() {
  const button = document.getElementById("colorChangeBtn");
  button.style.color = button.style.color === "red" ? "green" : "red";
  button.textContent = button.style.color === "red" ? "Changed Color to Red" : "Changed Color to Green";
});

// Image Gallery - Change image source
const galleryImage = document.getElementById("galleryImage");
const imageArray = [
  "https://via.placeholder.com/200?text=Image+1",
  "https://via.placeholder.com/200?text=Image+2",
  "https://via.placeholder.com/200?text=Image+3"
];
let currentIndex = 0;
galleryImage.addEventListener("click", function() {
  currentIndex = (currentIndex + 1) % imageArray.length;
  galleryImage.src = imageArray[currentIndex];
});

// Tabs (Accordion style content)
const tabButtons = document.querySelectorAll(".tabButton");
tabButtons.forEach(function(button) {
  button.addEventListener("click", function() {
    const target = document.getElementById(button.getAttribute("data-target"));
    const tabContents = document.querySelectorAll(".tabContent");
    tabContents.forEach(function(content) {
      content.style.display = "none";
    });
    target.style.display = "block";
  });
});

// 3. Form Validation 📋✅
// Real-time validation feedback
const form = document.getElementById("form");

form.addEventListener("submit", function(event) {
  const name = document.getElementById("name").value;
  const email = document.getElementById("email").value;
  const password = document.getElementById("password").value;

  // Name Validation
  if (!name) {
    alert("Name is required!");
    event.preventDefault();
  }

  // Email Validation
  const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
  if (!emailRegex.test(email)) {
    alert("Invalid email format!");
    event.preventDefault();
  }

  // Password Validation (min 8 characters)
  if (password.length < 8) {
    alert("Password must be at least 8 characters!");
    event.preventDefault();
  }
});

