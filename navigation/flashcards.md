---
layout: base
title: Inventory
description: Inventory Management System
hide: true
permalink: /flashcards
---

<style>
  body {
    font-family: 'Inter', sans-serif;
    background: linear-gradient(135deg, #1a2980, #26d0ce); /* Dark blue gradient */
    color: #ffffff;
    margin: 0;
    padding: 20px;
    min-height: 100vh;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    background: rgba(255, 255, 255, 0.1); /* Semi-transparent white */
    backdrop-filter: blur(10px); /* Frosted glass effect */
    border-radius: 8px 8px 0 0;
    box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
    padding: 20px;
    min-height: calc(100vh - 40px);
    border: 1px solid rgba(255, 255, 255, 0.2); /* Subtle border */
  }

  .empty-state {
    text-align: center;
    padding: 40px 20px;
    animation: fadeIn 0.5s ease-in-out;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 300px; /* Give it some minimum height */
  }

  .empty-state img {
    max-width: 200px;
    margin-bottom: 20px;
    filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1)); /* Subtle shadow */
  }

  .empty-state h3 {
    color: #ffffff; /* White text for better contrast */
    margin-bottom: 10px;
    font-size: 1.5rem;
    font-weight: 600;
  }

  .empty-state p {
    color: #e0e0e0; /* Light grey for better visibility */
    margin-bottom: 20px;
    font-size: 1.1rem;
    max-width: 400px;
  }

  .empty-state button {
    background: #ffffff;
    color: #2c3e50;
    border: none;
    padding: 10px 20px;
    border-radius: 4px;
    font-weight: 500;
    transition: all 0.3s ease;
  }

  .empty-state button:hover {
    background: #f0f0f0;
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  h1 {
    color: #2c3e50;
    border-bottom: 2px solid #eee;
    padding-bottom: 10px;
    margin-bottom: 20px;
  }

  .action-bar {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
    align-items: center;
  }

  button {
    background: #3498db;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 8px 16px;
    cursor: pointer;
    font-size: 14px;
    transition: background 0.3s;
  }

  button:hover {
    background: #2980b9;
  }

  button.danger {
    background: #e74c3c;
  }

  button.danger:hover {
    background: #c0392b;
  }

  button.secondary {
    background: #95a5a6;
  }

  button.secondary:hover {
    background: #7f8c8d;
  }

  .table-container {
    overflow-x: auto;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    margin-bottom: 20px;
    color: #ffffff; /* White text for tables */
  }

  th {
    background-color: rgba(255, 255, 255, 0.1); /* Semi-transparent header */
    font-weight: 600;
  }

  tr:hover {
    background-color: rgba(255, 255, 255, 0.05); /* Subtle hover effect */
  }

  .edit-input {
    width: 100%;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }

  .modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    z-index: 1000;
    justify-content: center;
    align-items: center;
  }

  .modal-content {
    background: white;
    padding: 20px;
    border-radius: 8px;
    width: 400px;
    max-width: 90%;
  }

  .modal-title {
    margin-top: 0;
    color: #2c3e50;
  }

  .form-group {
    margin-bottom: 15px;
  }

  .form-group label {
    display: block;
    margin-bottom: 5px;
    font-weight: 600;
  }

  .form-group input, .form-group textarea {
    width: 100%;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }

  .modal-actions {
    display: flex;
    justify-content: flex-end;
    gap: 10px;
    margin-top: 20px;
  }

  .search-container {
    margin-bottom: 20px;
    display: flex;
    gap: 10px;
  }
  
  .search-container input {
    flex: 1;
    padding: 8px 12px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
  }
  
  .search-container button {
    padding: 8px 16px;
  }

  .sort-options {
    display: flex;
    gap: 10px;
    margin-left: auto;
  }

  .sort-options select {
    padding: 8px;
    border-radius: 4px;
    border: 1px solid #ddd;
  }

  .total-items-display {
    font-weight: bold;
    margin-left: 10px;
    color: #2c3e50;
  }
  
  .count-description-container {
    display: flex;
    align-items: center;
    gap: 8px;
    width: 100%;
  }

  .count-section {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-shrink: 0;
  }

  .count-section input {
    width: 50px;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
  }


  #item-description {
    flex: 1;
    min-width: 0;
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
    resize: vertical; /* Allows vertical resizing */
    min-height: 40px; /* Minimum height for 2 lines */
    white-space: pre-wrap; /* Ensures text wraps */
    overflow-wrap: break-word; /* Breaks long words */
  }
  
  .item-content-container {
    display: flex;
    gap: 8px;
    align-items: flex-start;
  }

  .item-count-display {
    font-weight: bold;
    min-width: 30px;
    text-align: center;
  }

  .separator {
    color: #666;
  }

  .item-description {
    white-space: pre-wrap;
    word-break: break-word;
    flex: 1;
    min-width: 0;
  }


  .zapier-modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
  justify-content: center;
  align-items: center;
}

.zapier-modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  width: 500px;
  max-width: 90%;
  color: #333;
}

.zapier-instructions {
  margin-top: 15px;
  background: #f5f5f5;
  padding: 15px;
  border-radius: 4px;
  font-size: 14px;
}

.zapier-steps {
  margin-left: 20px;
  margin-bottom: 10px;
}

.zapier-code {
  background: #ebebeb;
  padding: 8px;
  border-radius: 4px;
  font-family: monospace;
  margin: 10px 0;
  word-break: break-all;
}
</style>

<div class="container">
  <h1>Inventory Management</h1>
  
  <!-- Groups search -->
  <div id="groups-search-container" class="search-container">
    <input type="text" id="search-groups" placeholder="Search groups...">
    <button id="clear-groups-search">Clear</button>
  </div>
  
  <div class="action-bar">
    <div>
      <button id="create-deck-btn">+ Create New Group</button>
    </div>
    <div class="sort-options">
      <select id="group-sort">
        <option value="name-asc">Sort by: Name (A-Z)</option>
        <option value="name-desc">Sort by: Name (Z-A)</option>
        <option value="count-asc">Sort by: Item Count (Low-High)</option>
        <option value="count-desc">Sort by: Item Count (High-Low)</option>
      </select>
    </div>
    <button id="google-import-btn">📥 Import from Google Sheets</button>
  </div>
  

  <div class="table-container">
    <table id="groups-table">
      <thead>
        <tr>
          <th>Group Name</th>
          <th>Item Count</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody id="groups-list">
        <!-- Groups will be loaded here -->
      </tbody>
    </table>
  </div>

  <div id="items-section" style="display: none;">
    <!-- Items search -->
    <div id="items-search-container" class="search-container">
      <input type="text" id="search-items" placeholder="Search items...">
      <button id="clear-items-search">Clear</button>
    </div>

  <div class="action-bar">
    <h2 id="current-group-name">Items in Group: <span></span> <span class="total-items-display" id="total-items-count"></span></h2>
    <div class="sort-options">
      <select id="item-sort">
        <option value="name-asc">Sort by: Name (A-Z)</option>
        <option value="name-desc">Sort by: Name (Z-A)</option>
        <option value="count-asc">Sort by: Count (Low-High)</option>
        <option value="count-desc">Sort by: Count (High-Low)</option>
      </select>
      <button id="add-item-btn">+ Add Item</button>
      <button id="back-to-groups" class="secondary">← Back to Groups</button>
    </div>
  </div>

  <div class="table-container">
    <table id="items-table">
      <thead>
        <tr>
          <th>Overview</th>
          <th>Description</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody id="items-list">
        <!-- Items will be loaded here -->
      </tbody>
    </table>
  </div>

  
  </div>

  <!-- Google Sheet ID Modal -->
  <div id="google-sheet-modal" class="modal">
    <div class="modal-content">
      <h3 class="modal-title">Import from Google Sheets</h3>
      <div class="form-group">
        <label for="sheet-id-input">Enter Google Sheet ID:</label>
        <input type="text" id="sheet-id-input" placeholder="e.g., 1A2B3C4D5E6F...">
      </div>
      <div class="modal-actions">
        <button id="cancel-google-import" class="secondary">Cancel</button>
        <button id="confirm-google-import">Import</button>
      </div>
    </div>
  </div>

  <!-- Zapier Alert Modal -->
<div id="zapier-modal" class="zapier-modal">
  <div class="zapier-modal-content">
    <h3 class="modal-title">Set Low Stock Alert</h3>
    
<div class="form-group">
  <label for="alert-threshold">Alert me when quantity falls below:</label>
  <input type="number" id="alert-threshold" min="1" value="5">
</div>

<div class="zapier-instructions">
  <p><strong>How to set up this alert in Zapier:</strong></p>
  <ol class="zapier-steps">
    <li>Create a free account on <a href="https://zapier.com" target="_blank">Zapier.com</a></li>
    <li>Create a new Zap with "Webhooks by Zapier" as the trigger</li>
    <li>Select "Retrieve Poll" as the event</li>
    <li>Use this API URL (copy it):</li>
  </ol>
  
  <div class="zapier-code" id="zapier-url"></div>
  
  <ol class="zapier-steps" start="5">
    <li>Choose where to send alerts: Email, SMS, Slack, etc.</li>
    <li>Test and enable your Zap</li>
  </ol>
  
  <p><small>Zapier will check stock levels every 15 minutes (free plan) or 1 minute (paid plan).</small></p>
</div>

<div class="modal-actions">
  <button id="close-zapier-modal" class="secondary">Close</button>
  <button id="copy-zapier-url">Copy URL</button>
</div>
  </div>
</div>
</div>

<!-- Create Group Modal -->
<div id="create-group-modal" class="modal">
  <div class="modal-content">
    <h3 class="modal-title">Create New Group</h3>
    <div class="form-group">
      <label for="group-name">Group Name</label>
      <input type="text" id="group-name" placeholder="Enter group name">
    </div>
    <div class="modal-actions">
      <button id="cancel-create-group" class="secondary">Cancel</button>
      <button id="confirm-create-group">Create</button>
    </div>
  </div>
</div>

<!-- Add/Edit Item Modal -->
<div id="item-modal" class="modal">
  <div class="modal-content">
    <h3 class="modal-title" id="item-modal-title">Add New Item</h3>
    <div class="form-group">
      <label for="item-title">Overview</label>
      <input type="text" id="item-title" placeholder="Enter overview">
    </div>
    <div class="form-group">
      <label for="item-content">Description</label>
      <div class="count-description-container">
        <div class="count-section">
          <input type="number" id="item-count" min="1" value="1">
          <span class="separator">/</span>
        </div>
        <textarea id="item-description" placeholder="Enter item description" rows="2"></textarea>      </div>
    </div>
    <div class="modal-actions">
      <button id="cancel-item" class="secondary">Cancel</button>
      <button id="confirm-item">Save</button>
    </div>
  </div>
</div>

<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

  // ========== STATE AND REFERENCES ========== //
  let groupsTable, itemsTable, itemsSection, currentGroupName;
  let currentGroup = null;
  let currentItem = null;
  let groups = [];
  let isEditingGroup = false;
  let searchGroupsInput, clearGroupsSearch, searchItemsInput, clearItemsSearch;
  let groupsSearchContainer, itemsSearchContainer;
  let filteredGroups = [];
  let filteredItems = [];

  // ========== CORE FUNCTIONS ========== //
  function initializeReferences() {
    groupsTable = document.getElementById('groups-list');
    itemsTable = document.getElementById('items-list');
    itemsSection = document.getElementById('items-section');
    currentGroupName = document.getElementById('current-group-name').querySelector('span');
    groupsSearchContainer = document.getElementById('groups-search-container');
    itemsSearchContainer = document.getElementById('items-search-container');
    searchGroupsInput = document.getElementById('search-groups');
    clearGroupsSearch = document.getElementById('clear-groups-search');
    searchItemsInput = document.getElementById('search-items');
    clearItemsSearch = document.getElementById('clear-items-search');
  }

  function calculateTotalItems() {
    if (!currentGroup?.cards) return 0;
    return currentGroup.cards.reduce((total, item) => {
      const countMatch = item.content.match(/^(\d+)\s*\/\s*/);
      const count = countMatch ? parseInt(countMatch[1]) : 1;
      return total + count;
    }, 0);
  }

  function updateGroupCount(groupId, count) {
    const groupIndex = groups.findIndex(g => g.id === groupId);
    if (groupIndex !== -1) {
      groups[groupIndex].card_count = count;
      renderGroups();
    }
  }

  function renderGroups() {
    if (!groupsTable) return;
    groupsTable.innerHTML = '';
    
    const groupsToRender = filteredGroups.length > 0 ? filteredGroups : groups;
    
    // Apply sorting
    const sortValue = document.getElementById('group-sort').value;
    switch(sortValue) {
      case 'name-asc':
        groupsToRender.sort((a, b) => a.title.localeCompare(b.title));
        break;
      case 'name-desc':
        groupsToRender.sort((a, b) => b.title.localeCompare(a.title));
        break;
      case 'count-asc':
        groupsToRender.sort((a, b) => (a.card_count || 0) - (b.card_count || 0));
        break;
      case 'count-desc':
        groupsToRender.sort((a, b) => (b.card_count || 0) - (a.card_count || 0));
        break;
    }
    if (groupsToRender.length === 0) {
      groupsTable.innerHTML = `
        <tr>
          <td colspan="3">
            <div class="empty-state">
              <img src="https://cdn-icons-png.flaticon.com/512/4076/4076478.png" alt="No groups">
              <h3>Your Inventory is Empty</h3>
              <p>Organize your products by creating your first group</p>
              <button id="create-first-group" class="primary-btn">+ Create First Group</button>
            </div>
          </td>
        </tr>
      `;
      document.getElementById('create-first-group').addEventListener('click', () => {
        document.getElementById('create-deck-btn').click();
      });
      return;
    }
    
    groupsToRender.forEach(group => {
      const row = document.createElement('tr');
      row.innerHTML = `
        <td>${group.title}</td>
        <td>${group.card_count || 0}</td>
        <td>
          <button class="open-group" data-id="${group.id}">Open</button>
          <button class="edit-group" data-id="${group.id}">Edit</button>
          <button class="delete-group danger" data-id="${group.id}">Delete</button>
        </td>
      `;
      groupsTable.appendChild(row);
    });
  }

  function renderItems() {
    if (!itemsTable) return;
    itemsTable.innerHTML = '';
    
    let itemsToRender = filteredItems.length > 0 ? filteredItems : (currentGroup?.cards || []);
    
    // Apply sorting
    const sortValue = document.getElementById('item-sort').value;
    switch (sortValue) {
      case 'name-asc':
        itemsToRender.sort((a, b) => a.title.localeCompare(b.title));
        break;
      case 'name-desc':
        itemsToRender.sort((a, b) => b.title.localeCompare(a.title));
        break;
      case 'count-asc':
        itemsToRender.sort((a, b) => {
          const aCount = parseInt(a.content.match(/^(\d+)\s*\/\s*/)?.[1] || "1");
          const bCount = parseInt(b.content.match(/^(\d+)\s*\/\s*/)?.[1] || "1");
          return aCount - bCount;
        });
        break;
      case 'count-desc':
        itemsToRender.sort((a, b) => {
          const aCount = parseInt(a.content.match(/^(\d+)\s*\/\s*/)?.[1] || "1");
          const bCount = parseInt(b.content.match(/^(\d+)\s*\/\s*/)?.[1] || "1");
          return bCount - aCount;
        });
        break;
    }
    
    if (itemsToRender.length === 0) {
      itemsTable.innerHTML = `
        <tr>
          <td colspan="3">
            <div class="empty-state">
              <img src="https://cdn-icons-png.flaticon.com/512/4076/4076472.png" alt="No items">
              <h3>No Items Found</h3>
              <p>This group is empty. Add your first item to get started</p>
              <button id="create-first-item">+ Add Item</button>
            </div>
          </td>
        </tr>
      `;
      document.getElementById('create-first-item').addEventListener('click', () => {
        document.getElementById('add-item-btn').click();
      });
      return;
    }
    
    itemsToRender.forEach(item => {
      const countMatch = item.content.match(/^(\d+)\s*\/\s*/);
      const count = countMatch ? countMatch[1] : '1';
      const description = item.content.replace(/^\d+\s*\/\s*/, '');
      
      const row = document.createElement('tr');
      row.innerHTML = `
        <td>${item.title}</td>
        <td>
          <div class="item-content-container">
            <span class="item-count-display">${count}</span>
            <span class="separator">/</span>
            <div class="item-description">${description}</div>
          </div>
        </td>
        <td>
          <button class="edit-item" data-id="${item.id}">Edit</button>
          <button class="delete-item danger" data-id="${item.id}">Delete</button>
           <button class="set-alert" data-id="${item.id}" data-name="${item.title}">Set Alert</button>
        </td>
      `;
      itemsTable.appendChild(row);
    });
  }

  function filterGroups(searchTerm) {
    if (!searchTerm) {
      filteredGroups = [];
      renderGroups();
      return;
    }
    
    const term = searchTerm.toLowerCase();
    filteredGroups = groups.filter(group => 
      group.title.toLowerCase().includes(term) ||
      (group.card_count + '').includes(term)
    );
    
    renderGroups();
  }

  function filterItems(searchTerm) {
    if (!searchTerm || !currentGroup?.cards) {
      filteredItems = [];
      renderItems();
      return;
    }
    
    const term = searchTerm.toLowerCase();
    filteredItems = currentGroup.cards.filter(item => {
      const countMatch = item.content.match(/^(\d+)\s*\/\s*/);
      const count = countMatch ? countMatch[1] : '1';
      const description = item.content.replace(/^\d+\s*\/\s*/, '');
      
      return (
        item.title.toLowerCase().includes(term) ||
        description.toLowerCase().includes(term) ||
        count.includes(term)
      );
    });
    
    renderItems();
  }

  // ========== API OPERATIONS ========== //
  async function fetchGroupsWithCounts() {
    try {
      const groupsResponse = await fetch(`${pythonURI}/api/deck`, {
        ...fetchOptions,
        method: 'GET'
      });

      if (groupsResponse.ok) {
        groups = await groupsResponse.json();
        
        await Promise.all(groups.map(async group => {
          try {
            const detailResponse = await fetch(`${pythonURI}/api/deck/${group.id}?include_cards=true`, {
              ...fetchOptions,
              method: 'GET'
            });
            
            if (detailResponse.ok) {
              const groupData = await detailResponse.json();
              group.card_count = groupData.cards?.length || 0;
              group.cards = groupData.cards || [];
            }
          } catch (error) {
            console.error(`Error fetching details for group ${group.id}:`, error);
            group.card_count = 0;
          }
        }));
        
        renderGroups();
      } else {
        console.error('Failed to fetch groups:', await groupsResponse.text());
      }
    } catch (error) {
      console.error('Error fetching groups:', error);
    }
  }

  async function openGroup(groupId) {
    try {
      const response = await fetch(`${pythonURI}/api/deck/${groupId}?include_cards=true`, {
        ...fetchOptions,
        method: 'GET'
      });

      if (response.ok) {
        currentGroup = await response.json();
        currentGroupName.textContent = currentGroup.title;
        
        // Calculate and display total items
        const totalItems = calculateTotalItems();
        document.getElementById('total-items-count').textContent = `(Total Items: ${totalItems})`;
        
        itemsSection.style.display = 'block';
        itemsSearchContainer.style.display = 'flex';
        groupsSearchContainer.style.display = 'none';
        
        searchItemsInput.value = '';
        filteredItems = [];
        
        updateGroupCount(currentGroup.id, currentGroup.cards?.length || 0);
        renderItems();
      } else {
        console.error('Failed to fetch group:', await response.text());
      }
    } catch (error) {
      console.error('Error fetching group:', error);
    }
  }

  async function createGroup() {
    if (isEditingGroup) return;
    
    const groupName = document.getElementById('group-name').value.trim();
    if (!groupName) {
      alert('Please enter a group name');
      return;
    }
    
    try {
      const response = await fetch(`${pythonURI}/api/deck`, {
        ...fetchOptions,
        method: 'POST',
        body: JSON.stringify({ title: groupName, user_id: 1 }),
      });

      if (response.ok) {
        document.getElementById('group-name').value = '';
        document.getElementById('create-group-modal').style.display = 'none';
        await fetchGroupsWithCounts();
      } else {
        console.error('Failed to create group:', await response.text());
      }
    } catch (error) {
      console.error('Error creating group:', error);
    }
  }

  async function editGroup(groupId) {
    const group = groups.find(g => g.id == groupId);
    if (!group) return;
    
    isEditingGroup = true;
    document.getElementById('group-name').value = group.title;
    document.getElementById('item-modal-title').textContent = 'Edit Group';
    document.getElementById('confirm-create-group').textContent = 'Update';
    document.getElementById('create-group-modal').style.display = 'flex';
    
    const originalHandler = document.getElementById('confirm-create-group').onclick;
    
    document.getElementById('confirm-create-group').onclick = async () => {
      const newName = document.getElementById('group-name').value.trim();
      if (!newName) {
        alert('Please enter a group name');
        return;
      }
      
      try {
        const response = await fetch(`${pythonURI}/api/deck/${groupId}`, {
          ...fetchOptions,
          method: 'PUT',
          body: JSON.stringify({ title: newName }),
        });

        if (response.ok) {
          document.getElementById('create-group-modal').style.display = 'none';
          isEditingGroup = false;
          document.getElementById('confirm-create-group').onclick = originalHandler;
          document.getElementById('confirm-create-group').textContent = 'Create';
          await fetchGroupsWithCounts();
          if (currentGroup && currentGroup.id === groupId) {
            currentGroup.title = newName;
            currentGroupName.textContent = newName;
          }
        } else {
          console.error('Failed to update group:', await response.text());
        }
      } catch (error) {
        console.error('Error updating group:', error);
      }
    };
  }

  async function deleteGroup(groupId) {
    if (!confirm('Are you sure you want to delete this group and all its items?')) {
      return;
    }
    
    try {
      const response = await fetch(`${pythonURI}/api/deck/${groupId}`, {
        ...fetchOptions,
        method: 'DELETE'
      });

      if (response.ok) {
        await fetchGroupsWithCounts();
        if (currentGroup && currentGroup.id == groupId) {
          itemsSection.style.display = 'none';
          currentGroup = null;
        }
      } else {
        console.error('Failed to delete group:', await response.text());
      }
    } catch (error) {
      console.error('Error deleting group:', error);
    }
  }

  async function saveItem() {
    const title = document.getElementById('item-title').value.trim();
    const count = document.getElementById('item-count').value;
    const description = document.getElementById('item-description').value.trim();
    
    if (!title || !description) {
      alert('Please fill in all fields');
      return;
    }
    
    // Combine count and description with fixed "/" separator
    const content = `${count} / ${description}`;
    
    try {
      let response;
      
      if (currentItem) {
        response = await fetch(`${pythonURI}/api/flashcard/${currentItem.id}`, {
          ...fetchOptions,
          method: 'PUT',
          body: JSON.stringify({ title, content }),
        });
      } else {
        response = await fetch(`${pythonURI}/api/flashcard`, {
          ...fetchOptions,
          method: 'POST',
          body: JSON.stringify({ 
            title, 
            content, 
            deck_id: currentGroup.id,
            user_id: 1
          }),
        });
      }

      if (response.ok) {
        document.getElementById('item-modal').style.display = 'none';
        const groupResponse = await fetch(`${pythonURI}/api/deck/${currentGroup.id}?include_cards=true`, {
          ...fetchOptions,
          method: 'GET'
        });
        
        if (groupResponse.ok) {
          currentGroup = await groupResponse.json();
          // Update total items display
          const totalItems = calculateTotalItems();
          document.getElementById('total-items-count').textContent = `(Total Items: ${totalItems})`;
          renderItems();
          updateGroupCount(currentGroup.id, currentGroup.cards?.length || 0);
        }
      } else {
        console.error('Failed to save item:', await response.text());
      }
    } catch (error) {
      console.error('Error saving item:', error);
    }
  }

  async function editItem(itemId) {
    const item = currentGroup.cards.find(i => i.id == itemId);
    if (!item) return;
    
    currentItem = item;
    document.getElementById('item-modal-title').textContent = 'Edit Item';
    document.getElementById('item-title').value = item.title;
    
    // Parse the existing content
    const countMatch = item.content.match(/^(\d+)\s*\/\s*/);
    const count = countMatch ? countMatch[1] : '1';
    const description = item.content.replace(/^\d+\s*\/\s*/, '');
    
    document.getElementById('item-count').value = count;
    document.getElementById('item-description').value = description;
    
    document.getElementById('item-modal').style.display = 'flex';
  }

  async function deleteItem(itemId) {
    if (!confirm('Are you sure you want to delete this item?')) {
      return;
    }
    
    try {
      const response = await fetch(`${pythonURI}/api/flashcard/${itemId}`, {
        ...fetchOptions,
        method: 'DELETE'
      });

      if (response.ok) {
        const groupResponse = await fetch(`${pythonURI}/api/deck/${currentGroup.id}?include_cards=true`, {
          ...fetchOptions,
          method: 'GET'
        });
        
        if (groupResponse.ok) {
          currentGroup = await groupResponse.json();
          // Update total items display
          const totalItems = calculateTotalItems();
          document.getElementById('total-items-count').textContent = `(Total Items: ${totalItems})`;
          renderItems();
          updateGroupCount(currentGroup.id, currentGroup.cards?.length || 0);
        }
      } else {
        console.error('Failed to delete item:', await response.text());
      }
    } catch (error) {
      console.error('Error deleting item:', error);
    }
  }

  // ========== EVENT HANDLING ========== //
  function setupEventListeners() {
    // Use event delegation for dynamic elements
    document.addEventListener('click', (e) => {
      if (e.target.classList.contains('open-group')) {
        openGroup(e.target.dataset.id);
      }
      if (e.target.classList.contains('edit-group')) {
        editGroup(e.target.dataset.id);
      }
      if (e.target.classList.contains('delete-group')) {
        deleteGroup(e.target.dataset.id);
      }
      if (e.target.classList.contains('edit-item')) {
        editItem(e.target.dataset.id);
      }
      if (e.target.classList.contains('delete-item')) {
        deleteItem(e.target.dataset.id);
      }
      if (e.target.id === 'create-first-group') {
        document.getElementById('create-deck-btn').click();
      }
      if (e.target.id === 'create-first-item') {
        document.getElementById('add-item-btn').click();
      }
    });

    // Static elements
    document.getElementById('create-deck-btn')?.addEventListener('click', () => {
      isEditingGroup = false;
      document.getElementById('group-name').value = '';
      document.getElementById('confirm-create-group').textContent = 'Create';
      document.getElementById('item-modal-title').textContent = 'Create New Group';
      document.getElementById('create-group-modal').style.display = 'flex';
    });
    
    document.getElementById('cancel-create-group')?.addEventListener('click', () => {
      document.getElementById('create-group-modal').style.display = 'none';
    });
    
    document.getElementById('confirm-create-group')?.addEventListener('click', createGroup);
    
    document.getElementById('add-item-btn')?.addEventListener('click', () => {
      document.getElementById('item-modal-title').textContent = 'Add New Item';
      document.getElementById('item-title').value = '';
      document.getElementById('item-count').value = '1';
      document.getElementById('item-description').value = '';
      currentItem = null;
      document.getElementById('item-modal').style.display = 'flex';
    });
    
    document.getElementById('cancel-item')?.addEventListener('click', () => {
      document.getElementById('item-modal').style.display = 'none';
    });
    
    document.getElementById('confirm-item')?.addEventListener('click', saveItem);
    
    document.getElementById('back-to-groups')?.addEventListener('click', () => {
      document.getElementById('items-section').style.display = 'none';
      itemsSearchContainer.style.display = 'none';
      groupsSearchContainer.style.display = 'flex';
      currentGroup = null;
      
      // Clear any existing group search
      searchGroupsInput.value = '';
      filteredGroups = [];
      renderGroups();
    });

    // Search functionality
    searchGroupsInput.addEventListener('input', (e) => {
      filterGroups(e.target.value);
    });
    
    clearGroupsSearch.addEventListener('click', () => {
      searchGroupsInput.value = '';
      filterGroups('');
    });
    
    searchItemsInput.addEventListener('input', (e) => {
      filterItems(e.target.value);
    });
    
    clearItemsSearch.addEventListener('click', () => {
      searchItemsInput.value = '';
      filterItems('');
    });

    // Sorting functionality
    document.getElementById('group-sort')?.addEventListener('change', () => {
      renderGroups();
    });

    document.getElementById('item-sort')?.addEventListener('change', () => {
      renderItems();
    });
  }

  // ========== INITIALIZATION ========== //
  document.addEventListener('DOMContentLoaded', () => {
    initializeReferences();
    setupEventListeners();
    fetchGroupsWithCounts();
  });

  // Add Zapier integration
let zapierItemId = null;
let zapierItemName = null;

function showZapierModal(itemId, itemName) {
  zapierItemId = itemId;
  zapierItemName = itemName;
  
  // Update the URL with the correct item ID and default threshold
  updateZapierUrl();
  
  document.getElementById('zapier-modal').style.display = 'flex';
}

function updateZapierUrl() {
  const threshold = document.getElementById('alert-threshold').value;
  const baseUrl = window.location.origin; // Gets the base URL of your site
  const apiUrl = `${pythonURI}/api/zapier/low-stock/${zapierItemId}/${threshold}`;
  
  document.getElementById('zapier-url').textContent = apiUrl;
}

// Setup additional event listeners for Zapier functionality
document.addEventListener('DOMContentLoaded', function() {
  // Handle the "Set Alert" button click
  document.addEventListener('click', (e) => {
    if (e.target.classList.contains('set-alert')) {
      showZapierModal(e.target.dataset.id, e.target.dataset.name);
    }
  });
  
  // Close Zapier modal
  document.getElementById('close-zapier-modal')?.addEventListener('click', () => {
    document.getElementById('zapier-modal').style.display = 'none';
  });
  
  // Copy URL button
  document.getElementById('copy-zapier-url')?.addEventListener('click', () => {
    const urlElement = document.getElementById('zapier-url');
    
    // Create a temporary input element to copy from
    const temp = document.createElement('input');
    document.body.appendChild(temp);
    temp.value = urlElement.textContent;
    temp.select();
    document.execCommand('copy');
    document.body.removeChild(temp);
    
    // Show feedback
    const originalText = document.getElementById('copy-zapier-url').textContent;
    document.getElementById('copy-zapier-url').textContent = 'Copied!';
    setTimeout(() => {
      document.getElementById('copy-zapier-url').textContent = originalText;
    }, 2000);
  });
  
  // Update URL when threshold changes
  document.getElementById('alert-threshold')?.addEventListener('input', updateZapierUrl);
});
// Store sheet ID in sessionStorage temporarily
document.getElementById('google-import-btn')?.addEventListener('click', () => {
  document.getElementById('google-sheet-modal').style.display = 'flex';
});

document.getElementById('cancel-google-import')?.addEventListener('click', () => {
  document.getElementById('google-sheet-modal').style.display = 'none';
});

document.getElementById('confirm-google-import')?.addEventListener('click', async () => {
  const sheetId = document.getElementById('sheet-id-input').value.trim();
  if (!sheetId) {
    alert("Please enter a valid Google Sheet ID.");
    return;
  }

  sessionStorage.setItem("pending_sheet_id", sheetId);
    const apiBaseURL = window.location.hostname === "localhost"
    ? "http://localhost:8212"
    : "https://your-deployment-domain.com";

  window.location.href = `${apiBaseURL}/google/connect`;
});

// Auto-import after OAuth callback
document.addEventListener("DOMContentLoaded", async () => {
  const urlParams = new URLSearchParams(window.location.search);
  const shouldImport = urlParams.get("import") === "1";
  const sheetId = sessionStorage.getItem("pending_sheet_id");

  if (shouldImport && sheetId) {
    try {
      const response = await fetch("http://localhost:8212/google/import", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        credentials: "include",
        body: JSON.stringify({ sheet_id: sheetId })
      });

      if (response.ok) {
        alert("✅ Google Sheets data imported successfully!");
        sessionStorage.removeItem("pending_sheet_id");
        location.href = "/optivize_frontend/flashcards";  // refresh
      } else {
        const error = await response.json();
        alert("❌ Import failed: " + (error.error || "Unknown error"));
      }
    } catch (err) {
      console.error(err);
      alert("❌ Error connecting to server");
    }
  }
});

</script>


