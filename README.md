EdTech Assessor Pro - 3D Analytics Edition 🎓📊
EdTech Assessor Pro is a zero-backend, client-side Single Page Application (SPA) designed for highly secure mock examinations and deep, data-driven 1-on-1 evaluator reviews. It features AES encryption for data security, strict anti-cheat mechanisms, and an advanced interactive dashboard equipped with Radar charts, Stacked bars, and Sankey (Cognitive Flow) diagrams.

🚀 Core Architecture
Zero Backend Required: Runs entirely in the browser. No databases, Python, or server environments are needed. Just double-click the index.html file.

Data Security: All exam submissions and evaluator reviews are compiled into JSON and encrypted using CryptoJS (AES Encryption) into a proprietary .examdata file format to prevent tampering.

Tech Stack: HTML5, CSS3, Vanilla JavaScript, Tailwind CSS (Styling), Chart.js (Radar & Bar charts), Plotly.js (Sankey diagrams).

✨ Features by Module
Module 1: Exam Interface (Aspirant Mode)

Designed for high-focus, timed assessments with strict integrity guardrails.

Strict Time Management: Features a 1 hour 45 minute countdown timer. If the timer hits zero, the exam is automatically submitted and locked.

Anti-Cheat Proctoring Engine:

3-Strike Tab Switching: Uses the browser's Page Visibility API. If the aspirant minimizes the window or opens a new tab, they receive a warning. On the 3rd strike, the exam auto-terminates.

Clipboard Lockdown: Completely disables right-click (context menu), Copy (Ctrl+C), Cut, and Paste (Ctrl+V).

Text-Selection Block: Prevents the user from highlighting question text to drag-and-drop into external search engines.

Encrypted Submission: Generates an unreadable [Aspirant]_submission.examdata blob file upon completion for the aspirant to send to their evaluator.

Module 2: Evaluator Dashboard (Reviewer Mode)

A comprehensive, interactive analytics suite designed for post-exam 1-on-1 mentoring.

Instant File Decryption: Securely uploads and decrypts the .examdata file entirely locally.

Interactive Visualizations (Dynamic Topic Filtering):

Sub-Topic Performance Radar (Chart.js): Maps the aspirant's actual Accuracy against the evaluator's logged Confidence Level across varying sub-topics.

Section Breakdown (Stacked Bar): Visualizes the ratio of Correct, Incorrect, and Unattempted questions per macro-section.

Cognitive Flow Map (Plotly Sankey Diagram): Traces the psychological pipeline of the aspirant by mapping Confidence → Root Cause → Final Outcome (e.g., High Confidence → Silly Mistake → Incorrect).

Detailed 1-on-1 Review Table:

Displays the question, detailed explanation, and highlights the aspirant's choice vs. the actual correct answer in color-coded boxes.

Deep Dive Integration: Auto-generates a "Search Google" link using the exact question and options.

Advanced Table Controls:

Live Status Filters: Clickable pill-badges to instantly filter the table by "All", "Correct", "Incorrect", or "Unattempted" (with dynamic question counters).

Smart Search Bar: Real-time text filtering by Topic/Sub-topic, complete with yellow pre-text highlighting for instant visual recognition.

Collaborative Metacognitive Tracker:

Dropdowns for the evaluator to log the Root Cause (Mastery, Misread, Conceptual Error, Timeout) and Aspirant Confidence.

Real-time Chart Updates: Selecting these dropdowns instantly redraws the Radar and Sankey diagrams above.

Save & Export State: Evaluators can click "Save & Export Evaluation" to inject their review notes back into the encrypted JSON and download an updated _evaluated_submission.examdata file for future reference.

🛠️ How to Use the Application
For the Aspirant (Taking the Exam)

Open index.html in any modern web browser (Chrome, Edge, Safari).

Click Start Exam (Aspirant Mode).

Complete the exam before the timer runs out. Do not switch tabs or try to copy text, or your exam will be terminated!

Upon clicking "Submit", a file named Aspirant_101_submission.examdata will automatically download to your machine.

Send this file to your Evaluator/Mentor.

For the Evaluator (Reviewing the Exam)

Open index.html and click Upload & Review (Evaluator Mode).

Upload the .examdata file provided by the Aspirant.

Use the Dashboard Tabs to filter the top charts by specific subjects (e.g., Economics, History).

Use the Quick Search and Status Filters (e.g., click "Incorrect") to navigate the table efficiently.

Discuss each missed question with the aspirant. Use the dropdowns in the Collaborative Tracker column to log why they missed it and how confident they were.

Watch the Cognitive Flow (Sankey Diagram) build itself as you log data.

Click 💾 Save & Export Evaluation at the top to download a permanent record of your 1-on-1 session.

🗄️ Adding New Questions (For Developers/Admins)
To add more questions to the test bank, open the index.html file in a text editor. Locate the rawQuestionBank array (around line 340). You can paste as many JSON question objects as you like into this array following the existing schema:

JSON
{
  "question_number": 1,
  "main_topic": "Subject Name",
  "sub_topic": "Chapter/Module Name",
  "question": "The question text here...",
  "options": ["A) Option 1", "B) Option 2", "C) Option 3", "D) Option 4"],
  "correct_answer": "A) Option 1",
  "explanation": "Detailed explanation here."
}
Note: The built-in Data Adapter will automatically format your raw JSON to fit the application's internal engine.
