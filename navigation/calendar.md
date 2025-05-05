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

<div class="container mt-5">
  <h2 class="mb-4 text-center">📅 Full Calendar V3</h2>

  <!-- Add Event Form -->
  <form id="eventForm" class="mb-4">
    <div class="row g-2">
      <div class="col-md-3">
        <input type="text" id="title" class="form-control" placeholder="Title" required>
      </div>
      <div class="col-md-3">
        <input type="text" id="description" class="form-control" placeholder="Description" required>
      </div>
      <div class="col-md-2">
        <input type="datetime-local" id="start_time" class="form-control" required>
      </div>
      <div class="col-md-2">
        <input type="datetime-local" id="end_time" class="form-control" required>
      </div>
      <div class="col-md-1">
        <input type="text" id="category" class="form-control" placeholder="Category" required>
      </div>
      <div class="col-md-1">
        <button type="submit" class="btn btn-primary w-100">Add</button>
      </div>
    </div>
  </form>

  <!-- Calendar -->
  <div id="calendar"></div>
</div>

<!-- FullCalendar + Script -->
<script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.js"></script>
<script>
  const API_URL = "https://your-domain.com/api/calendarv3/";  // change to your actual domain
    document.addEventListener("DOMContentLoaded", function () {
    const calendarEl = document.getElementById("calendar");
     const calendar = new FullCalendar.Calendar(calendarEl, {
      initialView: "dayGridMonth",
      selectable: true,
      editable: false,
      events: fetchEvents,
      eventClick: onEventClick
    });
    calendar.render();
    // GET events
    async function fetchEvents(fetchInfo, successCallback, failureCallback) {
      try {
        const res = await fetch(API_URL);
        const json = await res.json();
        const events = json.events.map(e => ({
          id: e.id,
          title: e.title,
          start: e.start_time,
          end: e.end_time,
          extendedProps: {
            description: e.description,
            category: e.category
          }
        }));
        successCallback(events);
      } catch (err) {
        console.error("Fetch error:", err);
        failureCallback(err);
      }
    }
    // POST (add) event
    document.getElementById("eventForm").addEventListener("submit", async function (e) {
      e.preventDefault();
      const title = document.getElementById("title").value;
      const description = document.getElementById("description").value;
      const start_time = formatDateTime(document.getElementById("start_time").value);
      const end_time = formatDateTime(document.getElementById("end_time").value);
      const category = document.getElementById("category").value;
      const newEvent = { title, description, start_time, end_time, category };
      try {
        const res = await fetch(API_URL, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(newEvent)
        });
        if (res.ok) {
          calendar.refetchEvents();
          e.target.reset();
        } else {
          alert("Failed to add event.");
        }
      } catch (err) {
        console.error("Add error:", err);
        alert("Error adding event.");
      }
    });
    // PUT (update) or DELETE
    function onEventClick(info) {
      const event = info.event;
      const newTitle = prompt("Edit title (leave blank to delete):", event.title);
      if (newTitle === null) return;
      if (newTitle === "") {
        if (confirm("Delete this event?")) {
          deleteEvent(event.id);
        }
      } else {
        const updatedEvent = {
          id: event.id,
          title: newTitle,
          description: event.extendedProps.description,
          start_time: formatDateTime(event.startStr),
          end_time: formatDateTime(event.endStr),
          category: event.extendedProps.category
        };
        updateEvent(updatedEvent);
      }
    }
    // PUT event
    async function updateEvent(eventData) {
      try {
        const res = await fetch(API_URL, {
          method: "PUT",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(eventData)
        });
        if (res.ok) {
          calendar.refetchEvents();
        } else {
          alert("Update failed.");
        }
      } catch (err) {
        console.error("Update error:", err);
        alert("Error updating.");
      }
    }
     // DELETE event
    async function deleteEvent(id) {
      try {
        const res = await fetch(API_URL, {
          method: "DELETE",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({ id })
        });
        if (res.ok) {
          calendar.refetchEvents();
        } else {
          alert("Delete failed.");
        }
      } catch (err) {
        console.error("Delete error:", err);
        alert("Error deleting.");
      }
    }
    // Format datetime to "YYYY-MM-DD HH:mm:ss"
    function formatDateTime(localDatetime) {
      const dt = new Date(localDatetime);
      return dt.toISOString().slice(0, 19).replace("T", " ");
    }
  });
</script>
