# **Google Pay API for Web 201: Advanced** 🚀  

## **1. Introduction**  

### **Welcome to Google Pay API for Web 201: Advanced!** 🎉  

Before proceeding, ensure you've completed **Google Pay API for Web 101: Basics**, as this guide builds upon its concepts.

### **📚 What You’ll Learn**  

- **How to customize the Google Pay button** 🎨  
- **How to start the payment process** 🛍️  
- **How to acknowledge payment authorization status** ✅  
- **How to handle shipping address changes** 🏠  
- **How to handle redemption codes** 🎟️  

### **🛠 What You’ll Need**  

- A **text editor** of your choice to edit **HTML** and **JavaScript** files.  
- **Google Chrome** or another browser that supports **local website testing**.  
- A **Google Pay merchant ID** (for production). Register at [Google Pay & Wallet Console](https://pay.google.com/) in just a minute.  

---

## **2. Button Customization**  

Customizing the **Google Pay button** enhances the user experience by aligning it with your brand and improving accessibility. Below is an overview of **ButtonOptions**:  

| **Option**              | **Necessity** | **Values** |
|-------------------------|--------------|------------|
| `onClick`               | Required     | Name of JavaScript event handler |
| `allowedPaymentMethods` | Optional     | `PaymentMethod[]` |
| `buttonColor`           | Optional     | `default`, `black`, `white` |
| `buttonLocale`          | Optional     | Two-letter ISO 639-1 language code |
| `buttonRadius`          | Optional     | `0 to 100` |
| `buttonRootNode`        | Optional     | `HTMLDocument` or `ShadowRoot` |
| `buttonSizeMode`        | Optional     | `static`, `fill` |
| `buttonType`            | Optional     | `book`, `buy`, `checkout`, `donate`, `order`, `pay`, `plain`, `subscribe` |

### **💻 Updating `main.js`**  

Find the `renderGooglePayButton()` method in **main.js** and replace it with:  

```javascript
function renderGooglePayButton() {
  const button = getGooglePaymentsClient().createButton({
    buttonColor: 'default',
    buttonType: 'buy',
    buttonRadius: 4,
    buttonLocale: 'en',
    onClick: onGooglePaymentButtonClicked,
    allowedPaymentMethods: baseGooglePayRequest.allowedPaymentMethods,
  });

  document.getElementById(GPAY_BUTTON_CONTAINER_ID).appendChild(button);
}
```

---

## **3. Payment Data Callbacks**  

Google Pay provides **callbacks** to handle specific **events** during the payment process.  

### **🛠 Update `main.js`**  

#### **Step 1: Replace `// todo: paymentDataCallbacks` with this code:**  

```javascript
paymentDataCallbacks: {
  onPaymentAuthorized: onPaymentAuthorized,
  onPaymentDataChanged: onPaymentDataChanged
},
```

#### **Step 2: Add the following event handlers at the end of `main.js`**  

```javascript
function onPaymentAuthorized(paymentData) {
  // We'll fill this in later
}

function onPaymentDataChanged(intermediatePaymentData) {
  // We'll fill this in later
}
```

#### **Step 3: Replace `// todo: callbackIntents` with this code:**  

```javascript
callbackIntents: [
  'PAYMENT_AUTHORIZATION', // Ensures payment is valid
  'SHIPPING_ADDRESS',      // Updates total cost dynamically
  'SHIPPING_OPTION',       // Updates available shipping choices
  'OFFER'                  // Applies promo codes in real time
],
shippingAddressRequired: true,
shippingOptionRequired: true,
shippingOptionParameters: {
  defaultSelectedOptionId: 'shipping-001',
  shippingOptions: [
    { id: 'shipping-001', label: '$0.00: Free shipping', description: 'Delivered in 5 business days.' },
    { id: 'shipping-002', label: '$1.99: Standard shipping', description: 'Delivered in 3 business days.' },
    { id: 'shipping-003', label: '$1000: Express shipping', description: 'Delivered in 1 business day.' }
  ],
},
```

---

## **4. Payment Authorization**  

### **🛠 Replace `onPaymentAuthorized()` in `main.js` with:**  

```javascript
function onPaymentAuthorized(paymentData) {
  return new Promise(function(resolve, reject) {
    console.log("onPaymentAuthorized", paymentData);

    // Simulate a payment processing success rate of 70%
    const paymentAuthorizationResult = (Math.random() > 0.3)
      ? { transactionState: 'SUCCESS' }
      : {
          transactionState: 'ERROR',
          error: {
            intent: 'PAYMENT_AUTHORIZATION',
            message: 'Insufficient funds',
            reason: 'PAYMENT_DATA_INVALID'
          }
        };

    resolve(paymentAuthorizationResult);
  });
}
```

**💡 Note:** In production, integrate with your backend payment processor to handle real transactions.  

---

## **5. Payment Data Change**  

### **🛠 Replace `onPaymentDataChanged()` in `main.js` with:**  

```javascript
function onPaymentDataChanged(intermediatePaymentData) {
  return new Promise(function(resolve, reject) {
    let paymentDataRequestUpdate = {};
    console.log("onPaymentDataChanged", intermediatePaymentData);

    switch(intermediatePaymentData.callbackTrigger) {
      case "INITIALIZE":
        // TODO: Handle initialization
        break;
      case "SHIPPING_ADDRESS":
        // TODO: Update shipping fees based on the selected address
        break;
      case "SHIPPING_OPTION":
        // TODO: Update shipping cost dynamically
        break;
      case "OFFER":
        // TODO: Apply discount based on promo code
        break;
      default:
        // TODO: Handle errors
    }

    resolve(paymentDataRequestUpdate);
  });
}
```

---

## **6. Conclusion**  

🎉 **Congratulations!** You've successfully implemented **Google Pay API for Web 201**!  

### **🚀 Running the Project**  

#### **Option 1: Open in Google Chrome**  
1️⃣ Open **Google Chrome**.  
2️⃣ Use **File > Open File…** to select `index.html`.  

#### **Option 2: Run a Local Web Server**  
```bash
$ cd /your/path/to/pay-web-101
$ python3 -m http.server
```
📍 Open **http://localhost:8000** in your browser.  

---

### **📉 Next Steps**  
- **Test in Google Pay’s test environment before going live.**  
- **Review security best practices for transactions.**  
- **Explore advanced features like tokenization & gateways.**  

🚀 Now deploy your integration and start accepting payments! 💳

