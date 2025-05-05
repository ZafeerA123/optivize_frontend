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

<div class="calendar-container" style="display: flex; justify-content: center; align-items: center; min-height: 100vh; background-color: #f8f9fa; padding: 20px;">
    <div class="calendar-wrapper" style="width: 95%; max-width: 1200px; background-color: #fff; border-radius: 8px; box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); overflow: hidden;">
        <div style="padding: 20px; border-bottom: 1px solid #eee; display: flex; justify-content: space-between; align-items: center;">
            <h1>Calendar</h1>
            <button id="addEventBtn" style="background-color: #007bff; color: white; border: none; padding: 10px 15px; border-radius: 5px; cursor: pointer; font-size: 16px;">Add Event</button>
        </div>
        <div id="calendar" style="padding: 20px;">
            </div>
    </div>
    <div id="eventModal" class="modal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.5); justify-content: center; align-items: center; z-index: 1000;">
        <div class="modal-content" style="background-color: #fff; padding: 20px; border-radius: 8px; width: 90%; max-width: 600px;">
            <h2 id="modalTitle">Add New Event</h2>
            <form id="eventDetailsForm">
                <div style="margin-bottom: 15px;">
                    <label for="title" style="display: block; margin-bottom: 5px; font-weight: bold;">Title:</label>
                    <input type="text" id="title" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px;" required>
                </div>
                <div style="margin-bottom: 15px;">
                    <label for="start_time" style="display: block; margin-bottom: 5px; font-weight: bold;">Start Time:</label>
                    <input type="datetime-local" id="start_time" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px;" required>
                </div>
                <div style="margin-bottom: 15px;">
                    <label for="end_time" style="display: block; margin-bottom: 5px; font-weight: bold;">End Time:</label>
                    <input type="datetime-local" id="end_time" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px;">
                </div>
                <div style="margin-bottom: 20px;">
                    <label for="description" style="display: block; margin-bottom: 5px; font-weight: bold;">Description:</label>
                    <textarea id="description" style="width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 4px; min-height: 80px;"></textarea>
                </div>
                <div style="display: flex; justify-content: flex-end;">
                    <button type="button" id="closeModalBtn" style="background-color: #6c757d; color: white; border: none; padding: 10px 15px; border-radius: 5px; cursor: pointer; font-size: 16px; margin-left: 10px;">Cancel</button>
                    <button type="submit" id="saveEventBtn" style="background-color: #28a745; color: white; border: none; padding: 10px 15px; border-radius: 5px; cursor: pointer; font-size: 16px;">Save Event</button>
                    <button type="button" id="deleteEventBtn" style="background-color: #dc3545; color: white; border: none; padding: 10px 15px; border-radius: 5px; cursor: pointer; font-size: 16px; margin-left: 10px; display: none;">Delete Event</button>
                </div>
            </form>
        </div>
    </div>
</div>

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.10.2/fullcalendar.min.css" />
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/fullcalendar/3.10.2/fullcalendar.min.js"></script>

<script type="module">
    import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

    const CALENDAR_API = `${pythonURI}/calendar`;
    let calendar;
    let currentEventId = null;

    // Function to fetch and display events
    async function loadEvents() {
        try {
            const events = await getEvents(1); // Replace with dynamic user ID
            calendar.fullCalendar('removeEvents');
            calendar.fullCalendar('addEventSource', events);
        } catch (error) {
            alert(`Error loading events: ${error.message}`);
        }
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

    // Initialize FullCalendar
    $(document).ready(function() {
        const calendarElement = $('#calendar');
        calendar = calendarElement.fullCalendar({
            header: {
                left: 'prev,next today',
                center: 'title',
                right: 'dayGridMonth,timeGridWeek,timeGridDay,listWeek'
            },
            selectable: true,
            select: function(start, end) {
                currentEventId = null;
                $('#modalTitle').text('Add New Event');
                $('#deleteEventBtn').hide();
                $('#eventForm').show();
                $('#start_time').val(moment(start).format('YYYY-MM-DDTHH:mm'));
                $('#end_time').val(moment(end).format('YYYY-MM-DDTHH:mm'));
                $('#eventModal').fadeIn();
            },
            eventClick: function(calEvent) {
                currentEventId = calEvent.id;
                $('#modalTitle').text('Edit Event');
                $('#deleteEventBtn').show();
                $('#eventForm').show();
                $('#title').val(calEvent.title);
                $('#start_time').val(moment(calEvent.start).format('YYYY-MM-DDTHH:mm'));
                $('#end_time').val(calEvent.end ? moment(calEvent.end).format('YYYY-MM-DDTHH:mm') : '');
                $('#description').val(calEvent.description);
                $('#eventModal').fadeIn();
            },
            events: async (fetchInfo, successCallback, failureCallback) => {
                try {
                    const events = await getEvents(1); // Replace with dynamic user ID
                    successCallback(events);
                } catch (error) {
                    failureCallback(error);
                }
            },
            editable: true,
            eventDrop: async function(event, delta, revertFunc) {
                try {
                    await updateEvent(event.id, {
                        start_time: moment(event.start).format('YYYY-MM-DDTHH:mm'),
                        end_time: event.end ? moment(event.end).format('YYYY-MM-DDTHH:mm') : ''
                    });
                    alert('Event moved successfully!');
                } catch (error) {
                    alert(`Error moving event: ${error.message}`);
                    revertFunc();
                }
            },
            eventResize: async function(event, delta, revertFunc) {
                try {
                    await updateEvent(event.id, {
                        start_time: moment(event.start).format('YYYY-MM-DDTHH:mm'),
                        end_time: moment(event.end).format('YYYY-MM-DDTHH:mm')
                    });
                    alert('Event resized successfully!');
                } catch (error) {
                    alert(`Error resizing event: ${error.message}`);
                    revertFunc();
                }
            }
        });

        // Load events on page load
        loadEvents();

        // Handle Add Event button click
        $('#addEventBtn').on('click', function() {
            currentEventId = null;
            $('#modalTitle').text('Add New Event');
            $('#deleteEventBtn').hide();
            $('#eventForm').show();
            $('#eventModal').fadeIn();
            $('#eventDetailsForm')[0].reset();
        });

        // Handle Close Modal button click
        $('#closeModalBtn').on('click', function() {
            $('#eventModal').fadeOut();
            $('#eventDetailsForm')[0].reset();
            currentEventId = null;
        });

        // Handle form submission for saving/updating event
        $('#eventDetailsForm').on('submit', async function(e) {
            e.preventDefault();

            const title = $('#title').val();
            const start_time = $('#start_time').val();
            const end_time = $('#end_time').val();
            const description = $('#description').val();
            const eventData = { title, start_time, end_time, description, user_id: 1 }; // Adjust user_id dynamically

            try {
                if (currentEventId) {
                    await updateEvent(currentEventId, eventData);
                    alert('Event updated successfully!');
                } else {
                    await createEvent(eventData);
                    alert('Event created successfully!');
                }
                $('#eventModal').fadeOut();
                $('#eventDetailsForm')[0].reset();
                loadEvents(); // Reload events to update the calendar
                currentEventId = null;
            } catch (error) {
                alert(`Error saving event: ${error.message}`);
            }
        });

        // Handle Delete Event button click
        $('#deleteEventBtn').on('click', async function() {
            if (currentEventId) {
                if (confirm('Are you sure you want to delete this event?')) {
                    try {
                        await deleteEvent(currentEventId);
                        alert('Event deleted successfully!');
                        $('#eventModal').fadeOut();
                        $('#eventDetailsForm')[0].reset();
                        loadEvents(); // Reload events to update the calendar
                        currentEventId = null;
                    } catch (error) {
                        alert(`Error deleting event: ${error.message}`);
                    }
                }
            }
        });
    });
</script>

<style>
    /* Basic styling for the container and wrapper */
    .calendar-container {
        background-color: #f8f9fa;
        padding: 20px;
    }

    .calendar-wrapper {
        background-color: #fff;
        border-radius: 8px;
        box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        overflow: hidden;
    }

    /* Style for the header */
    .calendar-wrapper h1 {
        margin: 0;
        font-size: 24px;
        color: #333;
    }

    /* Style for buttons */
    .button-container button {
        background-color: #007bff;
        color: white;
        border: none;
        padding: 10px 15px;
        border-radius: 5px;
        cursor: pointer;
        font-size: 16px;
        margin-right: 10px;
    }

    .button-container button:hover {
        background-color: #0056b3;
    }

    /* Style for the modal */
    .modal {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.5);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
    }

    .modal-content {
        background-color: #fff;
        padding: 20px;
        border-radius: 8px;
        width: 90%;
        max-width: 600px;
    }

    .modal-content h2 {
        margin-top: 0;
        color: #333;
        margin-bottom: 15px;
    }

    .modal-content label {
        display: block;
        margin-bottom: 5px;
        font-weight: bold;
        color: #555;
    }

    .modal-content input[type="text"],
    .modal-content input[type="datetime-local"],
    .modal-content textarea {
        width: 100%;
        padding: 10px;
        border: 1px solid #ccc;
        border-radius: 4px;
        margin-bottom: 15px;
        font-size: 16px;
    }

    .modal-content textarea {
        min-height: 100px;
    }

    .modal-content button {
        background-color: #007bff;
        color: white;
        border: none;
        padding: 10px 15px;
        border-radius: 5px;
        cursor: pointer;
        font-size: 16px;
        margin-right: 10px;
    }

    .modal-content button:last-child {
        margin-right: 0;
    }

    .modal-content button:hover {
        opacity: 0.9;
    }

    .modal-content #closeModalBtn {
        background-color: #6c757d;
    }

    .modal-content #deleteEventBtn {
        background-color: #dc3545;
    }

    /* FullCalendar Styles (you might need to adjust based on the theme) */
    .fc-header-toolbar {
        margin-bottom: 1em;
    }

    .fc-day-grid-event .fc-content {
        white-space: normal;
    }
</style>