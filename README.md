# 💫 About Me:
🔭 I’m currently working on: Web Analytics, GTM Server-side Tracking, and GA4 Audit projects.<br><br>👯 I’m looking to collaborate on: Advanced Data Tracking and Conversion Rate Optimization (CRO) projects.<br><br>🤝 I’m looking for help with: Scaling Server-side tagging for high-traffic e-commerce sites.<br><br>🌱 I’m currently learning: BigQuery for Marketing Analytics and Advanced Python for Data Automation.<br><br>💬 Ask me about: GA4, GTM, FB CAPI, TikTok Pixel, and Microsoft Clarity.<br><br>⚡ Fun fact: I believe precise data is the fuel for every successful digital marketing campaign.


## 🌐 Socials:
[![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/eqbalbaharemon0) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/eqbal-bahar-emon-7126b33a1) [![X](https://img.shields.io/badge/X-black.svg?logo=X&logoColor=white)](https://x.com/eqbalbaharemon0) 

---

### 🚀 Featured Project: Custom eCommerce Tracking Script
I developed this standardized JavaScript template for deep eCommerce tracking integration. It captures transaction data, customer location, and item details into the GTM Data Layer.

```javascript
/**
 * Professional eCommerce Tracking Template
 * Purpose: Standardizing GTM Data Layer for GA4/Ads tracking
 */

(function() {
  // 1. Define backend variables (Mapping needed based on CMS)
  var orderID = '{{order_id_from_backend}}';      
  var totalPrice = '{{total_price_from_backend}}'; 
  var userAddress = '{{user_address_from_backend}}'; 
  var userCity = '{{user_city_from_backend}}';
  var userCountry = '{{user_country_from_backend}}';
  var currencyCode = '{{currency_code}}'; 

  // 2. Data Layer Push with GA4 Standardized Schema
  window.dataLayer = window.dataLayer || [];
  window.dataLayer.push({ 'ecommerce': null }); 
  window.dataLayer.push({
    'event': 'purchase',
    'ecommerce': {
      'transaction_id': orderID,
      'value': parseFloat(totalPrice.toString().replace(/[^\d.]/g, '')), 
      'currency': currencyCode,
      'customer_details': {
        'billing_address': userAddress,
        'city': userCity,
        'country': userCountry
      },
      'metadata': {
        'timestamp': new Date().toISOString(),
        'page_url': window.location.href
      },
      'items': [
        {
          'item_id': '{{item_id}}',
          'item_name': '{{item_name}}',
          'price': parseFloat('{{item_price}}'),
          'quantity': 1
        }
      ]
    }
  });
})();
'''
