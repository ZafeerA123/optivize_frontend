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
      <!-- Tasks Tab -->
      <div class="tab-pane fade" id="tasksSection">
        <div class="dashboard-box">
          <h4 class="mb-4">✅ Task Management</h4>
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

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.js"></script>
  <script>
    let calendar;
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
            const res = await fetch('/api/events');
            const eventsData = await res.json();
            const holidaysRes = await fetch('https://calendarific.com/api/v2/holidays?api_key=YOUR_API_KEY&country=US&year=' + new Date().getFullYear());
            const holidays = await holidaysRes.json();
            const holidayEvents = holidays.response.holidays.map(h => ({
              title: h.name,
              start: h.date.iso,
              classNames: ['event-holiday']
            }));
            const formatted = eventsData.map(e => ({
              title: e.title,
              start: e.start,
              end: e.end,
              classNames: [e.type]
            }));
            successCallback([...formatted, ...holidayEvents]);
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
    document.addEventListener('DOMContentLoaded', initCalendar);
    document.getElementById('eventForm').addEventListener('submit', async function(e) {
      e.preventDefault();
      const title = document.getElementById('eventTitle').value;
      const start = document.getElementById('eventDate').value;
      const type = document.getElementById('eventType').value;
      await fetch('/api/events', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ title, start, type })
      });
      calendar.refetchEvents();
      this.reset();
    });
    document.getElementById('workforceForm').addEventListener('submit', async function(e) {
      e.preventDefault();
      const name = document.getElementById('name').value;
      const availability = document.getElementById('availability').value;
      await fetch('/api/workforce', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({ name, availability })
      });
      alert(`Added ${name} with availability: ${availability}`);
      this.reset();
    });
  </script>
</body>
</html>
