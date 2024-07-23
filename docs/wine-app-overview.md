# Wine Portal APP Overview

## Introduction

The Wine Portal Web Application is a comprehensive platform designed for wineries to register their companies and manage their wine products. The application offers advanced features such as QR code generation, vineyard mapping, detailed wine registration, wine tokenization on the Cardano blockchain, and integration with IoT storage systems. This overview provides a detailed technical description of the application's architecture, functionalities, and technologies used.

## Architecture

### Backend

The backend of the application is built using a robust framework such as Node.js with Express for handling HTTP requests. The backend is responsible for managing user authentication, database interactions, blockchain transactions, and IoT data integration.

### Frontend

The frontend is developed using React and NextJS, providing a responsive and interactive user interface. The frontend communicates with the backend through RESTful APIs.

### Database

A NoSQL document database is used for storing winery and wine information and keeping realtime subscriptions to crucial data changes and updates. The database schema includes document collections for wineries, wines, blend components, vineyard locations, and much more.

### Blockchain

The application integrates with the Cardano blockchain for wine tokenization and supply chain tracking. Smart contracts are utilized to ensure secure and transparent transactions while hydra takes cares of updating these when needed.

### IoT Integration

The IoT storage system is integrated using real-time sensor data. The Hydra protocol on the Cardano blockchain is employed for scalable and efficient data updates.

## Main Features

### Winery and Wine Registration

- User Authentication: Secure user registration and login system.
- Company Registration: Wineries can register their companies, providing detailed information including location, history, and contact details.
- Wine Registration: Detailed wine registration form capturing properties such as name, vintage, blend components, and tasting notes.

### QR Code Generation

- **QR Code Creation:** Generate unique QR codes for each registered wine.
- **Printing:** Option to download and print QR codes for labeling wine bottles.
- **Scanning:** Consumers can scan QR codes to access detailed information about the wine.

### Vineyard Mapping

- **Google Maps Integration:** Use Google Maps API to display vineyard locations.
- **Polygon Mapping:** Define and display vineyard boundaries using polygon mapping tools.
- **Geospatial Data Storage:** Store vineyard location data in the database for mapping and analysis.

### Wine Tokenization and Blockchain Integration

- **Tokenization:** Convert wine bottles into unique digital tokens on the Cardano blockchain.
- **Supply Chain Tracking:** Track the movement of wine through the supply chain using blockchain transactions.
- **Smart Contracts:** Implement smart contracts for secure and transparent transactions.

### IoT Storage System

- **Sensor Data Integration:** Integrate IoT sensors for real-time data collection (e.g., temperature, humidity).
- **Blockchain Updates:** Use the Hydra protocol for scalable blockchain updates with sensor data.
- **Monitoring:** We provide monitoring for wineries to track real-time sensor data and blockchain status.
