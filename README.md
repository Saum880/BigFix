# BigFix Lifecycle Training Hub & Dashboard

An interactive, high-fidelity, single-page training website for learning **HCL BigFix Lifecycle**. Designed for Systems Administrators, Security Engineers, and Operations Teams to master endpoint management at scale.

## Features

- **5 Core Learning Modules**:
  1. Architecture & Client Operations (Relays, Server, UDP/TCP Port 52311)
  2. Patch Management & Action Sites (Fixlets, Tasks, Baselines, Relevance checking)
  3. Software Distribution (Dashboard, pre-caching, prefetch hashing, waithidden installer logs)
  4. OS Deployment (OSD) (PXE configurations, captured reference WIMs, driver bindings)
  5. Server Automation & Relevance Language (Relevance query clauses, ActionScript registry edits)
- **Interactive Quizzes**: Direct assessment at the end of each module with detailed logical rationale for right/wrong options.
- **Progress Tracking**: Automatic percentage tracking and module completion saving utilizing browser `localStorage`.
- **Integrated Google Form**: Clean registration/feedback form area ready to link directly to your custom Google Form.
- **Premium Styling**: Sleek glassmorphism cards, neon tech theme, responsive grids, and subtle micro-animations.

---

## Getting Started

### 1. Run Locally
Since this project is built entirely on native web standards (HTML5, CSS3, ES6 JavaScript), you do not need to install heavy dependencies or build frameworks.

Simply double-click the [index.html](file:///C:/Users/saumi/.gemini/antigravity/scratch/bigfix-lifecycle-training/index.html) file to open it in your browser, or run a local web server (e.g., using Python, Node, or VS Code's Live Server).

To run a server with Python:
```bash
# From within the directory: C:\Users\saumi\.gemini\antigravity\scratch\bigfix-lifecycle-training
python -m http.server 8000
```
Then visit: `http://localhost:8000`

---

## Customizing the Google Form

To replace the demo feedback form with your own **Google Form**, follow these simple steps:

1. **Get the Embed Code from Google Forms**:
   - Go to your Google Form.
   - Click the **Send** button in the top right.
   - Select the `< >` (HTML Embed) tab.
   - Copy the link URL from the `src` attribute inside the iframe tag (it looks like `https://docs.google.com/forms/d/e/.../viewform?embedded=true`).

2. **Replace the Link in the Code**:
   - Open `app.js`.
   - Scroll down to the `loadGoogleForm` function around **line 527**:
     ```javascript
     function loadGoogleForm() {
         if (formPlaceholder && googleFormIframe) {
             formPlaceholder.classList.add("hidden");
             
             // REPLACE THIS URL WITH YOUR GOOGLE FORM LINK:
             googleFormIframe.src = "https://docs.google.com/forms/d/e/YOUR-FORM-ID/viewform?embedded=true";
         }
     }
     ```
   - Paste your copied link, save the file, and reload your browser.

---

## Customizing the Email Form (Direct Gmail Delivery)

To route registration and feedback details directly to your Gmail address without leaving the webpage:

1. **Get a Free Web3Forms Access Key**:
   - Go to [web3forms.com](https://web3forms.com/).
   - Enter your Gmail address and click **Create Access Key**.
   - You will instantly receive an Access Key in your Gmail inbox.

2. **Paste your Access Key into the Code**:
   - Open `app.js`.
   - Near the top of the file, update the `CONFIG` object around **line 6**:
     ```javascript
     const CONFIG = {
         // Paste your Web3Forms Access Key here:
         web3formsAccessKey: "YOUR_ACCESS_KEY_HERE", 

         // (Optional Fallback) Replace this email address with your actual email address.
         targetEmail: "your-email@example.com"
     };
     ```
   - Replace `"YOUR_ACCESS_KEY_HERE"` with your actual key and save.

3. **Enjoy Direct Submissions**:
   - Now, when users click **Send Message**, a loading spinner will appear, and the form will submit *directly on the page itself*.
    - A success banner will display, and you will receive a clean notification email directly to your Gmail containing their name, email, phone number (if provided), query type, comments, and **their live course progress percentage**!

---

## File Directory

- `index.html` - Semantic layout, structural elements, SVG graphics, and container divs.
- `styles.css` - Harmonious dark colors, responsive grids, custom typography (Outfit), and active progress animations.
- `app.js` - Data arrays (modules, quizzes) and user state handling (`localStorage`).

