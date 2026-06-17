# UrbanFlow Setup Instructions

Welcome to the UrbanFlow repository. This guide provides all necessary instructions to set up the dependencies, configure the environment, and run the project locally.

## Prerequisites

Before you begin, ensure you have the following installed on your machine:
*   **Node.js** (v18 or higher recommended)
*   **Python** (v3.9 or higher recommended)
*   **MongoDB** (Local instance or Atlas cluster)
*   **Redis** (Local instance or Cloud instance like RedisLabs)
*   **RabbitMQ** (Local instance or Cloud CloudAMQP instance)
*   **Expo CLI** (for running the mobile app)

---

## 1. Clone the Repository

Make sure the repository is public and fully accessible as per the requirements. Clone it to your local machine:

```bash
git clone <your-repository-url>
cd UrbanFlow
```

## 2. Environment Configuration

You must set up environment variables for each of the four main components. We have provided `example.env` files in each directory.

1.  Navigate into each of the following directories: `agents`, `server`, `client`, and `client-native`.
2.  Copy or rename `example.env` to `.env`.
3.  Fill in the required placeholder values (such as API keys, database URIs, Auth0 domains, etc.) in the newly created `.env` files.

---

## 3. Installation & Setup

### A. Agents (Python AI Microservice)
This service handles the AI inferences, Langchain workflows, and specialized AI agents.
```bash
cd agents
# Create a Python virtual environment
python -m venv venv
# Activate the virtual environment
# On macOS/Linux:
source venv/bin/activate
# On Windows:
venv\Scripts\activate
# Install all required Python dependencies
pip install -r requirements.txt
```

### B. Server (Node.js API Gateway)
This service acts as the primary API, managing the database, authentication, and routing requests to the AI service.
```bash
cd ../server
npm install
```

### C. Client (React Web Dashboard)
This is the administrative command hub built with React and Vite.
```bash
cd ../client
npm install
```

### D. Client Native (React Native App)
This is the citizen mobile application built using Expo.
```bash
cd ../client-native
npm install
```

---

## 4. Running the Application

For the complete UrbanFlow ecosystem to work correctly, run all four services concurrently in separate terminal windows.

### Start the AI Agents Service
```bash
cd agents
source venv/bin/activate
# Depending on your exact entry point, it could be:
uvicorn main:app --reload --port 8000
```

### Start the Node.js Server
```bash
cd server
npm run dev
# Server generally starts on port 3000
```

### Start the Web Client
```bash
cd client
npm run dev
# Client generally starts on port 5173
```

### Start the Mobile App
```bash
cd client-native
npm start
```
After starting Expo, you can use the Expo Go app on your physical device to scan the generated QR code, or press `a` (Android) / `i` (iOS) to run it on an emulator.

---

## Project Structure at a Glance
*   `agents/`: Python FastAPI backend executing LangChain logic and hosting AI pipelines.
*   `server/`: Node.js Express backend acting as the main REST API gateway.
*   `client/`: React frontend (Vite) offering a detailed administrative dashboard.
*   `client-native/`: Expo mobile application for citizen tools like SisterHood, EcoSnap, and StreetGig.
