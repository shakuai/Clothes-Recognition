# Shaku - Clothes Recognition (Auto-Tagging)

**AI-Powered Clothes Recognition from 2D Images**

The **Shaku Clothes Recognition (Auto-Tagging)** API is an intelligent service that uses computer vision and deep learning models to automatically detect and tag clothing items in an image. It identifies multiple attributes such as clothing type, color, pattern, sleeve length, collar style, material, and overall style.

This solution helps e-commerce platforms, apparel retailers, and virtual fitting systems automatically label clothing items, standardize catalog data, improve search and recommendation systems, and enhance user experience.

---

<img width="1872" height="1491" alt="Add a subheading (7)" src="https://github.com/user-attachments/assets/07595dff-c5df-47e9-b01e-841a8c7b2cf5" />


## Overview

**Shaku Clothes Recognition API** receives an image, detects clothing items, and returns their categories and attributes in a structured JSON format.  
The model is trained on large-scale datasets of fashion imagery and supports a wide range of clothing types, including:

- **Type:** blouse, suits, coat, dress, hoodie, jacket, shirt, sweatshirt, T-shirt, pants, skirt, shorts  
- **Design:** animal, floral, gingham, graphic, simple, spot, stripe, zebra
- **Sleeve:** long sleeve, short sleeve, sleeveless
- **Neckline:** bandeau, crew-neck, halter-neck, high-neck, off-shoulder, one-shoulder, square-neck, sweetheart-neck, v-neck
- **Crop:** crop, not-crop
- **Color:** Detect color of the clothes
  

## Key Features
- Multi-item detection from a single image  
- Attribute prediction 
- JSON-based structured output  
- Simple integration via REST API or SDK (Python, PHP, Node.js)



## Use Cases

- **E-commerce automation:** Automatically tag clothing products before uploading them to catalogs.  
- **Catalog standardization:** Unify tags and attributes for consistent search and filtering.  
- **Visual search engines:** Enhance product discovery using visual attributes like color or pattern.  
- **Style analytics:** Extract attributes for trend analysis and data-driven fashion insights.  
- **Virtual try-on and outfit recommendation systems.**



## Architecture & Workflow

1. **Image Upload** – The client sends a product or model image. 
2. **Preprocessing** – The API normalizes image resolution, adjusts brightness, and removes noise.  
3. **Detection Model** – An AI model identifies clothing items and generates bounding boxes.  
4. **Attribute Extraction** – A secondary model predicts attributes like color, sleeve type, pattern, etc.  
5. **Filtering & Normalization** – Output attributes are normalized to consistent vocabulary terms.  
6. **Response** – Final JSON output is returned to the client.



## Integration

### 1. API Integration
The Clothes Recognition (Auto Tagging) API by Shaku enables developers to automatically analyze clothing images and extract meaningful fashion attributes in real-time. It’s designed for e-commerce platforms, virtual try-on systems, fashion analytics tools, and inventory management systems that require precise and scalable clothing recognition.
The API can detect multiple attributes from a single image. With a simple HTTP request, you can integrate advanced fashion intelligence into your applications.

Developers can easily connect via RESTful API calls, send image URLs or base64-encoded images, and receive structured JSON responses with detected tags.

You can explore and test the API by logging into the Shaku Dashboard:
[Shaku Dashboard - Login & Test](https://dashboard.shaku.tech/auth/login)

Below are example HTTP requests for Python, PHP, and Node.js that can also be executed in Postman.

#### 1.1. Authentication (API Tokens)
 - **Get Access Token**
   
   Use this endpoint to log in with client ID, client secret, username, and password to receive an access token.
   
   - **Python**
      ```python
      import requests
      import json
      
      url = "https://api.shaku.tech/oauth/token"
      
      payload = json.dumps({
        "grant_type": "password",
        "client_id": "YOUR_CLIENT_ID",
        "client_secret": "YOUR_SECRET_KEY",
        "username": "YOUR_EMAIL_ADDRESS",
        "password": "YOUR_PASSWORD"
      })
      headers = {
        'Content-Type': 'application/json',
        'Accept': 'application/json'
      }
      
      response = requests.request("POST", url, headers=headers, data=payload)
      
      print(response.text)
      
      ```

   - **PHP**
      ```php
      <?php
      
      $curl = curl_init();
      
      curl_setopt_array($curl, array(
        CURLOPT_URL => 'https://api.shaku.tech/oauth/token',
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_ENCODING => '',
        CURLOPT_MAXREDIRS => 10,
        CURLOPT_TIMEOUT => 0,
        CURLOPT_FOLLOWLOCATION => true,
        CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
        CURLOPT_CUSTOMREQUEST => 'POST',
        CURLOPT_POSTFIELDS =>'{
          "grant_type":"password",
          "client_id":"YOUR_CLIENT_ID",
          "client_secret":"YOUR_SECRET_KEY",
          "username":"YOUR_EMAIL_ADDRESS",
          "password":"YOUR_PASSWORD"
      }',
        CURLOPT_HTTPHEADER => array(
          'Content-Type: application/json',
          'Accept: application/json'
        ),
      ));
      
      $response = curl_exec($curl);
      
      curl_close($curl);
      echo $response;

      ```
   - **Node.Js**
      ```javascript
      var request = require('request');
      var options = {
        'method': 'POST',
        'url': 'https://api.shaku.tech/oauth/token',
        'headers': {
          'Content-Type': 'application/json',
          'Accept': 'application/json'
        },
        body: JSON.stringify({
          "grant_type": "password",
          "client_id": "YOUR_CLIENT_ID",
          "client_secret": "YOUR_SECRET_KEY",
          "username": "YOUR_EMAIL_ADDRESS",
          "password": "YOUR_PASSWORD"
        })
      
      };
      request(options, function (error, response) {
        if (error) throw new Error(error);
        console.log(response.body);
      });

      ```
  - **Refresh Token**
    
    Refresh the access token when it expires.
     
    - **Python**
      ```python
      import requests
      import json
      
      url = "https://api.shaku.tech/oauth/token"
      
      payload = json.dumps({
        "grant_type": "refresh_token",
        "refresh_token": "YOUR_REFRESH_TOKEN",
        "client_id": "YOUR_CLIENT_ID",
        "client_secret": "YOUR_SECRET_KEY"
      })
      headers = {
        'Content-Type': 'application/json',
        'Accept': 'application/json',
        'Cookie': 'shaku_session=N3tqPfDYa4oCHa1YBkWLIfHoiuJ7LvuRIZZ0Kbna'
      }
      
      response = requests.request("POST", url, headers=headers, data=payload)
      
      print(response.text)
      
      ```

    - **PHP**
      ```php
      <?php
      
      $curl = curl_init();
      
      curl_setopt_array($curl, array(
        CURLOPT_URL => 'https://api.shaku.tech/oauth/token',
        CURLOPT_RETURNTRANSFER => true,
        CURLOPT_ENCODING => '',
        CURLOPT_MAXREDIRS => 10,
        CURLOPT_TIMEOUT => 0,
        CURLOPT_FOLLOWLOCATION => true,
        CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
        CURLOPT_CUSTOMREQUEST => 'POST',
        CURLOPT_POSTFIELDS =>'{
          "grant_type":"refresh_token",
          "refresh_token":"YOUR_REFRESH_TOKEN",
          "client_id":"YOUR_CLIENT_ID",
          "client_secret":"YOUR_SECRET_KEY"
      }',
        CURLOPT_HTTPHEADER => array(
          'Content-Type: application/json',
          'Accept: application/json',
          'Cookie: shaku_session=N3tqPfDYa4oCHa1YBkWLIfHoiuJ7LvuRIZZ0Kbna'
        ),
      ));
      
      $response = curl_exec($curl);
      
      curl_close($curl);
      echo $response;


      ```
    - **Node.Js**
      ```javascript
      var request = require('request');
      var options = {
        'method': 'POST',
        'url': 'https://api.shaku.tech/oauth/token',
        'headers': {
          'Content-Type': 'application/json',
          'Accept': 'application/json',
          'Cookie': 'shaku_session=N3tqPfDYa4oCHa1YBkWLIfHoiuJ7LvuRIZZ0Kbna'
        },
        body: JSON.stringify({
          "grant_type": "refresh_token",
          "refresh_token": "YOUR_REFRESH_TOKEN",
          "client_id": "YOUR_CLIENT_ID",
          "client_secret": "YOUR_SECRET_KEY"
        })
      
      };
      request(options, function (error, response) {
        if (error) throw new Error(error);
        console.log(response.body);

      ```

   - **Revoke Token**
    
     Revoke an access token to log out or terminate access.
     
     - **Python**
       ```python
       import requests
       
       url = "https://api.shaku.tech/api/v1/auth/revoke"
       
       payload = ""
       headers = {
         'Authorization': 'Bearer YOUR_ACCESS_TOKEN',
         'Cookie': 'shaku_session=oQhS4k3h5QBHs77YoGVKhEwsWmtu8E48lr4sTimt'
       }
       
       response = requests.request("GET", url, headers=headers, data=payload)
       
       print(response.text)
            
       ```

     - **PHP**
       ```php
       <?php
       
       $curl = curl_init();
       
       curl_setopt_array($curl, array(
         CURLOPT_URL => 'https://api.shaku.tech/api/v1/auth/revoke',
         CURLOPT_RETURNTRANSFER => true,
         CURLOPT_ENCODING => '',
         CURLOPT_MAXREDIRS => 10,
         CURLOPT_TIMEOUT => 0,
         CURLOPT_FOLLOWLOCATION => true,
         CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
         CURLOPT_CUSTOMREQUEST => 'GET',
         CURLOPT_HTTPHEADER => array(
           'Authorization: Bearer YOUR_ACCESS_TOKEN'
         ),
       ));
       
       $response = curl_exec($curl);
       
       curl_close($curl);
       echo $response;
 
 
       ```
     - **Node.Js**
       ```javascript
       var request = require('request');
       var options = {
         'method': 'GET',
         'url': 'https://api.shaku.tech/api/v1/auth/revoke',
         'headers': {
           'Authorization': 'Bearer YOUR_ACCESS_TOKEN'
         }
       };
       request(options, function (error, response) {
         if (error) throw new Error(error);
         console.log(response.body);
       });
       ```

#### 1.2. Clothes Recognition API Service

 
  Recognize clothing from an image and return type, size, and other relevant features.

  
  - **Python**
      ```python
      import requests
      import json
      
      url = "https://api.shaku.tech/api/v1/services/autoTagging"
      
      payload = json.dumps({
        "image": "IMAGE_BASE64_FORMAT"
      })
      headers = {
        'Authorization': 'Bearer YOUR_ACCESS_TOKEN'
      }
      
      response = requests.request("POST", url, headers=headers, data=payload)
      
      print(response.text)
           
      ```
      
- **PHP**
     ```php
     <?php
     
     $curl = curl_init();
     
     curl_setopt_array($curl, array(
       CURLOPT_URL => 'https://api.shaku.tech/api/v1/services/autoTagging',
       CURLOPT_RETURNTRANSFER => true,
       CURLOPT_ENCODING => '',
       CURLOPT_MAXREDIRS => 10,
       CURLOPT_TIMEOUT => 0,
       CURLOPT_FOLLOWLOCATION => true,
       CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
       CURLOPT_CUSTOMREQUEST => 'POST',
       CURLOPT_POSTFIELDS =>'{
         "image":"IMAGE_BASE64_FORMAT"
     }',
       CURLOPT_HTTPHEADER => array(
         'Authorization: Bearer YOUR_ACCESS_TOKEN'
       ),
     ));
     
     $response = curl_exec($curl);
     
     curl_close($curl);
     echo $response;


     ```
- **Node.Js**
    ```javascript

    var request = require('request');
    var options = {
      'method': 'POST',
      'url': 'https://api.shaku.tech/api/v1/services/autoTagging',
      'headers': {
        'Authorization': 'Bearer YOUR_ACCESS_TOKEN'
      },
      body: JSON.stringify({
        "image": "IMAGE_BASE64_FORMAT"
      })
    
    };
    request(options, function (error, response) {
      if (error) throw new Error(error);
      console.log(response.body);

    ```
        
- **SDK Integration**
  
  For simpler and faster integration, you can test directly on the Dashboard or use the Python package.
  - [Shaku Dashboard - Login & Test](https://dashboard.shaku.tech/auth/login)
  - Install via PyPI:
    ```python
    pip install shakuapi
    ```
    
    Python Example:

    ```python
    from shakuapi import ShakuClient
    
    client = ShakuClient(client_id="YOUR_CLIENT_ID", client_secret="YOUR_CLIENT_SECRET")
    
    # login
    client.login(username="YOUR_USERNAME", password="YOUR_PASSWORD")
    
    
    # clothes recognition
    clothes = client.clothes_recognition("clothes_image.jpg")
    print(clothes)

    ```


## Pricing

Shaku offers a cost-effective and scalable solution that provides maximum features for online fashion and apparel businesses. By reducing return rates and improving customer satisfaction, Shaku helps businesses increase revenue and optimize operations. Pricing plans are designed to accommodate small shops to large enterprises, ensuring that every business can benefit from AI-powered clothes recognition technology. For detailed pricing, subscription plans, and enterprise solutions, visit [Shaku Pricing](https://shaku.tech/#pricing)

## Application

Shaku also offers a mobile application that brings AI-powered clothes recognition directly to users’ smartphones. The app enables users to capture or upload clothing images and instantly receive automatic tags describing the garment’s type, color, pattern, style, and fit.

This intelligent tagging system enhances the shopping experience by helping users easily identify, categorize, and explore similar items. Retailers and fashion platforms can integrate the app as a companion tool, allowing customers to discover products visually and receive style recommendations on the go.


## Privacy & Data Handling

- Uploaded images are processed and deleted immediately after inference.
- No personal data is stored or shared.

## Resources

- Official website: [Shaku.tech](https://shaku.tech)
- GitHub Repository: [https://github.com/shakuai/clothes_recognition](https://github.com/shakuai/Clothes-Recognition)
- Documentation: [[API Reference]](https://api.shaku.tech/docs.html)


## License

MIT License © 2025 ShakuAI

