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

<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

  const CALENDAR_API = `${pythonURI}/calendar`;

  // POST: Create a new calendar event
  async function createEvent(eventData) {
    const response = await fetch(CALENDAR_API, {
      ...fetchOptions,
      method: 'POST',
      body: JSON.stringify(eventData)
    });
    if (!response.ok) {
      const error = await response.json();
      throw new Error(error.error || 'Failed to create event');
    }
    return await response.json();
  }

  // GET: Fetch all calendar events for a user
  async function getEvents(userId) {
    const response = await fetch(`${CALENDAR_API}?user_id=${userId}`, {
      ...fetchOptions,
      method: 'GET'
    });
    if (!response.ok) {
      const error = await response.json();
      throw new Error(error.error || 'Failed to fetch events');
    }
    return await response.json();
  }

  // PUT: Update an existing event by ID
  async function updateEvent(eventId, updatedData) {
    const response = await fetch(`${CALENDAR_API}/${eventId}`, {
      ...fetchOptions,
      method: 'PUT',
      body: JSON.stringify(updatedData)
    });
    if (!response.ok) {
      const error = await response.json();
      throw new Error(error.error || 'Failed to update event');
    }
    return await response.json();
  }

  // DELETE: Delete an event by ID
  async function deleteEvent(eventId) {
    const response = await fetch(`${CALENDAR_API}/${eventId}`, {
      ...fetchOptions,
      method: 'DELETE'
    });
    if (!response.ok) {
      const error = await response.json();
      throw new Error(error.error || 'Failed to delete event');
    }
    return await response.json();
  }

  // Example: Load events on page load (optional)
  document.addEventListener('DOMContentLoaded', async () => {
    const userId = 1; // Replace with dynamic user ID
    try {
      const events = await getEvents(userId);
      console.log('Fetched Events:', events);
      // You can now use this data to render events on the calendar UI
    } catch (err) {
      console.error('Error loading events:', err.message);
    }
  });
</script>
>
