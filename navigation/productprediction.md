---
layout: base
title: Predictions
description: Product Success Prediction
hide: true
permalink: /navigation/predictions
---
<style>
:root {
  --bg-start: #0b1e3b;
  --bg-end: #162b4d;
  --text: #ffffff;
  --primary: #fbb034;
  --secondary: #ffdd00;
  --glass: rgba(255, 255, 255, 0.05);
  --glass-border: rgba(255, 255, 255, 0.1);
  --glass-highlight: rgba(255, 255, 255, 0.15);
  --success: #4ade80;
  --warning: #f59e0b;
  --danger: #ef4444;
  --info: #60a5fa;
}

body {
  background: linear-gradient(135deg, var(--bg-start), var(--bg-end));
  color: var(--text);
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  min-height: 100vh;
  padding: 0;
  margin: 0;
}

/* Main container */
.product-prediction-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 2rem;
  display: grid;
  gap: 2rem;
  grid-template-columns: 1fr;
  grid-template-areas:
    "train"
    "predict"
    "history";
}

/* Card styles */
.section-card {
  background: var(--glass);
  backdrop-filter: blur(10px);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 1.5rem;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.section-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 40px rgba(0, 0, 0, 0.3);
}

.section-card h2 {
  color: var(--primary);
  margin-top: 0;
  font-size: 1.5rem;
  font-weight: 600;
  border-bottom: 1px solid var(--glass-border);
  padding-bottom: 0.75rem;
  margin-bottom: 1.5rem;
}

/* Form styles */
.form-group {
  margin-bottom: 1.25rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-size: 0.875rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.8);
}

.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  background: var(--glass-highlight);
  border: 1px solid var(--glass-border);
  border-radius: 8px;
  color: var(--text);
  font-size: 0.9375rem;
  transition: all 0.2s ease;
}
/* Style for all select elements */
select {
  background-color: var(--glass-highlight) !important;
  color: var(--text) !important;
  border: 1px solid var(--glass-border) !important;
}

/* Style for dropdown options */
select option {
  background-color: var(--bg-end) !important;
  color: var(--text) !important;
}

/* Style for dropdown panel */
select:focus, select:hover {
  border-color: var(--primary) !important;
}

/* Remove default styling and add custom arrow */
select {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' fill='%23fbb034' viewBox='0 0 16 16'%3E%3Cpath d='M7.247 11.14 2.451 5.658C1.885 5.013 2.345 4 3.204 4h9.592a1 1 0 0 1 .753 1.659l-4.796 5.48a1 1 0 0 1-1.506 0z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 0.75rem center;
  background-size: 12px 12px;
  padding-right: 2rem;
}

/* Firefox specific fix */
@-moz-document url-prefix() {
  select {
    color: var(--text) !important;
  }
  select option {
    background-color: var(--bg-end);
  }
}

/* Edge/IE fix */
select::-ms-expand {
  display: none;
}
.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--primary);
  box-shadow: 0 0 0 2px rgba(251, 176, 52, 0.2);
}

.form-group textarea {
  min-height: 120px;
  resize: vertical;
}

.form-row {
  display: flex;
  gap: 1rem;
}

.form-row .form-group {
  flex: 1;
}

/* Button styles */
.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  font-weight: 600;
  font-size: 0.9375rem;
  cursor: pointer;
  transition: all 0.2s ease;
  border: none;
}

.primary-btn {
  background: var(--primary);
  color: #0b1e3b;
}

.primary-btn:hover {
  background: var(--secondary);
  transform: translateY(-2px);
}

.secondary-btn {
  background: var(--glass-highlight);
  color: var(--text);
}

.secondary-btn:hover {
  background: rgba(255, 255, 255, 0.1);
}

/* Results containers */
.results-container {
  margin-top: 1.5rem;
  border-radius: 8px;
  overflow: hidden;
}

.loading {
  padding: 1rem;
  text-align: center;
  color: rgba(255, 255, 255, 0.7);
  font-style: italic;
}

/* Training results */
.success-message {
  background: rgba(74, 222, 128, 0.1);
  border-left: 4px solid var(--success);
  padding: 1.25rem;
}

.success-message h3 {
  margin-top: 0;
  color: var(--success);
}

.error-message {
  background: rgba(239, 68, 68, 0.1);
  border-left: 4px solid var(--danger);
  padding: 1.25rem;
}

.error-message h3 {
  margin-top: 0;
  color: var(--danger);
}

.feature-importance {
  margin-top: 1rem;
}

.feature-importance h4 {
  margin-bottom: 0.5rem;
  font-size: 1rem;
}

.feature-importance ul {
  padding-left: 1.25rem;
  margin: 0;
}

/* Prediction results */
.prediction-result {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  padding: 1.5rem;
  border-radius: 8px;
}

.prediction-result.success {
  background: rgba(74, 222, 128, 0.1);
  border-left: 4px solid var(--success);
}

.prediction-result.warning {
  background: rgba(245, 158, 11, 0.1);
  border-left: 4px solid var(--warning);
}

.score-display {
  text-align: center;
}

.score-value {
  font-size: 3rem;
  font-weight: 700;
  display: block;
  line-height: 1;
  background: linear-gradient(to right, var(--primary), var(--secondary));
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  margin-bottom: 0.25rem;
}

.score-label {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.7);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.probability {
  display: block;
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.7);
  margin-top: 0.5rem;
}

.prediction-details h3 {
  margin-top: 0;
  font-size: 1.25rem;
}

.category {
  font-size: 0.875rem;
  color: rgba(255, 255, 255, 0.7);
  margin-top: -0.5rem;
  margin-bottom: 1rem;
}

/* Insights grid */
.insights-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.25rem;
  margin-top: 1.5rem;
}

.insight-card {
  background: var(--glass-highlight);
  border-radius: 12px;
  padding: 1.25rem;
  border: 1px solid var(--glass-border);
}

.insight-card h4 {
  margin-top: 0;
  margin-bottom: 1rem;
  font-size: 1rem;
  font-weight: 600;
  color: var(--primary);
  display: flex;
  align-items: center;
}

/* Score visualization */
.score-visualization {
  display: flex;
  gap: 1.5rem;
  align-items: center;
}

.gauge-container {
  flex: 1;
  max-width: 200px;
}

.gauge-track {
  height: 8px;
  background: var(--glass);
  border-radius: 4px;
  position: relative;
  overflow: hidden;
}

.gauge-fill {
  height: 100%;
  background: linear-gradient(to right, var(--danger), var(--warning), var(--success));
  border-radius: 4px;
  transition: width 0.5s ease;
}

.gauge-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.6);
  margin-bottom: 0.5rem;
}

.score-details {
  flex: 2;
}

/* Price analysis */
.price-comparison {
  margin: 1rem 0;
}

.price-bar {
  height: 6px;
  background: linear-gradient(to right, var(--success), var(--warning), var(--danger));
  border-radius: 3px;
  position: relative;
  margin: 1.5rem 0;
}

.current-price-marker {
  position: absolute;
  top: -28px;
  transform: translateX(-50%);
  background: var(--primary);
  color: var(--bg-start);
  padding: 0.25rem 0.5rem;
  border-radius: 4px;
  font-size: 0.75rem;
  font-weight: 600;
  white-space: nowrap;
}

.current-price-marker::after {
  content: "";
  position: absolute;
  bottom: -4px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 5px solid var(--primary);
}

.range-labels {
  display: flex;
  justify-content: space-between;
  font-size: 0.75rem;
  color: rgba(255, 255, 255, 0.6);
  margin-top: 0.5rem;
}

/* Marketing meter */
.marketing-meter {
  height: 8px;
  background: var(--glass);
  border-radius: 4px;
  margin: 1rem 0;
  position: relative;
  overflow: hidden;
}

.marketing-meter .meter-fill {
  height: 100%;
  background: linear-gradient(to right, var(--info), #7c3aed);
  border-radius: 4px;
}

/* Distribution analysis */
.distribution-analysis {
  margin-top: 1rem;
  padding-top: 1rem;
  border-top: 1px solid var(--glass-border);
}

.distribution-meter {
  height: 8px;
  background: var(--glass);
  border-radius: 4px;
  margin: 0.5rem 0;
  position: relative;
  overflow: hidden;
}

.distribution-meter .meter-fill {
  height: 100%;
  background: linear-gradient(to right, var(--info), #3F51B5);
  border-radius: 4px;
}

/* History table */
.history-controls {
  display: flex;
  gap: 0.75rem;
  margin-bottom: 1rem;
}

.history-controls input {
  flex: 1;
  padding: 0.75rem;
  background: var(--glass-highlight);
  border: 1px solid var(--glass-border);
  border-radius: 8px;
  color: var(--text);
  font-size: 0.9375rem;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 1rem;
  font-size: 0.875rem;
}

th, td {
  padding: 0.75rem 1rem;
  text-align: left;
  border-bottom: 1px solid var(--glass-border);
}

th {
  background: var(--glass-highlight);
  font-weight: 600;
  color: var(--primary);
  text-transform: uppercase;
  font-size: 0.75rem;
  letter-spacing: 0.05em;
}

tr:last-child td {
  border-bottom: none;
}

.success-row {
  background: rgba(74, 222, 128, 0.05);
}

.warning-row {
  background: rgba(245, 158, 11, 0.05);
}

/* Tooltip styles */
.tooltip-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 18px;
  height: 18px;
  border-radius: 50%;
  background: var(--primary);
  color: var(--bg-start);
  font-size: 12px;
  font-weight: bold;
  margin-left: 6px;
  cursor: help;
  vertical-align: middle;
  position: relative;
}

.tooltip-icon::after {
  content: attr(data-tooltip);
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 100%;
  margin-bottom: 10px;
  width: 250px;
  padding: 12px;
  background: rgba(0, 0, 0, 0.9);
  color: #fff;
  border-radius: 8px;
  font-size: 14px;
  line-height: 1.4;
  white-space: pre-wrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease;
  z-index: 100;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

.tooltip-icon:hover::after {
  opacity: 1;
}

.tooltip-icon::before {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom: 100%;
  margin-bottom: 2px;
  border-width: 6px;
  border-style: solid;
  border-color: rgba(0, 0, 0, 0.9) transparent transparent transparent;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.tooltip-icon:hover::before {
  opacity: 1;
}

/* Grid areas */
#training-section {
  grid-area: train;
}

#prediction-section {
  grid-area: predict;
}

#history-section {
  grid-area: history;
}

/* Animations */
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(10px); }
  to { opacity: 1; transform: translateY(0); }
}

.results-container {
  animation: fadeIn 0.3s ease-out;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .product-prediction-container {
    padding: 1rem;
  }
  
  .form-row {
    flex-direction: column;
    gap: 1rem;
  }
  
  .score-visualization {
    flex-direction: column;
  }
  
  table {
    display: block;
    overflow-x: auto;
  }
}
</style>

<div class="product-prediction-container">
  <!-- Training Section -->
  <div id="training-section" class="section-card">
    <h2>Train Model</h2>
    <div class="form-group">
      <label>Training Samples (JSON)</label>
      <textarea id="training-data" rows="8" placeholder='[
  {
    "product_type": "Phone",
    "seasonality": "All Year",
    "price": 3.75,
    "marketing": 8,
    "distribution_channels": 9,
    "success_score": 82
  },
  {
    "product_type": "Pants",
    "seasonality": "Fall",
    "price": 4.25,
    "marketing": 7,
    "distribution_channels": 8,
    "success_score": 78
  }
]'></textarea>
    </div>
    <button id="train-model" class="button primary-btn">Train Model</button>
    <div id="training-results" class="results-container"></div>
  </div>

  <!-- Prediction Section - Now wider below training -->
  <div id="prediction-section" class="section-card">
    <h2>Predict Success</h2>
    <div class="form-row">
      <div class="form-group">
        <label>Product Title</label>
        <input type="text" id="product-type" placeholder="e.g. Laptop">
      </div>
      <div class="form-group">
        <label>Seasonality</label>
        <select id="seasonality">
          <option value="year-round">All Year</option>
          <option value="Winter">Winter</option>
          <option value="Spring">Spring</option>
          <option value="Summer">Summer</option>
          <option value="Fall">Fall</option>
          <option value="holiday">Holiday</option>
        </select>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label>Price ($)</label>
        <input type="number" id="price" step="0.01" min="0" placeholder="3.99">
      </div>
      <div class="form-group">
        <label>
          Marketing (1–10)
          <span class="tooltip-icon" data-tooltip="
            1 – No marketing or brand awareness
            2 – Limited local word of mouth
            3 – Small social media presence
            4 – Infrequent promotions or ads
            5 – Occasional targeted marketing
            6 – Consistent online ads and local campaigns
            7 – Strong digital presence, some brand recognition
            8 – Influencer partnerships, seasonal ads
            9 – National ad campaigns, consistent brand messaging
            10 – Iconic branding, omnipresent media visibility
          ">?</span>
        </label>
        <input type="number" id="marketing" min="1" max="10" placeholder="7">
      </div>
      <div class="form-group">
        <label>
          Distribution (1–10)
          <span class="tooltip-icon" data-tooltip="
            1 – Sold in one small local store
            2 – Limited availability in select neighborhoods
            3 – Only available in one city
            4 – Some regional presence
            5 – Moderate availability across multiple areas
            6 – Broad regional distribution
            7 – Available in multiple states or regions
            8 – National availability via stores or online
            9 – Widespread presence in major chains and platforms
            10 – Global distribution and fulfillment
          ">?</span>
        </label>
        <input type="number" id="distribution" min="1" max="10" placeholder="8">
      </div>
    </div>
    <button id="predict-success" class="button primary-btn">Predict Success</button>
    <div id="prediction-results" class="results-container"></div>
  </div>

  <!-- History Section -->
  <div id="history-section" class="section-card">
    <h2>Prediction History</h2>
    <div class="history-controls">
      <button id="refresh-history" class="button secondary-btn">Refresh</button>
      <input type="text" id="history-search" placeholder="Search history...">
    </div>
    <div id="history-results" class="results-container">
      <table>
        <thead>
          <tr>
            <th>Title</th>
            <th>Score</th>
            <th>Price</th>
            <th>Category</th>
            <th>Date</th>
          </tr>
        </thead>
        <tbody id="history-table-body">
          <!-- Filled dynamically -->
        </tbody>
      </table>
    </div>
  </div>
</div>

<script type="module">
  import { pythonURI, fetchOptions } from '{{site.baseurl}}/assets/js/api/config.js';

  document.addEventListener('DOMContentLoaded', function() {
    const API_BASE = pythonURI + '/api';
    
    // Training Functionality
    document.getElementById('train-model').addEventListener('click', async function() {
      const trainingData = document.getElementById('training-data').value;
      const resultsDiv = document.getElementById('training-results');
      
      try {
        const data = JSON.parse(trainingData);
        resultsDiv.innerHTML = '<p class="loading">Training model...</p>';
        
        const response = await fetch(`${API_BASE}/train`, {
          ...fetchOptions,
          method: 'POST',
          body: JSON.stringify({ samples: data })
        });
        
        const result = await response.json();
        
        if (response.ok) {
          resultsDiv.innerHTML = `
            <div class="success-message">
              <h3>Model Trained Successfully</h3>
              <p>Samples used: ${result.samples_used}</p>
              <p>Accuracy (R²): ${result.r2_score?.toFixed(4) || 'N/A'}</p>
              <p>Average Error: ±${result.mae?.toFixed(2) || 'N/A'} points</p>
              <div class="feature-importance">
                <h4>What Matters Most:</h4>
                <ul>
                  ${Object.entries(result.feature_importance || {})
                    .map(([feature, score]) => `<li>${feature}: ${Math.round(score*100)}%</li>`)
                    .join('')}
                </ul>
              </div>
            </div>
          `;
        } else {
          throw new Error(result.message || 'Training failed');
        }
      } catch (error) {
        resultsDiv.innerHTML = `
          <div class="error-message">
            <h3>Training Error</h3>
            <p>${error.message}</p>
            ${error.message.includes('JSON') ? '<p>Please check your JSON format</p>' : ''}
          </div>
        `;
      }
    });

    // Prediction Functionality
    document.getElementById('predict-success').addEventListener('click', async function() {
      const type = document.getElementById('product-type').value;
      const seasonality = document.getElementById('seasonality').value;
      const price = parseFloat(document.getElementById('price').value);
      const marketing = parseInt(document.getElementById('marketing').value);
      const distribution = parseInt(document.getElementById('distribution').value);
      const resultsDiv = document.getElementById('prediction-results');
      
      if (!type || isNaN(price) || isNaN(marketing) || isNaN(distribution)) {
        resultsDiv.innerHTML = '<div class="error-message">Please fill all fields with valid values</div>';
        return;
      }
      if (price <= 0) {
        resultsDiv.innerHTML = '<div class="error-message">Please enter a valid price greater than 0</div>';
        return;
      }
      
      try {
        resultsDiv.innerHTML = '<p class="loading">Making prediction...</p>';
        
        const response = await fetch(`${API_BASE}/predict`, {
          ...fetchOptions,
          method: 'POST',
          body: JSON.stringify({
            product_type: type,
            seasonality: seasonality,
            price: price,
            marketing: marketing,
            distribution_channels: distribution
          })
        });
        
        const result = await response.json();
        
        if (response.ok) {
          const successClass = result.is_success ? 'success' : 'warning';
          resultsDiv.innerHTML = `
            <div class="prediction-result ${successClass}">
              <div class="score-display">
                <span class="score-value">${(result.score || 0).toFixed(1)}</span>
                <span class="score-label">Success Score</span>
                <span class="probability">${result.insights?.success_probability?.range || ''}</span>
              </div>
              <div class="prediction-details">
                <h3>${result.is_success ? '👍 Launch Recommended' : '👎 Needs Improvement'}</h3>
                <p class="category">${result.category || 'N/A'} • ${result.insights?.score_analysis?.label || ''}</p>
                ${renderInsights(result.insights, result)}
              </div>
            </div>
          `;
          loadHistory();
        } else {
          throw new Error(result.message || 'Prediction failed');
        }
      } catch (error) {
        resultsDiv.innerHTML = `
          <div class="error-message">
            <h3>Prediction Error</h3>
            <p>${error.message}</p>
            ${error.message.includes('trained') ? '<p>Please train the model first</p>' : ''}
          </div>
        `;
      }
    });

    // History Functionality
    async function loadHistory(searchTerm = '') {
      const tableBody = document.getElementById('history-table-body');
      tableBody.innerHTML = '<tr><td colspan="5" class="loading">Loading history...</td></tr>';
      
      try {
        const response = await fetch(`${API_BASE}/history`, {
          ...fetchOptions,
          method: 'GET'
        });
        const history = await response.json();
        
        if (response.ok) {
          let filtered = Array.isArray(history) ? history : [];
          if (searchTerm) {
            const term = searchTerm.toLowerCase();
            filtered = filtered.filter(item => 
              (item.product_type?.toLowerCase().includes(term) || false) ||
              (item.product_category?.toLowerCase().includes(term) || false) ||
              (item.price?.toString().includes(term) || false) ||
              (item.success_score?.toString().includes(term) || false)
            );
          }
          
          tableBody.innerHTML = filtered.length > 0 
            ? filtered.map(item => `
                <tr class="${item.predicted_success ? 'success-row' : 'warning-row'}">
                  <td>${item.product_type || 'N/A'}</td>
                  <td>${item.success_score?.toFixed(1) || 'N/A'}</td>
                  <td>$${item.price?.toFixed(2) || 'N/A'}</td>
                  <td>${item.product_category || 'N/A'}</td>
                  <td>${item.date_created ? new Date(item.date_created).toLocaleString() : 'N/A'}</td>
                </tr>
              `).join('')
            : '<tr><td colspan="5">No matching predictions found</td></tr>';
        } else {
          throw new Error(history.message || 'Failed to load history');
        }
      } catch (error) {
        tableBody.innerHTML = `<tr><td colspan="5" class="error">Error loading history: ${error.message}</td></tr>`;
      }
    }

    document.getElementById('refresh-history').addEventListener('click', () => loadHistory());
    document.getElementById('history-search').addEventListener('input', (e) => loadHistory(e.target.value));
    
    // Initial load
    loadHistory();
    
    // Helper function to render insights
    function renderInsights(insights, result) {
      if (!insights) {
        return '<div class="no-data">No insights data available</div>';
      }

      // Safe data access with fallbacks
      const safeGet = (obj, ...path) => {
        return path.reduce((acc, key) => (acc && acc[key] !== undefined ? acc[key] : null), obj);
      };

      const scoreAnalysis = {
        label: safeGet(insights, 'score_analysis', 'label'),
        range: safeGet(insights, 'score_analysis', 'range'),
        description: safeGet(insights, 'score_analysis', 'description'),
        risk_level: safeGet(insights, 'score_analysis', 'risk_level') || 0
      };

      const priceAnalysis = {
        current_price: safeGet(insights, 'price_analysis', 'current_price'),
        category_average: safeGet(insights, 'price_analysis', 'category_average'),
        position: safeGet(insights, 'price_analysis', 'position'),
        advice: safeGet(insights, 'price_analysis', 'advice'),
        price_range: {
          min: safeGet(insights, 'price_analysis', 'price_range', 'min'),
          max: safeGet(insights, 'price_analysis', 'price_range', 'max')
        }
      };

      const marketingAnalysis = {
        current: safeGet(insights, 'marketing_analysis', 'current'),
        average_successful: safeGet(insights, 'marketing_analysis', 'average_successful'),
        rating: safeGet(insights, 'marketing_analysis', 'rating'),
        advice: safeGet(insights, 'marketing_analysis', 'advice'),
        effective_range: {
          min: safeGet(insights, 'marketing_analysis', 'effective_range', 'min'),
          max: safeGet(insights, 'marketing_analysis', 'effective_range', 'max')
        }
      };

      const seasonalityAnalysis = {
        match: safeGet(insights, 'seasonality_analysis', 'match'),
        current_season: safeGet(insights, 'seasonality_analysis', 'current_season'),
        recommended_season: safeGet(insights, 'seasonality_analysis', 'recommended_season'),
        message: safeGet(insights, 'seasonality_analysis', 'message'),
        impact: safeGet(insights, 'seasonality_analysis', 'impact')
      };

      const successProbability = {
        range: safeGet(insights, 'success_probability', 'range'),
        confidence: safeGet(insights, 'success_probability', 'confidence')
      };

      const recommendations = safeGet(insights, 'recommendations') || [];

      // Calculate price position for visualization
      const calculatePricePosition = () => {
        if (!priceAnalysis.price_range || !priceAnalysis.current_price) return 50;
        const range = priceAnalysis.price_range.max - priceAnalysis.price_range.min;
        return ((priceAnalysis.current_price - priceAnalysis.price_range.min) / range) * 100;
      };

      return `
        <div class="insights-container">
          <!-- Score Analysis -->
          <div class="insight-card score-analysis">
            <h4>Success Potential</h4>
            ${scoreAnalysis.label ? `
              <div class="score-visualization">
                <div class="gauge-container">
                  <div class="gauge-labels">
                    <span>0</span>
                    <span>50</span>
                    <span>100</span>
                  </div>
                  <div class="gauge-track">
                    <div class="gauge-fill" style="width: ${result?.score || 0}%"></div>
                  </div>
                </div>
                <div class="score-details">
                  <h3>${scoreAnalysis.label} (${result?.score?.toFixed(1) || 'N/A'})</h3>
                  <p>${scoreAnalysis.description}</p>
                </div>
              </div>
            ` : '<p class="no-data">No score analysis available</p>'}
          </div>
          
          <!-- Price Analysis -->
          <div class="insight-card price-analysis">
            <h4>Price Positioning</h4>
            ${priceAnalysis.current_price ? `
              <div class="price-comparison">
                <div class="price-bar">
                  <div class="current-price-marker" style="left: ${calculatePricePosition()}%">
                    $${priceAnalysis.current_price.toFixed(2)}
                  </div>
                </div>
                <div class="range-labels">
                  <span>$${(priceAnalysis.price_range.min || 0).toFixed(2)}</span>
                  <span>Avg: $${(priceAnalysis.category_average || 0).toFixed(2)}</span>
                  <span>$${(priceAnalysis.price_range.max || 0).toFixed(2)}</span>
                </div>
              </div>
              <p><strong>${priceAnalysis.position || 'N/A'}</strong>: ${priceAnalysis.advice || ''}</p>
            ` : '<p class="no-data">No price analysis available</p>'}
          </div>
          
          <!-- Marketing Analysis -->
          <div class="insight-card marketing-analysis">
            <h4>Marketing Effectiveness</h4>
            ${marketingAnalysis.current ? `
              <div class="marketing-meter">
                <div class="meter-fill" style="width: ${(marketingAnalysis.current / 10) * 100}%"></div>
              </div>
              <p><strong>${marketingAnalysis.rating || 'N/A'}</strong>: ${marketingAnalysis.advice || ''}</p>
              <p>Effective range: ${marketingAnalysis.effective_range?.min || 'N/A'}-${marketingAnalysis.effective_range?.max || 'N/A'}/10</p>
            ` : '<p class="no-data">No marketing data available</p>'}


          </div>

          
          <!-- Recommendations -->
          <div class="insight-card recommendations">
            <h4>Actionable Recommendations</h4>
            ${recommendations.filter(r => !r.includes('$0.00') && !r.includes('None')).length ? `
              <ul>
                ${recommendations.filter(r => !r.includes('$0.00') && !r.includes('None'))
                  .map(r => `<li>${r}</li>`).join('')}
              </ul>
            ` : '<p class="no-data">No recommendations available</p>'}
          </div>
        </div>
      `;
    }
  });
</script>