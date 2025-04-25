---
layout: base
title: Crumbl
description: Product Success Prediction
hide: true
permalink: /predictions
---
<style>
/* Reset and base styles */
html, body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    overflow-x: hidden;
    font-family: 'Poppins', sans-serif;
    background: url('https://i.imgur.com/7R0g4Kg.jpg'); /* Cookie pattern background */
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    position: relative;
    z-index: 0;
}

/* Sprinkle overlay full-screen */
.sprinkle-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    overflow: hidden;
    pointer-events: none;
    z-index: 1;
}

/* Sprinkle styles */
.sprinkle {
    position: absolute;
    width: 6px;
    height: 6px;
    border-radius: 50%;
    animation: sprinkleFall linear infinite;
    z-index: 1;
}

/* Sprinkle animation keyframes */
@keyframes sprinkleFall {
    0% {
        transform: translateY(-10px) rotate(0deg);
        opacity: 1;
    }
    100% {
        transform: translateY(110vh) rotate(360deg);
        opacity: 0;
    }
}

/* Container over backdrop */
.main-content {
    position: relative;
    z-index: 2;
    text-align: center;
    padding: 2rem;
    background: rgba(255, 255, 255, 0.8);
    margin: 2rem;
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}

/* Heading with cookie font style */
.main-content h1 {
    font-size: 3rem;
    color: #5a3e36;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
}

/* Button styles */
.button {
    background: #ffb4a2;
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 30px;
    font-weight: bold;
    cursor: pointer;
    transition: all 0.3s ease;
}

.button:hover {
    background: #ffcad4;
    transform: translateY(-2px);
}

/* Optional: fade-in animation for main content */
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
}
.main-content {
    animation: fadeIn 1s ease forwards;
}
</style>

<div class="sprinkle-overlay" id="sprinkle-overlay"></div>

<script>
const sprinkleColors = ['#ffafcc', '#ffcba4', '#b5ead7', '#caffbf', '#9bf6ff', '#a0c4ff', '#e0c3fc'];
const overlay = document.getElementById('sprinkle-overlay');

function createSprinkle() {
    const sprinkle = document.createElement('div');
    sprinkle.classList.add('sprinkle');
    const size = Math.random() * 4 + 6;
    sprinkle.style.width = `${size}px`;
    sprinkle.style.height = `${size}px`;
    sprinkle.style.left = `${Math.random() * window.innerWidth}px`;
    sprinkle.style.backgroundColor = sprinkleColors[Math.floor(Math.random() * sprinkleColors.length)];
    sprinkle.style.animationDuration = `${Math.random() * 5 + 5}s`;
    sprinkle.style.opacity = Math.random() * 0.5 + 0.5;

    overlay.appendChild(sprinkle);
    setTimeout(() => sprinkle.remove(), 10000);
}

setInterval(createSprinkle, 100);
</script>

<div class="cookie-prediction-container">
  <!-- Training Section -->
  <div class="section-card">
    <h2>Train Model</h2>
    <div class="form-group">
      <label>Training Samples (JSON)</label>
      <textarea id="training-data" rows="8" placeholder='[
  {
    "cookie_flavor": "Double Chocolate",
    "seasonality": "All Year",
    "price": 3.75,
    "marketing": 8,
    "distribution_channels": 9,
    "success_score": 82
  },
  {
    "cookie_flavor": "Pumpkin Spice",
    "seasonality": "Fall",
    "price": 4.25,
    "marketing": 7,
    "distribution_channels": 8,
    "success_score": 78
  }
]'></textarea>
    </div>
    <button id="train-model" class="primary-btn">Train Model</button>
    <div id="training-results" class="results-container"></div>
  </div>

  <!-- Prediction Section -->
  <div class="section-card">
    <h2>Predict Success</h2>
    <div class="form-row">
      <div class="form-group">
        <label>Cookie Flavor</label>
        <input type="text" id="cookie-flavor" placeholder="e.g. Triple Chocolate">
      </div>
      <div class="form-group">
        <label>Seasonality</label>
        <select id="seasonality">
          <option value="All Year">All Year</option>
          <option value="Winter">Winter</option>
          <option value="Spring">Spring</option>
          <option value="Summer">Summer</option>
          <option value="Fall">Fall</option>
          <option value="Holiday">Holiday</option>
          <option value="Seasonal">Holiday</option> # Ill have to test this later

        </select>
      </div>
    </div>
    <div class="form-row">
      <div class="form-group">
        <label>Price ($)</label>
        <input type="number" id="price" step="0.01" min="0" placeholder="3.99">
      </div>
      <div class="form-group">
        <label>Marketing (1-10)</label>
        <input type="number" id="marketing" min="1" max="10" placeholder="7">
      </div>
      <div class="form-group">
        <label>Distribution (1-10)</label>
        <input type="number" id="distribution" min="1" max="10" placeholder="8">
      </div>
    </div>
    <button id="predict-success" class="primary-btn">Predict Success</button>
    <div id="prediction-results" class="results-container"></div>
  </div>

  <!-- History Section -->
  <div class="section-card">
    <h2>Prediction History</h2>
    <div class="history-controls">
      <button id="refresh-history" class="secondary-btn">Refresh</button>
      <input type="text" id="history-search" placeholder="Search history...">
    </div>
    <div id="history-results" class="results-container">
      <table>
        <thead>
          <tr>
            <th>Flavor</th>
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

    // Enhanced Insight Rendering with Fallbacks
    function renderInsights(insights, result) {
      if (!insights) {
        return `
          <div class="error-message">
            <h4>Data Loading Issue</h4>
            <p>No insights data was received from the server.</p>
            <p>Possible causes:</p>
            <ul>
              <li>Model not properly trained</li>
              <li>Insufficient historical data</li>
              <li>Backend API issue</li>
            </ul>
          </div>
        `;
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
                  ${scoreAnalysis.distribution_analysis ? `
                    <div class="distribution-analysis">
                      <h4>Distribution Analysis</h4>
                      <div class="distribution-meter">
                        <div class="meter-fill" 
                            style="width: ${((scoreAnalysis.distribution_score || 0) / 10) * 100}%"></div>
                        <span>${scoreAnalysis.distribution_score || 0}/10</span>
                      </div>
                      <p>${scoreAnalysis.distribution_analysis}</p>
                    </div>
                  ` : ''}
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
                  <div class="range-labels">
                    <span>$${(priceAnalysis.price_range.min || 0).toFixed(2)}</span>
                    <span>Avg: $${(priceAnalysis.category_average || 0).toFixed(2)}</span>
                    <span>$${(priceAnalysis.price_range.max || 0).toFixed(2)}</span>
                  </div>
                </div>
              </div>
              <p><strong>${priceAnalysis.position || 'N/A'}</strong>: ${priceAnalysis.advice || ''}</p>
            ` : '<p class="no-data">No price analysis available</p>'}
          </div>
          <!-- NEW Distribution Analysis Card -->
          ${renderDistributionAnalysis(insights.distribution_analysis)}
          <!-- Marketing Analysis -->
          <div class="insight-card marketing-analysis">
            <h4>Marketing Effectiveness</h4>
            ${marketingAnalysis.current ? `
              <div class="marketing-meter">
                <div class="meter-fill" style="width: ${(marketingAnalysis.current / 10) * 100}%"></div>
                <span>${marketingAnalysis.current}/10 (Avg: ${marketingAnalysis.average_successful?.toFixed(1) || 'N/A'})</span>
              </div>
              <p><strong>${marketingAnalysis.rating || 'N/A'}</strong>: ${marketingAnalysis.advice || ''}</p>
              <p>Effective range: ${marketingAnalysis.effective_range?.min || 'N/A'}-${marketingAnalysis.effective_range?.max || 'N/A'}/10</p>
            ` : '<p class="no-data">No marketing data available</p>'}
          </div>
          
          <!-- Seasonality Analysis -->
          <div class="insight-card seasonality-analysis ${seasonalityAnalysis.match ? 'match' : 'mismatch'}">
            <h4>Seasonal Timing</h4>
            ${seasonalityAnalysis.message ? `
              <p>${seasonalityAnalysis.message}</p>
              <p>Current: ${seasonalityAnalysis.current_season || 'N/A'}</p>
              <p>Recommended: ${seasonalityAnalysis.recommended_season || 'N/A'}</p>
              <p class="impact">${seasonalityAnalysis.impact || ''}</p>
            ` : '<p class="no-data">No seasonality data available</p>'}
          </div>
          
          <!-- Recommendations -->
          <div class="insight-card recommendations">
            <h4>Actionable Recommendations</h4>
            ${recommendations.length ? `
              <ul>
                ${recommendations.map(r => `<li>${r}</li>`).join('')}
              </ul>
            ` : '<p class="no-data">No recommendations available</p>'}
          </div>
        </div>
      `;
    }

    function renderDistributionAnalysis(distAnalysis) {
      if (!distAnalysis) return '<div class="no-data">No distribution data</div>';

      return `
        <div class="insight-card distribution-analysis">
          <h4>Distribution Channels</h4>
          
          <div class="distribution-header">
            <div class="distribution-score">
              <span class="score">${distAnalysis.score}/100</span>
              <span class="rating">${distAnalysis.rating}</span>
            </div>
            <div class="distribution-meter">
              <div class="meter-fill" style="width: ${distAnalysis.score * 10}%"></div>
            </div>
          </div>
          
          <p class="distribution-description">${distAnalysis.description}</p>
          
          <div class="channel-details">
            <h5>Current Channel Status:</h5>
            <ul class="channel-list">
              ${distAnalysis.channel_analysis.map(item => `<li>${item}</li>`).join('')}
            </ul>
          </div>
          
          <div class="distribution-recommendations">
            <h5>Recommendations:</h5>
            <ul class="recommendation-list">
              ${distAnalysis.recommendations.map(item => `<li>${item}</li>`).join('')}
            </ul>
          </div>
        </div>
      `;
    }
    // Prediction Functionality with Debugging
    document.getElementById('predict-success').addEventListener('click', async function() {
      const flavor = document.getElementById('cookie-flavor').value;
      const seasonality = document.getElementById('seasonality').value;
      const price = parseFloat(document.getElementById('price').value);
      const marketing = parseInt(document.getElementById('marketing').value);
      const distribution = parseInt(document.getElementById('distribution').value);
      const resultsDiv = document.getElementById('prediction-results');
      
      if (!flavor || isNaN(price) || isNaN(marketing) || isNaN(distribution)) {
        resultsDiv.innerHTML = '<div class="error-message">Please fill all fields with valid values</div>';
        return;
      }
      
      try {
        resultsDiv.innerHTML = '<p class="loading">Making prediction...</p>';
        
        const response = await fetch(`${API_BASE}/predict`, {
          ...fetchOptions,
          method: 'POST',
          body: JSON.stringify({
            cookie_flavor: flavor,
            seasonality: seasonality,
            price: price,
            marketing: marketing,
            distribution_channels: distribution
          })
        });
        
        const result = await response.json();
        console.log("API Response:", result);  // Debugging line
        
        if (response.ok) {
          const successClass = result.is_success ? 'success' : 'warning';
          resultsDiv.innerHTML = `
            <div class="prediction-result ${successClass}">
              <div class="score-display">
                  <span class="score-value">${(result.score || 0).toFixed(1)}%</span>  <!-- Ensuring it's a percentage -->
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
        console.error("Prediction error:", error);  // Debugging line
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
        console.log("History data:", history);  // Debugging line
        
        if (response.ok) {
          let filtered = Array.isArray(history) ? history : [];
          if (searchTerm) {
            const term = searchTerm.toLowerCase();
            filtered = filtered.filter(item => 
              (item.cookie_flavor?.toLowerCase().includes(term) || false) ||
              (item.product_category?.toLowerCase().includes(term) || false) ||
              (item.price?.toString().includes(term) || false) ||
              (item.success_score?.toString().includes(term) || false)
            );
          }
          
          tableBody.innerHTML = filtered.length > 0 
            ? filtered.map(item => `
                <tr class="${item.predicted_success ? 'success-row' : 'warning-row'}">
                  <td>${item.cookie_flavor || 'N/A'}</td>
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
        console.error("History load error:", error);  // Debugging line
        tableBody.innerHTML = `<tr><td colspan="5" class="error">Error loading history: ${error.message}</td></tr>`;
      }
    }

    document.getElementById('refresh-history').addEventListener('click', () => loadHistory());
    document.getElementById('history-search').addEventListener('input', (e) => loadHistory(e.target.value));
    
    // Initial load
    loadHistory();
  });
</script>

<style>
.cookie-prediction-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

.section-card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  padding: 20px;
  margin-bottom: 20px;
}

.form-group {
  margin-bottom: 15px;
}

.form-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.form-row {
  display: flex;
  gap: 15px;
}

.form-row .form-group {
  flex: 1;
}

.primary-btn {
  background: #4CAF50;
  color: white;
  border: none;
  padding: 10px 15px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

.secondary-btn {
  background: #f0f0f0;
  border: none;
  padding: 8px 12px;
  border-radius: 4px;
  cursor: pointer;
}

.results-container {
  margin-top: 20px;
  padding: 15px;
  border-radius: 4px;
}

.loading {
  color: #666;
  font-style: italic;
}

.success-message {
  background: #e8f5e9;
  padding: 15px;
  border-left: 4px solid #4CAF50;
}

.error-message {
  background: #ffebee;
  padding: 15px;
  border-left: 4px solid #f44336;
}

.prediction-result {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 15px;
}

.prediction-result.success {
  background: #e8f5e9;
  border-left: 4px solid #4CAF50;
}

.prediction-result.warning {
  background: #fff8e1;
  border-left: 4px solid #ffc107;
}

.score-display {
  text-align: center;
}

.score-value {
  font-size: 2.5rem;
  font-weight: bold;
  display: block;
}

.score-label {
  font-size: 0.9rem;
  color: #666;
}

.probability {
  display: block;
  font-size: 0.9rem;
  color: #666;
}

.category {
  font-size: 0.9rem;
  color: #666;
  margin-top: -10px;
  font-style: italic;
}

/* Insights Styles */
.insights-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.insight-card {
  background: white;
  border-radius: 8px;
  padding: 15px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.05);
}

.insight-card h4 {
  margin-top: 0;
  color: #333;
  border-bottom: 1px solid #eee;
  padding-bottom: 8px;
}

.gauge, .marketing-meter {
  height: 20px;
  background: #f0f0f0;
  border-radius: 10px;
  margin: 10px 0;
  position: relative;
}

.gauge-fill {
  height: 100%;
  background: linear-gradient(to right, #4CAF50, #FFC107);
  border-radius: 10px;
}

.meter-fill {
  height: 100%;
  background: linear-gradient(to right, #2196F3, #9C27B0);
  border-radius: 10px;
}

.price-comparison {
  margin: 15px 0;
}

.price-bar {
  height: 30px;
  background: linear-gradient(to right, #8BC34A, #FFC107, #F44336);
  border-radius: 4px;
  position: relative;
}

.current-price-marker {
  position: absolute;
  top: -25px;
  transform: translateX(-50%);
  background: #333;
  color: white;
  padding: 2px 6px;
  border-radius: 4px;
  font-size: 12px;
}

.range-labels {
  display: flex;
  justify-content: space-between;
  margin-top: 5px;
  font-size: 12px;
  color: #666;
}

.seasonality-analysis.match {
  border-left: 4px solid #4CAF50;
}

.seasonality-analysis.mismatch {
  border-left: 4px solid #FFC107;
}

.impact {
  font-weight: bold;
  margin-top: 8px;
}

.no-data {
  color: #666;
  font-style: italic;
}

/* History Table Styles */
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

th, td {
  padding: 12px 15px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

th {
  background: #f5f5f5;
  font-weight: bold;
}

.success-row {
  background-color: #e8f5e9;
}

.warning-row {
  background-color: #fff8e1;
}

.history-controls {
  display: flex;
  gap: 10px;
  margin-bottom: 15px;
}

.history-controls input {
  flex: 1;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
/* Updated Gauge Styles */
.score-visualization {
  display: flex;
  gap: 20px;
  align-items: center;
}

.gauge-container {
  flex: 1;
  max-width: 200px;
}

.gauge-track {
  height: 20px;
  background: #f0f0f0;
  border-radius: 10px;
  position: relative;
  overflow: hidden;
}

.gauge-fill {
  height: 100%;
  background: linear-gradient(to right, #f44336, #FFC107, #4CAF50);
  border-radius: 10px;
  transition: width 0.5s ease;
}

.gauge-labels {
  display: flex;
  justify-content: space-between;
  font-size: 12px;
  color: #666;
  margin-bottom: 5px;
}

.score-details {
  flex: 2;
}

.distribution-analysis {
  margin-top: 15px;
  padding-top: 15px;
  border-top: 1px solid #eee;
}

.distribution-meter {
  height: 15px;
  background: #f0f0f0;
  border-radius: 7px;
  margin: 8px 0;
  position: relative;
  overflow: hidden;
}

.distribution-meter .meter-fill {
  height: 100%;
  background: linear-gradient(to right, #2196F3, #3F51B5);
  border-radius: 7px;
}

.distribution-meter span {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 10px;
  font-weight: bold;
  text-shadow: 0 1px 1px rgba(0,0,0,0.3);
}
/* Distribution Analysis Card */
.insight-card.distribution-analysis {
  border-left: 4px solid #3F51B5;
  background: white;
}

.distribution-header {
  display: flex;
  align-items: center;
  gap: 15px;
  margin: 15px 0;
}

.distribution-score {
  display: flex;
  flex-direction: column;
  min-width: 80px;
}

.distribution-score .score {
  font-size: 1.8rem;
  font-weight: bold;
  color: #3F51B5;
  line-height: 1;
}

.distribution-score .rating {
  font-size: 0.9rem;
  color: #666;
}

.distribution-meter {
  flex-grow: 1;
  height: 20px;
  background: #f0f0f0;
  border-radius: 10px;
  overflow: hidden;
}

.distribution-meter .meter-fill {
  height: 100%;
  background: linear-gradient(to right, #2196F3, #3F51B5);
  transition: width 0.5s ease;
}

.distribution-description {
  color: #444;
  margin: 15px 0;
  line-height: 1.5;
}

.channel-details, .distribution-recommendations {
  margin-top: 15px;
  padding-top: 15px;
  border-top: 1px solid #eee;
}

.channel-details h5, .distribution-recommendations h5 {
  margin-top: 0;
  color: #333;
}

.channel-list, .recommendation-list {
  padding-left: 20px;
  margin: 10px 0;
}

.channel-list li {
  margin-bottom: 8px;
  color: #555;
  list-style-type: disc;
}

.recommendation-list li {
  margin-bottom: 8px;
  color: #3F51B5;
  font-weight: 500;
  list-style-type: circle;
}
</style>