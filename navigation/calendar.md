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
    <style>
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
    <h1 class="text-center mb-4">Crumble Cookies Operations Dashboard</h1>   
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
<h4>Employees</h4>
<table>
  <thead><tr><th>Name</th><th>Position</th><th>Work Time</th><th>Actions</th></tr></thead>
  <tbody id="employeeTableBody"></tbody>
</table>

<h4>Shipments</h4>
<table>
  <thead><tr><th>Inventory</th><th>Amount</th><th>Transport</th><th>Shipment Time</th><th>Actions</th></tr></thead>
  <tbody id="shipmentTableBody"></tbody>
</table>

<script>
  const { pythonURI, fetchOptions } = window.apiConfig;
  async function loadCalendarEvents(calendar) {
    const res = await fetch(`${pythonURI}/api/calendarv3/events`, { ...fetchOptions });
    const data = await res.json();
    calendar.removeAllEvents();
    data.events.forEach(event => {
      calendar.addEvent({
        id: event.id,
        title: event.title,
        start: event.start,
        end: event.end
      });
    });
  }
  async function deleteCalendarEvent(id) {
    await fetch(`${pythonURI}/api/calendarv3/events/${id}`, {
      ...fetchOptions, method: 'DELETE'
    });
  }
  async function updateCalendarEvent(id, updatedEvent) {
    await fetch(`${pythonURI}/api/calendarv3/events/${id}`, {
      ...fetchOptions,
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(updatedEvent)
    });
  }
  async function loadEmployeeTable() {
    const res = await fetch(`${pythonURI}/api/calendarv3/employees`, { ...fetchOptions });
    const data = await res.json();
    const tbody = document.getElementById('employeeTableBody');
    tbody.innerHTML = data.employees.map(emp => `
      <tr data-id="${emp.id}">
        <td contenteditable="true">${emp.name}</td>
        <td contenteditable="true">${emp.position}</td>
        <td contenteditable="true">${emp.work_time}</td>
        <td>
          <button onclick="updateEmployee(this)">Update</button>
          <button onclick="deleteEmployee(${emp.id})">Delete</button>
        </td>
      </tr>
    `).join('');
  }
  async function loadShipmentTable() {
    const res = await fetch(`${pythonURI}/api/calendarv3/shipments`, { ...fetchOptions });
    const data = await res.json();
    const tbody = document.getElementById('shipmentTableBody');
    tbody.innerHTML = data.shipments.map(ship => `
      <tr data-id="${ship.id}">
        <td contenteditable="true">${ship.inventory}</td>
        <td contenteditable="true">${ship.amount}</td>
        <td contenteditable="true">${ship.transport_method}</td>
        <td contenteditable="true">${new Date(ship.shipment_time).toISOString()}</td>
        <td>
          <button onclick="updateShipment(this)">Update</button>
          <button onclick="deleteShipment(${ship.id})">Delete</button>
        </td>
      </tr>
    `).join('');
  }
  async function updateEmployee(btn) {
    const tr = btn.closest('tr');
    const id = tr.dataset.id;
    const [name, position, work_time] = [...tr.children].slice(0, 3).map(td => td.innerText.trim());
    await fetch(`${pythonURI}/api/calendarv3/employees/${id}`, {
      ...fetchOptions,
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name, position, work_time })
    });
  }
  async function deleteEmployee(id) {
    await fetch(`${pythonURI}/api/calendarv3/employees/${id}`, {
      ...fetchOptions, method: 'DELETE'
    });
    loadEmployeeTable();
  }
  async function updateShipment(btn) {
    const tr = btn.closest('tr');
    const id = tr.dataset.id;
    const [inventory, amount, transport_method, shipment_time] = [...tr.children].slice(0, 4).map(td => td.innerText.trim());
    await fetch(`${pythonURI}/api/calendarv3/shipments/${id}`, {
      ...fetchOptions,
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        inventory,
        amount: parseInt(amount),
        transport_method,
        shipment_time
      })
    });
  }
  async function deleteShipment(id) {
    await fetch(`${pythonURI}/api/calendarv3/shipments/${id}`, {
      ...fetchOptions, method: 'DELETE'
    });
    loadShipmentTable();
  }
  document.addEventListener('DOMContentLoaded', async () => {
    // Initialize FullCalendar
    const calendar = new FullCalendar.Calendar(document.getElementById('calendar'), {
      initialView: 'dayGridMonth',
      editable: true,
      eventClick: async function (info) {
        if (confirm("Delete this event?")) {
          await deleteCalendarEvent(info.event.id);
          info.event.remove();
        }
      },
      eventDrop: async function (info) {
        await updateCalendarEvent(info.event.id, {
          title: info.event.title,
          start: info.event.start.toISOString(),
          end: info.event.end ? info.event.end.toISOString() : null
        });
      }
    });
    calendar.render();
    await loadCalendarEvents(calendar);
// Load Employee and Shipment Tables
    await loadEmployeeTable();
    await loadShipmentTable();
  });
</script>
