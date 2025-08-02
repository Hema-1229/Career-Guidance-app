<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Career Guidance App</title>
  <meta name="description" content="A career guidance app using HTML, CSS, JS, Firebase for students seeking college & course recommendations.">
  <style>
    body { font-family: 'Segoe UI', sans-serif; margin: 0; background: #f6f8fc; color: #333; }
    header { background: #34495e; color: white; padding: 20px; text-align: center; }
    nav { text-align: center; margin: 15px 0; }
    nav button { margin: 5px; padding: 10px 15px; background: #2ecc71; color: white; border: none; border-radius: 5px; cursor: pointer; }
    nav button:hover { background: #27ae60; }
    section { display: none; max-width: 800px; margin: 20px auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
    section.active { display: block; }
    h2 { color: #2c3e50; margin-top: 0; }
    form input, form select, form button, form textarea {
      width: 100%; padding: 10px; margin: 8px 0; border-radius: 5px; border: 1px solid #ccc;
    }
    form button { background: #3498db; color: white; border: none; cursor: pointer; }
    form button:hover { background: #2980b9; }
    ul { padding-left: 20px; }
    .radio-group label { display: block; margin: 5px 0; }
    .test-block { margin-bottom: 20px; }
  </style>
</head>
<body>

<header>
  <h1>Career Guidance App</h1>
  <p><em>Project Title:</em> Career Guidance | <em>Tech:</em> HTML, CSS, JS, Firebase | <em>Domain:</em> Education </p>
</header>

<nav>
  <button onclick="showSection('student-login')">Login</button>
  <button onclick="showSection('student-signup')">Sign Up</button>
  <button onclick="showSection('career-selection')">Career</button>
  <button onclick="showSection('location-selection')">Location</button>
  <button onclick="showSection('college-list')">College List</button>
  <button onclick="showSection('eligibility-test')">Eligibility & Aptitude</button>
  <button onclick="showSection('college-registration')">Registration</button>
  <button onclick="showSection('admin-login')">Admin</button>
</nav>

<section id="student-login" class="active">
  <h2>Student Login</h2>
  <form onsubmit="event.preventDefault(); loginStudent()">
    <input type="email" placeholder="Email" required />
    <input type="password" placeholder="Password" required />
    <button type="submit">Login</button>
  </form>
</section>

<section id="student-signup">
  <h2>Student Sign Up</h2>
  <form onsubmit="event.preventDefault(); handleSignUp()">
    <input type="text" id="name" placeholder="Full Name" required />
    <input type="email" id="signup-email" placeholder="Email" required />
    <input type="password" id="signup-password" placeholder="Password" required />
    <input type="text" id="mobile" placeholder="Mobile Number" required />
    <input type="text" id="qualification" placeholder="Highest Qualification" required />
    <button type="submit">Register</button>
  </form>
</section>

<section id="career-selection">
  <h2>Select Career Path</h2>
  <select onchange="alert('Selected: ' + this.value)">
    <option disabled selected>Select one</option>
    <option>Engineering</option>
    <option>Management</option>
  </select>
</section>

<section id="location-selection">
  <h2>Preferred Location</h2>
  <button id="india-btn">India</button>
  <button id="abroad-btn">Abroad</button>
</section>

<section id="college-list">
  <h2>Recommended Colleges</h2>
  <ul id="college-ul"></ul>
</section>

<section id="college-details">
  <h2>College Details</h2>
  <div id="details-content"></div>
</section>

<section id="eligibility-test">
  <h2>Eligibility & Aptitude Test</h2>
  <form onsubmit="event.preventDefault(); checkEligibility()">
    <input type="text" id="cgpa" placeholder="Enter CGPA (e.g. 8.2)" required />
    <button type="submit">Check Eligibility</button>
  </form>

  <div id="aptitude-section" style="display:none;">
    <h3>Aptitude Test</h3>
    <form onsubmit="event.preventDefault(); gradeTest()">
      <div class="test-block">
        <h4> Verbal Reasoning</h4>
        <p>Q1: Antonym of 'Transparent'?</p>
        <div class="radio-group">
          <label><input type="radio" name="q1" value="Opaque"> Opaque</label>
          <label><input type="radio" name="q1" value="Clear"> Clear</label>
          <label><input type="radio" name="q1" value="Visible"> Visible</label>
        </div>
      </div>
      <div class="test-block">
        <h4> Quantitative Ability</h4>
        <p>Q2: What is 25 × 4?</p>
        <div class="radio-group">
          <label><input type="radio" name="q2" value="100"> 100</label>
          <label><input type="radio" name="q2" value="80"> 80</label>
          <label><input type="radio" name="q2" value="120"> 120</label>
        </div>
      </div>
      <div class="test-block">
        <h4> General Knowledge</h4>
        <p>Q3: Who is the current Prime Minister of India?</p>
        <div class="radio-group">
          <label><input type="radio" name="q3" value="Narendra Modi"> Narendra Modi</label>
          <label><input type="radio" name="q3" value="Amit Shah"> Amit Shah</label>
          <label><input type="radio" name="q3" value="Rahul Gandhi"> Rahul Gandhi</label>
        </div>
      </div>
      <button type="submit">Submit Test</button>
    </form>
    <p id="score-result"></p>
  </div>
</section>

<section id="college-registration">
  <h2>College Registration</h2>
  <p><strong>Name:</strong> <span id="student-name">–</span></p>
  <p><strong>Mobile:</strong> <span id="student-mobile">–</span></p>
  <p><strong>Qualification:</strong> <span id="student-qualification">–</span></p>
  <p><strong>CGPA:</strong> <span id="student-cgpa">–</span></p>
  <p><strong>Test Score:</strong> <span id="student-score">–</span></p>
  <button onclick="alert('Registration Submitted Successfully!')">Finalize Registration</button>
</section>

<section id="admin-login">
  <h2>Admin Login</h2>
  <form onsubmit="event.preventDefault(); validateAdmin()">
    <input type="text" id="admin-id" placeholder="Admin ID" required />
    <input type="password" id="admin-pass" placeholder="Password" required />
    <button type="submit">Login</button>
  </form>
</section>

<script>
document.addEventListener('DOMContentLoaded', function () {
  function showSection(sectionId) {
    document.querySelectorAll('section').forEach(sec => sec.classList.remove('active'));
    const target = document.getElementById(sectionId);
    if (target) target.classList.add('active');
  }
  window.showSection = showSection;

  const collegeData = [
    {
        name: "IIT Delhi",
        location: "New Delhi, India",
        tuition: "₹2,00,000",
        housing: "₹30,000/year",
        eligibility: "JEE Advanced Rank < 1000",
        placement: "95%, Avg ₹18 LPA",
        scholarship: "Merit-based & Financial Aid",
        services: "Labs, Hostel, Counseling, Internet",
        rules: "Attendance ≥ 75%, No ragging",
        rating: 5
    },
  {
    name: "IIT Bombay",
    location: "Mumbai, India",
    tuition: "₹2,00,000",
    housing: "₹40,000/year",
    eligibility: "JEE Advanced Rank < 2000",
    placement: "95%, Avg ₹20 LPA",
    scholarship: "Merit-based & Financial Aid",
    services: "Labs, Hostel, Counseling, Internet",
    rules: "Attendance ≥ 75%, No ragging",
    rating: 5
  },
  {
    name: "IIM Ahmedabad",
    location: "Ahmedabad, India",
    tuition: "₹26,50,000",
    housing: "₹60,000/year",
    eligibility: "CAT Percentile ≥ 98",
    placement: "100%, Avg ₹34 LPA",
    scholarship: "Govt & Corporate Sponsored",
    services: "Library, Wi-Fi, Mentorship",
    rules: "Code of Conduct, Ethics Training",
    rating: 5
  },
  {
    name: "AIIMS Delhi",
    location: "New Delhi, India",
    tuition: "₹1,628",
    housing: "₹15,000/year",
    eligibility: "NEET Rank < 100",
    placement: "98%, Avg ₹12 LPA",
    scholarship: "Govt Medical Grants",
    services: "Clinical Labs, Hostel, Research",
    rules: "Strict attendance, Medical ethics",
    rating: 5
  },
    {
        name: "NIT Trichy",
        location: "Tiruchirappalli, India",
        tuition: "₹1,25,000/year",
        housing: "₹30,000/year",
        eligibility: "JEE Main Rank < 5000",
        placement: "90%, Avg ₹10 LPA",
        scholarship: "Merit-based, Govt Schemes",
        services: "Labs, Hostel, Sports, Wi-Fi",
        rules: "Attendance ≥ 75%, Anti-ragging",
        rating: 4
    },
  {
    name: "IIT Madras",
    location: "Chennai, India",
    tuition: "₹2,53,000/year",
    housing: "₹45,000/year",
    eligibility: "JEE Advanced Rank < 2500",
    placement: "94%, Avg ₹19 LPA",
    scholarship: "Merit-based, Govt Schemes",
    services: "Labs, Hostel, Sports, Wi-Fi",
    rules: "Attendance ≥ 75%, Anti-ragging",
    rating: 5
  },
  {
    name: "IISc Bangalore",
    location: "Bangalore, India",
    tuition: "₹30,000/year",
    housing: "₹20,000/year",
    eligibility: "JEE Advanced, KVPY, GATE",
    placement: "92%, Avg ₹22 LPA",
    scholarship: "DST, CSIR, Institute Grants",
    services: "Research Labs, Hostel, Library",
    rules: "Research Ethics, Attendance",
    rating: 5
  },
  {
    name: "BITS Pilani",
    location: "Pilani, India",
    tuition: "₹6,03,775/year",
    housing: "₹60,000/year",
    eligibility: "BITSAT Score ≥ 300",
    placement: "98%, Avg ₹18 LPA",
    scholarship: "Merit & Need-based",
    services: "Innovation Labs, Clubs, Hostel",
    rules: "Honor Code, Attendance",
    rating: 5
  },
  {
    name: "NUS Singapore",
    location: "Singapore",
    tuition: "₹22,00,000/year",
    housing: "₹6,00,000/year",
    eligibility: "IELTS ≥ 6.5, Academic Merit",
    placement: "96%, Avg ₹35 LPA",
    scholarship: "ASEAN, Merit-based",
    services: "Global Labs, Career Center, Dorms",
    rules: "Academic Integrity, Visa Rules",
    rating: 5
  },
  {
    name: "ETH Zurich",
    location: "Zurich, Switzerland",
    tuition: "₹1,50,000/year",
    housing: "₹8,00,000/year",
    eligibility: "German/English Proficiency, GPA ≥ 8.5",
    placement: "93%, Avg ₹38 LPA",
    scholarship: "Swiss Govt, ETH Excellence",
    services: "Research Labs, Language Support",
    rules: "Research Ethics, Cultural Respect",
    rating: 5
  },
  {
    name: "University of Melbourne",
    location: "Melbourne, Australia",
    tuition: "₹30,00,000/year",
    housing: "₹10,00,000/year",
    eligibility: "IELTS ≥ 7.0, Academic Merit",
    placement: "90%, Avg ₹28 LPA",
    scholarship: "Melbourne International, Need-based",
    services: "Labs, Clubs, Career Services",
    rules: "Visa Compliance, Attendance",
    rating: 4
  },
    {
        name: "Harvard University",
        location: "Cambridge, USA",
        tuition: "₹50,00,000/year",
        housing: "₹20,00,000/year",
        eligibility: "TOEFL ≥ 100, SAT ≥ 1500",
        placement: "97%, Avg ₹50 LPA",
        scholarship: "Need-blind, Merit-based",
        services: "Research Labs, Career Counseling",
        rules: "Honor Code, Campus Safety",
        rating: 5
    },

  {
    name: "University of Oxford",
    location: "Oxford, UK",
    tuition: "₹47,28,000/year",
    housing: "₹19,77,000/year",
    eligibility: "IELTS ≥ 7.5, Academic Excellence",
    placement: "95%, Avg ₹40 LPA",
    scholarship: "Rhodes, Clarendon, Need-based",
    services: "Libraries, Career Services, Clubs",
    rules: "Academic Integrity, Visa Compliance",
    rating: 5
  },
  {
    name: "Massachusetts Institute of Technology (MIT)",
    location: "Cambridge, USA",
    tuition: "₹51,93,000/year",
    housing: "₹17,41,000/year",
    eligibility: "TOEFL ≥ 100, SAT ≥ 1500",
    placement: "98%, Avg ₹45 LPA",
    scholarship: "Need-blind, Research Grants",
    services: "Labs, Innovation Centers, Mentors",
    rules: "Honor Code, Research Ethics",
    rating: 5
  },
  {
    name: "University of Tokyo",
    location: "Tokyo, Japan",
    tuition: "₹5,00,000/year",
    housing: "₹3,00,000/year",
    eligibility: "JLPT N2/N1, Academic Merit",
    placement: "90%, Avg ₹18 LPA",
    scholarship: "MEXT, JASSO, University Grants",
    services: "Language Support, Labs, Dorms",
    rules: "Cultural Respect, Attendance",
    rating: 4
  },

    {
        name: "Stanford University",
        location: "California, USA",
        tuition: "₹50,00,000/year",
        housing: "₹20,00,000/year",
        eligibility: "TOEFL ≥ 100, SAT ≥ 1500",
        placement: "97%, Avg ₹50 LPA",
        scholarship: "Need-based, Athletic Scholarships",
        services: "Research Labs, Career Counseling",
        rules: "Honor Code, Campus Safety",
        rating: 5
    }

];

  function loadColleges() {
    const collegeUl = document.getElementById('college-ul');
    collegeUl.innerHTML = '';
    collegeData.forEach(college => {
      const li = document.createElement('li');
      li.textContent = college.name + ' - ' + college.location;
      li.onclick = () => showCollegeDetails(college);
      collegeUl.appendChild(li);
    });
  }
  loadColleges();

  function showCollegeDetails(college) {
    const detailsContent = document.getElementById('details-content');
    detailsContent.innerHTML = `
      <h3>${college.name}</h3>
      <p><strong>Location:</strong> ${college.location}</p>
      <p><strong>Tuition Fees:</strong> ${college.tuition}</p>
      <p><strong>Housing Costs:</strong> ${college.housing}</p>
      <p><strong>Eligibility Criteria:</strong> ${college.eligibility}</p>
      <p><strong>Placement Rate:</strong> ${college.placement}</p>
      <p><strong>Scholarships:</strong> ${college.scholarship}</p>
    `;
    showSection('college-details');
  }

  window.loginStudent = function() {
    alert('Login Successful!');
    showSection('career-selection');
  };

  window.handleSignUp = function() {
    alert('Sign Up Successful!');
    showSection('career-selection');
  };

  window.checkEligibility = function() {
    const cgpaInput = document.getElementById('cgpa').value;
    if (parseFloat(cgpaInput) >= 7.0) {
      document.getElementById('aptitude-section').style.display = 'block';
      alert('Eligible for Aptitude Test!');
    } else {
      alert('Not Eligible. Minimum CGPA is 7.0');
    }
  };

  window.gradeTest = function() {
    let score = 0;
    const q1 = document.querySelector('input[name="q1"]:checked');
    const q2 = document.querySelector('input[name="q2"]:checked');
    const q3 = document.querySelector('input[name="q3"]:checked');

    if (q1 && q1.value === 'Opaque') score += 1;
    if (q2 && q2.value === '100') score += 1;
    if (q3 && q3.value === 'Narendra Modi') score += 1;
  }

    const scoreResult = document.getElementById('score-result');
    scoreResult.textContent = 'Score: ' + score + '/3';

    const studentName = document.getElementById('name').value;
    const studentMobile = document.getElementById('mobile').value;
    const studentQualification = document.getElementById('qualification').value;
    const studentCgpa = document.getElementById('cgpa').value;

    document.getElementById('student-name').textContent = studentName;
    document.getElementById('student-mobile').textContent = studentMobile;
    document.getElementById('student-qualification').textContent = studentQualification;
    document.getElementById('student-cgpa').textContent = studentCgpa;
    document.getElementById('student-score').textContent = score + '/3';

    showSection('college-registration');
} 
);
  window.showSection = showSection;

  window.validateAdmin = function() {
    const adminId = document.getElementById('admin-id').value;
    const adminPass = document.getElementById('admin-pass').value;
    if (adminId === 'admin' && adminPass === 'password') {
      alert('Admin Login Successful!');
      showSection('college-list');
    } else {
      alert('Invalid Admin Credentials');
    }
  };
</script>
</body>
