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

<!-- Tailwind & FullCalendar UI for Calendar App -->
<div class="flex h-screen">
  <!-- Sidebar -->
  <div class="w-64 bg-gray-800 text-white p-4 space-y-4">
    <h2 class="text-2xl font-bold mb-4">Calendar Actions</h2>
    <button id="addEventBtn" class="w-full bg-green-500 hover:bg-green-600 py-2 rounded">Add Event</button>
    <button id="updateEventBtn" class="w-full bg-yellow-500 hover:bg-yellow-600 py-2 rounded">Update Event</button>
    <button id="deleteEventBtn" class="w-full bg-red-500 hover:bg-red-600 py-2 rounded">Delete Event</button>
  </div>

  <!-- Calendar Content -->
  <div class="flex-1 p-6">
    <div id="calendar" class="shadow-lg rounded-xl bg-white p-4"></div>
  </div>
</div>

<!-- Modal for Event Form -->
<div id="eventModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
  <div class="bg-white p-6 rounded-lg shadow-lg w-96">
    <h3 class="text-xl font-semibold mb-4">Event Details</h3>
    <form id="eventForm" class="space-y-3">
      <input type="hidden" id="eventId">
      <input id="title" type="text" placeholder="Title" class="w-full border p-2 rounded" required>
      <input id="start_time" type="datetime-local" class="w-full border p-2 rounded" required>
      <input id="end_time" type="datetime-local" class="w-full border p-2 rounded">
      <textarea id="description" placeholder="Description" class="w-full border p-2 rounded"></textarea>
      <select id="eventType" class="w-full border p-2 rounded">
        <option value="meeting">Meeting</option>
        <option value="task">Task</option>
        <option value="reminder">Reminder</option>
      </select>
      <div class="flex justify-end gap-2">
        <button type="button" id="cancelBtn" class="bg-gray-300 px-4 py-2 rounded">Cancel</button>
        <button type="submit" class="bg-blue-500 hover:bg-blue-600 text-white px-4 py-2 rounded">Save</button>
      </div>
    </form>
  </div>
</div>

<!-- JavaScript -->
<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.js"></script>
<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';
  const API_BASE = `${pythonURI}/calendar`;
  const calendarEl = document.getElementById('calendar');
  const modal = document.getElementById('eventModal');
  const eventForm = document.getElementById('eventForm');
  const cancelBtn = document.getElementById('cancelBtn');
  const userId = 1; // Replace with actual user ID from session/auth
  const calendar = new FullCalendar.Calendar(calendarEl, {
    initialView: 'dayGridMonth',
    selectable: true,
    events: async function (info, successCallback, failureCallback) {
      const res = await fetch(`${API_BASE}?user_id=${userId}`);
      const data = await res.json();
      const formatted = data.map(ev => ({
        id: ev.id,
        title: ev.title,
        start: ev.start_time,
        end: ev.end_time,
        extendedProps: { description: ev.description, user_id: ev.user_id }
      }));
      successCallback(formatted);
    },
    eventClick: function (info) {
      const event = info.event;
      document.getElementById('eventId').value = event.id;
      document.getElementById('title').value = event.title;
      document.getElementById('start_time').value = event.startStr;
      document.getElementById('end_time').value = event.endStr || '';
      document.getElementById('description').value = event.extendedProps.description || '';
      modal.classList.remove('hidden');
    }
  });
  calendar.render();
  document.getElementById('addEventBtn').addEventListener('click', () => {
    eventForm.reset();
    document.getElementById('eventId').value = '';
    modal.classList.remove('hidden');
  });
  document.getElementById('updateEventBtn').addEventListener('click', () => {
    const selectedId = document.getElementById('eventId').value;
    if (!selectedId) return alert('Select an event to update.');
    modal.classList.remove('hidden');
  });
  document.getElementById('deleteEventBtn').addEventListener('click', async () => {
    const selectedId = document.getElementById('eventId').value;
    if (!selectedId) return alert('Select an event to delete.');
    await fetch(`${API_BASE}/${selectedId}`, { ...fetchOptions, method: 'DELETE' });
    calendar.refetchEvents();
    eventForm.reset();
  });
  cancelBtn.addEventListener('click', () => modal.classList.add('hidden'));
  eventForm.addEventListener('submit', async function (e) {
    e.preventDefault();
  const id = document.getElementById('eventId').value;
    const payload = {
      title: document.getElementById('title').value,
      start_time: document.getElementById('start_time').value,
      end_time: document.getElementById('end_time').value,
      description: `${document.getElementById('eventType').value.toUpperCase()}: ${document.getElementById('description').value}`,
      user_id: userId
    };
  const url = id ? `${API_BASE}/${id}` : API_BASE;
    const method = id ? 'PUT' : 'POST';
  const res = await fetch(url, {
      ...fetchOptions,
      method,
      body: JSON.stringify(payload)
    });
  if (res.ok) {
      calendar.refetchEvents();
      eventForm.reset();
      modal.classList.add('hidden');
    }
  });
</script>
