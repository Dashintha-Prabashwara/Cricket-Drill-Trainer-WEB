# Player Dashboard

A comprehensive web-based application for cricket player registration and performance management with real-time sensor integration.

## Overview

The Player Dashboard is a modern web application designed to manage cricket player registrations and track performance data from IoT sensors. It provides an intuitive interface for registering players, capturing real-time angle measurements from ESP32-based sensors, and viewing detailed performance analytics.

## Features

### Authentication
- Simple login system with demo credentials
- Session management with logout functionality
- Clean, modern login interface

### Player Registration
- Complete player profile registration (name, age, handedness, email)
- Real-time angle measurement capture from ESP32 sensors
- Automatic Player ID generation with validation
- Email notifications via EmailJS integration
- Seven different angle measurements:
  - Stance Angle
  - Forward Defence End Angle
  - Forward Drive End Angle
  - Backward Defence End Angle
  - Backward Drive End Angle
  - Cut End Angle
  - Pull End Angle

### Real-time Sensor Integration
- WebSocket connection to ESP32-based bat sensors
- Live angle monitoring (main angle, pitch, roll)
- Connection status indicators
- Automatic reconnection with retry logic
- Visual feedback for data capture

### Data Management
- View all registered players with collapsible details
- Performance submissions tracking with enhanced metrics
- Advanced search and filtering capabilities
- Responsive data display with modern UI

### Performance Analytics
- Overall performance metrics
- Foot segment performance tracking
- Enhanced bat segment analytics including:
  - Grip performance breakdown
  - Angle performance analysis
  - Success rate calculations
- Drill-specific performance data

## Technical Stack

- **Frontend**: Pure HTML, CSS, JavaScript
- **Styling**: Modern CSS with gradients, animations, and responsive design
- **Icons**: Font Awesome 6.4.2
- **Email**: EmailJS for automated notifications
- **Real-time Communication**: WebSocket for ESP32 integration
- **API Integration**: RESTful API calls for data persistence

## Setup Instructions

### Prerequisites
- Web server capable of serving HTML files
- ESP32 device configured for WebSocket communication
- EmailJS account for email notifications
- Backend API endpoints for data persistence

### Configuration

1. **EmailJS Setup**:
   ```javascript
   emailjs.init({
     publicKey: "YOUR_PUBLIC_KEY", // Replace with your EmailJS public key
   });
   ```

2. **API Endpoints**:
   Update the following endpoints in the JavaScript code:
   - Player registration endpoint
   - Registered players fetch endpoint
   - Submissions fetch endpoint

3. **ESP32 Configuration**:
   - Default IP address: `10.34.29.41`
   - WebSocket port: `81`
   - Ensure ESP32 is on the same network

### Demo Credentials
- **Username**: `admin`
- **Password**: `1234`

## Usage

### Player Registration
1. Log in using demo credentials
2. Navigate to "Register Player" tab
3. Fill in player details (name, age, handedness, email)
4. Connect to ESP32 bat sensor using IP address
5. Capture angle measurements for different cricket strokes
6. Submit registration to generate unique Player ID
7. Automatic email sent to player with ID confirmation

### Viewing Data
1. **Registered Players**: View all registered players with expandable details
2. **Submissions**: Track performance data with advanced filtering
3. Use search functionality to find specific players or submissions

### Sensor Integration
1. Power on ESP32 bat sensor
2. Ensure device is connected to same network
3. Enter IP address in dashboard
4. Click "Connect to Bat Segment"
5. Select angle type to measure
6. Use "Capture Angle" to record measurements

## API Integration

The application expects the following API structure:

### Player Registration
```json
{
  "playerId": "string",
  "name": "string",
  "age": "number",
  "email": "string",
  "handedness": "Left|Right",
  "stanceAngle": "number",
  "forwardDefenceEndAngle": "number",
  "forwardDriveEndAngle": "number",
  "backwardDefenceEndAngle": "number",
  "backwardDriveEndAngle": "number",
  "cutEndAngle": "number",
  "pullEndAngle": "number",
  "timestamp": "ISO string",
  "angleData": "object"
}
```

### Performance Submissions
Expected fields include overall metrics, foot segment data, and enhanced bat segment analytics with grip and angle breakdowns.

## Features Highlights

### Modern UI/UX
- Responsive design for all device sizes
- Smooth animations and transitions
- Intuitive tab-based navigation
- Real-time visual feedback
- Professional gradient styling

### Data Visualization
- Collapsible player cards with summary views
- Color-coded performance indicators
- Organized data segments (overall, foot, bat)
- Search and filter capabilities

### Sensor Integration
- Real-time angle monitoring display
- Connection status indicators
- Automatic reconnection handling
- Visual capture feedback

### Performance Tracking
- Comprehensive drill analytics
- Success rate calculations
- Enhanced bat performance with grip/angle separation
- Historical data viewing

## Browser Compatibility
- Modern browsers with WebSocket support
- JavaScript ES6+ features required
- Responsive design for mobile and desktop

## Security Considerations
- Demo authentication for development use
- Input sanitization implemented
- Email validation included
- Connection timeout handling

## Troubleshooting

### ESP32 Connection Issues
- Verify IP address is correct
- Ensure ESP32 and dashboard are on same network
- Check WebSocket port (default: 81)
- Verify ESP32 firmware is running WebSocket server

### Email Delivery Issues
- Verify EmailJS configuration
- Check public key is correct
- Ensure template ID matches
- Validate email addresses

### Data Loading Issues
- Check API endpoint availability
- Verify network connectivity
- Review browser console for errors
- Ensure proper JSON format from APIs

## Future Enhancements
- Advanced analytics dashboard
- Player comparison tools
- Export functionality for data
- Enhanced sensor calibration
- Mobile app integration
- Real-time coaching feedback

---

This Player Dashboard provides a comprehensive solution for cricket training facilities to manage player registrations and track performance using modern IoT sensors and web technologies.

# Player Dashboard

A web-based dashboard for player registration and performance monitoring.

## Setup Instructions

1. Clone the repository
2. Create a `credentials.json` file in the root directory with the following structure:
```json
{
    "emailjs": {
        "publicKey": "YOUR_PUBLIC_KEY",
        "serviceId": "YOUR_SERVICE_ID",
        "templateId": "YOUR_TEMPLATE_ID"
    },
    "apis": {
        "storePlayer": "YOUR_STORE_PLAYER_API_URL",
        "validatePlayerId": "YOUR_VALIDATE_PLAYER_ID_API_URL",
        "fetchRegisteredPlayers": "YOUR_FETCH_REGISTERED_PLAYERS_API_URL",
        "fetchSubmissions": "YOUR_FETCH_SUBMISSIONS_API_URL"
    }
}
```

3. Update the `credentials.json` file with your actual credentials
4. Open `index.html` in a web browser

## Features

- Player registration with angle measurements
- Real-time angle monitoring via WebSocket connection
- Email notifications using EmailJS
- Player data management and search
- Performance tracking and submissions
- Responsive design for mobile devices

## Security Notes

- The `credentials.json` file is included in `.gitignore` to prevent sensitive data exposure
- Keep a secure backup of your credentials
- Consider using environment variables for production deployments

## Default Login

- Username: admin
- Password: 1234

## WebSocket Connection

The application connects to an ESP32 device for real-time angle measurements:
- Default ESP32 IP: 10.34.29.41
- WebSocket Port: 81
