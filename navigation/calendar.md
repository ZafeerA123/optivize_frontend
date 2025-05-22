---
layout: base
title: Optivize Calendar 
description: Product Success Prediction
hide: true
permalink: /Calendar 
---


<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Crumble Cookies Operations Dashboard</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.css" rel="stylesheet">
  <style>
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #1a2980, #26d0ce);
      color: #fbb034;
      margin: 0;
      padding: 20px;
      min-height: 100vh;
    }
  /* Base styles with dark blue theme */
  body {
    margin: 0;
    padding: 0;
    font-family: 'Inter', sans-serif;
    color: #fff;
  }
  /* Gradient background with animation */
  .page-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #0b1e3b, #162b4d);
    z-index: -2;
  }
  /* Gradient overlay animation */
  .gradient-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at 70% 20%, rgba(43, 83, 158, 0.2), transparent 60%),
                radial-gradient(circle at 20% 80%, rgba(29, 47, 94, 0.3), transparent 60%);
    animation: gradientMove 20s infinite alternate;
    z-index: -1;
  }
  @keyframes gradientMove {
    0% { background-position: 0% 0%; }
    100% { background-position: 100% 100%; }
  }
  .hero-container {
    position: relative;
    padding: 40px 20px;
    overflow: hidden;
  }
  /* Glowing orbs in background */
  .glow-orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(60px);
    opacity: 0.15;
    z-index: 0;
  }
  .glow-orb-1 {
    top: 10%;
    left: 5%;
    width: 300px;
    height: 300px;
    background: radial-gradient(circle, rgba(251, 176, 52, 0.6), rgba(251, 176, 52, 0) 70%);
    animation: float 25s infinite alternate;
  }
  .glow-orb-2 {
    bottom: 10%;
    right: 5%;
    width: 400px;
    height: 400px;
    background: radial-gradient(circle, rgba(66, 99, 176, 0.4), rgba(66, 99, 176, 0) 70%);
    animation: float 30s infinite alternate-reverse;
  }
  .glow-orb-3 {
    top: 50%;
    left: 50%;
    width: 350px;
    height: 350px;
    background: radial-gradient(circle, rgba(251, 176, 52, 0.3), rgba(66, 99, 176, 0.2), rgba(66, 99, 176, 0) 70%);
    animation: float 35s infinite alternate;
  }
  @keyframes float {
    0% { transform: translate(0, 0) scale(1); }
    50% { transform: translate(50px, -30px) scale(1.1); }
    100% { transform: translate(-30px, 50px) scale(0.9); }
  }
  /* Hero section */
  .hero-section {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 40px;
    position: relative;
    z-index: 1;
  }
  .hero-content {
    flex: 1;
    min-width: 300px;
  }
  .hero-title {
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 20px;
    background: linear-gradient(to right, #fbb034, #ffdd00, #fbb034);
    background-size: 200% auto;
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    animation: shine 3s linear infinite;
  }
    .container {
      max-width: 1200px;
      margin: 0 auto;
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      border-radius: 8px;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
      padding: 30px;
      min-height: calc(100vh - 40px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    /* Improved Tab Styling */
    .nav-tabs {
      border-bottom: none;
      gap: 8px;
    }
    .nav-tabs .nav-link {
      border: none;
      border-radius: 8px;
      background: rgba(255, 255, 255, 0.1);
      color: rgba(255, 255, 255, 0.8);
      transition: all 0.3s ease;
      padding: 12px 24px;
    }
    .nav-tabs .nav-link:hover,
    .nav-tabs .nav-link.active {
      background: rgba(255, 255, 255, 0.2);
      color: #fbb034;
      transform: translateY(-2px);
    }
    /* Updated Button Styling */
    .btn-primary {
      background: linear-gradient(135deg, #ffdd00, #fbb034);
      border: none;
      color: #333;
      transition: all 0.3s ease;
    }
    .btn-primary:hover {
      background: linear-gradient(135deg, #fbb034, #ffdd00);
      color: #000;
      transform: translateY(-2px);
    }
    /* Updated Title Styling */
    h1 {
      background: linear-gradient(135deg, #ffdd00, #fbb034);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    /* Updated Tab Styling */
    .nav-tabs .nav-link:hover,
    .nav-tabs .nav-link.active {
      background: linear-gradient(135deg, rgba(255, 221, 0, 0.2), rgba(251, 176, 52, 0.2));
      color: #ffdd00;
    }
    /* Updated Calendar Button Styling */
    .fc-button {
      background: linear-gradient(135deg, rgba(255, 221, 0, 0.2), rgba(251, 176, 52, 0.2)) !important;
      color: #fbb034 !important;
      border: 1px solid rgba(251, 176, 52, 0.3) !important;
    }
    .fc-button:hover {
      background: linear-gradient(135deg, rgba(255, 221, 0, 0.3), rgba(251, 176, 52, 0.3)) !important;
    }
    /* Updated Event Color */
    .fc-event {
      background: linear-gradient(135deg, #ffdd00, #fbb034) !important;
      border: none !important;
      color: #333 !important;
    }
    /* Calendar Styling */
    #calendar {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 12px;
      padding: 20px;
      border: 1px solid rgba(255, 255, 255, 0.1);
    }
    .fc-toolbar {
      color: white !important;
      padding: 15px 0;
    }
    .fc-toolbar-title {
      color: white !important;
      font-size: 1.4rem !important;
    }
    .fc-button {
      background: rgba(255, 255, 255, 0.1) !important;
      border: 1px solid rgba(255, 255, 255, 0.2) !important;
      color: white !important;
      transition: all 0.3s ease;
    }
    .fc-button:hover {
      background: rgba(255, 255, 255, 0.2) !important;
    }
    .dashboard-box {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 12px;
      padding: 20px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      color: white;
    }
    .form-control {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(255, 255, 255, 0.1);
      color: white;
    }
    .form-control::placeholder {
      color: rgba(255, 255, 255, 0.6) !important;
    }
    .btn-primary {
      background: #4a90e2;
      border: none;
      transition: all 0.3s ease;
    }
    .btn-primary:hover {
      background: #357abd;
      transform: translateY(-2px);
    }
    .list-item {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 8px;
      padding: 15px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1 class="text-center mb-4">Operations Dashboard</h1>   
    <div id="notifications" class="alert alert-warning mb-4" style="display: none;"></div>
    <ul class="nav nav-tabs mb-4" id="tabMenu" role="tablist">
      <li class="nav-item" role="presentation">
        <button class="nav-link active" data-bs-toggle="tab" data-bs-target="#calendarSection">📅 Calendar</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" data-bs-toggle="tab" data-bs-target="#inventorySection">📦 Inventory</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" data-bs-toggle="tab" data-bs-target="#shipmentsSection">🚚 Shipments</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" data-bs-toggle="tab" data-bs-target="#eventsSection">🎉 Events</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" data-bs-toggle="tab" data-bs-target="#tasksSection">✅ Tasks</button>
      </li>
    </ul>
    <div class="tab-content">
      <!-- Calendar Tab -->
      <div class="tab-pane fade show active" id="calendarSection">
        <div id="calendar"></div>
      </div>
      <!-- Inventory Tab -->
      <div class="tab-pane fade" id="inventorySection">
        <div class="dashboard-box">
          <h4 class="mb-4">📦 Current Inventory</h4>
          <div id="inventoryList" class="mb-4"></div>
          <form id="inventoryForm">
            <div class="row g-3">
              <div class="col-md-6">
                <input type="text" class="form-control" placeholder="Item name" required>
              </div>
              <div class="col-md-4">
                <input type="number" class="form-control" placeholder="Quantity" required>
              </div>
              <div class="col-md-2">
                <button type="submit" class="btn btn-primary w-100">Update</button>
              </div>
            </div>
          </form>
        </div>
      </div>
      <!-- Shipments Tab -->
      <div class="tab-pane fade" id="shipmentsSection">
        <div class="dashboard-box">
          <h4 class="mb-4">🚚 Shipment Schedule</h4>
          <form id="shipmentForm" class="mb-4">
            <div class="row g-3">
              <div class="col-md-5">
                <input type="text" class="form-control" placeholder="Item name" required>
              </div>
              <div class="col-md-5">
                <input type="date" class="form-control" required>
              </div>
              <div class="col-md-2">
                <button type="submit" class="btn btn-primary w-100">Add</button>
              </div>
            </div>
          </form>
          <div id="shipmentList"></div>
        </div>
      </div>
      <!-- Events Tab -->
      <div class="tab-pane fade" id="eventsSection">
        <div class="dashboard-box">
            <h4 class="mb-4">🎉 Manage Events</h4>
            <form id="eventForm" class="mb-4">
  <div class="mb-3">
    <small style="color: white;">Title</small>
    <input type="text" class="form-control" name="title" placeholder="Event title" required>
  </div>

  <div class="mb-3">
    <small style="color: white;">Description</small>
    <input type="text" class="form-control" name="description" placeholder="Event description">
  </div>

  <div class="mb-3">
    <small style="color: white;">Start Date & Time</small>
    <input type="datetime-local" class="form-control" name="start_time" required>
  </div>

  <div class="mb-3">
    <small style="color: white;">End Date & Time</small>
    <input type="datetime-local" class="form-control" name="end_time" required>
  </div>

  <div class="mb-3">
    <small style="color: white;">Category (emoji + name)</small>
    <select class="form-select" name="category" required>
      <option value="" disabled selected>Select a category</option>
      <option value="general">🎯 General</option>
      <option value="delivery">🚚 Delivery</option>
      <option value="marketing">📣 Marketing</option>
      <option value="maintenance">🛠️ Maintenance</option>
      <option value="custom">🌀 Custom</option>
    </select>
  </div>

  <div class="mb-3">
    <button type="submit" class="btn btn-primary">Add Event</button>
  </div>
</form>
            <div id="eventList"></div>
        </div>
      </div>
      <!-- Tasks Tab -->
      <div class="tab-pane fade" id="tasksSection">
        <div class="dashboard-box">
          <h4 class="mb-4">✅ Employee Management</h4>
          <form id="taskForm" class="mb-4">
            <div class="row g-3">
              <div class="col-md-4">
                <input type="text" class="form-control" placeholder="Employee name" required>
              </div>
              <div class="col-md-4">
                <input type="text" class="form-control" placeholder="Task description" required>
              </div>
              <div class="col-md-3">
                <input type="date" class="form-control" required>
              </div>
              <div class="col-md-1">
                <button type="submit" class="btn btn-primary w-100">➕</button>
              </div>
            </div>
          </form>
          <div id="taskList"></div>
        </div>
      </div>
    </div>
  </div>
</head>
<div class="container">
  <h1>Calendar</h1>
  <div id="calendar"></div>
</div>

<!-- Scripts -->
<!-- Bootstrap CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- Bootstrap JS + Popper.js -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.js"></script>
<script>
  document.addEventListener('DOMContentLoaded', function () {
    var calendarEl = document.getElementById('calendar');
    var calendar = new FullCalendar.Calendar(calendarEl, {
      initialView: 'dayGridMonth',
      events: [
        {
          title: 'Launch Date',
          start: '2025-05-21'
        }
      ]
    });
    calendar.render();
  });
</script>

<h1>Calendar and Management</h1>

<!-- Employee Table -->
<h2>Employee Table</h2>
<table id="employeeTable" border="1">
  <thead>
    <tr>
      <th>Name</th>
      <th>Position</th>
      <th>Work Time</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<!-- Shipment Table -->
<h2>Shipment Table</h2>
<table id="shipmentTable" border="1">
  <thead>
    <tr>
      <th>Inventory</th>
      <th>Amount</th>
      <th>Transport Method</th>
      <th>Shipment Time</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<script>
  const pythonURI = 'https://optivize.stu.nighthawkcodingsociety.com'; // Replace with your backend
  const fetchOptions = { credentials: 'include' };

  // --- EVENTS ---
  async function getEvents() {
    const res = await fetch(`${pythonURI}/api/calendarv3/events`, fetchOptions);
    return await res.json();
  }
  async function postEvent({ title, description, start_time, end_time, category }) {
    await fetch(`${pythonURI}/api/calendarv3/events`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ title, description, start_time, end_time, category })
    });
  }
  async function getEvents() {
  try {
    const response = await fetch('https://optivize.stu.nighthawkcodingsociety.com/api/calendarv3/events', {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json'
      }
    });

    if (!response.ok) throw new Error('Failed to fetch events');

    const events = await response.json();
    displayEvents(events);
  } catch (error) {
    console.error('Error fetching events:', error);
  }
}

function displayEvents(events) {
  const calendarDiv = document.getElementById('calendar');
  calendarDiv.innerHTML = ''; // Clear existing

  if (!events.length) {
    calendarDiv.innerHTML = '<p>No events found.</p>';
    return;
  }

  // Simple list output of events
  const ul = document.createElement('ul');

  events.forEach(event => {
    const li = document.createElement('li');

    // Adjust based on your event data structure
    li.textContent = `${event.title || 'No title'} — ${event.date || 'No date'}`;
    ul.appendChild(li);
  });

  calendarDiv.appendChild(ul);
}
async function updateEvent(id, { title, description, start_time, end_time, category }) {
    await fetch(`${pythonURI}/api/calendarv3/events/${id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ title, description, start_time, end_time, category })
    });
  }
  async function deleteEvent(id) {
    await fetch(`${pythonURI}/api/calendarv3/events/${id}`, {
      method: 'DELETE'
    });
  }

  // --- EMPLOYEES ---
  async function getEmployees() {
    const res = await fetch(`${pythonURI}/api/calendarv3/employees`, fetchOptions);
    return await res.json();
  }
  async function postEmployee({ name, position, work_time }) {
    await fetch(`${pythonURI}/api/calendarv3/employees`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name, position, work_time })
    });
  }
  async function getEmployees() {
  try {
    const response = await fetch('https://optivize.stu.nighthawkcodingsociety.com/api/calendarv3/employees', {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json'
      }
    });

    if (!response.ok) throw new Error('Failed to fetch employees');

    const employees = await response.json();
    displayEmployees(employees);
  } catch (error) {
    console.error('Error fetching employees:', error);
  }
}
  function displayEmployees(employees) {
  const tableBody = document.querySelector('#employee-table tbody');
  tableBody.innerHTML = ''; // Clear existing rows

  employees.forEach(emp => {
    const tr = document.createElement('tr');

    // Adjust these according to your employee data structure
    tr.innerHTML = `
      <td>${emp.id || ''}</td>
      <td>${emp.name || ''}</td>
      <td>${emp.position || ''}</td>
      <td>${emp.department || ''}</td>
    `;

    tableBody.appendChild(tr);
  });
}
async function updateEmployee(id, { name, position, work_time }) {
    await fetch(`${pythonURI}/api/calendarv3/employees/${id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name, position, work_time })
    });
  }
  async function deleteEmployee(id) {
    await fetch(`${pythonURI}/api/calendarv3/employees/${id}`, {
      method: 'DELETE'
    });
  }

  // --- SHIPMENTS ---
  async function getShipments() {
    const res = await fetch(`${pythonURI}/api/calendarv3/shipments`, fetchOptions);
    return await res.json();
  }
  async function postShipment({ inventory, amount, transport_method, shipment_time }) {
    await fetch(`${pythonURI}/api/calendarv3/shipments`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ inventory, amount, transport_method, shipment_time })
    });
  }
  async function getShipments() {
  try {
    const response = await fetch("https://optivize.stu.nighthawkcodingsociety.com/api/calendarv3/shipments", {
      method: "GET",
    });

    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Error fetching shipments:", error);
    return { shipments: [] }; // return default object to prevent crash
  }
}

function displayShipments(shipments) {
  const tableBody = document.querySelector('#shipment-table tbody');
  tableBody.innerHTML = ''; // Clear existing rows

  shipments.forEach(shipment => {
    const tr = document.createElement('tr');

    // Adjust these fields based on your shipment data structure
    tr.innerHTML = `
      <td>${shipment.id || ''}</td>
      <td>${shipment.item || ''}</td>
      <td>${shipment.quantity || ''}</td>
      <td>${shipment.status || ''}</td>
      <td>${shipment.date || ''}</td>
    `;

    tableBody.appendChild(tr);
  });
}

  async function updateShipment(id, { inventory, amount, transport_method, shipment_time }) {
    await fetch(`${pythonURI}/api/calendarv3/shipments/${id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ inventory, amount, transport_method, shipment_time })
    });
  }
  async function deleteShipment(id) {
    await fetch(`${pythonURI}/api/calendarv3/shipments/${id}`, {
      method: 'DELETE'
    });
  }

  // --- TABLE LOGIC ---

  // EMPLOYEES
  async function loadEmployeeTable() {
    const data = await getEmployees();
    const tbody = document.querySelector('#employeeTable tbody');
    tbody.innerHTML = '';
    data.employees.forEach(emp => {
      const row = document.createElement('tr');
      row.innerHTML = `
        <td contenteditable="true">${emp.name}</td>
        <td contenteditable="true">${emp.position}</td>
        <td contenteditable="true">${emp.work_time}</td>
        <td>
          <button onclick="saveEmployee(${emp.id}, this)">Update</button>
          <button onclick="deleteEmployee(${emp.id}).then(loadEmployeeTable)">Delete</button>
        </td>
      `;
      tbody.appendChild(row);
    });
  }

  async function saveEmployee(id, btn) {
    const row = btn.closest('tr');
    const [name, position, work_time] = Array.from(row.children).map(td => td.textContent.trim());
    await updateEmployee(id, { name, position, work_time });
    loadEmployeeTable();
  }

  // SHIPMENTS
  async function loadShipmentTable() {
    const data = await getShipments();
    const tbody = document.querySelector('#shipmentTable tbody');
    tbody.innerHTML = '';
    data.shipments.forEach(ship => {
      const row = document.createElement('tr');
      row.innerHTML = `
        <td contenteditable="true">${ship.inventory}</td>
        <td contenteditable="true">${ship.amount}</td>
        <td contenteditable="true">${ship.transport_method}</td>
        <td contenteditable="true">${ship.shipment_time}</td>
        <td>
          <button onclick="saveShipment(${ship.id}, this)">Update</button>
          <button onclick="deleteShipment(${ship.id}).then(loadShipmentTable)">Delete</button>
        </td>
      `;
      tbody.appendChild(row);
    });
  }

  async function saveShipment(id, btn) {
    const row = btn.closest('tr');
    const [inventory, amount, transport_method, shipment_time] = Array.from(row.children).map(td => td.textContent.trim());
    await updateShipment(id, {
      inventory,
      amount: parseInt(amount),
      transport_method,
      shipment_time
    });
    loadShipmentTable();
  }

  // LOAD EVERYTHING
  document.addEventListener('DOMContentLoaded', () => {
    loadEmployeeTable();
    loadShipmentTable();
    if (typeof loadCalendar === 'function') loadCalendar(); // your calendar init function
  });
</script>

