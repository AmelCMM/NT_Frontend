# Lumina Messaging - Frontend

A modern, end-to-end encrypted messaging platform with a cyberpunk-inspired user interface. This frontend application provides secure, real-time communication between users with zero-knowledge architecture ensuring complete privacy.

## Overview

Lumina Messaging Frontend is a sophisticated web-based chat application built with vanilla JavaScript and Web Crypto APIs. It implements client-side encryption using ECDH key exchange and AES-GCM encryption, ensuring that all communications remain completely private and encrypted.

**Key Philosophy:** No message data is persisted on servers. All communications are ephemeral, with no logs or user data collection.

## Features

- **End-to-End Encryption** - All messages encrypted using ECDH + AES-GCM cryptography
- **Zero-Knowledge Architecture** - No message data retention on backend
- **Real-Time Messaging** - WebSocket-based instant message delivery via Socket.IO
- **Secure Session Management** - Token-based authentication with automatic session timeout
- **User-Friendly Interface** - Cyberpunk-themed dark mode design with responsive layout
- **Contact Management** - Add and manage conversation contacts via unique ID keys
- **Message History** - Per-session message history with end-to-end decryption
- **Cross-Platform** - Works on desktop and mobile browsers

## Technical Stack

- **HTML5** - Semantic markup structure
- **CSS3** - Advanced styling with CSS Grid, Flexbox, and animations
- **JavaScript (ES6+)** - Modern JavaScript with async/await
- **Web Crypto API** - Native cryptographic operations
- **Socket.IO** - Real-time bidirectional communication
- **No External Dependencies** - Pure vanilla JavaScript (apart from Socket.IO client)

## Project Structure

```
frontend/
├── index.html              # Login and account creation page
├── index.css               # Login page styling
├── createAccount.html      # Account registration interface
├── createAccount.css       # Account page styling
├── chatView.html           # Main chat interface
├── chatView.css            # Chat interface styling
└── README.md               # This file
```

## File Descriptions

### Chat Interface (`chatView.html` / `chatView.css`)
- Main messaging interface after authentication
- Sidebar with contact list and session information
- Real-time message encryption and decryption
- Send and receive encrypted messages

### Authentication (`index.html` / `index.css`)
- User login and account creation forms
- Session token management
- Secure credential handling

## Getting Started

### Prerequisites
- Modern web browser with WebSocket support
- Backend server running at `https://nt-secure-chat-backend-api.onrender.com`

### Installation

1. Clone the repository
2. Place frontend files on a web server or run locally
3. Ensure the backend server is accessible
4. Open `index.html` in your web browser

### Usage

1. **Create Account or Login**
   - Navigate to the application
   - Enter credentials to authenticate
   - Session token is stored in sessionStorage

2. **Add Contact**
   - Paste a contact's 256-character ID key
   - Click "Add Contact" to start messaging

3. **Send Message**
   - Select a contact from the sidebar
   - Type your message in the input field
   - Message is automatically encrypted before sending
   - Press Enter or click Send button

4. **View History**
   - Contact message history is displayed with automatic decryption
   - No data is permanently stored

## Security Implementation

- **ECDH Key Exchange (P-256)** - Establishes shared encryption keys with peers
- **AES-GCM Encryption** - Authenticated encryption for all messages
- **IV (Initialization Vector)** - Unique IV for each encrypted message
- **Base64 Encoding** - Safe transmission of binary cryptographic data
- **Session Expiration** - Automatic logout after 10 minutes of inactivity

## Browser Compatibility

- Chrome/Edge 37+
- Firefox 34+
- Safari 11+
- Opera 24+

## Configuration

### Backend URL
Modify the `backendUrl` constant in `chatView.html`:
```javascript
const backendUrl = 'https://your-backend-url.com';
```

### Socket.IO Connection
Connection path and transports are configured for optimal performance:
```javascript
const socket = io(backendUrl, {
  path: "/nt_backends_api/v1/socket.io",
  transports: ["websocket"],
  auth: { token }
});
```

## Known Limitations

- Messages are not persistent after server restart
- Session data is stored in browser sessionStorage
- One active session per browser/device
- Contact list is local to the session

## Performance Notes

- Encryption/decryption happens client-side (minimal latency)
- WebSocket provides real-time delivery
- Optimized for modern browsers with hardware-accelerated crypto

## Error Handling

- Connection failures redirect to login page
- Session expiration prompts re-authentication
- Invalid ID key format displays validation messages
- Network errors are communicated to the user

## Development Notes

- No build process required - pure frontend application
- Follows vanilla JavaScript best practices
- Responsive design using CSS Flexbox and media queries
- Cyberpunk color scheme with cyan (#0ff) and green (#00ff99) accents

## Future Enhancements

- Message search functionality
- File sharing with encryption
- Group chat support
- Message reactions and typing indicators
- Push notifications
- Progressive Web App (PWA) features

## Support

For issues or questions, refer to the main project README or contact the development team.
