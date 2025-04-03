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
    <form id="predictionForm">
        <label>Cookie Flavor:</label>
        <input type="text" id="cookieFlavor" required>
        <label>Price ($):</label>
        <input type="number" id="price" step="0.01" required>
        <label>Marketing Spend ($):</label>
        <input type="number" id="marketing" required>
        <button type="submit">📊 Predict Success</button>
    </form>
    <div class="loading" id="loading" style="display: none;">🔄 Predicting...</div>
    <h3>Success Probability</h3>
    <p id="predictionResult">Enter details to see prediction</p>
    <h3>Projected Profit Over Time</h3>
    <canvas id="salesChart"></canvas>
    <h3>Marketing Strategy</h3>
    <p id="marketingAdvice">Enter data to receive insights...</p>
</div>

<script>
    const API_URL = "https://optivize.stu.nighthawkcodingsociety.com/api/predict";

    document.getElementById("predictionForm").addEventListener("submit", async function (e) {
        e.preventDefault();

        let flavor = document.getElementById("cookieFlavor").value.trim();
        let price = parseFloat(document.getElementById("price").value);
        let marketing = parseFloat(document.getElementById("marketing").value);
        let loading = document.getElementById("loading");

        if (!flavor || isNaN(price) || isNaN(marketing)) {
            Swal.fire("Error", "Please fill all fields correctly!", "error");
            return;
        }

        loading.style.display = "block";

        const payload = {
            cookie_flavor: flavor,
            price: price,
            marketing: marketing  // Corrected here, removed extra 'price'
        };

        try {
            let response = await fetch(API_URL, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(payload)
            });

            let result = await response.json();
            if (!response.ok) throw new Error(result.message || "Prediction failed.");

            Swal.fire("Success", "Prediction generated!", "success");

            // Display the prediction result
            document.getElementById("predictionResult").textContent = `📊 Success Probability: ${result.success_probability}%`;

            // Update the profit chart
            updateChart([50, 60, 80, 100, 150, 200, 300]);  // Example profit trend
            document.getElementById("marketingAdvice").textContent = generateMarketingAdvice(result.success_probability);

        } catch (error) {
            Swal.fire("Error", error.message, "error");
        } finally {
            loading.style.display = "none";
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
                    backgroundColor: "rgba(75, 192, 192, 0.2)",
                    borderColor: "rgba(75, 192, 192, 1)",
                    borderWidth: 2
                }]
            }
        });
    }

    function generateMarketingAdvice(successRate) {
        if (successRate > 80) return "🚀 Your product is highly likely to succeed! Consider investing more in marketing.";
        if (successRate > 50) return "📈 Good potential! Try seasonal promotions or bundling.";
        return "⚠️ Low success chance. Consider adjusting pricing or marketing approach.";
    }
</script>

<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
        background-color: #f4f4f4;
        padding: 20px;
    }
    .container {
        background: white;
        padding: 20px;
        border-radius: 10px;
        max-width: 500px;
        margin: auto;
        box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
    }
    input, button {
        width: 100%;
        padding: 10px;
        margin: 5px 0;
        font-size: 16px;
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
    canvas {
        margin-top: 20px;
        max-width: 100%;
    }
</style>
