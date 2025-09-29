<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Aakash Fertility Centre - Smart Health Consulting</title>
<style>
body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin:0; padding:0; background-color:#f4f8ff; }
header { background-color:#005f99; color:white; padding:15px 0; text-align:center; position:sticky; top:0; z-index:1000; }
nav { background-color:#007acc; display:flex; justify-content:center; padding:10px; }
nav button { background-color:white; color:#007acc; border:none; padding:10px 20px; margin:0 10px; font-weight:bold; cursor:pointer; border-radius:5px; }
h1 { font-size:36px; text-align:center; margin-top:30px; color:#003366; }
.description { text-align:center; max-width:900px; margin:20px auto; font-size:18px; line-height:1.8; color:#333; padding:0 15px; }
.description img { margin-top:20px; max-width:100%; height:auto; border-radius:10px; box-shadow:0 0 10px #ccc; }
.section { display:none; background:#fff; margin:20px auto; padding:25px; border-radius:10px; box-shadow:0 0 10px #ccc; max-width:500px; }
label { display:block; margin-top:15px; }
input, textarea, select, button { width:100%; padding:10px; margin-top:5px; border-radius:8px; border:1px solid #ccc; font-size:16px; }
button[type="submit"], button.lookup { background-color:#005f99; color:white; font-weight:bold; margin-top:20px; }
#diseaseDescription { margin-top:20px; padding:15px; background:white; border-radius:8px; box-shadow:0 0 10px #ccc; }
</style>
</head>
<body>

<header>
<h1>Smart Health Consulting & Appointment System</h1>
</header>

<nav>
<button onclick="showSection('home')">Home</button>
<button onclick="showSection('login')">Login</button>
<button onclick="showSection('register')">Register</button>
<button onclick="showSection('book')">Book Appointment</button>
<button onclick="showSection('disease')">Disease Lookup</button>
</nav>

<div class="description" id="home" style="display:block;">
<p>
The Aakash Fertility Centre in Chennai empowers individuals to realize their dream of parenthood through cutting-edge research techniques and specialized expertise. Recognized as one of the best IVF hospitals in Chennai, Aakash Fertility Centre provides compassionate care, advanced fertility treatments, and personalized support at every stage of your parenthood journey.
</p>
<p>
Our team of experienced fertility specialists, embryologists, and nurses is dedicated to helping couples achieve their dreams of parenthood. We employ cutting-edge technologies to provide world-class treatments with a remarkable success rate. Since our inception, we've offered hope to numerous couples struggling with infertility.
</p>
<img src="https://www.careerstaff.com/wp-content/uploads/2023/07/hospital-setting-nurse-career.png" alt="Hospital Image">
</div>

<div class="section" id="login">
<h2>Login</h2>
<form>
<label for="loginUser">Username:</label>
<input type="text" id="loginUser" placeholder="Enter your username" required>

<label for="loginPass">Password:</label>
<input type="password" id="loginPass" placeholder="Enter your password" required>

<button type="submit">Login</button>
</form>
</div>

<div class="section" id="register">
<h2>Register</h2>
<form>
<label for="regName">Patient Name:</label>
<input type="text" id="regName" placeholder="Enter your full name" required>

<label for="regPass">Password:</label>
<input type="password" id="regPass" placeholder="Create a password" required>

<button type="submit">Register</button>
</form>
</div>

<div class="section" id="book">
<h2>Book Appointment</h2>
<form>
<label for="patientName">Patient Name:</label>
<input type="text" id="patientName" required>

<label for="doctorName">Doctor Name:</label>
<input type="text" id="doctorName" required>

<label for="timing">Preferred Timing:</label>
<input type="datetime-local" id="timing" required>

<label for="payment">Payment (₹):</label>
<input type="number" id="payment" value="500" readonly>

<label for="summary">Problem Summary (max 500 characters):</label>
<textarea id="summary" maxlength="500" rows="5" placeholder="Describe your health problem..."></textarea>

<button type="submit">Confirm Booking</button>
</form>
</div>

<div class="section" id="disease">
<h2>Disease Lookup by Symptom</h2>
<label for="symptomInput">Enter Symptom:</label>
<input type="text" id="symptomInput" placeholder="e.g., Fever, Cough">
<button class="lookup" onclick="findDisease()">Find Disease</button>
<div id="diseaseDescription">Disease description will appear here...</div>
</div>

<script>
function showSection(id) {
    const sections = document.querySelectorAll('.section, .description');
    sections.forEach(sec => sec.style.display = 'none');
    document.getElementById(id).style.display = 'block';
}

// =======================
// Dataset in JavaScript
// =======================
const diseases = [
    {
        name: "Flu",
        symptoms: ["Fever", "Cough", "Sore throat", "Body ache"],
        description: "A contagious respiratory illness caused by influenza viruses."
    },
    {
        name: "Diabetes",
        symptoms: ["Frequent urination", "Increased thirst", "Fatigue"],
        description: "A chronic condition that affects how the body processes blood sugar."
    },
    {
        name: "Asthma",
        symptoms: ["Shortness of breath", "Wheezing", "Coughing"],
        description: "A condition in which airways narrow and swell, producing extra mucus."
    },
    {
        name: "Hypertension",
        symptoms: ["Headache", "Dizziness", "Blurred vision"],
        description: "A condition where the blood pressure in arteries is persistently high."
    }
];

function findDisease() {
    const symptom = document.getElementById('symptomInput').value.toLowerCase();
    const descDiv = document.getElementById('diseaseDescription');

    if (!symptom) {
        descDiv.textContent = "Please enter a symptom.";
        return;
    }

    const found = diseases.find(d =>
        d.symptoms.some(s => s.toLowerCase().includes(symptom))
    );

    if (found) {
        descDiv.innerHTML = `<strong>Disease:</strong> ${found.name}<br>
                             <strong>Description:</strong> ${found.description}`;
    } else {
        descDiv.textContent = "No disease found matching this symptom.";
    }
}
</script>

</body>
</html>yar
