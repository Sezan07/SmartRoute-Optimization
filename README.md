# SmartRoute-Optimization

## Team - Mavericks

### Introduction
SmartRoute Optimizer is a web-based application built using Streamlit for optimizing delivery routes. It leverages geospatial algorithms to efficiently assign vehicles, compute optimal routes, and visualize trip details on an interactive map. The application allows users to upload shipment data, select delivery time slots, and generate optimized routes for efficient logistics operations.

---

## Features
- **Shipment Data Upload:** Users can upload shipment data in `.xlsx` format.
- **Time Slot Selection:** Select a preferred time slot for route optimization.
- **Optimized Trip Generation:** View optimized delivery trips with assigned vehicle details and performance metrics.
- **Interactive Route Visualization:** Display trip routes on an interactive map with shipment locations and route paths.

---

## System Requirements
### Prerequisites
To run SmartRoute Optimizer locally, ensure the following dependencies are installed:
- Python 3.8+
- Required Python Libraries

Install the necessary libraries using:
```sh
pip install streamlit pandas folium openpyxl streamlit-folium streamlit-lottie subprocess
```

---

## Installation & Setup

### Step 1: Clone the Repository
Clone the SmartRoute Optimizer repository to your local machine:
```sh
git clone https://github.com/Sezan07/SmartRoute-Optimization
cd SmartRoute-Optimizer
```

### Step 2: Install Dependencies
Install all required dependencies using:
```sh
pip install -r requirements.txt
```
Alternatively, you can install them individually using:
```sh
pip install pandas folium openpyxl streamlit-folium streamlit-lottie subprocess
```

### Step 3: Prepare the Input File
The shipment data file should be in `.xlsx` format and must contain the following columns:
- Shipment ID
- Latitude
- Longitude
- Delivery Timeslot
- Additional relevant details

### Step 4: Run the Application
Start the Streamlit application by running:
```sh
streamlit run app.py
```
This command will launch the app in a web browser, allowing you to interact with the SmartRoute Optimizer interface.

---

## Application Workflow
1. **Upload Shipment Data**
   - Users can upload a `.xlsx` file containing shipment details through the Upload Shipment Data section.
2. **Select a Time Slot**
   - Select a delivery time slot for which optimization should be performed.
3. **Start Optimization**
   - Click on "Start Optimization" to execute the backend process, which will generate optimized trip details.
4. **View Optimized Trips**
   - After optimization, users can view trip details, including:
     - Trip ID
     - Vehicle Type
     - Total Distance
     - Trip Duration
     - Performance Metrics
5. **Route Visualization**
   - Users can select a Trip ID to visualize its route on an interactive folium map.

---

## System Architecture
### Backend (Optimization Engine)
The `backend.py` script handles:
1. **Data Processing:** Reads shipment data (latitude, longitude, timeslot, etc.).
2. **Route Optimization:** Uses a genetic algorithm to assign vehicles and compute the most efficient routes.
3. **Output Generation:** Exports optimized trip data into `optimized_trips.xlsx`.

### Frontend (Streamlit UI)
The frontend provides:
- A file upload interface for shipment data.
- A time slot selection dropdown.
- Optimized trip details displayed in a table.
- A folium-based interactive map for route visualization.

---

## Data Format
### Sample Shipment Data (`Shipment_Data.xlsx`)
| Shipment ID | Latitude | Longitude | Delivery Timeslot |
|------------|----------|----------|------------------|
| S1         | 19.0760  | 72.8777  | 9:30-12:00      |
| S2         | 19.0820  | 72.8820  | 9:30-12:00      |

### Sample Optimized Output (`optimized_trips.xlsx`)
| TRIP ID | Shipment IDs | MST_DIST | TRIP_TIME | Vehicle Type | CAPACITY_UTI | TIME_UTI | COV_UTI |
|---------|-------------|----------|-----------|--------------|--------------|---------|--------|
| T101    | S1, S2      | 15.2     | 45        | 3W           | 0.8          | 0.9     | 0.95   |
| T102    | S3, S4      | 18.4     | 60        | 4W-EV        | 0.75         | 0.85    | 0.92   |
