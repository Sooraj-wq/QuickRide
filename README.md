# QuickRide

> **Note:** This is a simulative project developed for a hackathon by novice developers. It is not a fully functional production-ready application and serves primarily as a proof of concept.

A web-based ridesharing application designed to match passengers traveling along similar routes, reducing costs and environmental impact through automatic ride matching.

## Overview

QuickRide connects users who share common travel routes and vehicle preferences, enabling cost-effective carpooling. The application calculates accurate distances between locations using the Haversine formula, determines pricing, and automatically searches for matching rides in the database.

When multiple passengers are matched for the same route and vehicle type, all participants receive a 30% discount on their fare, promoting both economic and environmental benefits.

## Technology Stack

**Backend:**
- Node.js with Express.js - RESTful API server
- MongoDB with Mongoose ODM - Database persistence
- In-memory fallback storage
- dotenv - Environment configuration management

**Frontend:**
- HTML, CSS, JavaScript
- Tailwind CSS

**External APIs:**
- OpenStreetMap Nominatim API - Geocoding service for address-to-coordinate conversion
- Browser Geolocation API - Real-time location tracking for safety features

## Setup
Installation

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (optional - application includes in-memory fallback)

### Setup Instructions

1. Clone the repository and install dependencies:
```bash
npm install
```

2. (Optional) Start MongoDB service:
```bash
# Linux/Mac
sudo systemctl start mongod

# Windows
net start MongoDB
```

3. Configure environment variables by creating a `.env` file:
```env
PORT=4000
MONGODB_URL=mongodb://127.0.0.1:27017/rideshare
```

4. Start the application:
```bash
npm start
```Usage

### Booking a Ride

1. Enter a unique user ID
2. Specify pickup and destination locations
3. Select vehicle type (SUV, Auto, or Sedan)
4. Choose payment method (Cash, UPI, Google Pay, or Apple Pay)
5. Submit the booking request

### Ride Matching Process

The application performs the following operations:
- Converts location strings to GPS coordinates via OpenStreetMap API
- Calculates precise distance using the Haversine formula
- Computes fare at ₹15 per kilometer
- Stores Functionality
- Accurate distance calculation using the Haversine formula
- Intelligent ride matching based on route and vehicle preferences
- Dynamic pricing with automatic rideshare discounts (30% reduction)
- Administrative dashboard to view all active rides
- Ride management and deletion capabilities

### Safety Features
- Emergency contact registration system
- One-click emergency alert functionality:
  - Real-time GPS location retrieval
- Ride status tracking and completion confirmation. It'll keep searching for matches. If it finds someone, you get the discount automatically. If not, you can either keep waiting or just book an individual ride.

## Features

### Core stuff
- Real distance calculation using the Haversine formula
- Automatic ride matching based on route and car type
- Dynamic pricing with rideshare discounts
- View all active rides
- Delete rides when they're done

### Safety features
Because this stuff matters:
- Save an emergency contact
- Emergency alert button that:
  - Grabs your GPS location
  - Sends it via WhatsApp to your emergency contact
  - Includes a Google Maps link
- Ride completion tracking

## Project Structure

```
├── app.js                 # Main server file
├── index.html            # Home page with booking form
├── package.json          # Dependencies
├── public/
│   ├── aboutus.html      # Team info
│   ├── all-rides.html    # View all active rides
│   ├── ride-details.html # Ride confirmation & matching
│   ├── home.js          # Main booking logic
│   └── haversine.js     # Distance calculation
```Limitations

- Location matching requires consistent naming conventions (e.g., "New York" and "NYC" are not recognized as equivalent)
- OpenStreetMap Nominatim API has rate limiting restrictions for high-frequency requests
- In-memory storage mode does not persist data across server restarts
- No authentication system implemented - user IDs are not validated or protected
- Geolocation features require HTTPS in production environments for browser security compliance
GET  /allrides           - Fetch all rides
DELETE /deleteride/:uid  - Remove a ride
```
To test the ride matching functionality:

1. Open the application in two separate browser tabs

**Tab 1:**
```
User ID: alice
From: Times Square, New York
To: Central Park, New York
Vehicle: Sedan
```

**Tab 2:**
```
User ID: bob
From: Times Square, New York
To: Central Park, New York
Vehicle: Sedan
```

The second user (Bob) should receive a notification of a matching ride with the first user (Alice), and both should be eligible for the 30%
- From: "Times Square, New York"
- To: "Central Park, New York"
- Car: Sedan

Tab 2:
- User ID: "bob"
- From: "Times Square, New York"
- To: "CenEnhancements

- User authentication and authorization system
- Driver/passenger role differentiation
- Real-time updates using WebSocket technology
- Location autocomplete with predictive search
- Ride history and analytics dashboard
- User rating and review system
- Payment gateway integration
- Mobile application development

## Contributors

- Sooraj
- Mareo 

Built for D-Solve Dotslash Hackathon, College of Engineering Trivandrum.

## License

MIT
