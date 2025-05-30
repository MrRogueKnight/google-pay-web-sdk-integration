# google-pay-web-sdk-integration

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/MrRogueKnight/google-pay-web-sdk-integration/pulls)
[![Project Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)](https://github.com/MrRogueKnight/google-pay-web-sdk-integration)

## Table of Contents

* [About The Project](#about-the-project)
    * [Built With](#built-with)
* [Features](#features)
* [Getting Started](#getting-started)
    * [Prerequisites](#prerequisites)
    * [Installation](#installation)
    * [Running the Application](#running-the-application)
* [Usage](#usage)
* [Project Structure](#project-structure)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgments](#acknowledgments)

---

## About The Project

This repository provides a focused and practical demonstration of integrating the Google Pay API into a web application. Its primary goal is to illustrate the process of initiating secure and expedited payment transactions using the Google Pay Web SDK, providing a clear and functional example for developers.

The project is designed to be a straightforward reference, showcasing:
* How to correctly initialize the Google Pay button.
* How to construct and handle payment requests.
* The structure of successful transaction responses.
* Logging of key payment data to the browser console for easy inspection and debugging during development.

This implementation aims to be a valuable starting point for integrating Google Pay into various e-commerce, checkout, or service-based web platforms.

### Built With

* HTML5
* CSS3
* JavaScript (ES6+)
* Google Pay Web SDK

---

## Features

* **Secure Google Pay Integration:** Implements the official Google Pay Web SDK for reliable and secure payment processing.
* **Dynamic Payment Button:** Displays the "Buy with GPay" button, respecting Google's branding guidelines.
* **Payment Request Flow:** Demonstrates the complete flow from button click to transaction completion or cancellation.
* **Transaction Data Logging:** Outputs essential payment method details and transaction responses directly to the browser's developer console.
* **Test Environment Support:** Configured to work in the Google Pay `test` environment for frictionless development and experimentation.
* **Minimalist UI:** A clean and uncluttered user interface focused solely on demonstrating the integration.

---

## Getting Started

To set up the project locally and begin experimenting with Google Pay, follow these instructions.

### Prerequisites

* **Web Browser:** A modern web browser (e.g., Chrome, Firefox, Edge, Safari) with developer tools.
* **Local Web Server (Recommended):** To ensure proper functionality and avoid cross-origin issues, it's highly recommended to serve the `index.html` file via a local HTTP server. Options include:
    * **VS Code Live Server Extension:** Easy to use for VS Code users.
    * **Node.js `http-server`:** Install globally via npm: `npm install -g http-server`
* **Google Pay Merchant ID:** For testing in the `PRODUCTION` environment, you will need a registered Google Pay Merchant ID. For initial development, the `TEST` environment (default in this project) is sufficient and does not require a Merchant ID.

### Installation

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/MrRogueKnight/google-pay-web-sdk-integration.git](https://github.com/MrRogueKnight/google-pay-web-sdk-integration.git)
    ```
2.  **Navigate to Project Directory:**
    ```bash
    cd google-pay-web-sdk-integration
    ```
3.  **Review Configuration (Optional):**
    Open `index.html`. If you plan to switch from the `TEST` environment, locate the Google Pay configuration object and update the `environment` and `merchantInfo` as needed.

    ```javascript
    // Example: Configuring for PRODUCTION (requires your actual merchantId)
    const googlePayConfig = {
      environment: 'PRODUCTION', // or 'TEST'
      apiVersion: 2,
      apiVersionMinor: 0,
      paymentMethodConfigs: [
        // ... payment method configuration ...
      ],
      merchantInfo: {
        merchantName: 'Your Merchant Name',
        merchantId: 'YOUR_MERCHANT_ID', // Replace with your actual merchant ID
      },
      // ...
    };
    ```

### Running the Application

Choose your preferred method to serve the `index.html` file:

1.  **Using Live Server (VS Code Extension):**
    * Open the `google-pay-web-sdk-integration` folder in Visual Studio Code.
    * Right-click on `index.html` in the file explorer.
    * Select "Open with Live Server".
    * Your default browser will launch the application (e.g., `http://127.0.0.1:5500/index.html`).

2.  **Using `http-server` (Node.js):**
    * Open your terminal or command prompt.
    * Navigate to the `google-pay-web-sdk-integration` directory.
    * Run the command: `http-server`
    * Open your web browser and go to `http://localhost:8080` (or the address provided by `http-server`).

---

## Usage

Once the application is running in your browser:

1.  You will see a "Buy with GPay" button prominently displayed.
2.  **Click the button:** This will trigger the Google Pay payment sheet/dialog.
3.  **Complete the Transaction:**
    * If in the `TEST` environment, you can use dummy card details (Google Pay will usually provide these in the dialog for testing).
    * If in `PRODUCTION`, use a valid Google Pay configured payment method.
4.  **Observe Console Output:** After completing or cancelling the transaction, open your browser's developer console (`F12` or `Ctrl+Shift+I` / `Cmd+Option+I`). You will see detailed logs regarding the payment method used and the full transaction response object (or an error message if the transaction failed). This logging is crucial for understanding the data returned by Google Pay.

---
