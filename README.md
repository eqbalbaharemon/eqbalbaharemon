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
 * Version: 2.0.1
 * Purpose: Standardizing GTM Data Layer for GA4 & Google Ads Enhanced Conversions
 */

(function() {
  'use strict';

  /**
   * Helper: Ensures price is a clean float
   * Handles strings with currency symbols or commas
   */
  var formatNumericValue = function(value) {
    if (value === undefined || value === null) return 0.00;
    var cleanValue = parseFloat(value.toString().replace(/[^\d.]/g, ''));
    return isNaN(cleanValue) ? 0.00 : cleanValue;
  };

  try {
    // 1. Transaction & Environment Variables
    var transactionId = '{{order_id_from_backend}}';
    var currency = '{{currency_code}}' || 'USD';
    var totalValue = formatNumericValue('{{total_price_from_backend}}');

    // 2. Clear previous ecommerce object to prevent data bleeding
    window.dataLayer = window.dataLayer || [];
    window.dataLayer.push({ 'ecommerce': null });

    // 3. Push DataLayer
    window.dataLayer.push({
      'event': 'purchase',
      'ecommerce': {
        'transaction_id': transactionId,
        'value': totalValue,
        'tax': formatNumericValue('{{tax_amount}}'),
        'shipping': formatNumericValue('{{shipping_amount}}'),
        'currency': currency,
        'coupon': '{{coupon_code}}' || '',
        'items': [
          {
            'item_id': '{{item_id}}',
            'item_name': '{{item_name}}',
            'price': formatNumericValue('{{item_price}}'),
            'item_brand': '{{item_brand}}',
            'item_category': '{{item_category}}',
            'quantity': parseInt('{{item_quantity}}') || 1
          }
        ]
      },
      // User Data for Enhanced Conversions (Google Ads)
      'user_data': {
        'email': '{{user_email}}',
        'phone_number': '{{user_phone}}',
        'address': {
          'first_name': '{{first_name}}',
          'last_name': '{{last_name}}',
          'street': '{{user_address_from_backend}}',
          'city': '{{user_city_from_backend}}',
          'region': '{{user_region}}',
          'postal_code': '{{user_postal_code}}',
          'country': '{{user_country_from_backend}}'
        }
      },
      'metadata': {
        'timestamp': new Date().toISOString(),
        'page_url': window.location.href,
        'user_agent': navigator.userAgent
      }
    });

  } catch (error) {
    console.error('DataLayer Purchase Error:', error);
  }
})();
```

🎥 Dynamic YouTube Interaction Tracker

This project demonstrates a professional JavaScript implementation for tracking user interactions with YouTube embeds dynamically without manual ID configuration.

🌟 Key Features:

Zero-Config Tracking: Automatically detects all YouTube iframes on the page.

Security Focused: Implements domain validation and secure event handling.

Performance Optimized: Uses an asynchronous loading pattern for the YouTube API.

💻 Implementation Code:




```The Code

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced YouTube Listener</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; padding: 30px; background-color: #f9f9f9; }
        .video-container { margin-bottom: 25px; border-radius: 10px; overflow: hidden; box-shadow: 0 4px 10px rgba(0,0,0,0.1); display: inline-block; }
        #tracking-log { 
            background: #1a1a1a; 
            color: #32ff7e; 
            padding: 20px; 
            border-radius: 8px; 
            height: 200px; 
            overflow-y: auto; 
            font-family: 'Courier New', Courier, monospace;
            border: 1px solid #333;
        }
        .log-entry { border-bottom: 1px solid #333; padding: 5px 0; }
    </style>
</head>
<body>

    <h2>YouTube Event Tracking System</h2>
    <p>Any YouTube video on this page is automatically tracked below.</p>
    
    <!-- Video Example -->
    <div class="video-container">
        <iframe width="560" height="315" src="[https://www.youtube.com/embed/dQw4w9WgXcQ](https://www.youtube.com/embed/dQw4w9WgXcQ)" frameborder="0" allowfullscreen></iframe>
    </div>

    <div id="tracking-log">
        <div class="log-entry">[System] System ready. Waiting for user interaction...</div>
    </div>

    <script>
        (function() {
            'use strict';
            const logElement = document.getElementById('tracking-log');

            const updateLog = (message) => {
                const entry = document.createElement('div');
                entry.className = 'log-entry';
                entry.textContent = `[${new Date().toLocaleTimeString()}] ${message}`;
                logElement.appendChild(entry);
                logElement.scrollTop = logElement.scrollHeight;
            };

            // Load YouTube API
            const tag = document.createElement('script');
            tag.src = "[https://www.youtube.com/iframe_api](https://www.youtube.com/iframe_api)";
            tag.async = true;
            const firstScriptTag = document.getElementsByTagName('script')[0];
            firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

            window.onYouTubeIframeAPIReady = function() {
                const iframes = document.getElementsByTagName('iframe');
                for (let i = 0; i < iframes.length; i++) {
                    let src = iframes[i].src;
                    if (src.includes('[youtube.com/embed/](https://youtube.com/embed/)')) {
                        // Ensure JS API is enabled
                        if (!src.includes('enablejsapi=1')) {
                            iframes[i].src = src + (src.includes('?') ? '&' : '?') + 'enablejsapi=1';
                        }
                        // Attach Player
                        new YT.Player(iframes[i], {
                            events: { 'onStateChange': onSecurePlayerStateChange }
                        });
                    }
                }
            };

            function onSecurePlayerStateChange(event) {
                const videoData = event.target.getVideoData();
                const videoTitle = videoData.title || "Unknown Video";
                
                if (event.data == YT.PlayerState.PLAYING) updateLog(`▶️ PLAYING: ${videoTitle}`);
                if (event.data == YT.PlayerState.PAUSED) updateLog(`⏸️ PAUSED: ${videoTitle}`);
                if (event.data == YT.PlayerState.ENDED) updateLog(`✅ COMPLETED: ${videoTitle}`);
            }
        })();
    </script>
</body>
</html>

```


### 💻 Tech Stack:
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white) ![Markdown](https://img.shields.io/badge/markdown-%23000000.svg?style=for-the-badge&logo=markdown&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=for-the-badge&logo=Cloudflare&logoColor=white) ![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&logo=google-cloud&logoColor=white) ![Firebase](https://img.shields.io/badge/firebase-%23039BE5.svg?style=for-the-badge&logo=firebase) ![WordPress](https://img.shields.io/badge/WordPress-%23117AC9.svg?style=for-the-badge&logo=WordPress&logoColor=white) ![Laravel](https://img.shields.io/badge/laravel-%23FF2D20.svg?style=for-the-badge&logo=laravel&logoColor=white) ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![Bootstrap](https://img.shields.io/badge/bootstrap-%238511FA.svg?style=for-the-badge&logo=bootstrap&logoColor=white) ![jQuery](https://img.shields.io/badge/jquery-%230769AD.svg?style=for-the-badge&logo=jquery&logoColor=white) ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![Firebase](https://img.shields.io/badge/firebase-a08021?style=for-the-badge&logo=firebase&logoColor=ffcd34) ![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white) ![Canva](https://img.shields.io/badge/Canva-%2300C4CC.svg?style=for-the-badge&logo=Canva&logoColor=white) ![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white) ![Adobe XD](https://img.shields.io/badge/Adobe%20XD-470137?style=for-the-badge&logo=Adobe%20XD&logoColor=#FF61F6) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![Meta](https://img.shields.io/badge/Meta-%230467DF.svg?style=for-the-badge&logo=Meta&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=for-the-badge&logo=notion&logoColor=white) ![Jira](https://img.shields.io/badge/jira-%230A0FFF.svg?style=for-the-badge&logo=jira&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white) ![Power Bi](https://img.shields.io/badge/power_bi-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
# 📊 GitHub Stats:
![](https://github-readme-stats.vercel.app/api?username=eqbalbaharemon&theme=dark&hide_border=false&include_all_commits=false&count_private=false)<br/>
![](https://nirzak-streak-stats.vercel.app/?user=eqbalbaharemon&theme=dark&hide_border=false)<br/>
![](https://github-readme-stats.vercel.app/api/top-langs/?username=eqbalbaharemon&theme=dark&hide_border=false&include_all_commits=false&count_private=false&layout=compact)

### ✍️ Random Dev Quote
![](https://quotes-github-readme.vercel.app/api?type=horizontal&theme=radical)

### 🔝 Top Contributed Repo
![](https://github-contributor-stats.vercel.app/api?username=eqbalbaharemon&limit=5&theme=dark&combine_all_yearly_contributions=true)

---
[![](https://visitcount.itsvg.in/api?id=eqbalbaharemon&icon=0&color=0)](https://visitcount.itsvg.in)

<!-- Proudly created with GPRM ( https://gprm.itsvg.in ) -->

---
## 🚀 Web Analytics & Tracking Portfolio (Full View)

| GTM Setup & Tags | Meta Events Manager |
| :---: | :---: |
| ![GTM](Meta%20Google%20Pixel%20Tiktok%20API%20CAPI%20GA4%20TAG%201.png) | ![Meta](Meta%20Google%20Pixel%20Tiktok%20API%20CAPI%20GA4%20TAG%204%20-%20Copy.png) |

| TikTok Event Activity | Server-side Hosting |
| :---: | :---: |
| ![TikTok](Meta%20Google%20Pixel%20Tiktok%20API%20CAPI%20GA4%20TAG%205%20-%20Copy.png) | ![Stape](Meta%20Google%20Pixel%20Tiktok%20API%20CAPI%20GA4%20TAG%206.png) |

| Additional GTM Tags | GA4 Event Tracking |
| :---: | :---: |
| ![GTM 2](Meta%20Google%20Pixel%20Tiktok%20API%20CAPI%20GA4%20TAG%202%20-%20Copy.png) | ![GTM 3](Meta%20Google%20Pixel%20Tiktok%20API%20CAPI%20GA4%20TAG%203.png) |
