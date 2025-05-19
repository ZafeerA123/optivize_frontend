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
      background-color: #eef1f5;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    .fc-toolbar-title {
      font-size: 1.8rem;
      font-weight: 700;
    }
    .fc-event {
      font-size: 0.85rem;
      padding: 5px 8px;
      border-radius: 10px;
      border: none;
    }
    .event-campaign { background-color: #ffc107; color: #000; }
    .event-social { background-color: #0d6efd; color: #fff; }
    .event-shipment { background-color: #198754; color: #fff; }
    .event-meeting { background-color: #6f42c1; color: #fff; }
    .event-holiday { background-color: #dc3545; color: #fff; }
    .event-workforce { background-color: #20c997; color: #fff; }
    .nav-tabs {
      border-bottom: none;
    }
    .nav-tabs .nav-link {
      border-radius: 12px;
      background: linear-gradient(to right, #4e54c8, #8f94fb);
      color: white;
      margin-right: 6px;
      font-weight: 600;
      transition: all 0.3s ease;
    }
    .nav-tabs .nav-link:hover {
      background: linear-gradient(to right, #3b3fba, #7a7ffb);
    }
    .nav-tabs .nav-link.active {
      background: #343a40;
      font-weight: bold;
    }
    .form-section {
      background-color: #fff;
      padding: 24px;
      border-radius: 14px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.1);
      margin-bottom: 24px;
    }
    .tab-pane {
      animation: fadeEffect 0.5s ease-in-out;
    }
    @keyframes fadeEffect {
      from {opacity: 0;}
      to {opacity: 1;}
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
