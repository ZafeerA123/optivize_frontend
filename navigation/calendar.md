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

<div class="calendar-container" style="display: flex; justify-content: center; align-items: center; height: 100vh;">
  <div class="calendar-wrapper" style="width: 80%; max-width: 800px; text-align: center;">
    <h1>Calendar</h1>
    <!-- Full Calendar -->
    <div id="calendar"></div>
<!-- Buttons for actions -->
    <div class="button-container" style="margin-top: 20px;">
      <button id="addEventBtn">Add Event</button>
      <button id="updateEventBtn" style="display: none;">Update Event</button>
      <button id="deleteEventBtn" style="display: none;">Delete Event</button>
    </div>
<!-- Form for adding/updating events -->
    <div id="eventForm" style="display: none; margin-top: 20px;">
      <h2>Event Details</h2>
      <form id="eventDetailsForm">
        <label for="title">Title:</label><br>
        <input type="text" id="title" required><br><br>
        <label for="start_time">Start Time:</label><br>
        <input type="datetime-local" id="start_time" required><br><br>
        <label for="end_time">End Time:</label><br>
        <input type="datetime-local" id="end_time"><br><br>
        <label for="description">Description:</label><br>
        <textarea id="description"></textarea><br><br>
        <button type="submit">Save Event</button>
      </form>
    </div>
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

  // Display events on the calendar
  function displayEvents(events) {
    const calendarElement = document.getElementById('calendar');
    // Clear existing events on the calendar (to be implemented depending on your calendar library)
    calendarElement.innerHTML = '';
    events.forEach(event => {
      // Add events to your calendar UI (use FullCalendar or any other calendar library)
      // Example: FullCalendar's `addEvent` method
      // calendar.addEvent({
      //   title: event.title,
      //   start: event.start_time,
      //   end: event.end_time,
      //   description: event.description,
      //   id: event.id,
      // });
    });
  }

  // Handle the form submission for adding/updating an event
  document.getElementById('eventDetailsForm').addEventListener('submit', async function (e) {
    e.preventDefault();

    const title = document.getElementById('title').value;
    const start_time = document.getElementById('start_time').value;
    const end_time = document.getElementById('end_time').value;
    const description = document.getElementById('description').value;
    const eventData = { title, start_time, end_time, description, user_id: 1 }; // Adjust user_id dynamically

    try {
      if (document.getElementById('updateEventBtn').style.display === 'block') {
        const eventId = document.getElementById('updateEventBtn').dataset.eventId;
        await updateEvent(eventId, eventData);
        alert('Event updated successfully');
      } else {
        await createEvent(eventData);
        alert('Event created successfully');
      }

      // Reload the events after update or create
      const events = await getEvents(1); // Replace with dynamic user ID
      displayEvents(events);
      resetForm();
    } catch (error) {
      alert(`Error: ${error.message}`);
    }
  });

  // Add event handler for Add Event button
  document.getElementById('addEventBtn').addEventListener('click', function () {
    resetForm();
    document.getElementById('eventForm').style.display = 'block';
    document.getElementById('updateEventBtn').style.display = 'none';
    document.getElementById('addEventBtn').style.display = 'none';
  });

  // Add event handler for Update Event button
  document.getElementById('updateEventBtn').addEventListener('click', function () {
    document.getElementById('eventForm').style.display = 'block';
    document.getElementById('addEventBtn').style.display = 'none';
  });

  // Add event handler for Delete Event button
  document.getElementById('deleteEventBtn').addEventListener('click', async function () {
    const eventId = document.getElementById('deleteEventBtn').dataset.eventId;
    try {
      await deleteEvent(eventId);
      alert('Event deleted successfully');
      const events = await getEvents(1); // Replace with dynamic user ID
      displayEvents(events);
      resetForm();
    } catch (error) {
      alert(`Error: ${error.message}`);
    }
  });

  // Function to reset the form
  function resetForm() {
    document.getElementById('eventForm').reset();
    document.getElementById('eventForm').style.display = 'none';
    document.getElementById('updateEventBtn').style.display = 'none';
    document.getElementById('deleteEventBtn').style.display = 'none';
    document.getElementById('addEventBtn').style.display = 'block';
  }

  // Load events when the page loads
  document.addEventListener('DOMContentLoaded', async function () {
    const events = await getEvents(1); // Replace with dynamic user ID
    displayEvents(events);
  });
</script>
