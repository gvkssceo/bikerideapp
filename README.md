# 🚲 Bike Taxi Service - Complete Microservices Architecture

A complete bike taxi booking system built with Spring Boot, Kafka, PostgreSQL, and real-time WebSocket communication.

## 🏗️ Project Architecture

```
🧱 Project 1: Booking Service (Spring Boot + Kafka Producer + PostgreSQL + WebSocket)
🧠 Project 2: Matching Service (Spring Boot + Kafka Consumer + Geohash)
🗺️ Project 3: Rider UI (HTML/JS + Google Maps API)
🚗 Project 4: Driver Simulator (WebSocket Client)
🐳 Project 5: Infrastructure (Kafka + PostgreSQL via Docker)
```

## 🚀 Quick Start

### 1. Start Infrastructure
```bash
# Start Kafka
cd kafka
docker-compose -f docker-compose-kafka.yml up -d

# Start PostgreSQL
cd ..
docker-compose up -d
```

### 2. Run Services
```bash
# Booking Service (Port 8080)
cd booking-service
./mvnw spring-boot:run

# Matching Service (Port 8081) - in new terminal
cd driver-matching-service
./mvnw spring-boot:run
```

### 3. Run Frontend
```bash
# Rider UI (Port 5500)
cd map-client
python -m http.server 5500

# Driver Simulator (Port 5600)
cd driver-simulator
python -m http.server 5600
```

### 4. Test the System
1. Open http://localhost:5500 (Rider UI)
2. Open http://localhost:5600 (Driver Simulator)
3. Click on map to set pickup/drop points
4. Click "Book" to create a booking
5. Watch real-time driver locations!

## 📁 Project Structure

```
bike-taxi-service/
├── booking-service/             # Project 1: Booking API
├── driver-matching-service/     # Project 2: Driver Matching
├── map-client/                  # Project 3: Rider Frontend
├── driver-simulator/            # Project 4: Driver App
├── kafka/                       # Project 5: Kafka Infrastructure
├── docker-compose.yml           # PostgreSQL
└── README.md
```

## 🔧 Tech Stack

- **Backend**: Spring Boot 3.3.0, Java 17
- **Message Queue**: Apache Kafka
- **Database**: PostgreSQL
- **Real-time**: WebSocket
- **Frontend**: HTML, JavaScript, Google Maps API
- **Infrastructure**: Docker, Docker Compose

## 📊 Data Flow

1. **User** → Rider UI → Booking Service
2. **Booking Service** → PostgreSQL (save) + Kafka (publish)
3. **Kafka** → Matching Service (consume)
4. **Driver Simulator** → WebSocket → Booking Service
5. **Booking Service** → WebSocket → Rider UI (live drivers)

## 🎯 Features

- ✅ Real-time driver location tracking
- ✅ Geohash-based driver matching
- ✅ Kafka event-driven architecture
- ✅ WebSocket live updates
- ✅ Google Maps integration
- ✅ Microservices design

## 🔍 API Endpoints

- `POST /booking` - Create new booking
- `GET /match/nearest?lat=x&lng=y` - Find nearby drivers
- `WS /ws/driver-location` - Real-time driver locations

## 🐛 Troubleshooting

- Ensure Kafka and PostgreSQL are running before starting services
- Check ports 8080, 8081, 5500, 5600 are available
- Verify Google Maps API key in map-client/index.html #   b i k e r i d e a p p  
 