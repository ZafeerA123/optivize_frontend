---
layout: page 
title: Login
permalink: /login
search_exclude: true
show_reading_time: false 
---

<style>
/* General Page Styling */
body {
    font-family: Arial, sans-serif;
    background-color: #f9f9f9;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding-top: 40px; /* Ensures space from the top */
}

/* Main Container */
.main-container {
    width: 90%;
    max-width: 1400px; /* Increased max-width for a more horizontal container */
    background: #fff;
    padding: 40px;
    border-radius: 12px;
    box-shadow: 4px 6px 12px rgba(0, 0, 0, 0.2);
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    margin-top: 40px; /* Creates better spacing */
}

/* Enlarged Login & Signup Cards */
.login-card, .signup-card {
    width: 48%;
    padding: 40px; /* Increased padding for more space inside */
    border: 1px solid #ddd;
    border-radius: 12px;
    box-shadow: 6px 8px 14px rgba(0, 0, 0, 0.2);
    background-color: #fff;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
}

/* Headings */
h1 {
    font-size: 28px;
    color: #333;
    text-align: center;
    margin-bottom: 20px;
}

/* Buttons */
button {
    width: 100%;
    padding: 18px; /* Increased padding for wider buttons */
    background: linear-gradient(to right, #007bff, #0056b3);
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 20px;
    cursor: pointer;
    transition: 0.3s ease-in-out;
    font-weight: bold;
    box-shadow: 3px 5px 8px rgba(0, 0, 0, 0.2);
}

button:hover {
    background: linear-gradient(to right, #0056b3, #003d80);
    transform: scale(1.07);
}

/* Input Fields */
form {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
}

input {
    width: 100%;
    padding: 14px;
    margin: 12px 0;
    border: 1px solid #ccc;
    border-radius: 6px;
    font-size: 18px;
}

/* Messages */
#message, #signupMessage {
    text-align: center;
    font-size: 16px;
    margin-top: 10px;
}

#message {
    color: red;
}

#signupMessage {
    color: green;
}

/* Responsive Design */
@media (max-width: 768px) {
    .main-container {
        flex-direction: column;
        align-items: center;
    }
    .login-card, .signup-card {
        width: 100%;
    }
}
</style>

<!-- Main Container for Login & Signup -->
<div class="main-container">
    <div class="login-card">
        <h1>Login</h1>
        <form id="pythonForm" onsubmit="pythonLogin(); return false;">
            <label>GitHub ID:</label>
            <input type="text" name="uid" id="uid" required>

            <label>Password:</label>
            <input type="password" name="password" id="password" required>

            <button type="submit">Login</button>
            <p id="message"></p>
        </form>
    </div>

    <div class="signup-card">
        <h1>Sign Up</h1>
        <form id="signupForm" onsubmit="signup(); return false;">
            <label>Name:</label>
            <input type="text" name="name" id="name" required>

            <label>GitHub ID:</label>
            <input type="text" name="signupUid" id="signupUid" required>

            <label>Password:</label>
            <input type="password" name="signupPassword" id="signupPassword" required>

            <button type="submit">Sign Up</button>
            <p id="signupMessage"></p>
        </form>
    </div>
</div>

<script type="module">
    import { login, pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

    // Function to handle Python login
    window.pythonLogin = function() {
        const options = {
            URL: `${pythonURI}/api/authenticate`,
            callback: pythonDatabase,
            message: "message",
            method: "POST",
            cache: "no-cache",
            body: {
                uid: document.getElementById("uid").value,
                password: document.getElementById("password").value,
            }
        };
        login(options);
    }

    // Function to handle signup
    window.signup = function() {
        const signupButton = document.querySelector(".signup-card button");
        signupButton.disabled = true;
        signupButton.style.backgroundColor = '#d3d3d3';

        const signupOptions = {
            URL: `${pythonURI}/api/user`,
            method: "POST",
            cache: "no-cache",
            body: {
                name: document.getElementById("name").value,
                uid: document.getElementById("signupUid").value,
                password: document.getElementById("signupPassword").value,
            }
        };

        fetch(signupOptions.URL, {
            method: signupOptions.method,
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(signupOptions.body)
        })
        .then(response => {
            if (!response.ok) {
                throw new Error(`Signup failed: ${response.status}`);
            }
            return response.json();
        })
        .then(data => {
            document.getElementById("signupMessage").textContent = "Signup successful!";
        })
        .catch(error => {
            console.error("Signup Error:", error);
            document.getElementById("signupMessage").textContent = `Signup Error: ${error.message}`;
            signupButton.disabled = false;
            signupButton.style.backgroundColor = '';
        });
    }

    function pythonDatabase() {
        const URL = `${pythonURI}/api/id`;

        fetch(URL, fetchOptions)
            .then(response => {
                if (!response.ok) {
                    throw new Error(`Flask server response: ${response.status}`);
                }
                return response.json();
            })
            .then(data => {
                window.location.href = '{{site.baseurl}}/profile';
            })
            .catch(error => {
                console.error("Python Database Error:", error);
            });
    }

    window.onload = function() {
        pythonDatabase();
    };
</script>
