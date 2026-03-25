---
layout: post
title: "Step 1 Breakfast"
description: "Breakfast time hits, and in NYC that means one thing: pick your spot and dive in."
permalink: /new-york/breakfast/
parent: "Analytics/Admin"
team: "Insightful Innovators"
submodule: 1
author: "Insightful Innocators"
date: 2025-11-20
microblog: true
footer:
   previous: /new-york/landmarks/
   home: /nyc/home/
   next: /new-york/shopping/
---

<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>NYC Breakfast Explorer</title>
 <style>
   * {
     margin: 0;
     padding: 0;
     box-sizing: border-box;
   }


   body {
     margin: 0;
     padding: 20px;
     font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
     background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
     color: white;
     min-height: 100vh;
   }
  
   .container {
     max-width: 1200px;
     margin: 0 auto;
   }
  
   .header {
     text-align: center;
     margin-bottom: 40px;
     padding: 20px;
     background: rgba(255, 255, 255, 0.1);
     border-radius: 15px;
     border: 2px solid #f59e0b;
   }
  
   .header h1 {
     font-size: 48px;
     margin: 0 0 10px 0;
     color: #fbbf24;
     text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
   }
  
   .header p {
     font-size: 1.2rem;
     color: #cbd5e1;
   }
  
   .live-hours-container {
     margin: 30px 0;
     padding: 25px;
     background: rgba(0, 0, 0, 0.3);
     border-radius: 15px;
     border-left: 5px solid #10b981;
   }
  
   .live-hours-container h2 {
     color: #10b981;
     margin-bottom: 20px;
     font-size: 1.8rem;
   }
  
   .restaurant-card {
     background: rgba(255, 255, 255, 0.1);
     border-radius: 15px;
     padding: 25px;
     margin: 20px 0;
     border: 2px solid transparent;
     transition: all 0.3s;
   }
  
   .restaurant-card:hover {
     transform: translateY(-5px);
     border-color: #f59e0b;
     box-shadow: 0 10px 30px rgba(245, 158, 11, 0.3);
   }
  
   .restaurant-card h3 {
     margin: 0 0 15px 0;
     font-size: 28px;
     color: #f59e0b;
     display: flex;
     align-items: center;
     gap: 10px;
   }
  
   .restaurant-card .badge {
     display: inline-block;
     padding: 5px 15px;
     background: rgba(245, 158, 11, 0.2);
     border-radius: 20px;
     font-size: 12px;
     margin: 10px 0;
   }
  
   .restaurant-card p {
     line-height: 1.6;
     color: #cbd5e1;
     margin: 10px 0;
   }
  
   .hours-display {
     background: rgba(0, 0, 0, 0.2);
     padding: 20px;
     border-radius: 10px;
     margin: 15px 0;
   }
  
   .day-hour {
     display: flex;
     justify-content: space-between;
     padding: 10px 0;
     border-bottom: 1px solid rgba(255, 255, 255, 0.1);
   }
  
   .day-hour:last-child {
     border-bottom: none;
   }
  
   .day-hour .day {
     font-weight: bold;
     color: #fbbf24;
   }
  
   .day-hour .time {
     color: #10b981;
     font-weight: bold;
   }
  
   .menu-grid {
     display: grid;
     grid-template-columns: repeat(2, 1fr);
     gap: 20px;
     margin: 20px 0;
   }
  
   .menu-item {
     background: rgba(255, 255, 255, 0.1);
     border-radius: 12px;
     padding: 20px;
     transition: transform 0.3s;
   }
  
   .menu-item:hover {
     transform: scale(1.02);
   }
  
   .menu-item h4 {
     margin: 0 0 5px 0;
     color: #fbbf24;
     font-size: 1.2rem;
   }
  
   .menu-item .price {
     color: #10b981;
     font-weight: bold;
     font-size: 20px;
     margin: 5px 0;
   }
  
   .menu-item p {
     color: #94a3b8;
     font-size: 14px;
     margin: 10px 0;
   }
  
   .btn {
     background: linear-gradient(90deg, #f59e0b, #f97316);
     color: white;
     border: none;
     padding: 12px 24px;
     border-radius: 8px;
     cursor: pointer;
     font-size: 16px;
     font-weight: bold;
     transition: all 0.3s;
     display: inline-flex;
     align-items: center;
     gap: 8px;
   }
  
   .btn:hover {
     transform: scale(1.05);
     box-shadow: 0 5px 15px rgba(245, 158, 11, 0.4);
   }
  
   .btn-primary {
     background: linear-gradient(90deg, #10b981, #059669);
     width: 100%;
     margin-top: 20px;
     justify-content: center;
   }
  
   .refresh-btn {
     background: linear-gradient(90deg, #8b5cf6, #7c3aed);
     margin-top: 10px;
   }
  
   .step {
     display: none;
   }
  
   .step.active {
     display: block;
   }
  
   .back-btn {
     background: transparent;
     border: 1px solid #64748b;
     color: #94a3b8;
     margin-bottom: 20px;
   }
  
   .back-btn:hover {
     border-color: white;
     color: white;
   }
  
   .order-section {
     background: rgba(255, 255, 255, 0.1);
     border-radius: 15px;
     padding: 30px;
   }
  
   .order-item {
     background: rgba(0, 0, 0, 0.3);
     padding: 15px;
     border-radius: 8px;
     margin: 10px 0;
     display: flex;
     justify-content: space-between;
     align-items: center;
   }
  
   .custom-input {
     width: 100%;
     padding: 12px;
     background: rgba(255, 255, 255, 0.1);
     border: 1px solid #475569;
     border-radius: 8px;
     color: white;
     font-size: 16px;
     margin: 10px 0;
   }
  
   .custom-input:focus {
     outline: none;
     border-color: #a855f7;
   }
  
   .remove-btn {
     background: #ef4444;
     color: white;
     border: none;
     padding: 8px 16px;
     border-radius: 6px;
     cursor: pointer;
   }
  
   .total {
     font-size: 28px;
     text-align: right;
     margin: 20px 0;
     color: #fbbf24;
   }
  
   .restaurant-info {
     display: flex;
     justify-content: space-between;
     align-items: center;
     margin-bottom: 15px;
   }
  
   .restaurant-location {
     color: #f59e0b;
     font-weight: bold;
   }
  
   .restaurant-cuisine {
     background: rgba(139, 92, 246, 0.2);
     color: #c4b5fd;
     padding: 5px 10px;
     border-radius: 12px;
     font-size: 0.8rem;
   }
  
   .location-grid {
     display: grid;
     grid-template-columns: repeat(2, 1fr);
     gap: 20px;
     margin: 20px 0;
   }
  
   .location-card {
     background: rgba(255, 255, 255, 0.1);
     border-radius: 15px;
     padding: 25px;
     transition: all 0.3s;
     border: 2px solid transparent;
     position: relative;
   }
  
   .location-card:hover {
     transform: translateY(-5px);
     border-color: #f59e0b;
     box-shadow: 0 10px 30px rgba(245, 158, 11, 0.3);
   }
  
   .location-card h3 {
     margin: 0 0 10px 0;
     font-size: 24px;
     color: #f59e0b;
   }


   .location-card-footer {
     margin-top: 20px;
     display: flex;
     gap: 10px;
   }


   .view-menu-btn {
     flex: 1;
     background: linear-gradient(90deg, #f59e0b, #f97316);
     color: white;
     border: none;
     padding: 12px 20px;
     border-radius: 8px;
     cursor: pointer;
     font-weight: bold;
     transition: all 0.3s;
     display: flex;
     align-items: center;
     justify-content: center;
     gap: 5px;
   }


   .view-menu-btn:hover {
     transform: scale(1.05);
     box-shadow: 0 5px 15px rgba(245, 158, 11, 0.4);
   }


   .quick-add-btn {
     background: linear-gradient(90deg, #ffd700, #ffed4e);
     color: #1a1a2e;
     border: none;
     padding: 12px 20px;
     border-radius: 8px;
     cursor: pointer;
     font-weight: bold;
     transition: all 0.3s;
     display: flex;
     align-items: center;
     gap: 5px;
   }


   .quick-add-btn:hover {
     transform: scale(1.05);
     box-shadow: 0 5px 20px rgba(255, 215, 0, 0.5);
   }


   .quick-add-btn.added {
     background: linear-gradient(90deg, #10b981, #059669);
     color: white;
   }
  
   .nav-to-landmarks {
     margin-top: 50px;
     margin-bottom: 50px;
     text-align: center;
     padding: 40px;
     background: rgba(255, 215, 0, 0.1);
     border-radius: 15px;
     border: 2px solid #ffd700;
   }
  
   .nav-to-landmarks h2 {
     color: #fbbf24;
     margin-bottom: 20px;
     font-size: 2rem;
   }
  
   .nav-to-landmarks p {
     color: #cbd5e1;
     font-size: 1.2rem;
     margin-bottom: 30px;
   }
  
   .landmarks-btn {
     display: inline-block;
     padding: 20px 50px;
     font-size: 1.3rem;
     font-weight: bold;
     color: #1a1a2e;
     background: linear-gradient(135deg, #ffd700 0%, #ffed4e 100%);
     border: none;
     border-radius: 50px;
     cursor: pointer;
     text-decoration: none;
     box-shadow: 0 10px 30px rgba(255, 215, 0, 0.4);
     transition: all 0.3s ease;
     text-transform: uppercase;
     letter-spacing: 0.05em;
   }
  
   .landmarks-btn:hover {
     transform: translateY(-5px) scale(1.05);
     box-shadow: 0 15px 40px rgba(255, 215, 0, 0.6);
     background: linear-gradient(135deg, #ffed4e 0%, #ffd700 100%);
   }


   /* Itinerary Tracker Sidebar */
   .itinerary-tracker {
     position: fixed;
     right: 20px;
     top: 50%;
     transform: translateY(-50%);
     width: 300px;
     background: rgba(26, 35, 50, 0.95);
     border-radius: 15px;
     padding: 20px;
     box-shadow: 0 10px 40px rgba(0,0,0,0.5);
     border: 2px solid #ffd700;
     z-index: 9999;
     max-height: 80vh;
     overflow-y: auto;
   }


   .itinerary-tracker h3 {
     color: #ffd700;
     margin-bottom: 15px;
     font-size: 1.3rem;
     text-align: center;
     border-bottom: 2px solid #ffd700;
     padding-bottom: 10px;
   }


   .itinerary-item {
     background: rgba(255, 255, 255, 0.1);
     border-radius: 8px;
     padding: 12px;
     margin-bottom: 10px;
     border-left: 4px solid #ffd700;
   }


   .itinerary-item.incomplete {
     border-left-color: #666;
     opacity: 0.6;
   }


   .itinerary-label {
     font-size: 0.85rem;
     color: #ffd700;
     text-transform: uppercase;
     font-weight: 600;
     margin-bottom: 5px;
   }


   .itinerary-value {
     color: #fff;
     font-size: 1rem;
     font-weight: 500;
   }


   .itinerary-empty {
     color: #999;
     font-style: italic;
     font-size: 0.9rem;
   }


   .clear-itinerary-btn {
     width: 100%;
     background: #ef4444;
     color: white;
     border: none;
     padding: 10px;
     border-radius: 8px;
     cursor: pointer;
     font-weight: 600;
     margin-top: 15px;
     transition: all 0.3s;
   }


   .clear-itinerary-btn:hover {
     background: #dc2626;
     transform: translateY(-2px);
   }


   .toggle-tracker-btn {
     position: fixed;
     right: 20px;
     top: 20px;
     background: #ffd700;
     color: #1a2332;
     border: none;
     padding: 12px 20px;
     border-radius: 25px;
     cursor: pointer;
     font-weight: 600;
     z-index: 10000;
     box-shadow: 0 5px 15px rgba(255, 215, 0, 0.4);
     transition: all 0.3s;
   }


   .toggle-tracker-btn:hover {
     transform: translateY(-2px);
     box-shadow: 0 8px 20px rgba(255, 215, 0, 0.6);
   }


   .itinerary-tracker.hidden {
     display: none;
   }


   .add-to-itinerary-btn {
     background: linear-gradient(90deg, #ffd700, #ffed4e);
     color: #1a1a2e;
     margin-top: 15px;
     font-weight: bold;
     width: 100%;
     justify-content: center;
   }


   .add-to-itinerary-btn:hover {
     transform: scale(1.05);
     box-shadow: 0 5px 20px rgba(255, 215, 0, 0.5);
   }


   .add-to-itinerary-btn.added {
     background: linear-gradient(90deg, #10b981, #059669);
     color: white;
   }


   .live-data-indicator {
     display: inline-block;
     padding: 4px 12px;
     background: #4CAF50;
     color: white;
     border-radius: 4px;
     font-size: 0.8rem;
     margin-left: 10px;
     animation: pulse 2s infinite;
   }
  
   .live-data-indicator.updating {
     background: #FF9800;
   }
  
   .live-data-indicator.offline {
     background: #F44336;
   }
  
   .hours-loading {
     text-align: center;
     padding: 40px;
     color: #94a3b8;
   }
  
   .live-loading-spinner {
     width: 40px;
     height: 40px;
     border: 4px solid rgba(255, 255, 255, 0.1);
     border-top: 4px solid #f59e0b;
     border-radius: 50%;
     animation: spin 1s linear infinite;
     margin: 0 auto 10px auto;
   }
  
   .hours-header {
     margin: 30px 0 20px 0;
     color: #fbbf24;
     font-size: 1.8rem;
     border-bottom: 2px solid #f59e0b;
     padding-bottom: 10px;
   }
  
   @keyframes spin {
     0% { transform: rotate(0deg); }
     100% { transform: rotate(360deg); }
   }
  
   @keyframes pulse {
     0%, 100% { opacity: 1; }
     50% { opacity: 0.7; }
   }
  
   .update-note {
     font-style: italic;
     color: #94a3b8;
     font-size: 0.9rem;
     margin-top: 10px;
     padding-top: 10px;
     border-top: 1px solid rgba(255, 255, 255, 0.1);
   }
  
   @media (max-width: 768px) {
     .location-grid,
     .menu-grid {
       grid-template-columns: 1fr;
     }
    
     .header h1 {
       font-size: 36px;
     }
    
     .restaurant-card h3 {
       font-size: 24px;
     }
    
     .landmarks-btn {
       padding: 15px 35px;
       font-size: 1.1rem;
     }


     .itinerary-tracker {
       width: 90%;
       right: 5%;
       left: 5%;
     }
   }
 </style>
</head>
<body>
 <button class="toggle-tracker-btn" onclick="toggleItineraryTracker()">
   📋 My Itinerary
 </button>


 <div class="container">
   <div class="header">
     <h1>🍳 NYC Breakfast Explorer</h1>
     <p>Choose your perfect morning meal with live restaurant hours</p>
     <div class="live-data-indicator" id="apiStatus">🔌 Connecting to API...</div>
   </div>


   <!-- Restaurant Selection Grid -->
   <div id="step1" class="step active">
     <h2 style="text-align: center; margin-bottom: 30px; color: #fbbf24;">Choose Your Breakfast Spot</h2>
     <div class="location-grid">
       <div class="location-card">
         <h3>Sarabeth's</h3>
         <div class="badge">Elegant & Classic</div>
         <p>📍 Upper West Side</p>
         <p>A beloved NYC institution known for its legendary homemade jams and elegant brunch classics. Perfect for a refined, upscale breakfast experience.</p>
         <div class="restaurant-cuisine">Breakfast & Pastries</div>
         <div class="location-card-footer">
           <button class="view-menu-btn" onclick="selectRestaurant('sarabeths')">
             <span>📖</span> View Menu
           </button>
           <button class="quick-add-btn" onclick="quickAddToItinerary('sarabeths', event)" data-restaurant="sarabeths">
             <span>⭐</span> Add
           </button>
         </div>
       </div>
       <div class="location-card">
         <h3>Jack's Wife Frida</h3>
         <div class="badge">Bold & Trendy</div>
         <p>📍 SoHo</p>
         <p>Mediterranean-inspired breakfast with bold Mexican flavors. A trendy spot with colorful dishes and creative twists on morning favorites.</p>
         <div class="restaurant-cuisine">Mediterranean</div>
         <div class="location-card-footer">
           <button class="view-menu-btn" onclick="selectRestaurant('jacks')">
             <span>📖</span> View Menu
           </button>
           <button class="quick-add-btn" onclick="quickAddToItinerary('jacks', event)" data-restaurant="jacks">
             <span>⭐</span> Add
           </button>
         </div>
       </div>
       <div class="location-card">
         <h3>Ess a Bagel</h3>
         <div class="badge">Authentic & Iconic</div>
         <p>📍 Midtown East</p>
         <p>The ultimate NYC bagel experience. Hand-rolled, kettle-boiled bagels that are crispy outside and pillowy inside. A true New York classic.</p>
         <div class="restaurant-cuisine">Bagels & Deli</div>
         <div class="location-card-footer">
           <button class="view-menu-btn" onclick="selectRestaurant('ess')">
             <span>📖</span> View Menu
           </button>
           <button class="quick-add-btn" onclick="quickAddToItinerary('ess', event)" data-restaurant="ess">
             <span>⭐</span> Add
           </button>
         </div>
       </div>
       <div class="location-card">
         <h3>Shuka</h3>
         <div class="badge">Fresh & Vibrant</div>
         <p>📍 East Village</p>
         <p>Modern Mediterranean cuisine with Israeli breakfast specialties. Fresh, vibrant dishes featuring tahini, hummus, and perfectly spiced shakshuka.</p>
         <div class="restaurant-cuisine">Mediterranean</div>
         <div class="location-card-footer">
           <button class="view-menu-btn" onclick="selectRestaurant('shuka')">
             <span>📖</span> View Menu
           </button>
           <button class="quick-add-btn" onclick="quickAddToItinerary('shuka', event)" data-restaurant="shuka">
             <span>⭐</span> Add
           </button>
         </div>
       </div>
     </div>
   </div>


   <!-- Restaurant Details & Menu -->
   <div class="step" id="step2">
     <button class="btn back-btn" onclick="goToStep(1)">
       <span>←</span> Back to Restaurants
     </button>
     <div class="restaurant-card" id="restaurantDetails">
       <div class="restaurant-info">
         <h3 id="restaurantName">Loading...</h3>
         <div class="restaurant-location" id="restaurantLocation"></div>
       </div>
       <p id="restaurantDescription"></p>
      
       <!-- Hours section moved here (AFTER restaurant selection) -->
       <div id="hoursSection">
         <h2 class="hours-header">🕒 Live Restaurant Hours</h2>
         <div id="restaurantHours">
           <div class="hours-loading">
             <div class="live-loading-spinner"></div>
             <div>Fetching live hours...</div>
           </div>
         </div>
         <button class="btn refresh-btn" onclick="refreshCurrentRestaurant()">
           <span>🔄</span> Update Live Hours
         </button>
       </div>
     </div>
    
     <h3 style="margin: 30px 0 20px 0; color: #fbbf24;">Menu Highlights</h3>
     <div class="menu-grid" id="menuGrid"></div>
    
     <button class="btn add-to-itinerary-btn" id="addToItineraryBtn" onclick="addBreakfastToItinerary()">
       <span>⭐</span> Add to My Itinerary
     </button>


     <button class="btn btn-primary" onclick="goToStep(3)">
       <span>📝</span> Continue to Order
       <span>→</span>
     </button>
   </div>


   <!-- Order Section -->
   <div class="step" id="step3">
     <button class="btn back-btn" onclick="goToStep(2)">
       <span>←</span> Back to Menu
     </button>
     <div class="order-section">
       <h2 style="color: #fbbf24; margin-bottom: 20px;">Your Order</h2>
       <div id="orderList"></div>
      
       <h3 style="margin-top: 30px; color: #fbbf24;">Add Custom Item</h3>
       <input type="text" class="custom-input" id="customInput" placeholder="E.g., Gluten-free waffle with almond butter">
       <button class="btn" onclick="addCustom()">
         <span>➕</span> Add Custom Item
       </button>
     </div>
     <button class="btn btn-primary" onclick="goToStep(4)">
       <span>✅</span> Review Order
       <span>→</span>
     </button>
   </div>


   <!-- Order Confirmation -->
   <div class="step" id="step4">
     <div class="order-section">
       <h2 style="color: #fbbf24; margin-bottom: 20px;">Order Confirmation</h2>
       <div id="reviewHeader"></div>
       <div id="reviewList"></div>
       <div class="total" id="totalPrice">Total: $0</div>
      
       <button class="btn back-btn" onclick="goToStep(3)">
         <span>←</span> Edit Order
       </button>
       <button class="btn btn-primary" onclick="confirmOrder()">
         <span>📦</span> Confirm Order
       </button>
     </div>
   </div>


   <!-- Navigation to Landmarks Page -->
   <div class="nav-to-landmarks">
     <h2>Ready for the Next Adventure?</h2>
     <p>With a full stomach, let's move on to picking your ideal attraction to sight see!</p>
     <a href="/student/new-york/landmarks/" class="landmarks-btn">
       🗽 Explore NYC Landmarks
     </a>
   </div>
 </div>


 <div class="itinerary-tracker hidden" id="itineraryTracker">
   <h3>🗽 Your NYC Trip</h3>
  
   <div class="itinerary-item" id="tripInfoItem">
     <div class="itinerary-label">📅 Trip Dates</div>
     <div class="itinerary-value" id="tripDatesValue">
       <span class="itinerary-empty">Not set yet</span>
     </div>
   </div>
  
   <div class="itinerary-item incomplete" id="breakfastItem">
     <div class="itinerary-label">🍳 Breakfast</div>
     <div class="itinerary-value" id="breakfastValue">
       <span class="itinerary-empty">Not selected</span>
     </div>
   </div>
  
   <div class="itinerary-item incomplete" id="landmarksItem">
     <div class="itinerary-label">🗽 Landmarks</div>
     <div class="itinerary-value" id="landmarksValue">
       <span class="itinerary-empty">Not selected</span>
     </div>
   </div>
  
   <div class="itinerary-item incomplete" id="shoppingItem">
     <div class="itinerary-label">🛍️ Shopping</div>
     <div class="itinerary-value" id="shoppingValue">
       <span class="itinerary-empty">Not selected</span>
     </div>
   </div>
  
   <div class="itinerary-item incomplete" id="broadwayItem">
     <div class="itinerary-label">🎭 Broadway</div>
     <div class="itinerary-value" id="broadwayValue">
       <span class="itinerary-empty">Not selected</span>
     </div>
   </div>
  
   <button class="clear-itinerary-btn" onclick="clearItinerary()">
     Clear All Selections
   </button>
 </div>


 <script type="module">
   // ============================================
   // ITINERARY TRACKER JAVASCRIPT
   // ============================================


   function initItinerary() {
     const itinerary = getItinerary();
     updateItineraryDisplay(itinerary);
     updateQuickAddButtons();
   }


   function getItinerary() {
     const stored = localStorage.getItem('nycItinerary');
     return stored ? JSON.parse(stored) : {
       tripInfo: null,
       breakfast: null,
       landmarks: null,
       shopping: null,
       broadway: null
     };
   }


   function saveItinerary(itinerary) {
     localStorage.setItem('nycItinerary', JSON.stringify(itinerary));
     updateItineraryDisplay(itinerary);
   }


   function updateItineraryDisplay(itinerary) {
     if (itinerary.tripInfo) {
       document.getElementById('tripDatesValue').innerHTML =
         `${itinerary.tripInfo.month} ${itinerary.tripInfo.startDate} - ${itinerary.tripInfo.endDate}`;
       document.getElementById('tripInfoItem').classList.remove('incomplete');
     }
    
     if (itinerary.breakfast) {
       document.getElementById('breakfastValue').textContent = itinerary.breakfast;
       document.getElementById('breakfastItem').classList.remove('incomplete');
     }
    
     if (itinerary.landmarks) {
       document.getElementById('landmarksValue').textContent = itinerary.landmarks;
       document.getElementById('landmarksItem').classList.remove('incomplete');
     }
    
     if (itinerary.shopping) {
       document.getElementById('shoppingValue').innerHTML =
         `${itinerary.shopping.center}<br><small>${itinerary.shopping.gender}'s Fashion</small>`;
       document.getElementById('shoppingItem').classList.remove('incomplete');
     }
    
     if (itinerary.broadway) {
       document.getElementById('broadwayValue').innerHTML =
         `${itinerary.broadway.theater}<br><small>${itinerary.broadway.show}</small>`;
       document.getElementById('broadwayItem').classList.remove('incomplete');
     }
   }


   function clearItinerary() {
     if (confirm('Are you sure you want to clear your entire itinerary?')) {
       localStorage.removeItem('nycItinerary');
       location.reload();
     }
   }


   function toggleItineraryTracker() {
     const tracker = document.getElementById('itineraryTracker');
     tracker.classList.toggle('hidden');
   }


   function addBreakfastToItinerary() {
     if (!currentRestaurant) return;
    
     const restaurantData = MENU_DATA[currentRestaurant];
     const itinerary = getItinerary();
     itinerary.breakfast = restaurantData.name;
     saveItinerary(itinerary);
    
     const btn = document.getElementById('addToItineraryBtn');
     btn.classList.add('added');
     btn.innerHTML = '<span>✓</span> Added to Itinerary';
    
     setTimeout(() => {
       updateAddButton();
     }, 2000);
   }


   function updateAddButton() {
     const itinerary = getItinerary();
     const btn = document.getElementById('addToItineraryBtn');
     if (btn && itinerary.breakfast && currentRestaurant) {
       const restaurantData = MENU_DATA[currentRestaurant];
       if (itinerary.breakfast === restaurantData.name) {
         btn.classList.add('added');
         btn.innerHTML = '<span>✓</span> Added to Itinerary';
       } else {
         btn.classList.remove('added');
         btn.innerHTML = '<span>⭐</span> Add to My Itinerary';
       }
     }
   }


   function updateQuickAddButtons() {
     const itinerary = getItinerary();
     const buttons = document.querySelectorAll('.quick-add-btn');
    
     buttons.forEach((btn) => {
       const restaurantKey = btn.getAttribute('data-restaurant');
       const restaurantData = MENU_DATA[restaurantKey];
      
       if (itinerary.breakfast === restaurantData.name) {
         btn.classList.add('added');
         btn.innerHTML = '<span>✓</span> Added';
       } else {
         btn.classList.remove('added');
         btn.innerHTML = '<span>⭐</span> Add';
       }
     });
   }


   function quickAddToItinerary(restaurantKey, event) {
     event.stopPropagation();
    
     const restaurantData = MENU_DATA[restaurantKey];
     const itinerary = getItinerary();
     itinerary.breakfast = restaurantData.name;
     saveItinerary(itinerary);
    
     updateQuickAddButtons();
   }


   // ============================================
   // DATE FILTERING FUNCTIONS
   // ============================================


   // Get selected days from itinerary
   function getSelectedDays() {
       const itinerary = getItinerary();
       if (!itinerary.tripInfo || !itinerary.tripInfo.startDate || !itinerary.tripInfo.endDate) {
           return null; // Return null if no dates are selected
       }
      
       const month = itinerary.tripInfo.month;
       const dateRange = parseDateRange(month, itinerary.tripInfo.startDate, itinerary.tripInfo.endDate);
      
       if (!dateRange) return null;
      
       // Get unique days of the week from the date range
       const selectedDays = new Set();
       const currentDate = new Date(dateRange.start);
      
       while (currentDate <= dateRange.end) {
           const dayName = currentDate.toLocaleDateString('en-US', { weekday: 'long' });
           selectedDays.add(dayName);
           currentDate.setDate(currentDate.getDate() + 1);
       }
      
       return Array.from(selectedDays);
   }


   // Parse date range from stored format
   function parseDateRange(month, startStr, endStr) {
       try {
           const currentYear = new Date().getFullYear();
          
           // Extract day numbers
           const startDay = parseInt(startStr.match(/\d+/)[0]);
           const endDay = parseInt(endStr.match(/\d+/)[0]);
          
           const startDate = new Date(`${month} ${startDay}, ${currentYear}`);
           const endDate = new Date(`${month} ${endDay}, ${currentYear}`);
          
           return { start: startDate, end: endDate };
       } catch (error) {
           console.error('Error parsing dates:', error);
           return null;
       }
   }


   // ============================================
   // LIVE BREAKFAST HOURS INTEGRATION
   // ============================================


   // API Configuration
   import { pythonURI, fetchOptions } from '{{ site.baseurl }}/assets/js/api/config.js';
   //const API_BASE_URL = 'http://localhost:8587/api/breakfast';
  
   // Restaurant mapping
   const RESTAURANT_MAP = {
     'sarabeths': { name: "Sarabeth's", endpoint: 'sarabeths' },
     'jacks': { name: "Jack's Wife Freda", endpoint: 'jacks' },
     'ess': { name: "Ess-a-Bagel", endpoint: 'bagel' },
     'shuka': { name: "Shuka", endpoint: 'shuka' }
   };


   // Menu data
   const MENU_DATA = {
     sarabeths: {
       name: "Sarabeth's",
       location: "Upper West Side",
       description: "A beloved NYC institution known for its legendary homemade jams and elegant brunch classics. Perfect for a refined, upscale breakfast experience.",
       items: [
         {name: 'Lemon Ricotta Pancakes', price: 18, desc: 'Fluffy pancakes with fresh lemon zest'},
         {name: 'Eggs Benedict', price: 22, desc: 'Poached eggs on English muffin'},
         {name: 'French Toast', price: 16, desc: 'Challah bread with maple syrup'},
         {name: 'Fresh Squeezed OJ', price: 8, desc: 'Orange juice made to order'}
       ]
     },
     jacks: {
       name: "Jack's Wife Frida",
       location: "SoHo",
       description: "Mediterranean-inspired breakfast with bold Mexican flavors. A trendy spot with colorful dishes and creative twists on morning favorites.",
       items: [
         {name: 'Shakshuka', price: 19, desc: 'Poached eggs in spicy tomato sauce'},
         {name: 'Avocado Toast', price: 16, desc: 'Sourdough with smashed avocado'},
         {name: 'Mexican Omelet', price: 18, desc: 'With chorizo and peppers'},
         {name: 'Cold Brew Coffee', price: 6, desc: 'Smooth and refreshing'}
       ]
     },
     ess: {
       name: "Ess a Bagel",
       location: "Midtown East",
       description: "The ultimate NYC bagel experience. Hand-rolled, kettle-boiled bagels that are crispy outside and pillowy inside. A true New York classic.",
       items: [
         {name: 'Everything Bagel', price: 5, desc: 'With cream cheese'},
         {name: 'Lox and Bagel', price: 18, desc: 'Nova lox with cream cheese'},
         {name: 'Egg Sandwich', price: 12, desc: 'Fried egg and cheese'},
         {name: 'Hot Coffee', price: 3, desc: 'Fresh brewed'}
       ]
     },
     shuka: {
       name: "Shuka",
       location: "East Village",
       description: "Modern Mediterranean cuisine with Israeli breakfast specialties. Fresh, vibrant dishes featuring tahini, hummus, and perfectly spiced shakshuka.",
       items: [
         {name: 'Israeli Breakfast', price: 22, desc: 'Eggs, hummus, tahini, salad'},
         {name: 'Halloumi Scramble', price: 19, desc: 'With grilled halloumi cheese'},
         {name: 'Quinoa Bowl', price: 17, desc: 'Roasted vegetables and egg'},
         {name: 'Turkish Coffee', price: 5, desc: 'Strong and aromatic'}
       ]
     }
   };


   let currentRestaurant = null;
   let cart = [];


   // ============================================
   // API FUNCTIONS
   // ============================================


   // Test API connection
   async function testAPIConnection() {
     try {
       //const response = await fetch(`${API_BASE_URL}/test`);
       const response = await fetch(`${pythonURI}/test`, fetchOptions );
       const data = await response.json();
      
       const statusIndicator = document.getElementById('apiStatus');
       if (data.success) {
         statusIndicator.textContent = '✅ API Connected';
         statusIndicator.className = 'live-data-indicator';
         return true;
       } else {
         statusIndicator.textContent = '⚠️ API Error';
         statusIndicator.className = 'live-data-indicator offline';
         return false;
       }
     } catch (error) {
       console.error('API connection failed:', error);
       const statusIndicator = document.getElementById('apiStatus');
       statusIndicator.textContent = '❌ API Offline';
       statusIndicator.className = 'live-data-indicator offline';
       return false;
     }
   }


   // MODIFIED: Format hours with date filtering
   function formatHoursInChronologicalOrder(hoursData, selectedDays = null) {
     const dayOrder = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];
     let html = '';
    
     if (hoursData.hours && typeof hoursData.hours === 'object') {
       // Filter days based on selected itinerary dates
       let daysToDisplay = dayOrder;
       if (selectedDays && selectedDays.length > 0) {
           daysToDisplay = dayOrder.filter(day => selectedDays.includes(day));
       }
      
       // Display only filtered days
       daysToDisplay.forEach(day => {
           if (hoursData.hours[day]) {
               html += `
                   <div class="day-hour">
                     <span class="day">${day}:</span>
                     <span class="time">${hoursData.hours[day]}</span>
                   </div>
               `;
           }
       });
      
       // Show message if no hours for selected days
       if (html === '' && Object.keys(hoursData.hours).length > 0) {
           html = `
               <div class="day-hour">
                   <span class="day">Note:</span>
                   <span class="time">No hours available for selected dates</span>
               </div>
           `;
       }
     } else if (typeof hoursData.hours === 'string') {
       html += `<div class="day-hour"><span class="time">${hoursData.hours}</span></div>`;
     }
    
     return html;
   }


   // Fetch hours for a specific restaurant
   async function fetchRestaurantHours(restaurantKey) {
     const restaurant = RESTAURANT_MAP[restaurantKey];
     if (!restaurant) return null;


     try {
       //const response = await fetch(`${API_BASE_URL}/${restaurant.endpoint}`);
      const response = await fetch(`${pythonURI}/${restaurant.endpoint}`, fetchOptions );

       const data = await response.json();
      
       if (data.success) {
         return data.data;
       } else {
         console.error(`Error fetching ${restaurant.name}:`, data.error);
         return null;
       }
     } catch (error) {
       console.error(`Network error for ${restaurant.name}:`, error);
       return null;
     }
   }


   // ============================================
   // UI FUNCTIONS
   // ============================================


   function goToStep(n) {
     document.querySelectorAll('.step').forEach(step => {
       step.classList.remove('active');
     });
     document.getElementById('step' + n).classList.add('active');
     if (n === 4) showReview();
     if (n === 2) updateAddButton();
   }


   async function selectRestaurant(restaurantKey) {
     currentRestaurant = restaurantKey;
    
     // Update restaurant details
     const restaurantData = MENU_DATA[restaurantKey];
     document.getElementById('restaurantName').textContent = restaurantData.name;
     document.getElementById('restaurantLocation').textContent = `📍 ${restaurantData.location}`;
     document.getElementById('restaurantDescription').textContent = restaurantData.description;
    
     // Fetch live hours
     await refreshCurrentRestaurant();
    
     // Show menu
     showMenu();
     goToStep(2);
   }


   // MODIFIED: Refresh restaurant with date filtering
   async function refreshCurrentRestaurant() {
     if (!currentRestaurant) return;
    
     const restaurantData = MENU_DATA[currentRestaurant];
     const hoursContainer = document.getElementById('restaurantHours');
    
     // Show loading
     hoursContainer.innerHTML = `
       <div class="hours-loading">
         <div class="live-loading-spinner"></div>
         <div>Fetching live hours for ${restaurantData.name}...</div>
       </div>
     `;
    
     try {
       const hoursData = await fetchRestaurantHours(currentRestaurant);
      
       if (hoursData) {
         let hoursHtml = `<div class="hours-display">`;
        
         // Get selected days from itinerary
         const selectedDays = getSelectedDays();
        
         // Add subtle indicator if filtering is active
         if (selectedDays && selectedDays.length > 0) {
           hoursHtml += `
             <div style="margin-bottom: 10px; padding: 8px; background: rgba(255, 215, 0, 0.05); border-radius: 6px; font-size: 0.9rem; color: #ffd700;">
               📅 Showing hours for: ${selectedDays.join(', ')}
             </div>
           `;
         }
        
         // Use filtered chronological order formatting
         hoursHtml += formatHoursInChronologicalOrder(hoursData, selectedDays);
        
         hoursHtml += `</div>`;
        
         if (hoursData.error) {
           hoursHtml += `<p style="color: #ef4444;">⚠️ Note: ${hoursData.error}</p>`;
         }
        
         hoursHtml += `
           <div class="update-note">
             <strong>Source:</strong> ${hoursData.source || 'Live API'}
             | <strong>Updated:</strong> ${new Date().toLocaleTimeString()}
             ${selectedDays ? ` | <strong>Filtered by itinerary</strong>` : ''}
           </div>
         `;
        
         hoursContainer.innerHTML = hoursHtml;
       } else {
         throw new Error('No hours data');
       }
     } catch (error) {
       console.error('Error fetching hours:', error);
      
       // Get selected days for error message
       const selectedDays = getSelectedDays();
       let errorMessage = 'Unable to fetch live hours';
       if (selectedDays) {
         errorMessage += ` for selected dates`;
       }
      
       hoursContainer.innerHTML = `
         <div class="hours-display">
           <div class="day-hour">
             <span class="day">Status:</span>
             <span class="time" style="color: #ef4444;">${errorMessage}</span>
           </div>
         </div>
         <div class="update-note">⚠️ Showing fallback information</div>
       `;
     }
   }


   function showMenu() {
     const menuGrid = document.getElementById('menuGrid');
     const items = MENU_DATA[currentRestaurant].items;
    
     menuGrid.innerHTML = items.map(item => `
       <div class="menu-item">
         <h4>${item.name}</h4>
         <div class="price">${item.price}</div>
         <p>${item.desc}</p>
         <button class="btn" onclick="addToCart('${item.name}', ${item.price})" style="width: 100%; margin-top: 10px;">
           <span>➕</span> Add to Order
         </button>
       </div>
     `).join('');
   }


   function addToCart(name, price) {
     cart.push({ name, price });
     updateOrderList();
   }


   function updateOrderList() {
     const orderList = document.getElementById('orderList');
     if (cart.length === 0) {
       orderList.innerHTML = '<p style="color: #94a3b8;">Your order is empty. Add items from the menu!</p>';
       return;
     }
    
     orderList.innerHTML = cart.map((item, index) => `
       <div class="order-item">
         <div>
           <strong>${item.name}</strong>
           <div style="color: #10b981;">${item.price}</div>
         </div>
         <button class="remove-btn" onclick="removeFromCart(${index})">Remove</button>
       </div>
     `).join('');
   }


   function removeFromCart(index) {
     cart.splice(index, 1);
     updateOrderList();
   }


   function addCustom() {
     const input = document.getElementById('customInput');
     const customItem = input.value.trim();
    
     if (customItem) {
       cart.push({ name: customItem, price: 0 });
       input.value = '';
       updateOrderList();
     }
   }


   function showReview() {
     const reviewHeader = document.getElementById('reviewHeader');
     const reviewList = document.getElementById('reviewList');
     const totalPrice = document.getElementById('totalPrice');
    
     reviewHeader.innerHTML = `<h3 style="color: #f59e0b; margin-bottom: 20px;">${MENU_DATA[currentRestaurant].name}</h3>`;
    
     if (cart.length === 0) {
       reviewList.innerHTML = '<p style="color: #94a3b8;">No items in order</p>';
       totalPrice.textContent = 'Total: $0';
       return;
     }
    
     reviewList.innerHTML = cart.map(item => `
       <div class="order-item">
         <div>
           <strong>${item.name}</strong>
         </div>
         <div style="color: #10b981; font-size: 20px; font-weight: bold;">${item.price}</div>
       </div>
     `).join('');
    
     const total = cart.reduce((sum, item) => sum + item.price, 0);
     totalPrice.textContent = `Total: ${total}`;
   }


   function confirmOrder() {
     alert(`Order confirmed at ${MENU_DATA[currentRestaurant].name}! Total: ${cart.reduce((sum, item) => sum + item.price, 0)}`);
     cart = [];
     goToStep(1);
   }


   // Initialize on page load
   document.addEventListener('DOMContentLoaded', () => {
     initItinerary();
     testAPIConnection();
    
     // Update API status if dates are set
     const itinerary = getItinerary();
     if (itinerary.tripInfo) {
       const selectedDays = getSelectedDays();
       if (selectedDays) {
         const statusIndicator = document.getElementById('apiStatus');
         if (statusIndicator && statusIndicator.textContent.includes('✅')) {
           statusIndicator.textContent = '✅ API Connected | 📅 Date Filter Active';
         }
       }
     }

     // ===== ADD THESE LINES HERE (at the end, inside DOMContentLoaded) =====
     // Expose functions to global scope so inline onclick="" can find them
     window.selectRestaurant = selectRestaurant;
     window.quickAddToItinerary = quickAddToItinerary;
     window.addBreakfastToItinerary = addBreakfastToItinerary;
     window.toggleItineraryTracker = toggleItineraryTracker;
     window.clearItinerary = clearItinerary;
     window.goToStep = goToStep;
     window.addToCart = addToCart;
     window.removeFromCart = removeFromCart;
     window.addCustom = addCustom;
     window.confirmOrder = confirmOrder;
     // ===== END EXPOSURES =====
   });
 </script>
</body>
</html>

