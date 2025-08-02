Career Guidance App
 Introduction
The Career Guidance App is a responsive and user-friendly web application developed to assist students in identifying suitable career paths and colleges based on their qualifications, preferences, and aptitude scores. Built with HTML, CSS, and JavaScript, the app simulates a structured student journey from registration to college recommendation and aptitude testing, offering both functionality and educational value.

 Features
 Student Portal
- Login & Sign Up: Secure access with required credentials (email, password, mobile, qualification).
- Career Selection: Choose from five career paths — Engineering, Management, Design, Medicine, Arts.
- Location Filter: Pick preferred study destination — India or Abroad.
College Listings
- A curated list of top universities with:
- Fee structure
- Location
- 5-star rating system
- Can be expanded dynamically using Firebase or APIs.
   Eligibility & Aptitude Section
- Enter CGPA to unlock aptitude test.
- Three categories:
- Verbal Reasoning
- Quantitative Ability
- General Knowledge
- Displays total score, stored for registration.
  Registration Confirmation
- Displays collected user data (name, mobile, qualification, CGPA, test score).
- Final submission simulated with an alert — expandable to backend integration.
🔐 Admin Access
- Admin login form (placeholder functionality).
- Future scope for backend control with role-based access.

🛠️ Technologies Used
| Layer | Stack | 
| Structure | HTML5 | 
| Styling | CSS3 | 
| Behavior | JavaScript | 
| Backend (Planned) | Firebase | 



🔧 How It Works
Section Navigation
Each button in the navigation bar triggers its corresponding section using the showSection() function.
Form Logic
JavaScript functions simulate user authentication, aptitude grading, and basic data handling:
- loginStudent(), handleSignUp(): Currently trigger alerts; can integrate with Firebase Auth.
- checkEligibility(): Activates aptitude section and captures CGPA.
- gradeTest(): Calculates score based on correct answers and stores it for final registration.
- validateAdmin(): Placeholder for admin validation logic.

📂 Suggested File Structure (Next Step)
/career-guidance-app
│
├── index.html
├── styles/
│   └── style.css
├── scripts/
│   └── main.js
├── assets/
│   └── images/
└── README.md



📈 Scope for Expansion
- Connect college listings to a real-time database or API.
- Add Firebase authentication for student and admin roles.
- Develop user dashboards to track performance and recommendations.
- Implement personalized career suggestions using aptitude scores.

🧪 Demo Test Questions Included
- Antonym of ‘Transparent’ → Opaque
- 25 × 4 → 100
- Current Prime Minister of India → Narendra Modi
Score calculated out of 3. Simple grading logic built using JavaScript radio inputs.

🤝 Credits & Author
Created by: Hemalatha Panam
Role: Full Stack Developer Intern
Institution: Eswar College of Engineering
Passion: Building educational tools with intuitive design and real-world impact

Let me know if you’d like a version written for GitHub, or help modularizing this app with Firebase integration and a clean folder structure. You’re really leveling up here! 🚀
