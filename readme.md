# Global Mental Health Dashboard

A comprehensive dashboard system for tracking and monitoring mental health data worldwide, featuring real-time scalability comparison between local JSON processing and MongoDB Atlas cloud queries.

---

## Project Overview

This project implements a web-based dashboard to analyze global mental health trends, focusing on depression rates by region. It combines local JSON datasets with MongoDB Atlas cloud storage and provides interactive visualizations with live performance metrics.

**Key Technologies:** Java, Groovy, MongoDB Atlas, Chart.js, HTML/CSS/JavaScript

---

## Software Artifacts Location

### **Core Java Applications**

| Artifact | Location | Description |
|----------|----------|-------------|
| **Dashboard Web Server** | `src/main/java/DashboardServer.java` | Main web server with integrated scalability testing, API endpoints, and MongoDB connection |
| **Scalability Comparison** | `src/main/java/ScalabilityComparison.java` | Standalone Java application for comprehensive performance testing (Local vs MongoDB) |

### **Groovy Scripts**

| Script | Location | Description |
|--------|----------|-------------|
| **Local JSON Query** | `src/main/groovy/query1.groovy` | Analyzes local JSON dataset, finds top depression regions |
| **MongoDB Query** | `src/main/groovy/mongo_query.groovy` | Executes cloud queries against MongoDB Atlas |
| **Groovy Scalability Test** | `src/main/groovy/QueryScalabilityLocal.groovy` | Local scalability testing with increasing dataset sizes |

### **Web Dashboard Files**

| File | Location | Description |
|------|----------|-------------|
| **HTML Interface** | `src/main/resources/public/index.html` | Dashboard frontend with charts and statistics |
| **Styling** | `src/main/resources/public/style.css` | Modern gradient design, responsive layout |
| **JavaScript Logic** | `src/main/resources/public/script.js` | API integration, Chart.js visualizations, real-time updates |

### **Configuration & Data**

| File | Location | Description |
|------|----------|-------------|
| **Gradle Build** | `build.gradle` | Project dependencies and task definitions |
| **Dataset** | `src/main/resources/mental_health_data.json` | Primary mental health dataset |
| **Test Datasets** | `mental_health_[1-10]x.json` | Scalability test files (root directory) |

---

## Running the Software Artifacts

### **1. Launch Interactive Web Dashboard** (Recommended)
```bash
.\gradlew run
```
**Access:** http://localhost:8080

**Features:**
- Real-time data overview (total records, depression cases)
- Interactive bar chart: Top 5 regions by depression rate
- Live scalability comparison chart (Local vs MongoDB)
- Performance metrics with speedup calculations

**API Endpoints:**
- `/api/local-summary` - Dataset statistics
- `/api/top-regions` - MongoDB aggregation results
- `/api/scalability-comparison` - Real-time performance tests
- `/api/status` - Health check

---

### **2. Run Standalone Java Scalability Test**
```bash
.\gradlew runJavaScalability
```
**Output:**
- CLI comparison table
- Performance summary statistics
- `scalability_full_comparison_java.png` visualization
- Interactive JFreeChart window

**Requirements:** Test files `mental_health_1x.json` through `mental_health_10x.json`

---

### **3. Execute Groovy Analysis Scripts**

#### Local JSON Analysis
```bash
.\gradlew runLocalQuery
```
Analyzes local dataset, prints top 5 regions with highest depression rates.

#### MongoDB Cloud Query
```bash
.\gradlew runMongoQuery
```
Fetches and displays top regions from MongoDB Atlas using aggregation pipeline.

#### Groovy Scalability Test
```bash
.\gradlew runGroovyScalability
```
Performance testing with progressively larger datasets (1x–10x multipliers).

---

## Key Features

- **Dual-Mode Analysis:** Local JSON processing + Cloud MongoDB queries  
- **Real-Time Scalability Testing:** Integrated performance comparison  
- **Interactive Visualizations:** Chart.js-powered bar and line charts  
- **RESTful API:** JSON endpoints for data access  
- **Responsive Design:** Modern gradient UI with hover effects  
- **Caching Mechanism:** 5-minute cache for scalability results  
- **Comprehensive Metrics:** Average rates, speedup factors, execution times

---

## Technical Stack

**Backend:**
- Java 21
- Groovy 5.0.2
- MongoDB Driver 4.9.0
- Jackson Databind 2.17.0
- JFreeChart 1.5.4

**Frontend:**
- HTML5, CSS3 
- Vanilla JavaScript (ES6+)
- Chart.js 4.4.0

**Build Tool:**
- Gradle 9.2.0 with wrapper scripts

---

## Dashboard Components

### **Data Overview Card**
Displays total records and depression case counts from local dataset.

### **Top Regions Chart (Bar)**
Interactive bar chart showing the 5 regions with highest average depression rates (MongoDB data).

### **Scalability Comparison Chart (Line)**
Real-time performance comparison:
- **Red line:** Local JSON processing time
- **Blue line:** MongoDB Atlas query time
- Shows exponential scaling differences

### **Performance Summary**
Calculated metrics:
- Average local query time
- Average MongoDB query time
- Performance speedup factor

---

## Configuration

### MongoDB Connection
Update the connection URI in both Java files:
```java
String uri = "mongodb+srv://studentuser191_db_user:lbysikFIHbIvynRd@mentalhealthcluster.ivxoqlx.mongodb.net/?appName=mentalhealthCluster";
```

**Files to update:**
- `src/main/java/DashboardServer.java`
- `src/main/java/ScalabilityComparison.java`
- `src/main/groovy/mongo_query.groovy`

### Dataset Location
Ensure `mental_health_data.json` exists at:
```
src/main/resources/mental_health_data.json
```

### Scalability Test Files
For full functionality, include in project root:
```
mental_health_1x.json
mental_health_2x.json
mental_health_4x.json
mental_health_8x.json
mental_health_10x.json
```

---

## Project Structure
```
Global_Mental_Health/
│
├── build.gradle                          # Gradle dependencies & tasks
├── settings.gradle
├── gradlew / gradlew.bat                 # Gradle wrapper
│
├── src/
│   ├── main/
│   │   ├── groovy/
│   │   │   ├── query1.groovy             # Local JSON analysis
│   │   │   ├── mongo_query.groovy        # MongoDB cloud query
│   │   │   └── QueryScalabilityLocal.groovy  # Groovy scalability test
│   │   │
│   │   ├── java/
│   │   │   ├── DashboardServer.java      # Main web server + API
│   │   │   └── ScalabilityComparison.java # Standalone performance tester
│   │   │
│   │   └── resources/
│   │       ├── mental_health_data.json   # Primary dataset
│   │       └── public/                   # Web dashboard assets
│   │           ├── index.html            # Dashboard UI
│   │           ├── style.css             # Styling
│   │           └── script.js             # Frontend logic
│
├── mental_health_[1-10]x.json            # Scalability test datasets
├── scalability_full_comparison_java.png  # Generated chart
└── README.md                             # This file
```

---

## Testing the Dashboard

1. **Start the server:**
   ```bash
   .\gradlew run
   ```

2. **Open browser:**
   Navigate to http://localhost:8080

3. **Verify functionality:**
   - Data Overview loads statistics
   - Top Regions chart displays bar graph
   - Scalability chart shows comparison (may take 10-30 seconds on first load)
   - Performance summary displays speedup metrics

4. **Check API responses:**
   ```bash
   curl http://localhost:8080/api/local-summary
   curl http://localhost:8080/api/top-regions
   curl http://localhost:8080/api/scalability-comparison
   ```

---

## Key Implementations

### **Real-Time Scalability Testing**
The dashboard now runs actual performance tests when you access `/api/scalability-comparison`:
- Loads multiple dataset sizes (1x through 10x)
- Measures local JSON processing time
- Measures MongoDB query execution time
- Caches results for 5 minutes
- Returns detailed comparison data

### **MongoDB Aggregation Pipeline**
```javascript
$match → $group → $sort → $limit
```
Efficiently processes cloud data to find top depression regions.

### **Chart.js Integration**
- Dynamic data loading from API endpoints
- Responsive charts that resize with viewport
- Interactive tooltips with formatted values
- Gradient fills and smooth animations

---

## Clean Build
Before submission or deployment:
```bash
.\gradlew clean
```
Removes build artifacts, reducing project size and supporting sustainable software practices.



