# Line-Lifft-App.
# Product Design Document (PDD): LIFF WebApp for Green Wxrp

## Overview
The Green Wxrp LIFF WebApp is a mobile-first, multilingual application tailored for a Thai herbal drink retailer. It integrates Google Sheets for data management, LIFF SDK for LINE-based authentication, and advanced analytics for operational insights. The app focuses on seamless sales, loyalty program management, and an optimized POS experience for both customers and staff.

### Key Features
- **Product List & Cart**: Browse products, manage a cart, and validate stock in real-time.
- **Cart & Checkout**: Review cart, search for members, track points, and process payments via PromptPay or manual slip uploads.
- **Sales Analytics & Admin Panel**: Track daily sales, top products, and customer analytics, with drill-downs and exportable reports.
- **Promotions & Coupons**: Display active promotions and coupons with redemption mechanisms.
- **Offline Mode**: Enable core functionality using localStorage during connectivity issues.
- **Member Registration**: Allow users to register personal details for targeted marketing and loyalty programs.

---

## System Architecture
- **Frontend**: Next.js, React, Tailwind CSS, Shadcn/ui
- **Backend/Integration**: Google Sheets API for CRUD operations
- **Authentication**: LIFF SDK for LINE-based user login
- **Analytics & Visualization**: Recharts for data visualization
- **Data Persistence**: localStorage for offline mode

---

## Features Breakdown

### 1. Product List & Cart
#### Description
Enables users to browse products and manage a cart for checkout.
#### Functionalities
- Display products as cards with image, name, price, and stock status.
- Search and filter products by category.
- Persistent cart (via localStorage) with add/remove/edit functionality.
- Seamless integration with Google Sheets for real-time product and stock updates.
#### Integration
- Fetch product data from Google Sheets API.
- Sync cart state with localStorage.
- Update UI dynamically on stock changes.
#### Offline Mode
- Display cached product data and enable cart actions offline.
#### UI/UX
- Mobile-friendly product cards.
- Floating cart button with item count.
- Thai language for labels and messages.

---

### 2. Cart & Checkout
#### Description
Allows users to review their cart, track member points, and complete payments.
#### Functionalities
- Edit cart: adjust quantities, remove items.
- Member search by phone/name to fetch points.
- Payment options: PromptPay QR code generation and manual slip uploads.
- Stock validation during checkout.
#### Integration
- Fetch member data, sales records, and payment status from Google Sheets.
- Store pending sales in localStorage during offline mode.
#### UI/UX
- Cart summary with breakdown of costs and promotions.
- Member details with points display.
- Payment slip viewer and approval/rejection interface.

---

### 3. Sales Analytics & Admin Panel
#### Description
Provides admins with insights into sales and customer behaviors.
#### Functionalities
- Daily sales summary, top products, and customer segmentation.
- Drill-down analytics for product and customer performance.
- Exportable reports (Excel/PDF).
#### Integration
- Fetch sales, product, and customer data from Google Sheets.
- Store analytics data locally for offline access.
#### UI/UX
- Dashboard with charts and summarized data.
- Thai labels and tooltips for accessibility.
- Permissions to restrict access to owners.

---

### 4. Promotions & Coupons
#### Description
Manages and displays active promotions and coupons for users.
#### Functionalities
- Display promotions and coupons with names, details, images, and validity dates.
- Allow users to redeem coupons and view usage status.
#### Integration
- Fetch and update promotion and coupon data via Google Sheets.
- Sync redemption status offline and online.
#### UI/UX
- Promotions and coupons displayed as cards with clear visuals.
- "Use Coupon" button with feedback for successful/failed redemption.

---

### 5. Member Registration
#### Description
Adds a registration mechanism for users to provide personal details.
#### Functionalities
- Registration form with fields for nickname, phone number, birthdate, occupation, and interests.
- Dropdown list for selecting knowledge areas of interest.
- Data saved to Google Sheets for marketing and loyalty program insights.
#### Integration
- Write new member data to Google Sheets.
#### UI/UX
- Simple, mobile-friendly form.
- Thai labels and placeholders.

---

### 6. Offline Mode
#### Description
Ensures the app functions seamlessly when offline or with intermittent connectivity.
#### Functionalities
- Cache product, cart, and sales data in localStorage.
- Queue cart actions and payment updates for later sync.
#### Integration
- Sync cached data with Google Sheets when online.
#### UI/UX
- Notification of offline mode with cached data status.
- Graceful degradation for unavailable features.

---

## Dependencies
1. **Google Sheets API**:
   - CRUD operations for products, members, promotions, and sales data.
   - URL or ID for each Google Sheet.
2. **LIFF SDK**:
   - Enable LINE-based authentication and user data retrieval.
   - LIFF ID required for integration.
3. **Recharts**:
   - Support for data visualization in analytics and admin panels.

---

## Edge Cases
1. **Stock Conflicts**:
   - Notify users of stock unavailability at checkout.
2. **Payment Slip Rejections**:
   - Provide reasons for rejection in Thai.
3. **Data Sync Conflicts**:
   - Resolve offline/online conflicts using last-write-wins.
4. **Large Datasets**:
   - Implement pagination for product, sales, and customer data.

---

## Acceptance Criteria
- All features (product list, cart, checkout, analytics, promotions, registration) work online and offline.
- Thai UI for all labels, messages, and tooltips.
- Error logging implemented for API failures and sync conflicts.
- Responsive, mobile-first design across all screens.
- Permissions restrict admin dashboard access to owners.
- Reports export correctly in Excel and PDF formats.

---

## Suggested Future Enhancements
1. **Push Notifications**:
   - Notify users of new promotions or expiring coupons.
2. **Order History**:
   - Display past orders and transaction details for members.
3. **Admin Panel**:
   - Enable dynamic management of products, promotions, and coupons.
4. **Social Sharing**:
   - Allow users to share promotions via LINE messages.

---

## Next Steps
### **Questions to Answer**
1. Do you have Google Sheets API credentials (API Key) and sheet IDs ready?
2. What is the LIFF ID for app integration?
3. Are there additional fields or data points needed for specific features (e.g., promotions, coupons)?
4. Confirm the structure of Google Sheets for all data tables.

### **Preparation Checklist**
- [ ] Ensure Google Sheets are created with the required structure and shared for API access.
- [ ] Create LIFF App and retrieve LIFF ID for integration.
- [ ] Provide graphics (e.g., product images, promotion banners) as URLs for seamless display.
- [ ] Define the dropdown options for the registration form.