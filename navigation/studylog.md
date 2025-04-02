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

<div class="container">
    <h1>Sales Analysis</h1>
    <div class="form-container">
        <h2>Add a Product</h2>
        <form id="productForm">
            <input type="text" id="productName" placeholder="Product Name" required />
            <input type="number" id="productValue" placeholder="Value" required />
            <button type="submit">Add Product</button>
        </form>
    </div>
    
    <div class="log-container">
        <h2>Product Logs</h2>
        <ul id="productList">
            <!-- Dynamic Product List Goes Here -->
        </ul>
    </div>
</div>

<script>
    let data = {
        labels: ["Product A", "Product B", "Product C", "Product D", "Product E"],
        datasets: {
            Revenue: [10000, 15000, 12000, 18000, 14000],
            "Units Sold": [500, 700, 600, 900, 750],
            Profit: [3000, 5000, 4000, 6000, 4500]
        }
    };

    // Update UI with current data
    function updateProductList() {
        let productList = document.getElementById("productList");
        productList.innerHTML = ''; // Clear existing list
        data.labels.forEach((product, index) => {
            let listItem = document.createElement("li");
            listItem.innerHTML = `
                <div><strong>${product}</strong></div>
                <div>Revenue: ${data.datasets.Revenue[index]}</div>
                <div>Units Sold: ${data.datasets["Units Sold"][index]}</div>
                <div>Profit: ${data.datasets.Profit[index]}</div>
            `;
            productList.appendChild(listItem);
        });
    }

    // Add product and update list
    document.getElementById("productForm").addEventListener("submit", function(e) {
        e.preventDefault();
        let name = document.getElementById("productName").value.trim();
        let value = parseFloat(document.getElementById("productValue").value);

        if (name === "" || isNaN(value) || value <= 0) {
            Swal.fire("Error", "Please enter a valid product name and value!", "error");
            return;
        }

        // Add new product to data
        data.labels.push(name);
        data.datasets.Revenue.push(value);  // Default revenue value, customize as needed
        data.datasets["Units Sold"].push(0); // Placeholder for unit sold
        data.datasets.Profit.push(0);  // Placeholder for profit

        updateProductList();
        document.getElementById("productName").value = "";
        document.getElementById("productValue").value = "";
    });

    // Initial product list rendering
    updateProductList();
</script>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sales Analysis Tool</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sweetalert2@11/dist/sweetalert2.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body { font-family: 'Inter', sans-serif; background: #1e3c72; color: white; padding: 20px; }
        .container { max-width: 900px; margin: auto; padding: 20px; background: rgba(255, 255, 255, 0.1); border-radius: 10px; }
        h1 { text-align: center; }
        .analytics { display: flex; justify-content: space-between; margin-bottom: 20px; }
        .analytics div { background: rgba(255, 255, 255, 0.2); padding: 10px; border-radius: 8px; }
        .chart-container { position: relative; height: 300px; }
        ul { list-style: none; padding: 0; }
        li { background: rgba(255, 255, 255, 0.15); padding: 10px; border-radius: 8px; margin: 5px 0; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Sales Analysis</h1>
        <div class="analytics">
            <div>Total Revenue: <span id="totalRevenue">$0</span></div>
            <div>Total Units Sold: <span id="totalUnits">0</span></div>
            <div>Avg. Profit: <span id="avgProfit">$0</span></div>
        </div>
        <div class="chart-container">
            <canvas id="salesChart"></canvas>
        </div>
        <h2>Product Logs</h2>
        <ul id="productList"></ul>
    </div>
    <script>
        async function fetchData() {
            let response = await fetch('/api/sales-data');
            let data = await response.json();
            updateUI(data);
        }
        function updateUI(data) {
            let productList = document.getElementById("productList");
            let totalRevenue = 0, totalUnits = 0, totalProfit = 0;
            productList.innerHTML = '';
            data.forEach(item => {
                totalRevenue += item.revenue;
                totalUnits += item.units;
                totalProfit += item.profit;
                let listItem = document.createElement("li");
                listItem.textContent = `${item.name} - Revenue: $${item.revenue}, Units: ${item.units}, Profit: $${item.profit}`;
                productList.appendChild(listItem);
            });            
            document.getElementById("totalRevenue").textContent = `$${totalRevenue}`;
            document.getElementById("totalUnits").textContent = totalUnits;
            document.getElementById("avgProfit").textContent = `$${(totalProfit / data.length).toFixed(2)}`;            
            updateChart(data);
        }
        function updateChart(data) {
            let ctx = document.getElementById("salesChart").getContext("2d");
            let labels = data.map(item => item.name);
            let revenues = data.map(item => item.revenue);
            let units = data.map(item => item.units);
            let profits = data.map(item => item.profit);            
            new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: labels,
                    datasets: [
                        { label: 'Revenue', data: revenues, backgroundColor: 'rgba(255, 99, 132, 0.5)' },
                        { label: 'Units Sold', data: units, backgroundColor: 'rgba(54, 162, 235, 0.5)' },
                        { label: 'Profit', data: profits, backgroundColor: 'rgba(75, 192, 192, 0.5)' }
                    ]
                },
                options: { responsive: true, scales: { y: { beginAtZero: true } } }
            });
        }
        fetchData();
    </script>

</body>
</html>
