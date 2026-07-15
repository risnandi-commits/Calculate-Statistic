# 🧮 StatCalc: Neumorphic CLI Statistical Calculator
**StatCalc** is a modern, lightweight, web-based statistical calculator built with React.js. It elegantly bridges the gap between retro Command Line Interfaces (CLI) and modern Neumorphic (soft UI) design, providing a tactile, interactive, and highly functional tool for instant statistical data analysis.
## ✨ Value Proposition & Key Features
Unlike standard calculators that perform basic arithmetic, StatCalc is engineered specifically for **dataset analysis**.
 * **📊 Comprehensive Statistical Engine:** Instantly compute complex dataset metrics including:
   * **Mean** (Average)
   * **Median** (Middle value)
   * **Mode** (Most frequent value)
   * **Variance** (Sample variance)
   * **Standard Deviation** (Sample std dev)
   * **Range** (Minimum and Maximum values)
 * **🕹️ Interactive "Floating" UI (Haptic-style Feedback):**
   The keypad utilizes advanced CSS transitions. Upon touch or click, buttons exhibit a "floating" effect—lifting towards the user, expanding slightly, and casting a dynamic blue shadow. This provides exceptional visual feedback that mimics physical tactile switches.
 * **💻 Retro-Modern CLI Display:**
   The screen features a monospace, terminal-inspired interface (green text on a dark background) with a subtle pulse animation, contrasting beautifully with the physical-looking Neumorphic casing.
 * **🎵 Auditory Feedback:**
   Integrated Web Audio API generates a subtle, high-frequency sine wave "beep" on every keystroke, enhancing the physical calculator experience without relying on external audio files.
 * **📱 Progressive Web App (PWA) Ready:**
   Built as a single-page application that is fully responsive. It behaves natively on mobile devices and can be added to the home screen for a standalone app experience.
## 🛠️ Technology Stack
 * **Core Framework:** React.js (Functional Components, Hooks: useState, useEffect)
 * **Styling:** Tailwind CSS (Utility-first CSS for Neumorphism, Grid layouts, and advanced state animations)
 * **Logic:** Modern JavaScript (ES6+) utilizing functional array methods (reduce, sort, filter) for O(n log n) statistical computations.
 * **Audio:** Native HTML5 Web Audio API.
## 📐 Architecture & Design Philosophy
### 1. State Management
The application strictly separates the currentInput (the number currently being typed) from the dataset (the array of submitted numbers). This allows users to build large arrays of data before executing any mathematical operation, which is critical for statistical analysis.
### 2. Neumorphism combined with Terminal Aesthetic
The outer chassis uses precise box-shadow techniques (shadow-[20px_20px_60px_#bebebe,-20px_-20px_60px_#ffffff]) on an #e0e5ec background to simulate extruded plastic or metal. The screen divots inward (shadow-inner) to house the CLI interface, creating a striking contrast between the physical and the digital.
## 🚀 How to Use
 1. **Input Data:** Type a numerical value using the keypad.
 2. **Add to Dataset:** Press the green **ADD** button. The number will be pushed to the dataset array displayed on the CLI screen. Repeat this for all your data points.
 3. **Calculate:** Once your dataset is populated, press any of the blue statistical operation buttons (e.g., **Mean**, **Std**, **Var**).
 4. **Clear/Edit:** Use **DEL** to remove the last typed character, or the red **AC** button to clear the entire dataset and start over.
## 📦 Installation & Local Development
To run this project locally:
```bash
# 1. Clone the repository
git clone [https://github.com/risnandi-commits/statcalc.git](https://github.com/risnandi-commits/statcalc.git)

# 2. Navigate to the directory
cd statcalc

# 3. Install dependencies
npm install

# 4. Start the development server
npm start

```
## 📜 License
This project is open-source and available under the MIT License. Feel free to fork, modify, and use it in your own projects!
