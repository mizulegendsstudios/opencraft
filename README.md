# Mizu MOBA – Identity Lab

A lightweight multiplayer identity and team inventory prototype built with vanilla JavaScript and Firebase Realtime Database.  
Players log in with a username, see a live list of other players and their inventories, and chat in real time.  
The project is fully client‑side and requires no backend server.

## Features

- **Player Identity** – Enter a username to join the session. A unique ID is generated on login and automatically removed on disconnect.
- **Live Player List** – See all online players and their current inventory items.
- **Shared Inventory** – Each player’s inventory is stored in the cloud. The “Add Wood” button simulates picking up a resource (e.g., for building a bridge).
- **Team Chat** – Send and receive messages instantly using Firebase’s real‑time listeners.
- **Auto‑cleanup** – When a player closes the tab or loses connection, their entry is removed from the database via `onDisconnect`.

## Tech Stack

- HTML5 / CSS3 / Vanilla JavaScript (ES modules)
- [Firebase Realtime Database](https://firebase.google.com/docs/database)
- CSS Grid & minimal custom styling

## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/yourusername/mizu-identity-lab.git
cd mizu-identity-lab
```

### 2. Firebase Configuration
The app uses a pre‑configured test database:  
`https://faketime-ab4fb-default-rtdb.firebaseio.com/`  

**To use your own Firebase project:**
1. Go to the [Firebase Console](https://console.firebase.google.com/).
2. Create a new project (or use an existing one).
3. Enable **Realtime Database** and copy your database URL.
4. Replace the `databaseURL` in the `firebaseConfig` object inside the `<script>` tag with your own.

> ⚠️ **Security note:** The current configuration has no authentication or security rules. It is intended for local testing only. Before deploying, set proper [Firebase Realtime Database rules](https://firebase.google.com/docs/database/security) to protect your data.

### 3. Run the app
Open `index.html` directly in your browser – no build tools or server required.  
(If you use VS Code, the Live Server extension provides a convenient local environment.)

## How It Works

1. **Login** – The user enters a username and clicks “Entrar al Mundo”.  
   A new player object (`uid_<timestamp>`) is written to `players/` with an initial inventory `["Poción Inicial"]`.
2. **Real‑time Sync** – `onValue` listeners update the player list and chat messages whenever the database changes.
3. **Inventory Update** – Clicking “Añadir Madera” reads the player’s current inventory, appends `"Madera"` if not already present, and writes it back.
4. **Chat** – Messages are pushed to `messages/` with the username and a server timestamp.
5. **Disconnect** – `onDisconnect().remove()` ensures the player’s data is deleted when the browser tab closes or the connection drops.

## File Structure
```
mizu-identity-lab/
├── index.html    # Main application (HTML + CSS + JS)
└── README.md     # This file
```

## Demo / Screenshot
*(Add a screenshot of the app running here if desired)*

## License
This project is provided for educational purposes. Feel free to modify and use it as you like.

*Built as part of a multiplayer identity exploration for a MOBA‑style game concept.*
```
