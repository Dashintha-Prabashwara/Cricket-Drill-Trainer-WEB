# API Documentation

## Configuration Requirements

### EmailJS Configuration
1. Create an account at [EmailJS](https://www.emailjs.com/)
2. Set up the following credentials in `index.html`:
   - `YOUR_EMAILJS_PUBLIC_KEY`: Your EmailJS public key
   - `YOUR_EMAILJS_SERVICE_ID`: Your EmailJS service ID
   - `YOUR_EMAILJS_TEMPLATE_ID`: Your EmailJS template ID

## API Endpoints

### 1. Store Player Data
- **Endpoint**: `YOUR_STORE_PLAYER_API_ENDPOINT`
- **Method**: POST
- **Description**: Stores new player registration data
- **Request Body**:
```json
{
  "playerId": "string",
  "name": "string",
  "age": "number",
  "email": "string",
  "handedness": "string",
  "stanceAngle": "number",
  "forwardDefenceEndAngle": "number",
  "forwardDriveEndAngle": "number",
  "backwardDefenceEndAngle": "number",
  "backwardDriveEndAngle": "number",
  "cutEndAngle": "number",
  "pullEndAngle": "number",
  "timestamp": "string",
  "angleData": {
    "stanceAngle": {
      "mainAngle": "number",
      "pitch": "number",
      "roll": "number",
      "timestamp": "string"
    }
    // ... similar objects for other angles
  }
}
```

### 2. Fetch Registered Players
- **Endpoint**: `YOUR_FETCH_REGISTERED_PLAYERS_API_ENDPOINT`
- **Method**: GET
- **Description**: Retrieves list of all registered players
- **Response**: Array of player objects

### 3. Fetch Player Submissions
- **Endpoint**: `YOUR_FETCH_SUBMISSIONS_API_ENDPOINT`
- **Method**: GET
- **Description**: Retrieves list of all player submissions
- **Response**: Array of submission objects

### 4. Validate Player ID
- **Endpoint**: `YOUR_VALIDATE_PLAYER_ID_API_ENDPOINT`
- **Method**: POST
- **Description**: Validates if a player ID is available
- **Request Body**:
```json
{
  "playerId": "string"
}
```
- **Response**:
```json
{
  "available": "boolean"
}
```

## WebSocket Connection
The application connects to an ESP32 device for real-time angle measurements.
- **WebSocket URL**: `ws://{ESP32_IP}:81`
- **Default ESP32 IP**: 10.34.29.41
- **Message Format**:
```json
{
  "angle": "number",
  "pitch": "number",
  "roll": "number"
}
```

## Security Considerations
1. Store all API keys and sensitive credentials in environment variables or secure configuration
2. Use HTTPS for all API endpoints in production
3. Implement proper authentication and authorization
4. Rate limit API endpoints to prevent abuse
5. Validate and sanitize all user inputs
6. Implement CORS policies as needed