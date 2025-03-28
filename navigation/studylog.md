---
layout: base
title: Sales Analysis
description: Sales Analysis Tool
permalink: naviagtion/log
---
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Sales Analysis Tool</title>
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css">
        <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
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
                border: 1px solid rgba(255, 255, 255, 0.18);
            }
            h1, h2 {
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
            /* Custom SweetAlert2 styling */
            .swal2-popup {
                background: rgba(255, 243, 224, 0.95) !important;
                border-radius: 15px !important;
            }
            .swal2-title {
                color: #ff7043 !important;
            }
            .swal2-html-container {
                color: #ff8a65 !important;
            }
            .swal2-confirm {
                background: #ff9966 !important;
                border-radius: 8px !important;
            }
            .swal2-cancel {
                background: #ffccbc !important;
                color: #ff7043 !important;
                border-radius: 8px !important;
            }
            .swal2-confirm:hover {
                background: #ff7043 !important;
            }
            .swal2-cancel:hover {
                background: #ffab91 !important;
            }
        </style>
    </head>



<!DOCTYPE html>
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
        .chart-container, .input-container, .analysis-container {
            background: rgba(255, 255, 255, 0.15);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            margin-top: 20px;
        }
        select, input, button {
            padding: 10px;
            border-radius: 8px;
            border: none;
            margin: 10px;
            cursor: pointer;
        }
        canvas {
            width: 100% !important;
            height: 400px !important;
        }
        button {
            background-color: #4CAF50;
            color: white;
            font-weight: bold;
        }
        button:hover {
            background-color: #43a047;
        }
        .analysis-container {
            font-size: 1.2rem;
            font-weight: bold;
            color: #ffce56;
        }
        .summary-container {
            background: rgba(255, 255, 255, 0.15);
            padding: 20px;
            border-radius: 15px;
            text-align: left;
            margin-top: 20px;
            color: #ffccbc;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Sales Analysis</h1>
    <!-- Product Input Section -->
    <div class="input-container">
        <h2>Add a Product</h2>
        <input type="text" id="productName" placeholder="Product Name">
        <input type="number" id="productValue" placeholder="Value">
        <button onclick="addProduct()">Add Product</button>
    </div>
    <!-- Graph Selection Controls -->
    <div class="chart-container">
        <label for="dataType">Choose Data:</label>
        <select id="dataType">
            <option value="Revenue">Revenue</option>
            <option value="Units Sold">Units Sold</option>
            <option value="Profit">Profit</option>
        </select>
        <label for="chartType">Choose Chart:</label>
        <select id="chartType">
            <option value="bar">Bar Chart</option>
            <option value="pie">Pie Chart</option>
            <option value="line">Line Graph</option>
            <option value="scatter">Scatter Plot</option>
        </select>
        <canvas id="salesChart"></canvas>
    </div>
    <!-- Sales Analysis -->
    <div class="analysis-container" id="analysisBox">
        <p>Most Successful Product: <span id="topProduct">N/A</span></p>
    </div>
    <!-- Summary of Analysis -->
    <div class="summary-container">
        <h3>Analysis Summary</h3>
        <p id="summaryText">Data will be analyzed here...</p>
    </div>
</div>

<script>
    // Default Sample Data
    let data = {
        labels: ["Product A", "Product B", "Product C", "Product D", "Product E"],
        datasets: {
            Revenue: [10000, 15000, 12000, 18000, 14000],
            "Units Sold": [500, 700, 600, 900, 750],
            Profit: [3000, 5000, 4000, 6000, 4500]
        }
    };

    let selectedData = "Revenue";
    let chartType = "bar";

    let ctx = document.getElementById("salesChart").getContext("2d");
    let salesChart = new Chart(ctx, {
        type: chartType,
        data: {
            labels: data.labels,
            datasets: [{
                label: selectedData,
                data: data.datasets[selectedData],
                backgroundColor: ["#ff6384", "#36a2eb", "#ffce56", "#4bc0c0", "#9966ff"],
                borderColor: "#ffffff",
                borderWidth: 1
            }]
        }
    });

    // Function to Update Chart
    function updateChart() {
        selectedData = document.getElementById("dataType").value;
        chartType = document.getElementById("chartType").value;

        salesChart.destroy();
        salesChart = new Chart(ctx, {
            type: chartType,
            data: {
                labels: data.labels,
                datasets: [{
                    label: selectedData,
                    data: data.datasets[selectedData],
                    backgroundColor: ["#ff6384", "#36a2eb", "#ffce56", "#4bc0c0", "#9966ff"],
                    borderColor: "#ffffff",
                    borderWidth: 1
                }]
            }
        });

        updateAnalysis();
    }

    // Function to Add a New Product
    function addProduct() {
        let name = document.getElementById("productName").value.trim();
        let value = parseFloat(document.getElementById("productValue").value);

        if (name === "" || isNaN(value) || value <= 0) {
            Swal.fire("Error", "Please enter a valid product name and value!", "error");
            return;
        }

        if (data.labels.includes(name)) {
            Swal.fire("Error", "Product already exists!", "warning");
            return;
        }

        data.labels.push(name);
        data.datasets[selectedData].push(value);

        updateChart();
        document.getElementById("productName").value = "";
        document.getElementById("productValue").value = "";
    }

    // Function to Update Analysis
    function updateAnalysis() {
        let values = data.datasets[selectedData];
        let maxIndex = values.indexOf(Math.max(...values));
        let minIndex = values.indexOf(Math.min(...values));
        let topProduct = data.labels[maxIndex];
        let lowestProduct = data.labels[minIndex];

        document.getElementById("topProduct").textContent = topProduct;

        let trend = values[maxIndex] > values[minIndex] * 2 ? "a strong growth trend" : "a balanced trend";

        let summaryText = `The most successful product is **${topProduct}**, leading in **${selectedData}**. 
            The product **${lowestProduct}** has the lowest performance. 
            Overall, the sales data suggests ${trend}, indicating areas for potential improvement or investment.`;

        document.getElementById("summaryText").innerHTML = summaryText;
    }

    document.getElementById("dataType").addEventListener("change", updateChart);
    document.getElementById("chartType").addEventListener("change", updateChart);
</script>

</body>
</html>


