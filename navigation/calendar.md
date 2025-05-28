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
  <title>Operations Dashboard</title>
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
<!-- Events Tab -->
<div id="events" class="tab-content mt-4">
  <div class="card shadow p-4 rounded-4">
    <h2 class="mb-4 fw-bold text-center">Event Manager</h2>
    <!-- Add New Event Form -->
    <div class="mb-5">
      <h4 class="fw-semibold mb-3">Add New Event</h4>
      <form id="eventForm" class="row g-3">
        <div class="col-md-6">
          <label class="form-label fw-bold">Title:</label>
          <input type="text" name="title" class="form-control rounded-3" placeholder="Enter event title" required />
        </div>
        <div class="col-md-6">
          <label class="form-label fw-bold">Location:</label>
          <input type="text" name="location" class="form-control rounded-3" placeholder="Enter location" required />
        </div>
        <div class="col-md-12">
          <label class="form-label fw-bold">Description:</label>
          <input type="text" name="description" class="form-control rounded-3" placeholder="Enter short description" required />
        </div>
        <div class="col-md-6">
          <label class="form-label fw-bold">Start Time:</label>
          <input type="text" name="start_time" class="form-control rounded-3" placeholder="YYYY-MM-DD HH:mm:ss" required />
        </div>
        <div class="col-md-6">
          <label class="form-label fw-bold">End Time:</label>
          <input type="text" name="end_time" class="form-control rounded-3" placeholder="YYYY-MM-DD HH:mm:ss" required />
        </div>
        <div class="col-12 text-end">
          <button type="submit" class="btn btn-warning fw-semibold rounded-3 px-4">Submit Event</button>
        </div>
      </form>
    </div>
    <!-- Upcoming Events Table -->
    <div>
      <h4 class="fw-semibold mb-3">Upcoming Events</h4>
      <div class="table-responsive">
        <table id="event-table" class="table table-bordered table-striped rounded-4 overflow-hidden">
          <thead class="table-dark text-center">
            <tr>
              <th>ID</th>
              <th>Title</th>
              <th>Location</th>
              <th>Description</th>
              <th>Start</th>
              <th>End</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody></tbody>
        </table>
      </div>
    </div>
  </div>
</div>


<!-- Shipments Tab -->
<div id="shipments" class="tab-content">
  <h2>Shipment Manager</h2>

  <h3>Add New Shipment</h3>
  <form id="shipmentForm">
    <label>
      Inventory Item:
      <input type="text" name="inventory" placeholder="e.g., Cookie Dough" required />
    </label>
    <label>
      Quantity:
      <input type="number" name="amount" placeholder="e.g., 100" required />
    </label>
    <label>
      Transport Method:
      <input type="text" name="transport_method" placeholder="e.g., Truck, Plane" required />
    </label>
    <label>
      Shipment Time:
      <input type="text" name="shipment_time" placeholder="YYYY-MM-DD HH:mm:ss" required />
    </label>
    <button type="submit">Submit Shipment</button>
  </form>

  <button type="submit">Add Event</button>
</form>

<h2>Add Shipment</h2>
<form id="shipmentForm">
  <label>
    Inventory Item:<br>
    <input type="text" name="inventory" required />
  </label><br><br>

  <label>
    Quantity:<br>
    <input type="number" name="amount" required />
  </label><br><br>

  <label>
    Transport Method:<br>
    <input type="text" name="transport_method" required />
  </label><br><br>

  <label>
    Shipment Time (YYYY-MM-DD HH:mm:ss):<br>
    <input type="text" name="shipment_time" required />
  </label><br><br>

  <button type="submit">Submit Shipment</button>
</form>

<h2>Shipment List</h2>
<table id="shipment-table" border="1">
  <thead>
    <tr>
      <th>ID</th>
      <th>Item</th>
      <th>Quantity</th>
      <th>Transport Method</th>
      <th>Shipment Time</th>
      <th>Actions</th>
    </tr>
  </thead>
  <tbody></tbody>
</table>

<div id="calendar"></div>
          <div id="eventList"></div>
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

<script>
  const pythonURI = 'https://optivize.stu.nighthawkcodingsociety.com'; // Replace with your backend
  const fetchOptions = { credentials: 'include' };
document.addEventListener('DOMContentLoaded', async () => {
  await loadShipmentTable(); // Load shipment table + events
  await loadEmployeeTable(); // Load employee table
});

 async function loadShipmentTable() {
  try {
    const response = await fetch('https://optivize.stu.nighthawkcodingsociety.com/api/calendarv3/shipments');
    const data = await response.json();

    const tableBody = document.querySelector("#shipment-table tbody");
    tableBody.innerHTML = "";

    const events = [];

    data.shipments.forEach(shipment => {
      // Populate table row
      const row = document.createElement("tr");
      row.innerHTML = `
        <td>${shipment.id}</td>
        <td>${shipment.title}</td>
        <td>${shipment.start_time}</td>
        <td>${shipment.end_time}</td>
        <td>${shipment.category}</td>
      `;
      tableBody.appendChild(row);

      // Add to calendar
      events.push({
        title: shipment.title,
        start: shipment.start_time,
        end: shipment.end_time,
        extendedProps: {
          category: shipment.category,
          description: shipment.description
        }
      });
    });

    // Render calendar
    renderCalendar(events);

  } catch (err) {
    console.error("Error fetching shipments:", err);
  }
}

 async function loadEmployeeTable() {
  try {
    const response = await fetch('https://optivize.stu.nighthawkcodingsociety.com/api/calendarv3/employees');
    const data = await response.json();

    const tableBody = document.querySelector("#employee-table tbody");
    tableBody.innerHTML = "";

    data.employees.forEach(emp => {
      const row = document.createElement("tr");
      row.innerHTML = `
        <td>${emp.id}</td>
        <td>${emp.name}</td>
        <td>${emp.role}</td>
        <td>${emp.email}</td>
      `;
      tableBody.appendChild(row);
    });

  } catch (err) {
    console.error("Error fetching employees:", err);
  }
}
function renderCalendar(events) {
  const calendarEl = document.getElementById('calendar');
  if (!calendarEl) {
    console.error("No calendar element found");
    return;
  }

  const calendar = new FullCalendar.Calendar(calendarEl, {
    initialView: 'dayGridMonth',
    height: 'auto',
    events: events,
    eventClick: function(info) {
      alert(`${info.event.title}\n${info.event.extendedProps.category}\n${info.event.extendedProps.description}`);
    }
  });

  calendar.render();
}

  async function postEvent({ title, description, start_time, end_time, category }) {
  try {
    const response = await fetch(`${pythonURI}/api/calendarv3/events`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ title, description, start_time, end_time, category })
    });

    if (!response.ok) {
      throw new Error('Failed to post event');
    }

    const data = await response.json();
    console.log('Event posted:', data);
    await getEvents();  // Refresh list after posting

  } catch (error) {
    console.error('Error posting event:', error);
    alert('Failed to add event: ' + error.message);
  }
}

async function getEvents() {
  try {
    const response = await fetch(`${pythonURI}/api/calendarv3/events`, {
      method: 'GET',
      headers: { 'Content-Type': 'application/json' }
    });

    if (!response.ok) {
      throw new Error(`Failed to fetch events: ${response.statusText}`);
    }

    const data = await response.json();

    if (data.success && Array.isArray(data.events)) {
      displayEvents(data.events);
    } else {
      console.error('Unexpected response structure:', data);
      document.getElementById('calendar').innerHTML = '<p>Failed to load events.</p>';
    }
  } catch (error) {
    console.error('Error fetching events:', error);
    document.getElementById('calendar').innerHTML = `<p>Error fetching events: ${error.message}</p>`;
  }
}

function displayEvents(events) {
  const calendarDiv = document.getElementById('calendar');
  calendarDiv.innerHTML = '';

  if (!events.length) {
    calendarDiv.innerHTML = '<p>No events found.</p>';
    return;
  }

  const ul = document.createElement('ul');

  events.forEach(event => {
    const li = document.createElement('li');
    li.innerHTML = `
      <strong>Title:</strong> ${event.title || 'N/A'}<br>
      <strong>Description:</strong> ${event.description || 'N/A'}<br>
      <strong>Start:</strong> ${event.start_time || 'N/A'}<br>
      <strong>End:</strong> ${event.end_time || 'N/A'}<br>
      <strong>Category:</strong> ${event.category || 'N/A'}
    `;
    ul.appendChild(li);
  });

  calendarDiv.appendChild(ul);
}

// Attach form submit handler
document.addEventListener('DOMContentLoaded', () => {
  getEvents();  // Load events on page load

  const form = document.getElementById('eventForm');
  form.addEventListener('submit', async (e) => {
    e.preventDefault();

    // Get form data
    const formData = new FormData(form);
    const eventData = {
      title: formData.get('title'),
      description: formData.get('description'),
      start_time: formData.get('start_time'),
      end_time: formData.get('end_time'),
      category: formData.get('category')
    };

    await postEvent(eventData);

    form.reset(); // Clear form after successful submission
  });
});

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
  document.addEventListener('DOMContentLoaded', async () => {
  const events = await fetchCalendarEvents();
  renderFullCalendar(events);
});
 async function fetchCalendarEvents() {
  try {
    const res = await fetch('https://optivize.stu.nighthawkcodingsociety.com/api/calendarv3/events');
    const json = await res.json();

    if (!json.success || !json.events) {
      console.error('Invalid API response', json);
      return [];
    }

    // Map events to FullCalendar format
    return json.events.map(event => ({
      id: event.id,
      title: event.title,
      start: event.start_time.replace(' ', 'T'),
      end: event.end_time.replace(' ', 'T'),
      extendedProps: {
        description: event.description,
        category: event.category
      }
    }));
  } catch (error) {
    console.error('Error fetching calendar events:', error);
    return [];
  }
}

function renderFullCalendar(events) {
  const calendarEl = document.getElementById('calendar');
  const calendar = new FullCalendar.Calendar(calendarEl, {
    initialView: 'dayGridMonth',
    height: 'auto',
    events: events,
    eventClick: function(info) {
      alert(`Title: ${info.event.title}
Description: ${info.event.extendedProps.description}
Category: ${info.event.extendedProps.category}`);
    }
  });

  calendar.render();
}
  // --- SHIPMENTS ---
  // Fetch all shipments
async function getShipments() {
  try {
    const response = await fetch(`${pythonURI}/api/calendarv3/shipments`, {
      method: 'GET',
      headers: { 'Content-Type': 'application/json' }
    });

    if (!response.ok) throw new Error(`HTTP error! Status: ${response.status}`);

    const data = await response.json();
    displayShipments(data.shipments || []);
  } catch (error) {
    console.error('Error fetching shipments:', error);
  }
}

// Add a shipment
async function postShipment({ inventory, amount, transport_method, shipment_time }) {
  try {
    await fetch(`${pythonURI}/api/calendarv3/shipments`, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ inventory, amount, transport_method, shipment_time })
    });

    getShipments(); // Refresh list
  } catch (error) {
    console.error('Error posting shipment:', error);
  }
}

// Update a shipment
async function updateShipment(id, { inventory, amount, transport_method, shipment_time }) {
  try {
    await fetch(`${pythonURI}/api/calendarv3/shipments/${id}`, {
      method: 'PUT',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ inventory, amount, transport_method, shipment_time })
    });

    getShipments();
  } catch (error) {
    console.error('Error updating shipment:', error);
  }
}

// Delete a shipment
async function deleteShipment(id) {
  try {
    await fetch(`${pythonURI}/api/calendarv3/shipments/${id}`, {
      method: 'DELETE'
    });

    getShipments();
  } catch (error) {
    console.error('Error deleting shipment:', error);
  }
}

// Display shipments in a table
function displayShipments(shipments) {
  const tableBody = document.querySelector('#shipment-table tbody');
  tableBody.innerHTML = '';

  shipments.forEach(shipment => {
    const tr = document.createElement('tr');

    tr.innerHTML = `
      <td>${shipment.id || ''}</td>
      <td>${shipment.inventory || ''}</td>
      <td>${shipment.amount || ''}</td>
      <td>${shipment.transport_method || ''}</td>
      <td>${shipment.shipment_time || ''}</td>
      <td>
        <button onclick="deleteShipment('${shipment.id}')">Delete</button>
      </td>
    `;

    tableBody.appendChild(tr);
  });
}

// Form submission handler
document.addEventListener('DOMContentLoaded', () => {
  getShipments();

  const shipmentForm = document.getElementById('shipmentForm');
  shipmentForm.addEventListener('submit', async (e) => {
    e.preventDefault();

    const formData = new FormData(shipmentForm);
    const shipmentData = {
      inventory: formData.get('inventory'),
      amount: parseInt(formData.get('amount')),
      transport_method: formData.get('transport_method'),
      shipment_time: formData.get('shipment_time')
    };

    await postShipment(shipmentData);
    shipmentForm.reset();
  });
});
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

