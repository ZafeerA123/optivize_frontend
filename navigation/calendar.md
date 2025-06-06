---
layout: base
title: Optivize Calendar
description: Product Success Prediction
hide: true
permalink: /Calendar
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Optivize Calendar Dashboard</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
  <link href="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.css" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary: #1a2980;
      --secondary: #26d0ce;
      --accent: #fbb034;
      --dark: #0b1e3b;
      --darker: #162b4d;
      --glass: rgba(255, 255, 255, 0.1);
    }
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, var(--primary), var(--secondary));
      color: var(--accent);
      margin: 0;
      padding: 20px;
      min-height: 100vh;
      overflow-x: hidden;
    }
    /* Gradient background with animation */
    .page-background {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(135deg, var(--dark), var(--darker));
      z-index: -2;
    }
    .gradient-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle at 70% 20%, rgba(43, 83, 158, 0.2), transparent 60%),
                  radial-gradient(circle at 20% 80%, rgba(29, 47, 94, 0.3), transparent 60%);
      animation: gradientMove 20s infinite alternate;
      z-index: -1;
    }
    @keyframes gradientMove {
      0% { background-position: 0% 0%; }
      100% { background-position: 100% 100%; }
    }
    /* Glowing orbs in background */
    .glow-orb {
      position: absolute;
      border-radius: 50%;
      filter: blur(60px);
      opacity: 0.15;
      z-index: 0;
    }
    .glow-orb-1 {
      top: 10%;
      left: 5%;
      width: 300px;
      height: 300px;
      background: radial-gradient(circle, rgba(251, 176, 52, 0.6), rgba(251, 176, 52, 0) 70%);
      animation: float 25s infinite alternate;
    }
    .glow-orb-2 {
      bottom: 10%;
      right: 5%;
      width: 400px;
      height: 400px;
      background: radial-gradient(circle, rgba(66, 99, 176, 0.4), rgba(66, 99, 176, 0) 70%);
      animation: float 30s infinite alternate-reverse;
    }
    .glow-orb-3 {
      top: 50%;
      left: 50%;
      width: 350px;
      height: 350px;
      background: radial-gradient(circle, rgba(251, 176, 52, 0.3), rgba(66, 99, 176, 0.2), rgba(66, 99, 176, 0) 70%);
      animation: float 35s infinite alternate;
    }
    @keyframes float {
      0% { transform: translate(0, 0) scale(1); }
      50% { transform: translate(50px, -30px) scale(1.1); }
      100% { transform: translate(-30px, 50px) scale(0.9); }
    }
    /* Main container */
    .container {
      max-width: 1400px;
      margin: 0 auto;
      background: var(--glass);
      backdrop-filter: blur(10px);
      border-radius: 16px;
      box-shadow: 0 8px 40px rgba(0, 0, 0, 0.2);
      padding: 30px;
      min-height: calc(100vh - 40px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }
    /* Header */
    .header {
      text-align: center;
      margin-bottom: 30px;
      padding-bottom: 20px;
      border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    }
    .header h1 {
      background: linear-gradient(135deg, #ffdd00, #fbb034);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      font-size: 2.8rem;
      font-weight: 700;
      margin-bottom: 10px;
    }
    .header p {
      color: rgba(255, 255, 255, 0.8);
      font-size: 1.2rem;
    }
    /* Action buttons */
    .action-buttons {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-bottom: 30px;
      flex-wrap: wrap;
    }
    .action-btn {
      background: linear-gradient(135deg, rgba(255, 221, 0, 0.2), rgba(251, 176, 52, 0.2));
      border: 1px solid rgba(251, 176, 52, 0.3);
      color: #ffdd00;
      padding: 12px 24px;
      border-radius: 50px;
      font-weight: 600;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .action-btn:hover {
      background: linear-gradient(135deg, rgba(255, 221, 0, 0.3), rgba(251, 176, 52, 0.3));
      transform: translateY(-3px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }
    /* Calendar styling */
    #calendar {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 12px;
      padding: 20px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      margin-bottom: 30px;
      height: 600px;
    }
    .fc-toolbar {
      color: white !important;
      padding: 15px 0;
    }
    .fc-toolbar-title {
      color: white !important;
      font-size: 1.6rem !important;
      font-weight: 600;
    }
    .fc-button {
      background: rgba(255, 255, 255, 0.1) !important;
      border: 1px solid rgba(255, 255, 255, 0.2) !important;
      color: white !important;
      transition: all 0.3s ease !important;
    }
    .fc-button:hover {
      background: rgba(255, 255, 255, 0.2) !important;
    }
    .fc-event {
      background: linear-gradient(135deg, #ffdd00, #fbb034) !important;
      border: none !important;
      color: #333 !important;
      font-weight: 600;
      padding: 3px 6px;
      border-radius: 4px;
    }
    /* Data tables */
    .data-section {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 12px;
      padding: 25px;
      border: 1px solid rgba(255, 255, 255, 0.1);
      margin-bottom: 30px;
    }
    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      padding-bottom: 15px;
      border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    }
    .section-header h3 {
      color: #fbb034;
      font-weight: 600;
      margin: 0;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .table-responsive {
      border-radius: 8px;
      overflow: hidden;
    }
    .table {
      background: rgba(255, 255, 255, 0.03);
      color: rgba(255, 255, 255, 0.9);
      margin-bottom: 0;
    }
    .table th {
      background: rgba(251, 176, 52, 0.15);
      color: #fbb034;
      font-weight: 600;
      padding: 15px 12px;
    }
    .table td {
      padding: 12px;
      vertical-align: middle;
      border-color: rgba(255, 255, 255, 0.1);
    }
    .table tr:nth-child(even) {
      background: rgba(255, 255, 255, 0.03);
    }
    .table tr:hover {
      background: rgba(251, 176, 52, 0.1);
    }
    /* Modal styling */
    .modal-content {
      background: linear-gradient(135deg, #0b1e3b, #162b4d);
      border-radius: 16px;
      border: 1px solid rgba(255, 255, 255, 0.2);
      color: rgba(255, 255, 255, 0.9);
    }
    .modal-header {
      border-bottom: 1px solid rgba(255, 255, 255, 0.2);
    }
    .modal-title {
      color: #fbb034;
      font-weight: 600;
    }
    .btn-close {
      filter: invert(1);
    }
    .form-control, .form-select {
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid rgba(255, 255, 255, 0.1);
      color: white;
      padding: 10px 15px;
      border-radius: 8px;
    }
    .form-control:focus, .form-select:focus {
      background: rgba(255, 255, 255, 0.08);
      border-color: rgba(251, 176, 52, 0.4);
      box-shadow: 0 0 0 0.25rem rgba(251, 176, 52, 0.25);
      color: white;
    }
    .form-control::placeholder {
      color: rgba(255, 255, 255, 0.6) !important;
    }
    .submit-btn {
      background: linear-gradient(135deg, #ffdd00, #fbb034);
      border: none;
      color: #333;
      font-weight: 600;
      padding: 10px 25px;
      border-radius: 8px;
      transition: all 0.3s ease;
    }
    .submit-btn:hover {
      background: linear-gradient(135deg, #fbb034, #ffdd00);
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
    }
    /* Responsive */
    @media (max-width: 768px) {
      .action-buttons {
        flex-direction: column;
        align-items: center;
      }
      .action-btn {
        width: 100%;
        justify-content: center;
      }
      #calendar {
        height: 400px;
      }
    }
  </style>
</head>
<body>
  <div class="page-background"></div>
  <div class="gradient-overlay"></div>
  <div class="glow-orb glow-orb-1"></div>
  <div class="glow-orb glow-orb-2"></div>
  <div class="glow-orb glow-orb-3"></div>

  <div class="container">
    <!-- Header -->
    <div class="header">
      <h1>Optivize Calendar Dashboard</h1>
      <p>Product Success Prediction & Operations Management</p>
    </div>
    <!-- Action Buttons -->
    <div class="action-buttons">
      <button type="button" class="btn action-btn" data-bs-toggle="modal" data-bs-target="#eventModal">
        <i class="fas fa-calendar-plus"></i> Add Event
      </button>
      <button type="button" class="btn action-btn" data-bs-toggle="modal" data-bs-target="#shipmentModal">
        <i class="fas fa-truck"></i> Add Shipment
      </button>
      <button type="button" class="btn action-btn" data-bs-toggle="modal" data-bs-target="#taskModal">
        <i class="fas fa-tasks"></i> Add Task
      </button>
      <button type="button" class="btn action-btn" data-bs-toggle="modal" data-bs-target="#employeeModal">
        <i class="fas fa-users"></i> Manage Employees
      </button>
      <button type="button" class="btn action-btn" id="connectCalendarBtn">
        <i class="fab fa-google me-2"></i> Connect Calendar
      </button>
    </div>
    <!-- Calendar -->
    <div id="calendar"></div>
    <!-- Data Sections -->
    <div class="data-section">
      <div class="section-header">
        <h3><i class="fas fa-calendar-day"></i> Upcoming Events</h3>
        <span class="badge bg-warning">5 events</span>
      </div>
      <div class="table-responsive">
        <table class="table table-hover">
          <thead>
            <tr>
              <th>Event</th>
              <th>Location</th>
              <th>Start Time</th>
              <th>End Time</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><i class="fas fa-bullhorn me-2"></i> Product Launch</td>
              <td>Conference Room A</td>
              <td>2025-05-21 10:00 AM</td>
              <td>2025-05-21 12:00 PM</td>
              <td><span class="badge bg-success">Confirmed</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-chart-line me-2"></i> Quarterly Review</td>
              <td>Main Office</td>
              <td>2025-05-25 09:00 AM</td>
              <td>2025-05-25 11:00 AM</td>
              <td><span class="badge bg-warning">Pending</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-lightbulb me-2"></i> Innovation Workshop</td>
              <td>Creative Space</td>
              <td>2025-05-28 01:00 PM</td>
              <td>2025-05-28 04:00 PM</td>
              <td><span class="badge bg-success">Confirmed</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-users me-2"></i> Team Building</td>
              <td>Outdoor Area</td>
              <td>2025-06-02 10:00 AM</td>
              <td>2025-06-02 03:00 PM</td>
              <td><span class="badge bg-info">Scheduled</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-gift me-2"></i> Anniversary Celebration</td>
              <td>Grand Hall</td>
              <td>2025-06-10 06:00 PM</td>
              <td>2025-06-10 10:00 PM</td>
              <td><span class="badge bg-primary">Planned</span></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="data-section">
      <div class="section-header">
        <h3><i class="fas fa-shipping-fast"></i> Recent Shipments</h3>
        <span class="badge bg-warning">3 shipments</span>
      </div>
      <div class="table-responsive">
        <table class="table table-hover">
          <thead>
            <tr>
              <th>Inventory</th>
              <th>Quantity</th>
              <th>Transport Method</th>
              <th>Shipment Time</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><i class="fas fa-box me-2"></i> Cookie Dough</td>
              <td>500 units</td>
              <td>Refrigerated Truck</td>
              <td>2025-05-20 08:00 AM</td>
              <td><span class="badge bg-success">Delivered</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-box me-2"></i> Packaging Materials</td>
              <td>2000 units</td>
              <td>Standard Truck</td>
              <td>2025-05-22 10:30 AM</td>
              <td><span class="badge bg-primary">In Transit</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-box me-2"></i> Promotional Items</td>
              <td>1500 units</td>
              <td>Air Freight</td>
              <td>2025-05-24 02:00 PM</td>
              <td><span class="badge bg-warning">Processing</span></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="data-section">
      <div class="section-header">
        <h3><i class="fas fa-tasks"></i> Employee Tasks</h3>
        <span class="badge bg-warning">4 tasks</span>
      </div>
      <div class="table-responsive">
        <table class="table table-hover">
          <thead>
            <tr>
              <th>Employee</th>
              <th>Task</th>
              <th>Due Date</th>
              <th>Priority</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><i class="fas fa-user me-2"></i> Sarah Johnson</td>
              <td>Prepare launch presentation</td>
              <td>2025-05-20</td>
              <td><span class="badge bg-danger">High</span></td>
              <td><span class="badge bg-success">Completed</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-user me-2"></i> Michael Chen</td>
              <td>Finalize product packaging</td>
              <td>2025-05-22</td>
              <td><span class="badge bg-danger">High</span></td>
              <td><span class="badge bg-primary">In Progress</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-user me-2"></i> Emma Rodriguez</td>
              <td>Coordinate media coverage</td>
              <td>2025-05-25</td>
              <td><span class="badge bg-warning">Medium</span></td>
              <td><span class="badge bg-primary">In Progress</span></td>
            </tr>
            <tr>
              <td><i class="fas fa-user me-2"></i> David Wilson</td>
              <td>Prepare inventory report</td>
              <td>2025-05-28</td>
              <td><span class="badge bg-info">Low</span></td>
              <td><span class="badge bg-secondary">Not Started</span></td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
  
  <!-- Event Modal -->
  <div class="modal fade" id="eventModal" tabindex="-1" aria-labelledby="eventModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="eventModalLabel"><i class="fas fa-calendar-plus me-2"></i> Add New Event</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form id="eventForm">
            <div class="row g-3 mb-4">
              <div class="col-md-6">
                <label class="form-label fw-bold">Title</label>
                <input type="text" name="title" class="form-control" placeholder="Enter event title" required>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">Location</label>
                <input type="text" name="location" class="form-control" placeholder="Enter location" required>
              </div>
              <div class="col-md-12">
                <label class="form-label fw-bold">Description</label>
                <textarea name="description" class="form-control" placeholder="Enter event description" rows="3" required></textarea>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">Start Time</label>
                <input type="datetime-local" name="start_time" class="form-control" required>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">End Time</label>
                <input type="datetime-local" name="end_time" class="form-control" required>
              </div>
              <div class="col-md-12">
                <label class="form-label fw-bold">Category</label>
                <select class="form-select" name="category" required>
                  <option value="">Select category</option>
                  <option value="Meeting">Meeting</option>
                  <option value="Workshop">Workshop</option>
                  <option value="Conference">Conference</option>
                  <option value="Social">Social Event</option>
                  <option value="Other">Other</option>
                </select>
              </div>
            </div>
            <div class="text-end">
              <button type="button" class="btn btn-secondary me-2" data-bs-dismiss="modal">Cancel</button>
              <button type="submit" class="btn submit-btn">Submit Event</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Shipment Modal -->
  <div class="modal fade" id="shipmentModal" tabindex="-1" aria-labelledby="shipmentModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="shipmentModalLabel"><i class="fas fa-truck me-2"></i> Add New Shipment</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form id="shipmentForm">
            <div class="row g-3 mb-4">
              <div class="col-md-12">
                <label class="form-label fw-bold">Inventory Item</label>
                <input type="text" name="inventory" class="form-control" placeholder="e.g., Cookie Dough" required>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">Quantity</label>
                <input type="number" name="amount" class="form-control" placeholder="e.g., 100" required>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">Transport Method</label>
                <select class="form-select" name="transport_method" required>
                  <option value="">Select method</option>
                  <option value="Truck">Truck</option>
                  <option value="Air Freight">Air Freight</option>
                  <option value="Ship">Ship</option>
                  <option value="Rail">Rail</option>
                </select>
              </div>
              <div class="col-md-12">
                <label class="form-label fw-bold">Shipment Time</label>
                <input type="datetime-local" name="shipment_time" class="form-control" required>
              </div>
              <div class="col-md-12">
                <label class="form-label fw-bold">Destination</label>
                <input type="text" name="destination" class="form-control" placeholder="Enter destination" required>
              </div>
            </div>
            <div class="text-end">
              <button type="button" class="btn btn-secondary me-2" data-bs-dismiss="modal">Cancel</button>
              <button type="submit" class="btn submit-btn">Submit Shipment</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Task Modal -->
  <div class="modal fade" id="taskModal" tabindex="-1" aria-labelledby="taskModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="taskModalLabel"><i class="fas fa-tasks me-2"></i> Add New Task</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form id="taskForm">
            <div class="row g-3 mb-4">
              <div class="col-md-12">
                <label class="form-label fw-bold">Employee</label>
                <select class="form-select" name="employee" required>
                  <option value="">Select employee</option>
                  <option value="Sarah Johnson">Sarah Johnson</option>
                  <option value="Michael Chen">Michael Chen</option>
                  <option value="Emma Rodriguez">Emma Rodriguez</option>
                  <option value="David Wilson">David Wilson</option>
                  <option value="Alex Thompson">Alex Thompson</option>
                </select>
              </div>
              <div class="col-md-12">
                <label class="form-label fw-bold">Task Description</label>
                <textarea name="description" class="form-control" placeholder="Enter task description" rows="3" required></textarea>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">Due Date</label>
                <input type="date" name="due_date" class="form-control" required>
              </div>
              <div class="col-md-6">
                <label class="form-label fw-bold">Priority</label>
                <select class="form-select" name="priority" required>
                  <option value="">Select priority</option>
                  <option value="High">High</option>
                  <option value="Medium">Medium</option>
                  <option value="Low">Low</option>
                </select>
              </div>
            </div>
            <div class="text-end">
              <button type="button" class="btn btn-secondary me-2" data-bs-dismiss="modal">Cancel</button>
              <button type="submit" class="btn submit-btn">Add Task</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Employee Modal -->
  <div class="modal fade" id="employeeModal" tabindex="-1" aria-labelledby="employeeModalLabel" aria-hidden="true">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="employeeModalLabel"><i class="fas fa-users me-2"></i> Manage Employees</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <div class="table-responsive">
            <table class="table table-hover">
              <thead>
                <tr>
                  <th>Name</th>
                  <th>Role</th>
                  <th>Email</th>
                  <th>Department</th>
                  <th>Status</th>
                  <th>Actions</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td><i class="fas fa-user me-2"></i> Sarah Johnson</td>
                  <td>Product Manager</td>
                  <td>sarah@optivize.com</td>
                  <td>Product</td>
                  <td><span class="badge bg-success">Active</span></td>
                  <td>
                    <button class="btn btn-sm btn-warning me-1"><i class="fas fa-edit"></i></button>
                    <button class="btn btn-sm btn-danger"><i class="fas fa-trash"></i></button>
                  </td>
                </tr>
                <tr>
                  <td><i class="fas fa-user me-2"></i> Michael Chen</td>
                  <td>Design Lead</td>
                  <td>michael@optivize.com</td>
                  <td>Design</td>
                  <td><span class="badge bg-success">Active</span></td>
                  <td>
                    <button class="btn btn-sm btn-warning me-1"><i class="fas fa-edit"></i></button>
                    <button class="btn btn-sm btn-danger"><i class="fas fa-trash"></i></button>
                  </td>
                </tr>
                <tr>
                  <td><i class="fas fa-user me-2"></i> Emma Rodriguez</td>
                  <td>Marketing Specialist</td>
                  <td>emma@optivize.com</td>
                  <td>Marketing</td>
                  <td><span class="badge bg-success">Active</span></td>
                  <td>
                    <button class="btn btn-sm btn-warning me-1"><i class="fas fa-edit"></i></button>
                    <button class="btn btn-sm btn-danger"><i class="fas fa-trash"></i></button>
                  </td>
                </tr>
                <tr>
                  <td><i class="fas fa-user me-2"></i> David Wilson</td>
                  <td>Operations Manager</td>
                  <td>david@optivize.com</td>
                  <td>Operations</td>
                  <td><span class="badge bg-success">Active</span></td>
                  <td>
                    <button class="btn btn-sm btn-warning me-1"><i class="fas fa-edit"></i></button>
                    <button class="btn btn-sm btn-danger"><i class="fas fa-trash"></i></button>
                  </td>
                </tr>
                <tr>
                  <td><i class="fas fa-user me-2"></i> Alex Thompson</td>
                  <td>Developer</td>
                  <td>alex@optivize.com</td>
                  <td>Engineering</td>
                  <td><span class="badge bg-info">On Leave</span></td>
                  <td>
                    <button class="btn btn-sm btn-warning me-1"><i class="fas fa-edit"></i></button>
                    <button class="btn btn-sm btn-danger"><i class="fas fa-trash"></i></button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
          <div class="text-end mt-4">
            <button type="button" class="btn btn-secondary me-2" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary">Add New Employee</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Scripts -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/fullcalendar@6.1.8/index.global.min.js"></script>
  <script>
document.addEventListener('DOMContentLoaded', function() {
  // Initialize data stores in localStorage if they don't exist
  if (!localStorage.getItem('optivizeEvents')) {
    localStorage.setItem('optivizeEvents', JSON.stringify([]));
  }
  if (!localStorage.getItem('optivizeGoogleEvents')) {
    localStorage.setItem('optivizeGoogleEvents', JSON.stringify([]));
  }
  if (!localStorage.getItem('optivizeShipments')) {
    localStorage.setItem('optivizeShipments', JSON.stringify([]));
  }
  if (!localStorage.getItem('optivizeTasks')) {
    localStorage.setItem('optivizeTasks', JSON.stringify([]));
  }
// Load data sections from localStorage
  function loadDataSections() {
    // Static events data
    const staticEvents = [
      {
        title: 'Product Launch',
        location: 'Conference Room A',
        start: '2025-05-21T10:00:00',
        end: '2025-05-21T12:00:00',
        status: 'Confirmed'
      },
      {
        title: 'Quarterly Review',
        location: 'Main Office',
        start: '2025-05-25T09:00:00',
        end: '2025-05-25T11:00:00',
        status: 'Pending'
      },
      {
        title: 'Innovation Workshop',
        location: 'Creative Space',
        start: '2025-05-28T13:00:00',
        end: '2025-05-28T16:00:00',
        status: 'Confirmed'
      },
      {
        title: 'Team Building',
        location: 'Outdoor Area',
        start: '2025-06-02T10:00:00',
        end: '2025-06-02T15:00:00',
        status: 'Scheduled'
      },
      {
        title: 'Anniversary Celebration',
        location: 'Grand Hall',
        start: '2025-06-10T18:00:00',
        end: '2025-06-10T22:00:00',
        status: 'Planned'
      }
    ];

    const staticShipments = [
      {
        inventory: 'Cookie Dough',
        amount: '500',
        transport_method: 'Refrigerated Truck',
        shipment_time: '2025-05-20T08:00:00',
        status: 'Delivered'
      },
      {
        inventory: 'Packaging Materials',
        amount: '2000',
        transport_method: 'Standard Truck',
        shipment_time: '2025-05-22T10:30:00',
        status: 'In Transit'
      },
      {
        inventory: 'Promotional Items',
        amount: '1500',
        transport_method: 'Air Freight',
        shipment_time: '2025-05-24T14:00:00',
        status: 'Processing'
      }
    ];

    const staticTasks = [
      {
        employee: 'Sarah Johnson',
        description: 'Prepare launch presentation',
        due_date: '2025-05-20',
        priority: 'High',
        status: 'Completed'
      },
      {
        employee: 'Michael Chen',
        description: 'Finalize product packaging',
        due_date: '2025-05-22',
        priority: 'High',
        status: 'In Progress'
      },
      {
        employee: 'Emma Rodriguez',
        description: 'Coordinate media coverage',
        due_date: '2025-05-25',
        priority: 'Medium',
        status: 'In Progress'
      },
      {
        employee: 'David Wilson',
        description: 'Prepare inventory report',
        due_date: '2025-05-28',
        priority: 'Low',
        status: 'Not Started'
      }
    ];

    // Load Events
    const events = JSON.parse(localStorage.getItem('optivizeEvents')) || [];
    const upcomingEventsTable = document.querySelector('.data-section .table tbody');
    if (upcomingEventsTable) {
      upcomingEventsTable.innerHTML = ''; // Clear existing rows
      
      // Add static events
      staticEvents.forEach(event => {
        const newRow = document.createElement('tr');
        newRow.innerHTML = `
          <td><i class="fas fa-calendar me-2"></i> ${event.title}</td>
          <td>${event.location}</td>
          <td>${new Date(event.start).toLocaleString()}</td>
          <td>${new Date(event.end).toLocaleString()}</td>
          <td><span class="badge bg-${getStatusColor(event.status)}">${event.status}</span></td>
        `;
        upcomingEventsTable.appendChild(newRow);
      });

      // Add dynamic events
      events.forEach(event => {
        if (!event.extendedProps?.type) { // Only show regular events, not shipments or tasks
          const newRow = document.createElement('tr');
          newRow.innerHTML = `
            <td><i class="fas fa-calendar me-2"></i> ${event.title}</td>
            <td>${event.extendedProps?.location || 'N/A'}</td>
            <td>${new Date(event.start).toLocaleString()}</td>
            <td>${event.end ? new Date(event.end).toLocaleString() : 'N/A'}</td>
            <td><span class="badge bg-success">Confirmed</span></td>
          `;
          upcomingEventsTable.appendChild(newRow);
        }
      });
      // Update events count badge
      const eventsBadge = document.querySelector('.data-section .section-header .badge');
      if (eventsBadge) {
        eventsBadge.textContent = `${staticEvents.length + events.filter(e => !e.extendedProps?.type).length} events`;
      }
    }

    // Load Shipments
    const shipments = JSON.parse(localStorage.getItem('optivizeShipments')) || [];
    const shipmentsTable = document.querySelectorAll('.data-section .table tbody')[1];
    if (shipmentsTable) {
      shipmentsTable.innerHTML = ''; // Clear existing rows
      
      // Add static shipments
      staticShipments.forEach(shipment => {
        const newRow = document.createElement('tr');
        newRow.innerHTML = `
          <td><i class="fas fa-box me-2"></i> ${shipment.inventory}</td>
          <td>${shipment.amount} units</td>
          <td>${shipment.transport_method}</td>
          <td>${new Date(shipment.shipment_time).toLocaleString()}</td>
          <td><span class="badge bg-${getStatusColor(shipment.status)}">${shipment.status}</span></td>
        `;
        shipmentsTable.appendChild(newRow);
      });

      // Add dynamic shipments
      shipments.forEach(shipment => {
        const newRow = document.createElement('tr');
        newRow.innerHTML = `
          <td><i class="fas fa-box me-2"></i> ${shipment.inventory}</td>
          <td>${shipment.amount} units</td>
          <td>${shipment.transport_method}</td>
          <td>${new Date(shipment.shipment_time).toLocaleString()}</td>
          <td><span class="badge bg-primary">Processing</span></td>
        `;
        shipmentsTable.appendChild(newRow);
      });
      // Update shipments count badge
      const shipmentsBadge = document.querySelectorAll('.data-section .section-header .badge')[1];
      if (shipmentsBadge) {
        shipmentsBadge.textContent = `${staticShipments.length + shipments.length} shipments`;
      }
    }

    // Load Tasks
    const tasks = JSON.parse(localStorage.getItem('optivizeTasks')) || [];
    const tasksTable = document.querySelectorAll('.data-section .table tbody')[2];
    if (tasksTable) {
      tasksTable.innerHTML = ''; // Clear existing rows
      
      // Add static tasks
      staticTasks.forEach(task => {
        const newRow = document.createElement('tr');
        newRow.innerHTML = `
          <td><i class="fas fa-user me-2"></i> ${task.employee}</td>
          <td>${task.description}</td>
          <td>${task.due_date}</td>
          <td><span class="badge bg-${getPriorityColor(task.priority)}">${task.priority}</span></td>
          <td><span class="badge bg-${getStatusColor(task.status)}">${task.status}</span></td>
        `;
        tasksTable.appendChild(newRow);
      });

      // Add dynamic tasks
      tasks.forEach(task => {
        const newRow = document.createElement('tr');
        newRow.innerHTML = `
          <td><i class="fas fa-user me-2"></i> ${task.employee}</td>
          <td>${task.description}</td>
          <td>${task.due_date}</td>
          <td><span class="badge bg-${getPriorityColor(task.priority)}">${task.priority}</span></td>
          <td><span class="badge bg-secondary">Not Started</span></td>
        `;
        tasksTable.appendChild(newRow);
      });
      // Update tasks count badge
      const tasksBadge = document.querySelectorAll('.data-section .section-header .badge')[2];
      if (tasksBadge) {
        tasksBadge.textContent = `${staticTasks.length + tasks.length} tasks`;
      }
    }
  }

  // Call loadDataSections when page loads
  loadDataSections();

  // Initialize calendar
  var calendarEl = document.getElementById('calendar');
  var calendar = new FullCalendar.Calendar(calendarEl, {
    initialView: 'dayGridMonth',
    headerToolbar: {
      left: 'prev,next today',
      center: 'title',
      right: 'dayGridMonth,timeGridWeek,timeGridDay'
    },
    events: function(fetchInfo, successCallback, failureCallback) {
      try {
        const staticEvents = [
          {
            title: 'Product Launch',
            start: '2025-05-21T10:00:00',
            end: '2025-05-21T12:00:00',
            backgroundColor: '#fbb034',
            borderColor: '#fbb034'
          },
          {
            title: 'Team Meeting',
            start: '2025-05-23T14:00:00',
            end: '2025-05-23T15:30:00'
          },
          {
            title: 'Shipment Arrival',
            start: '2025-05-24T09:00:00',
            backgroundColor: '#4a90e2',
            borderColor: '#4a90e2'
          },
          {
            title: 'Quarterly Review',
            start: '2025-05-25T09:00:00',
            end: '2025-05-25T11:00:00'
          },
          {
            title: 'Innovation Workshop',
            start: '2025-05-28T13:00:00',
            end: '2025-05-28T16:00:00'
          },
          {
            title: 'Team Building',
            start: '2025-06-02T10:00:00',
            end: '2025-06-02T15:00:00'
          }
        ];
        const localEvents = JSON.parse(localStorage.getItem('optivizeEvents')) || [];
        const googleEvents = JSON.parse(localStorage.getItem('optivizeGoogleEvents')) || [];
        successCallback([...staticEvents, ...localEvents, ...googleEvents]);
      } catch (error) {
        console.error('Error loading events:', error);
        successCallback([]);
      }
    },
    eventClick: function(info) {
      showEventDetails(info.event);
    }
  });
  calendar.render();

  // Update the event form submission to use loadDataSections
  document.getElementById('eventForm')?.addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = {
      id: Date.now().toString(),
      title: this.elements.title.value,
      description: this.elements.description.value,
      category: this.elements.category.value,
      date: this.elements.start_time.value.split('T')[0],
      start_time: this.elements.start_time.value,
      end_time: this.elements.end_time.value,
      location: this.elements.location.value
    };
    try {
      // Get current events
      const events = JSON.parse(localStorage.getItem('optivizeEvents')) || [];
      // Add new event
      events.push({
        id: formData.id,
        title: formData.title,
        start: formData.start_time,
        end: formData.end_time,
        description: formData.description,
        backgroundColor: '#28a745',
        borderColor: '#28a745',
        extendedProps: {
          location: formData.location,
          category: formData.category
        }
      });
      // Save back to localStorage
      localStorage.setItem('optivizeEvents', JSON.stringify(events));
      
      showAlert('Event created successfully!', 'success');
      calendar.refetchEvents();
      loadDataSections(); // Reload all data sections
      this.reset();
      bootstrap.Modal.getInstance(document.getElementById('eventModal')).hide();
    } catch (error) {
      console.error('Error saving event:', error);
      showAlert('Failed to create event', 'danger');
    }
  });

  // Update the shipment form submission to use loadDataSections
  document.getElementById('shipmentForm')?.addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = {
      id: Date.now().toString(),
      inventory: this.elements.inventory.value,
      amount: this.elements.amount.value,
      transport_method: this.elements.transport_method.value,
      shipment_time: this.elements.shipment_time.value,
      destination: this.elements.destination.value
    };
    const shipments = JSON.parse(localStorage.getItem('optivizeShipments')) || [];
    shipments.push(formData);
    localStorage.setItem('optivizeShipments', JSON.stringify(shipments));

    // Add to calendar events
    const events = JSON.parse(localStorage.getItem('optivizeEvents')) || [];
    events.push({
      id: `shipment-${formData.id}`,
      title: `Shipment: ${formData.inventory}`,
      start: formData.shipment_time,
      backgroundColor: '#4a90e2',
      borderColor: '#4a90e2',
      extendedProps: {
        type: 'shipment',
        amount: formData.amount,
        transport_method: formData.transport_method,
        destination: formData.destination
      }
    });
    localStorage.setItem('optivizeEvents', JSON.stringify(events));

    showAlert('Shipment submitted successfully!', 'success');
    this.reset();
    bootstrap.Modal.getInstance(document.getElementById('shipmentModal')).hide();
    calendar.refetchEvents();
    loadDataSections(); // Reload all data sections
  });

  // Update the task form submission to use loadDataSections
  document.getElementById('taskForm')?.addEventListener('submit', function(e) {
    e.preventDefault();
    const formData = {
      id: Date.now().toString(),
      employee: this.elements.employee.value,
      description: this.elements.description.value,
      due_date: this.elements.due_date.value,
      priority: this.elements.priority.value
    };
    const tasks = JSON.parse(localStorage.getItem('optivizeTasks')) || [];
    tasks.push(formData);
    localStorage.setItem('optivizeTasks', JSON.stringify(tasks));

    // Add to calendar events
    const events = JSON.parse(localStorage.getItem('optivizeEvents')) || [];
    events.push({
      id: `task-${formData.id}`,
      title: `Task: ${formData.description}`,
      start: formData.due_date,
      backgroundColor: '#fbb034',
      borderColor: '#fbb034',
      extendedProps: {
        type: 'task',
        employee: formData.employee,
        priority: formData.priority
      }
    });
    localStorage.setItem('optivizeEvents', JSON.stringify(events));

    showAlert('Task added successfully!', 'success');
    this.reset();
    bootstrap.Modal.getInstance(document.getElementById('taskModal')).hide();
    calendar.refetchEvents();
    loadDataSections(); // Reload all data sections
  });

  // Show event details popup
  function showEventDetails(event) {
    const description = event.extendedProps?.description || 'No description';
    const start = event.start ? event.start.toLocaleString() : 'No start time';
    const end = event.end ? event.end.toLocaleString() : 'No end time';
    alert(`Event: ${event.title}\n\nDescription: ${description}\n\nStart: ${start}\nEnd: ${end}`);
  }

  // Alert helper
  function showAlert(message, type) {
    const alertDiv = document.createElement('div');
    alertDiv.className = `alert alert-${type} fixed-top w-50 mx-auto mt-2 text-center`;
    alertDiv.textContent = message;
    document.body.appendChild(alertDiv);
    setTimeout(() => {
      alertDiv.remove();
    }, 3000);
  }

  // Google Calendar Simulation
  function checkCalendarConnection() {
    // For localStorage implementation, we'll simulate being always connected
    updateConnectionUI(true);
  }
  function updateConnectionUI(isConnected) {
    const connectBtn = document.getElementById('connectCalendarBtn');
    if (connectBtn) connectBtn.style.display = isConnected ? 'none' : 'block';
  }
  function connectGoogleCalendar() {
    // Simulate Google connection by adding some sample events
    const sampleGoogleEvents = [
      {
        id: 'google-1',
        title: 'Google Meeting',
        start: '2025-05-26T10:00:00',
        end: '2025-05-26T11:00:00',
        description: 'Scheduled via Google Calendar',
        backgroundColor: '#4285F4',
        borderColor: '#4285F4'
      },
      {
        id: 'google-2',
        title: 'Team Sync',
        start: '2025-05-29T15:00:00',
        end: '2025-05-29T16:00:00',
        description: 'Weekly team sync',
        backgroundColor: '#4285F4',
        borderColor: '#4285F4'
      }
    ];
    localStorage.setItem('optivizeGoogleEvents', JSON.stringify(sampleGoogleEvents));
    updateConnectionUI(true);
    showAlert('Google Calendar connected with sample events!', 'success');
    calendar.refetchEvents();
  }

  // Initialize Google Calendar connection button listener
  checkCalendarConnection();
  document.getElementById('connectCalendarBtn')?.addEventListener('click', connectGoogleCalendar);

  // Helper function to get badge color based on priority
  function getPriorityColor(priority) {
    switch(priority.toLowerCase()) {
      case 'high': return 'danger';
      case 'medium': return 'warning';
      case 'low': return 'info';
      default: return 'secondary';
    }
  }

  // Helper function to get badge color based on status
  function getStatusColor(status) {
    switch(status.toLowerCase()) {
      case 'confirmed':
      case 'delivered':
      case 'completed':
        return 'success';
      case 'pending':
      case 'processing':
        return 'warning';
      case 'in transit':
      case 'in progress':
        return 'primary';
      case 'scheduled':
      case 'planned':
        return 'info';
      default:
        return 'secondary';
    }
  }
});
</script>
