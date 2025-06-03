# Optivize - Business Management Platform

## Introduction
Optivize is a business management platform that helps small businesses organize their inventory and predict product success. It's built with Jekyll for the website and Python for the backend, demonstrating full-stack web development skills.  
This project was created for Computer Science coursework to showcase web development, database management, and basic AI integration.

## Key Features
- **Product Success Predictor**: Upload business data to train an AI that predicts if products will succeed  
- **Inventory Manager**: Organize products into groups, track quantities, search and sort everything  
- **Google Sheets Import**: Connect your Google Sheets to automatically import inventory data  
- **Low Stock Alerts**: Set up notifications when you're running low on items  
- **Search Everything**: Find any product or group instantly as you type  

## How It Works
- **Frontend**: Website built with Jekyll that users interact with  
- **Backend**: Python server that handles data and AI predictions  
- **Database**: Stores all the inventory and user data  
- **External Services**: Connects to Google Sheets and Zapier for extra features  

## Quick Start

### What You Need
- Computer with Ubuntu/WSL or Mac  
- Git installed  
- Python installed  

### Setup Instructions
```bash
# Get the code
git clone https://github.com/ZafeerA123/optivize_frontend.git
git clone https://github.com/ZafeerA123/optivize_backend.git

# Start the website
cd optivize_frontend
make

# Start the server (in another terminal)
cd optivize_backend
python main.py
````

## View the Project

* **Website**: Open [http://127.0.0.1:4887/optivize\_frontend/](http://127.0.0.1:4887/optivize_frontend/)
* **Live Version**: [https://optivize.opencodingsociety.com/](https://optivize.opencodingsociety.com/)

## Project Files

### Frontend (Website)

```
├── navigation/
│   ├── productprediction.md    # AI prediction page
│   ├── flashcards.md          # Inventory management page
│   └── about.md               # About page
├── assets/js/                 # JavaScript files
├── _config.yml               # Website settings
└── index.md                  # Homepage
```

### Backend (Server)

```
├── main.py                   # Main server file
├── api/                      # API endpoints
├── models/                   # Database setup
└── requirements.txt          # Python packages needed
```

## Main Features Explained

### 1. AI Product Predictor (`productprediction.md`)

* Users enter product details (name, price, marketing score, etc.)
* AI gives a success score from 0–100
* Shows business advice like "your price is too high"
* Users can train the AI with their own data

### 2. Inventory Manager (`flashcards.md`)

* Create groups to organize products (like "Electronics", "Clothing")
* Add items to each group with quantities and descriptions
* Search through everything instantly
* Sort by name, quantity, or date

### 3. Google Sheets Import

* Connect your Google account safely
* Import inventory data from your existing spreadsheets
* Automatically converts sheet data into our format

### 4. Smart Alerts

* Set up notifications when inventory gets low
* Works with Zapier to send emails or texts
* No more running out of stock unexpectedly

## Development Commands

### Frontend (Website)

* `make` – Start the website
* `make stop` – Stop the website
* `make clean` – Reset everything

### Backend (Server)

* `python main.py` – Start the server
* `python -m pytest` – Run tests (if any)

## File Organization

### Adding New Pages

* Create a new `.md` file in the `navigation/` folder
* Add it to `_config.yml` under `header_pages:`
* Write your content in markdown

## Database Structure

* **Groups**: Store inventory categories
* **Items**: Store individual products with quantities
* **Users**: Store user accounts and settings
* **Predictions**: Store AI prediction history

---

## 📅 Calendar

* The calendar helps businesses visualize important events like:

  * Product launches
  * Restock dates
  * Prediction runs
  * Inventory reviews
* Implemented with a lightweight JS library integrated into `calendar.md`
* Pulls events from the backend based on prediction & inventory history

---

## 🌐 Frontend Integration

* Real-time API integration using JS `fetch()` to communicate with Flask backend
* Fully dynamic updates for:

  * Inventory changes
  * Prediction results
  * Calendar entries
* Frontend is modular:

  * `productprediction.md`: Hooks into `/api/predict`
  * `flashcards.md`: Fetches and manages inventory via `/api/items` and `/api/groups`
  * `calendar.md`: Loads events from `/api/calendar`


