
---
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

## Project Structure

```
google-pay-web-sdk-integration/
├── index.html        # The core HTML file containing the Google Pay button and JavaScript integration logic.
├── style.css         # Basic CSS for minimal styling and layout.
├── README.md         # This comprehensive README file.
└── .gitignore        # Specifies files and directories to be ignored by Git.
```

---

## Roadmap

This project currently serves as a fundamental integration example. Future enhancements could include:

* **Backend Integration:** Demonstrating how to send the payment token from the frontend to a backend server for processing.
* **Error Handling:** More robust client-side error handling and user feedback.
* **Dynamic Pricing:** Implementing dynamic product data and pricing for a more realistic scenario.
* **Multiple Payment Methods:** Expanding to support other payment methods beyond basic card payments (e.g., tokenized cards, gift cards).
* **User Interface Improvements:** Enhancing the visual appeal and user experience.

---

## Contributing

Contributions are highly valued and welcome! Whether it's bug fixes, new features, or documentation improvements, your input helps make this project better for everyone.

To contribute:

1.  **Fork the repository.**
2.  **Create your Feature Branch:** `git checkout -b feature/AmazingFeature`
3.  **Commit your Changes:** `git commit -m 'feat: Add some AmazingFeature'` (using conventional commits is encouraged)
4.  **Push to the Branch:** `git push origin feature/AmazingFeature`
5.  **Open a Pull Request:** Describe your changes and their benefits clearly.

Please ensure your code adheres to good practices and passes any existing linting/formatting checks.

---

## License

Distributed under the MIT License. See the `LICENSE` file in the root of the repository for more information.

---

Project Link: [https://github.com/MrRogueKnight/google-pay-web-sdk-integration](https://github.com/MrRogueKnight/google-pay-web-sdk-integration)

---

## Acknowledgments

* [Google Pay API for the Web Documentation](https://developers.google.com/pay/api/web)
* [Shields.io](https://shields.io/) for the awesome badges.
* [Choose an Open Source License](https://choosealicense.com/)
```