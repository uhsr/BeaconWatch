# BeaconWatch - Real-time Bluetooth Beacon Monitoring and Analysis

BeaconWatch is a robust, TypeScript-based application designed for the comprehensive monitoring and analysis of Bluetooth Low Energy (BLE) beacons. It provides a centralized platform for discovering, tracking, and reporting on beacon activity within a defined environment. The application leverages advanced scanning techniques and data processing to deliver real-time insights into beacon proximity, signal strength variations, and potential anomalies.

This project addresses the growing need for reliable beacon management in various sectors, including retail, healthcare, and asset tracking. By utilizing BeaconWatch, organizations can gain valuable data on customer behavior, optimize operational efficiency, and improve overall safety. The application offers a flexible architecture that can be easily integrated with existing infrastructure and customized to meet specific business requirements. Its modular design allows for seamless expansion with new features and protocols in the future.

BeaconWatch goes beyond simple beacon detection by incorporating advanced filtering and analysis capabilities. It can identify and flag beacons based on specific criteria, such as signal strength thresholds or proximity zones. The application also provides historical data logging and reporting, enabling users to track beacon performance over time and identify potential issues before they escalate. Furthermore, the user-friendly interface makes it easy to configure and manage beacon monitoring parameters, ensuring that the application is always optimized for the specific environment.

Key Features:

*   **Real-time Beacon Discovery:** Utilizes the `noble` library for continuous BLE scanning to detect and identify active beacons within range. Employs a debouncing mechanism to prevent duplicate detection events.
*   **Proximity Estimation:** Implements Received Signal Strength Indication (RSSI) based distance estimation using a configurable path loss exponent. Provides an approximation of beacon proximity for triggering location-based events. The formula used is: *Distance = 10^((TxPower - RSSI)/(10 * PathLossExponent))* where TxPower is transmitted power and RSSI is received signal strength.
*   **Configurable Alerting:** Allows setting custom RSSI thresholds for each beacon, triggering alerts when signal strength falls below or exceeds the defined limits. Alerts can be dispatched via various channels (e.g., email, webhooks).
*   **Data Logging and Reporting:** Logs beacon data, including RSSI, MAC address, and timestamp, to a persistent storage (e.g., database, file). Generates reports on beacon activity over specified time periods. Uses `date-fns` for timestamp formatting and manipulation.
*   **REST API for Data Access:** Provides a secure REST API for accessing beacon data and configuration settings. The API is built using `Express.js` and protected by authentication middleware.
*   **Web-based User Interface (Optional):** Offers a web-based interface for visualizing beacon data and managing application settings. The UI is built using a modern JavaScript framework (e.g., React, Angular) and communicates with the REST API. This is planned and not currently implemented.
*   **Beacon Identification Filtering:** Provides a mechanism to filter beacon discovery based on UUID, Major, and Minor values, allowing focus on specific beacons of interest.

Technology Stack:

*   **TypeScript:** The application is written in TypeScript, providing strong typing and enhanced code maintainability.
*   **Node.js:** A JavaScript runtime environment for executing the application on the server-side.
*   **noble:** A Node.js library for interacting with Bluetooth Low Energy (BLE) devices.
*   **Express.js:** A Node.js web application framework for building the REST API.
*   **date-fns:** A modern JavaScript date utility library for formatting and manipulating timestamps.
*   **(Optional) MongoDB/PostgreSQL:** Database options for persistent data storage.

Installation:

1.  Ensure Node.js and npm are installed on your system. Node.js version 16 or higher is recommended.
2.  Clone the BeaconWatch repository from GitHub:
    `git clone https://github.com/uhsr/BeaconWatch.git`
3.  Navigate to the project directory:
    `cd BeaconWatch`
4.  Install the project dependencies:
    `npm install`
5.  (Optional) If using a database, configure the database connection settings as described in the Configuration section.

Configuration:

1.  Create a `.env` file in the project root directory.
2.  Define the following environment variables:
    *   `BLE_DEVICE_NAME`: (Optional) The name of the Bluetooth adapter to use (defaults to the system's default adapter).
    *   `DATABASE_URL`: (Optional) The connection string for your database (if using persistent storage). Format depends on chosen DB.
    *   `API_PORT`: (Optional) The port number for the REST API (defaults to 3000).
    *   `BEACON_UUID_FILTER`: (Optional) Beacon UUID to filter for in scanning. If not provided, all beacons will be shown.

    Example `.env` file:
    

Usage:

1.  Start the BeaconWatch application:
    `npm start`
2.  (If API is enabled) Access the REST API documentation at `http://localhost:<API_PORT>/api-docs` (if using Swagger or similar). Example API calls:
    *   `GET /beacons`: Retrieves a list of currently detected beacons.
    *   `GET /beacons/:macAddress`: Retrieves detailed information for a specific beacon.

3. Example code to interact with the API:
    

Contributing:

We welcome contributions to BeaconWatch! Please follow these guidelines:

1.  Fork the repository on GitHub.
2.  Create a new branch for your feature or bug fix.
3.  Implement your changes and write unit tests to ensure code quality.
4.  Submit a pull request to the `main` branch.

License:

This project is licensed under the MIT License. See the [LICENSE](https://github.com/uhsr/BeaconWatch/blob/main/LICENSE) file for details.

Acknowledgements:

We would like to acknowledge the developers of the `noble` library for providing the foundation for BLE device interaction in Node.js. Their work has been invaluable in the development of BeaconWatch.