# HidroWeb

## Project Structure


hidroweb/
├── public/
│   ├── index.html
│   └── ...
├── src/
│   ├── componentes/
│   │   ├── BarChart/
│   │   │   ├── BarChart.tsx
│   │   │   └── BarChart.test.tsx
│   │   ├── HistoricalChart/
│   │   │   ├── HistoricalChart.tsx
│   │   │   └── HistoricalChart.test.tsx
│   │   ├── Notif/
│   │   │   ├── Notif.tsx
│   │   │   └── Notif.test.tsx
│   │   └── ...
│   ├── context/
│   │   ├── NotificationContext.tsx
│   │   └── ...
│   ├── App.tsx
│   ├── index.tsx
│   └── ...
├── .eslintrc.js
├── package.json
├── tsconfig.json
└── ...


## Running the Backend

To run the backend, follow these steps:

1. **Navigate to the backend directory**:
   ```sh
   cd backend
   ```

2. **Install dependencies**:
   ```sh
   npm install
   ```

3. **Start the backend server**:
   ```sh
   npm start
   ```

The backend server should now be running on `http://localhost:5000`.

## Firebase Configuration

To configure Firebase, follow these steps:

1. **Create a Firebase project**:
   Go to the [Firebase Console](https://console.firebase.google.com/) and create a new project.

2. **Add a web app to your Firebase project**:
   In the Firebase Console, go to your project settings and add a new web app. Copy the Firebase configuration object.

3. **Add Firebase configuration to your project**:
   Create a file named `firebaseConfig.ts` in the `src` directory and add the following code:

   ```tsx
   // filepath: /c:/Users/ALEXANDRA/Documents/GitHub/HidroWeb_2024A/hidroweb/src/firebaseConfig.ts
   import { initializeApp } from 'firebase/app';
   import { getFirestore } from 'firebase/firestore';
   import { getAuth } from 'firebase/auth';

   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_AUTH_DOMAIN",
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_STORAGE_BUCKET",
     messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
     appId: "YOUR_APP_ID"
   };

   const app = initializeApp(firebaseConfig);
   const db = getFirestore(app);
   const auth = getAuth(app);

   export { db, auth };
   ```

4. **Use Firebase in your project**:
   Import the `db` and `auth` objects from `firebaseConfig.ts` wherever you need to use Firebase services.

## Endpoints and Connection

### Available Endpoints

- **GET /api/sensors**: Fetch sensor data.
- **POST /api/alerts**: Create a new alert.
- **GET /api/alerts**: Fetch all alerts.
- **POST /api/telegram/send-telegram-alert**: Send an alert to Telegram.

### Connecting to the Backend

To connect to the backend, use the following base URL:
```
http://localhost:5000
```

### Example API Call

Here is an example of how to make an API call to fetch sensor data:

```tsx
import axios from 'axios';

const fetchSensorData = async () => {
  try {
    const response = await axios.get('http://localhost:5000/api/sensors');
    console.log(response.data);
  } catch (error) {
    console.error('Error fetching sensor data:', error);
  }
};

fetchSensorData();
```

## Plugins

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

