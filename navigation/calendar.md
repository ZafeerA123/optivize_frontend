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
  <title>Unified Smart Marketing & Operations Calendar</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.css" rel="stylesheet">
 <style>
  body {
    background-color: #f4f1fa;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  .fc {
    background-color: #fff6fb; /* light pinkish background for calendar */
    border-radius: 10px;
    padding: 20px;
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);
  }

  .fc-daygrid-day {
    background-color: #fff;
    color: #333;
    border: 1px solid #f0e8f5;
  }

  .fc-daygrid-day-number {
    color:rgb(228, 216, 226); /* date numbers */
    font-weight: 600;
  }

  .fc-col-header-cell-cushion {
    color:rgb(20, 140, 26); /* day headers */
    font-weight: 700;
    font-size: 0.9rem;
  }

  .fc-toolbar-title {
    font-size: 1.8rem;
    font-weight: 700;
    color:rgb(146, 85, 27);
  }

  .fc-button {
    background-color:rgb(209, 15, 15) !important;
    border: none !important;
    color: #fff !important;
  }

  .fc-button:hover {
    background-color: #8e24aa !important;
  }

  .fc-event {
    font-size: 0.85rem;
    padding: 5px 8px;
    border-radius: 10px;
    border: none;
  }

  .event-campaign { background-color: #ffb300; color: #000; }
  .event-social { background-color: #5c6bc0; color: #fff; }
  .event-shipment { background-color: #43a047; color: #fff; }
  .event-meeting { background-color: #8e24aa; color: #fff; }
  .event-holiday { background-color: #e53935; color: #fff; }
  .event-workforce { background-color: #00acc1; color: #fff; }

  .nav-tabs {
    border-bottom: none;
  }

  .nav-tabs .nav-link {
    border-radius: 12px;
    background: linear-gradient(to right, #8e24aa, #ce93d8);
    color: white;
    margin-right: 6px;
    font-weight: 600;
    transition: all 0.3s ease;
  }

  .nav-tabs .nav-link:hover {
    background: linear-gradient(to right, #6a1b9a, #ba68c8);
  }

  .nav-tabs .nav-link.active {
    background: #4a148c;
    font-weight: bold;
  }

  .form-section {
    background-color: #ffffff;
    padding: 24px;
    border-radius: 14px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    margin-bottom: 24px;
  }

  .tab-pane {
    animation: fadeEffect 0.5s ease-in-out;
  }

  @keyframes fadeEffect {
    from { opacity: 0; }
    to { opacity: 1; }
  }
</style>
 
</head>
<body>
  <div class="container my-4">
    <h1 class="text-center mb-4">Unified Smart Marketing & Operations Calendar</h1>
    <ul class="nav nav-tabs mb-4" id="tabMenu" role="tablist">
      <li class="nav-item" role="presentation">
        <button class="nav-link active" id="calendar-tab" data-bs-toggle="tab" data-bs-target="#calendarSection" type="button">Calendar View</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" id="workforce-tab" data-bs-toggle="tab" data-bs-target="#workforceSection" type="button">Add Workforce</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" id="events-tab" data-bs-toggle="tab" data-bs-target="#eventsSection" type="button">Add Event</button>
      </li>
    </ul>
    <div class="tab-content">
      <div class="tab-pane fade show active" id="calendarSection">
        <div id='calendar'></div>
      </div>
      <div class="tab-pane fade" id="workforceSection">
        <div class="form-section">
          <h5>Add New Team Member</h5>
          <form id="workforceForm">
            <div class="mb-3">
              <label for="name" class="form-label">Name</label>
              <input type="text" class="form-control" id="name" required>
            </div>
            <div class="mb-3">
              <label for="availability" class="form-label">Availability</label>
              <input type="text" class="form-control" id="availability" placeholder="e.g. Mon-Fri, 9am-5pm" required>
            </div>
            <button type="submit" class="btn btn-success">Add Member</button>
          </form>
        </div>
      </div>
      <div class="tab-pane fade" id="eventsSection">
        <div class="form-section">
          <h5>Add New Event</h5>
          <form id="eventForm">
            <div class="mb-3">
              <label for="eventTitle" class="form-label">Event Title</label>
              <input type="text" class="form-control" id="eventTitle" required>
            </div>
            <div class="mb-3">
              <label for="eventDate" class="form-label">Event Date</label>
              <input type="date" class="form-control" id="eventDate" required>
            </div>
            <div class="mb-3">
              <label for="eventType" class="form-label">Event Type</label>
              <select class="form-select" id="eventType">
                <option value="event-campaign">Campaign</option>
                <option value="event-social">Social</option>
                <option value="event-shipment">Shipment</option>
                <option value="event-meeting">Meeting</option>
                <option value="event-holiday">Holiday</option>
                <option value="event-workforce">Workforce</option>
              </select>
            </div>
            <button type="submit" class="btn btn-primary">Add Event</button>
          </form>
        </div>
      </div>
    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.js"></script>
<script type="module">
  import { pythonURI } from '{{site.baseurl}}/assets/js/api/config.js';
  let calendar;
  async function fetchEvents() {
    const res = await fetch(`${pythonURI}/api/events`);
    return res.json();
  }
  async function fetchEmployees() {
    const res = await fetch(`${pythonURI}/api/employees`);
    return res.json();
  }
  async function fetchShipments() {
    const res = await fetch(`${pythonURI}/api/shipments`);
    return res.json();
  }
  async function initCalendar() {
    const calendarEl = document.getElementById('calendar');
    calendar = new FullCalendar.Calendar(calendarEl, {
      initialView: 'dayGridMonth',
      headerToolbar: {
        left: 'prev,next today',
        center: 'title',
        right: 'dayGridMonth,timeGridWeek,timeGridDay,listWeek'
      },
      events: async function(fetchInfo, successCallback, failureCallback) {
        try {
          const eventsData = await fetchEvents();
          // Format events for calendar
          const formatted = eventsData.map(e => ({
            id: e.id,
            title: e.title,
            start: e.start,
            end: e.end,
            classNames: [e.type]
          }));
          successCallback(formatted);
        } catch (error) {
          console.error('Event load error:', error);
          failureCallback(error);
        }
      },
      eventClick: function(info) {
        alert(`Event: ${info.event.title}\nStart: ${info.event.start}`);
      }
    });
    calendar.render();
  }
  // Render Employees and Shipments in HTML tables or lists - you need to create these containers in your HTML with these IDs
  async function renderEmployees() {
    const employees = await fetchEmployees();
    const container = document.getElementById('employeeList');
    container.innerHTML = '';
    employees.forEach(emp => {
      const div = document.createElement('div');
      div.textContent = `Name: ${emp.name}, Availability: ${emp.availability}, Position: ${emp.position || 'N/A'}`;
      // Update and Delete buttons
      const updateBtn = document.createElement('button');
      updateBtn.textContent = 'Update';
      updateBtn.onclick = () => updateEmployeePrompt(emp);
      const deleteBtn = document.createElement('button');
      deleteBtn.textContent = 'Delete';
      deleteBtn.onclick = () => deleteEmployee(emp.id);
      div.appendChild(updateBtn);
      div.appendChild(deleteBtn);
      container.appendChild(div);
    });
  }
  async function renderShipments() {
    const shipments = await fetchShipments();
    const container = document.getElementById('shipmentList');
    container.innerHTML = '';
    shipments.forEach(ship => {
      const div = document.createElement('div');
      div.textContent = `Amount: ${ship.amount}, Inventory: ${ship.inventory}, Transporting: ${ship.transport}, Time: ${ship.time}`;
// Update and Delete buttons
      const updateBtn = document.createElement('button');
      updateBtn.textContent = 'Update';
      updateBtn.onclick = () => updateShipmentPrompt(ship);
      const deleteBtn = document.createElement('button');
      deleteBtn.textContent = 'Delete';
      deleteBtn.onclick = () => deleteShipment(ship.id);
      div.appendChild(updateBtn);
      div.appendChild(deleteBtn);
      container.appendChild(div);
    });
  }
  // CRUD Functions
  async function addEvent(event) {
    await fetch(`${pythonURI}/api/events`, {
      method: 'POST',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(event)
    });
    calendar.refetchEvents();
  }
  async function updateEvent(id, event) {
    await fetch(`${pythonURI}/api/events/${id}`, {
      method: 'PUT',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(event)
    });
    calendar.refetchEvents();
  }
  async function deleteEvent(id) {
    await fetch(`${pythonURI}/api/events/${id}`, {
      method: 'DELETE'
    });
    calendar.refetchEvents();
  }
  async function addEmployee(employee) {
    await fetch(`${pythonURI}/api/employees`, {
      method: 'POST',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(employee)
    });
    await renderEmployees();
  }
  async function updateEmployee(id, employee) {
    await fetch(`${pythonURI}/api/employees/${id}`, {
      method: 'PUT',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(employee)
    });
    await renderEmployees();
  }
  async function deleteEmployee(id) {
    if (!confirm('Delete this employee?')) return;
    await fetch(`${pythonURI}/api/employees/${id}`, {
      method: 'DELETE'
    });
    await renderEmployees();
  }
  async function addShipment(shipment) {
    await fetch(`${pythonURI}/api/shipments`, {
      method: 'POST',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(shipment)
    });
    await renderShipments();
  }
  async function updateShipment(id, shipment) {
    await fetch(`${pythonURI}/api/shipments/${id}`, {
      method: 'PUT',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(shipment)
    });
    await renderShipments();
  }
  async function deleteShipment(id) {
    if (!confirm('Delete this shipment?')) return;
    await fetch(`${pythonURI}/api/shipments/${id}`, {
      method: 'DELETE'
    });
    await renderShipments();
  }
  // Prompt helpers for updating (simplified)
  function updateEmployeePrompt(emp) {
    const name = prompt('Name:', emp.name);
    const availability = prompt('Availability:', emp.availability);
    const position = prompt('Position:', emp.position || '');
    if (name && availability) {
      updateEmployee(emp.id, {name, availability, position});
    }
  }
  function updateShipmentPrompt(ship) {
    const amount = prompt('Amount:', ship.amount);
    const inventory = prompt('Inventory:', ship.inventory);
    const transport = prompt('Transporting:', ship.transport);
    const time = prompt('Time:', ship.time);
    if (amount && inventory && transport && time) {
      updateShipment(ship.id, {amount, inventory, transport, time});
    }
  }
  // Event Form submit with add
  document.getElementById('eventForm').addEventListener('submit', async function(e) {
    e.preventDefault();
    const title = document.getElementById('eventTitle').value;
    const start = document.getElementById('eventDate').value;
    const type = document.getElementById('eventType').value;
    if (!title || !start) {
      alert('Please fill all event fields');
      return;
    }
    await addEvent({title, start, type});
    this.reset();
  });
  // Employee Form submit with add
  document.getElementById('workforceForm').addEventListener('submit', async function(e) {
    e.preventDefault();
    const name = document.getElementById('name').value;
    const availability = document.getElementById('availability').value;
    const position = document.getElementById('position').value || '';
    if (!name || !availability) {
      alert('Please fill all employee fields');
      return;
    }
    await addEmployee({name, availability, position});
    this.reset();
  });
  // Shipment Form submit with add (assumes you have one)
  document.getElementById('shipmentForm').addEventListener('submit', async function(e) {
    e.preventDefault();
    const amount = document.getElementById('amount').value;
    const inventory = document.getElementById('inventory').value;
    const transport = document.getElementById('transport').value;
    const time = document.getElementById('time').value;
    if (!amount || !inventory || !transport || !time) {
      alert('Please fill all shipment fields');
      return;
    }
    await addShipment({amount, inventory, transport, time});
    this.reset();
  });
  // Initial render
  document.addEventListener('DOMContentLoaded', async () => {
    await initCalendar();
    await renderEmployees();
    await renderShipments();
  });
</script>
