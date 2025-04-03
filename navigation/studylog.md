---
layout: base
title: Sales Analysis
description: Sales Analysis Tool
permalink: navigation/log
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sales Analysis Tool</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body {
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 20px;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: #ffffff;
            min-height: 100vh;
        }
        .container {
            max-width: 900px;
            margin: 20px auto;
            padding: 30px;
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
        }
        h1 {
            text-align: center;
            color: #ffffff;
            margin-bottom: 30px;
            font-weight: 600;
        }
        .log-container ul {
            list-style-type: none;
            padding: 0;
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
        }
        .log-container li {
            background: rgba(255, 255, 255, 0.15);
            padding: 20px;
            border-radius: 15px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .log-container li:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }
        .log-container li div {
            margin-bottom: 12px;
            font-size: 0.95rem;
        }
        .log-container li strong {
            color: #ff7043;
            font-weight: 500;
        }
        .button-group {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        .edit-btn, .delete-btn, .save-btn {
            background: none;
            border: none;
            padding: 8px;
            cursor: pointer;
            border-radius: 50%;
            transition: all 0.3s ease;
            width: 35px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .edit-btn {
            background-color: rgba(76, 175, 80, 0.2);
            color: #4CAF50;
        }
        .delete-btn {
            background-color: rgba(244, 67, 54, 0.2);
            color: #f44336;
        }
        .save-btn {
            background-color: rgba(33, 150, 243, 0.2);
            color: #2196F3;
        }
        .edit-btn:hover, .delete-btn:hover, .save-btn:hover {
            transform: translateY(-2px);
        }
        .fa-pencil-alt, .fa-trash-alt {
            font-size: 1rem;
        }
        .form-container {
            background: rgba(255, 255, 255, 0.15);
            padding: 30px;
            border-radius: 15px;
            margin-top: 30px;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        .form-container form {
            display: grid;
            gap: 15px;
        }
        .form-container label {
            font-size: 0.9rem;
            color: #a8d0ff;
            margin-bottom: 5px;
        }
        .form-container input, 
        .form-container textarea {
            width: 100%;
            padding: 12px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
            transition: all 0.3s ease;
        }
        .form-container input:focus, 
        .form-container textarea:focus {
            outline: none;
            border-color: #4CAF50;
            background: rgba(255, 255, 255, 0.15);
        }
        .form-container button {
            background-color: #4CAF50;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 1px;
            transition: all 0.3s ease;
        }
        .form-container button:hover {
            background-color: #43a047;
            transform: translateY(-2px);
        }
        .error {
            color: #ff4757;
            font-size: 0.9rem;
            margin-top: 5px;
        }
        @media (max-width: 768px) {
            .container {
                padding: 20px;
                margin: 10px;
            }
            .log-container ul {
                grid-template-columns: 1fr;
            }
        }
        .edit-input {
            width: 100%;
            padding: 8px;
            margin: 4px 0;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
        }
        .edit-input:focus {
            outline: none;
            border-color: #4CAF50;
            background: rgba(255, 255, 255, 0.15);
        }
        textarea.edit-input {
            min-height: 60px;
            resize: vertical;
        }
        .save-btn {
            background-color: #4CAF50;
            color: white;
            padding: 8px 15px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 500;
            text-transform: uppercase;
            font-size: 0.8rem;
            letter-spacing: 0.5px;
            transition: all 0.3s ease;
        }
        .save-btn:hover {
            background-color: #43a047;
            transform: translateY(-2px);
        }
    </style>
</head>
<body>

<h2 style="text-align: center; color: #333;">🍪 Predict Cookie Success</h2>

<div class="container">
    <form id="productForm">
        <label>Cookie Flavor: <input type="text" id="cookieFlavor" required></label>
        <label>Price ($): <input type="number" id="price" step="0.01" required></label>
        <label>Marketing Spend ($): <input type="number" id="marketing" required></label>
        <button type="submit">📊 Predict Success</button>
    </form>

    <div class="loading" id="loading">🔄 Predicting...</div>

    <h3>Projected Profit Over Time</h3>
    <canvas id="salesChart"></canvas>

    <h3>Marketing Advice</h3>
    <p id="marketingAdvice">Enter data to receive insights...</p>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>

<style>
    .container {
        max-width: 500px;
        margin: auto;
        text-align: center;
        font-family: Arial, sans-serif;
    }
    form {
        display: flex;
        flex-direction: column;
        gap: 10px;
        margin-bottom: 20px;
    }
    input, button {
        padding: 10px;
        font-size: 16px;
        width: 100%;
    }
    button {
        background-color: #28a745;
        color: white;
        border: none;
        cursor: pointer;
    }
    button:hover {
        background-color: #218838;
    }
    .loading {
        display: none;
        font-size: 16px;
        margin-top: 10px;
    }
</style>

<script>
    const pythonURI = "https://optivize.stu.nighthawkcodingsociety.com";

    document.getElementById("productForm").addEventListener("submit", async function (e) {
        e.preventDefault();

        let cookieFlavor = document.getElementById("cookieFlavor").value.trim();
        let price = parseFloat(document.getElementById("price").value);
        let marketing = parseFloat(document.getElementById("marketing").value);
        let loading = document.getElementById("loading");

        // Basic Validation
        if (!cookieFlavor || isNaN(price) || isNaN(marketing)) {
            Swal.fire("Error", "Please fill all fields correctly!", "error");
            return;
        }

        loading.style.display = "block";  // Show loading indicator

        // Log the payload for debugging
        const payload = {
            cookie_flavor: cookieFlavor,
            price: price,
            marketing: marketing
        };
        console.log("Sending payload:", payload);

        try {
            let response = await fetchWithTimeout(`${pythonURI}/api/predict`, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(payload)
            });

            // Check if response is OK
            if (!response.ok) {
                const result = await response.json();
                throw new Error(result.message || `Error ${response.status}: Bad Request`);
            }

            let result = await response.json();
            console.log("Prediction result:", result);
            Swal.fire("Success", "Prediction generated!", "success");

            // Update UI
            updateChart(result.profit_over_time);
            document.getElementById("marketingAdvice").textContent = generateMarketingAdvice(result);

        } catch (error) {
            console.error("Error:", error);
            Swal.fire("Error", error.message, "error");
        } finally {
            loading.style.display = "none";  // Hide loading indicator
        }
    });

    function updateChart(profitData) {
        let ctx = document.getElementById("salesChart").getContext("2d");
        let labels = profitData.map((_, index) => `Month ${index + 1}`);

        new Chart(ctx, {
            type: "line",
            data: {
                labels: labels,
                datasets: [{
                    label: "Projected Profit ($)",
                    data: profitData,
                    backgroundColor: "rgba(75, 192, 192, 0.5)",
                    borderColor: "rgba(75, 192, 192, 1)",
                    fill: true
                }]
            },
            options: { responsive: true, scales: { y: { beginAtZero: true } } }
        });
    }

    function generateMarketingAdvice(result) {
        let successProbability = result.success_probability;
        let marketingSpend = result.recommended_marketing_spend;

        if (successProbability > 80) {
            return `🎉 Your cookie has a high chance of success! Maintain a marketing spend of $${marketingSpend} and focus on social media engagement.`;
        } else if (successProbability > 50) {
            return `📈 Moderate success expected. Consider increasing marketing by 20% and testing promotions.`;
        } else {
            return `⚠️ Low success probability. Improve recipe quality, reduce price slightly, and invest in influencer marketing.`;
        }
    }

    async function fetchWithTimeout(url, options, timeout = 5000) {
        const controller = new AbortController();
        const timeoutId = setTimeout(() => controller.abort(), timeout);
        try {
            return await fetch(url, { ...options, signal: controller.signal });
        } finally {
            clearTimeout(timeoutId);
        }
    }
</script>

