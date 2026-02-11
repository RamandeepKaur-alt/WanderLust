diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..d8d26198259e3684a7c74ef2d6c2fd074bcab298
--- /dev/null
+++ b/README.md
@@ -0,0 +1,207 @@
+# WanderLust 🌍
+ A production-style MVC travel listing platform inspired by Airbnb.
+ 🌐 Live Demo: [Visit WanderLust](https://majorproject-t36a.onrender.com/)


+A full-stack travel accommodation platform where users can discover unique stays, publish listings, upload photos, and share trusted reviews.
+
+WanderLust is built as a production-style MVC Node.js application and demonstrates practical backend engineering skills recruiters look for: authentication, authorization, RESTful routing, schema validation, media storage, geocoding, session persistence, and clean project structure.
+
+---
+
+## Why this project stands out
+
+- **Real product flow:** browse listings, create/own listings, review stays, and manage account sessions.
+- **Security-focused fundamentals:** Passport auth, route protection, ownership checks, and Joi request validation.
+- **Cloud integrations:** image uploads via Cloudinary and geolocation support via Mapbox.
+- **Scalable patterns:** MVC architecture, middleware layering, reusable utilities, and Mongo-backed sessions.
+
+---
+
+## Core Features
+
+### 1) Listings Management
+- View all listings with card-based browsing.
+- Create new listings with title, description, pricing, location, and country.
+- Edit or delete listings (owner-only).
+- Server-side validation for all listing inputs.
+
+### 2) Image Upload Pipeline
+- Listing images are uploaded with **Multer**.
+- Files are stored in **Cloudinary** through `multer-storage-cloudinary`.
+- Optimized image URLs are used in edit previews.
+
+### 3) Geospatial Support
+- Uses **Mapbox Geocoding API** to convert listing locations into coordinates.
+- Stores GeoJSON `Point` data in MongoDB for map-ready listing records.
+
+### 4) Authentication & Authorization
+- User signup/login/logout using **Passport + passport-local-mongoose**.
+- Session-based auth with persistent storage in MongoDB (`connect-mongo`).
+- Access control middleware ensures:
+  - only authenticated users can create listings/reviews
+  - only listing owners can edit/delete listings
+  - only review authors can delete reviews
+
+### 5) Review System
+- Logged-in users can post ratings and comments.
+- Reviews are linked to both listing and user.
+- Review cleanup occurs automatically when a listing is deleted.
+
+### 6) Search
+- Case-insensitive location search with regex filtering for fast listing discovery.
+
+---
+
+## Tech Stack
+
+**Backend**
+- Node.js
+- Express.js
+- MongoDB + Mongoose
+
+**Frontend**
+- EJS templates
+- EJS-Mate layouts
+- Static CSS + JS
+
+**Authentication & Sessions**
+- Passport
+- passport-local
+- passport-local-mongoose
+- express-session
+- connect-mongo
+- connect-flash
+
+**Validation & Utilities**
+- Joi
+- method-override
+
+**Cloud / External Services**
+- Cloudinary (image hosting)
+- Mapbox SDK (geocoding)
+
+---
+
+## Project Structure
+
+```bash
+WanderLust/
+├── app.js
+├── cloudConfig.js
+├── controllers/
+│   ├── listings.js
+│   ├── reviews.js
+│   └── users.js
+├── models/
+│   ├── listing.js
+│   ├── review.js
+│   └── user.js
+├── routes/
+│   ├── listing.js
+│   ├── review.js
+│   └── user.js
+├── views/
+│   ├── listings/
+│   ├── users/
+│   ├── includes/
+│   └── layouts/
+├── public/
+│   ├── css/
+│   └── js/
+├── middleware.js
+├── schema.js
+└── init/
+    ├── data.js
+    └── index.js
+```
+
+---
+
+## Local Setup
+
+### 1) Clone and install
+
+```bash
+git clone <your-repo-url>
+cd WanderLust
+npm install
+```
+
+### 2) Create `.env`
+
+```env
+ATLASDB_URL=<your_mongodb_connection_string>
+SECRET=<your_session_secret>
+MAP_TOKEN=<your_mapbox_token>
+CLOUD_NAME=<your_cloudinary_cloud_name>
+CLOUD_API_KEY=<your_cloudinary_api_key>
+CLOUD_API_SECRET=<your_cloudinary_api_secret>
+NODE_ENV=development
+```
+
+### 3) Run the app
+
+```bash
+node app.js
+```
+
+Server starts at:
+
+```text
+http://localhost:8080
+```
+
+---
+
+
+
+To populate the database with starter listings:
+
+```bash
+node init/index.js
+```
+
+> Note: the seeding script uses a local MongoDB URL by default. Update `init/index.js` if you want to seed a cloud database.
+
+---
+
+## API & Route Highlights
+
+- `GET /listings` → list all stays
+- `GET /listings/new` → create form (auth required)
+- `POST /listings` → create listing (auth + validation)
+- `GET /listings/:id` → listing detail page
+- `PUT /listings/:id` → update listing (owner only)
+- `DELETE /listings/:id` → delete listing (owner only)
+- `POST /listings/:id/reviews` → create review (auth)
+- `DELETE /listings/:id/reviews/:reviewId` → delete review (author only)
+- `GET /signup | POST /signup`
+- `GET /login | POST /login`
+- `GET /logout`
+
+---
+
+## Recruiter-Focused Engineering Highlights
+
+- Implemented **session-backed auth lifecycle** with redirect-after-login UX.
+- Applied **defensive backend validation** with Joi schemas before DB writes.
+- Designed **ownership-based authorization** to protect user-generated content.
+- Integrated **third-party cloud services** (Mapbox + Cloudinary) into core CRUD flow.
+- Structured code with **separation of concerns** (routes/controllers/models/middleware).
+- Built with maintainable conventions that support future upgrades (favorites, bookings, payments, maps filtering).
+
+---
+
+## Future Enhancements
+
+- Booking availability calendar
+- Wishlist/Favorites
+- Advanced geospatial filters (radius, price range, amenities)
+- Pagination + sorting + caching
+- CI/CD pipeline and test suite (unit/integration)
+- Dockerized deployment profile
+
+---
+
+## Author
+
+Built by Ramandeep Kaur to demonstrate full-stack development capability,
secure backend design, and cloud service integration.

