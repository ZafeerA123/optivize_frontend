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

    <div>
      <label class="block font-medium">User ID</label>
      <input type="number" id="user_id" class="w-full p-2 border rounded" required />
    </div>

    <button type="submit" class="bg-blue-600 text-white py-2 px-4 rounded hover:bg-blue-700">Save Event</button>
  </form>

  <hr class="my-6"/>

  <div>
    <h3 class="text-xl font-semibold mb-2">Your Events</h3>
    <div id="eventsContainer" class="space-y-4 text-sm"></div>
  </div>
</div>

<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

  document.addEventListener('DOMContentLoaded', function () {
    const API_BASE = pythonURI + '/calendar';

    const eventForm = document.getElementById('eventForm');
    const userIdInput = document.getElementById('user_id');
    const eventsContainer = document.getElementById('eventsContainer');

    const fetchEvents = async () => {
      const userId = userIdInput.value;
      if (!userId) return;

      try {
        const res = await fetch(`${API_BASE}?user_id=${userId}`, { ...fetchOptions });
        const events = await res.json();
        eventsContainer.innerHTML = '';

        if (Array.isArray(events)) {
          events.forEach(event => {
            const div = document.createElement('div');
            div.className = "border p-4 rounded bg-gray-50";
            div.innerHTML = `
              <h4 class="font-bold text-lg">${event.title}</h4>
              <p><strong>Start:</strong> ${event.start_time}</p>
              <p><strong>End:</strong> ${event.end_time || 'N/A'}</p>
              <p><strong>Description:</strong> ${event.description || 'N/A'}</p>
              <div class="mt-2 space-x-2">
                <button class="text-blue-600 underline" onclick="editEvent(${event.id})">Edit</button>
                <button class="text-red-600 underline" onclick="deleteEvent(${event.id})">Delete</button>
              </div>
            `;
            eventsContainer.appendChild(div);
          });
        } else {
          eventsContainer.innerHTML = '<p>No events found.</p>';
        }
      } catch (err) {
        console.error('Fetch error:', err);
        eventsContainer.innerHTML = `<p class="text-red-500">Failed to load events.</p>`;
      }
    };

    window.editEvent = async (id) => {
      try {
        const res = await fetch(`${API_BASE}?user_id=${userIdInput.value}`, { ...fetchOptions });
        const data = await res.json();
        const event = data.find(ev => ev.id === id);

        if (event) {
          document.getElementById('eventId').value = event.id;
          document.getElementById('title').value = event.title;
          document.getElementById('start_time').value = event.start_time;
          document.getElementById('end_time').value = event.end_time || '';
          document.getElementById('description').value = event.description || '';
        }
      } catch (err) {
        console.error('Edit fetch error:', err);
      }
    };

    window.deleteEvent = async (id) => {
      if (!confirm('Are you sure you want to delete this event?')) return;

      try {
        const res = await fetch(`${API_BASE}/${id}`, {
          ...fetchOptions,
          method: 'DELETE'
        });

        if (res.ok) fetchEvents();
        else alert('Delete failed.');
      } catch (err) {
        console.error('Delete error:', err);
      }
    };

    eventForm.addEventListener('submit', async function (e) {
      e.preventDefault();
      const id = document.getElementById('eventId').value;

      const eventData = {
        title: document.getElementById('title').value,
        start_time: document.getElementById('start_time').value,
        end_time: document.getElementById('end_time').value,
        description: document.getElementById('description').value,
        user_id: parseInt(userIdInput.value)
      };

      try {
        const res = await fetch(`${API_BASE}${id ? '/' + id : ''}`, {
          ...fetchOptions,
          method: id ? 'PUT' : 'POST',
          body: JSON.stringify(eventData)
        });

        if (res.ok) {
          eventForm.reset();
          document.getElementById('eventId').value = '';
          fetchEvents();
        } else {
          alert('Save failed.');
        }
      } catch (err) {
        console.error('Save error:', err);
      }
    });

    userIdInput.addEventListener('change', fetchEvents);
  });
</script>
