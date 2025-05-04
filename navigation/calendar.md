---
layout: base
title: Calendar 
description: Schedule management
permalink: /navigation/calendar
---

<style>
  body {
    font-family: 'Inter', sans-serif;
    margin: 0;
    padding: 20px;
    background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
    color: #ffffff;
    min-height: 100vh;
  }

  h2 {
    text-align: center;
    color: #ffffff;
    margin-bottom: 30px;
    font-weight: 600;
  }

  #create-log-btn {
    background-color: #4CAF50;
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 1px;
    transition: all 0.3s ease;
    margin: 20px auto;
    display: block;
  }

  #create-log-btn:hover {
    background-color: #43a047;
    transform: translateY(-2px);
  }

  #grade-log-form-container {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    padding: 30px;
    margin: 20px auto;
    max-width: 400px;
    box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
    border: 1px solid rgba(255, 255, 255, 0.18);
  }

  #grade-log-form input,
  #grade-log-form textarea {
    width: 100%;
    padding: 12px;
    margin-bottom: 15px;
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 8px;
    background: rgba(255, 255, 255, 0.1);
    color: white;
    font-size: 1rem;
    transition: all 0.3s ease;
  }

  #grade-log-form input:focus,
  #grade-log-form textarea:focus {
    outline: none;
    border-color: #4CAF50;
    background: rgba(255, 255, 255, 0.15);
  }

  #grade-log-form button {
    background-color: #4CAF50;
    color: white;
    padding: 12px;
    width: 100%;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 1px;
    transition: all 0.3s ease;
  }

  #grade-log-form button:hover {
    background-color: #43a047;
    transform: translateY(-2px);
  }

  .grade-log-container {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    justify-content: center;
    margin-top: 30px;
    padding: 20px;
  }

  .grade-log {
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(5px);
    border-radius: 15px;
    padding: 20px;
    width: 320px;
    border: 1px solid rgba(255, 255, 255, 0.2);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
  }

  .grade-log:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  }

  .grade-log h3 {
    color: #ff7043;
    margin-bottom: 15px;
  }

  .grade-log p {
    margin: 10px 0;
    color: #ffffff;
  }

  .grade-log p strong {
    color: #ff7043;
  }

  .grade {
    font-size: 1.5em;
    color: #4CAF50;
    background-color: rgba(255, 255, 255, 0.1);
    padding: 0.2em 0.5em;
    border-radius: 5px;
    display: inline-block;
  }

  .edit-btn, .delete-btn {
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
    margin: 0 5px;
  }

  .edit-btn {
    background-color: rgba(76, 175, 80, 0.2);
    color: #4CAF50;
  }

  .delete-btn {
    background-color: rgba(244, 67, 54, 0.2);
    color: #f44336;
  }

  .edit-btn:hover, .delete-btn:hover {
    transform: translateY(-2px);
  }

  .button-group {
    display: flex;
    justify-content: flex-end;
    margin-top: 15px;
  }

  @media (max-width: 768px) {
    .grade-log {
      width: 100%;
      max-width: 300px;
    }
  }

  /* SweetAlert2 styling to match theme */
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

  .save-btn {
    background-color: rgba(76, 175, 80, 0.2);
    color: #4CAF50;
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
    margin: 0 5px;
  }

  .save-btn:hover {
    transform: translateY(-2px);
    background-color: rgba(76, 175, 80, 0.3);
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
</style>

<div class="max-w-2xl mx-auto mt-8 p-6 rounded-xl shadow-lg border border-gray-200">
  <h2 class="text-2xl font-semibold mb-4">📅 Calendar Event Manager</h2>

 <link href="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.10/index.global.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.10/index.global.min.js"></script>

<div class="max-w-6xl mx-auto mt-10 px-4">
  <h2 class="text-3xl font-bold mb-6 text-center text-blue-700">📆 Calendar Event Manager</h2>

  <div class="grid md:grid-cols-2 gap-6">
    <!-- Event Form -->
    <div class="p-6 bg-white rounded-xl shadow border border-gray-200">
      <form id="eventForm" class="space-y-4">
        <input type="hidden" id="eventId" />
        <div>
          <label class="block font-medium">Title</label>
          <input type="text" id="title" class="w-full p-2 border rounded" required />
        </div>
        <div>
          <label class="block font-medium">Start Time</label>
          <input type="datetime-local" id="start_time" class="w-full p-2 border rounded" required />
        </div>
        <div>
          <label class="block font-medium">End Time</label>
          <input type="datetime-local" id="end_time" class="w-full p-2 border rounded" />
        </div>
        <div>
          <label class="block font-medium">Description</label>
          <textarea id="description" rows="3" class="w-full p-2 border rounded"></textarea>
        </div>
        <button type="submit" class="bg-blue-600 text-white py-2 px-4 rounded hover:bg-blue-700">Save Event</button>
        <!-- Add these buttons right after the Save button inside the <form> -->
        <div id="event-actions" class="flex gap-4 mt-4 hidden">
        <button type="submit" class="bg-green-600 text-white py-2 px-4 rounded hover:bg-green-700">Update Event</button>
        <button type="button" id="delete-event" class="bg-red-600 text-white py-2 px-4 rounded hover:bg-red-700">Delete Event</button>
        </div>
    </form>
    </div>
   
   <!-- Calendar Container -->
<div class="p-4 bg-white rounded-xl shadow border border-gray-200">
  <div id="calendar" class="min-h-[600px]"></div>
</div>

<!-- FullCalendar CSS & JS -->
<link href="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/main.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/main.min.js"></script>

<script type="module">
  import { pythonURI, fetchOptions } from '/assets/js/api/config.js';

  const userId = 1; // Replace with logic to get the current user's ID

  document.addEventListener('DOMContentLoaded', function () {
    const calendarEl = document.getElementById('calendar');

    const calendar = new FullCalendar.Calendar(calendarEl, {
      initialView: 'dayGridMonth',
      height: 'auto',
      headerToolbar: {
        left: 'prev,next today',
        center: 'title',
        right: 'dayGridMonth,timeGridWeek,timeGridDay'
      },
      events: async function (info, successCallback, failureCallback) {
        try {
          const res = await fetch(`${pythonURI}/calendar?user_id=${userId}`, fetchOptions);
          const data = await res.json();
          const events = data.map(event => ({
            id: event.id,
            title: event.title,
            start: event.start_time,
            end: event.end_time,
            description: event.description
          }));
          successCallback(events);
        } catch (error) {
          console.error('Failed to load events:', error);
          failureCallback(error);
        }
      },
      eventClick: function (info) {
        alert(`Event: ${info.event.title}\nDescription: ${info.event.extendedProps.description}`);
      }
    });

    calendar.render();
  });
</script>


<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

  document.addEventListener('DOMContentLoaded', function () {
    const API_BASE = pythonURI + '/calendar';
    const calendarEl = document.getElementById('calendar');
    const calendar = new FullCalendar.Calendar(calendarEl, {
      initialView: 'dayGridMonth',
      events: [],
      eventClick: function (info) {
        const event = info.event;
        document.getElementById('eventId').value = event.id;
        document.getElementById('title').value = event.title;
        document.getElementById('start_time').value = event.start;
        document.getElementById('end_time').value = event.end || '';
        document.getElementById('description').value = event.extendedProps.description || '';
        document.getElementById('event-actions').classList.remove('hidden');
      }
    });
    calendar.render();

    const userId = 1; // TEMP: Replace with dynamic user ID if available

    // Fetch and load events
    async function loadEvents() {
      const res = await fetch(`${API_BASE}?user_id=${userId}`, { ...fetchOptions });
      const events = await res.json();
      calendar.removeAllEvents();
      events.forEach(ev => {
        calendar.addEvent({
          id: ev.id,
          title: ev.title,
          start: ev.start_time,
          end: ev.end_time,
          description: ev.description
        });
      });
    }

    loadEvents();
  // Create or Update Event
  document.getElementById('eventForm').addEventListener('submit', async function (e) {
    e.preventDefault();

    const id = document.getElementById('eventId').value;
    const title = document.getElementById('title').value;
    const start_time = document.getElementById('start_time').value;
    const end_time = document.getElementById('end_time').value;
    const description = document.getElementById('description').value;

    const payload = {
      title,
      start_time,
      end_time,
      description,
      user_id: userId // Make sure userId is defined in your context
    };

    const url = id ? `${pythonURI}/calendar/${id}` : `${pythonURI}/calendar`;
    const method = id ? 'PUT' : 'POST';

    try {
      const res = await fetch(url, {
        ...fetchOptions,
        method,
        body: JSON.stringify(payload)
      });

      if (res.ok) {
        loadEvents();
        document.getElementById('eventForm').reset();
        document.getElementById('event-actions').classList.add('hidden');
      } else {
        const error = await res.json();
        console.error('Error:', error);
      }
    } catch (err) {
      console.error('Fetch failed:', err);
    }
  });
});


    // Delete event
    document.getElementById('delete-event').addEventListener('click', async function () {
      const id = document.getElementById('eventId').value;
      if (!id) return;

      const res = await fetch(`${API_BASE}/${id}`, {
        ...fetchOptions,
        method: 'DELETE'
      });

      if (res.ok) {
        loadEvents();
        document.getElementById('eventForm').reset();
        document.getElementById('event-actions').classList.add('hidden');
      }
    });
  });
</script>
