 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
new file mode 100644
index 0000000000000000000000000000000000000000..c0c4f17a020578a86a4b37627c214f88c2bee425
--- /dev/null
+++ b/README.md
@@ -0,0 +1,201 @@
+# WanderLust 🌍
+
+**WanderLust** is a full-stack travel-stay listing platform inspired by Airbnb, built to demonstrate production-style backend and full-stack engineering skills.
+
+Users can browse places, create and manage property listings, upload listing images, post reviews, and authenticate securely.
+
+---
+
+## ✨ Features
+
+- **User Authentication & Sessions**
+  - Sign up, log in, and log out
+  - Session-based authentication with Passport
+  - Flash messages for user feedback
+
+- **Listings (CRUD)**
+  - Create, view, update, and delete listings
+  - Only listing owners can edit/delete their listings
+  - Server-side form validation with Joi
+
+- **Image Uploads**
+  - Image upload support with Multer
+  - Cloud image storage using Cloudinary
+
+- **Reviews**
+  - Authenticated users can add ratings/comments
+  - Review author-based delete authorization
+  - Automatic review cleanup when listing is deleted
+
+- **Search**
+  - Case-insensitive location search
+
+- **Maps/Geocoding**
+  - Location-to-coordinates conversion via Mapbox Geocoding API
+  - GeoJSON storage in MongoDB for map-ready data
+
+---
+
+## 🧰 Tech Stack
+
+### Backend
+- Node.js
+- Express.js
+- MongoDB
+- Mongoose
+
+### Frontend
+- EJS
+- EJS-Mate
+- CSS / JavaScript
+
+### Authentication & Session
+- Passport
+- passport-local
+- passport-local-mongoose
+- express-session
+- connect-mongo
+- connect-flash
+
+### Validation & Utilities
+- Joi
+- method-override
+
+### Cloud Integrations
+- Cloudinary (media storage)
+- Mapbox SDK (geocoding)
+
+---
+
+## 📁 Project Structure
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
+## 🚀 Getting Started
+
+### 1) Clone & Install
+
+```bash
+git clone <your-repo-url>
+cd WanderLust
+npm install
+```
+
+### 2) Create `.env`
+
+Create a `.env` file in the root folder with:
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
+### 3) Run the App
+
+```bash
+node app.js
+```
+
+App runs at:
+
+```text
+http://localhost:8080
+```
+
+---
+
+## 🌱 Seed Sample Data (Optional)
+
+```bash
+node init/index.js
+```
+
+> Note: The seed script uses a local MongoDB URL by default. Update `init/index.js` if needed.
+
+---
+
+## 🔐 Authorization Rules
+
+- Must be logged in to create listings/reviews
+- Only listing owner can edit/delete listing
+- Only review author can delete review
+
+---
+
+## 🛣️ Key Routes
+
+- `GET /listings` — list all listings
+- `GET /listings/new` — new listing form (auth required)
+- `POST /listings` — create listing
+- `GET /listings/:id` — listing details
+- `PUT /listings/:id` — update listing (owner only)
+- `DELETE /listings/:id` — delete listing (owner only)
+- `POST /listings/:id/reviews` — create review (auth required)
+- `DELETE /listings/:id/reviews/:reviewId` — delete review (author only)
+- `GET /signup` / `POST /signup`
+- `GET /login` / `POST /login`
+- `GET /logout`
+
+---
+
+## 💼 Recruiter Highlights
+
+This project demonstrates:
+
+- Clean **MVC architecture** and modular Express design
+- Real-world **authentication + authorization** patterns
+- Secure input handling with **Joi validation**
+- Third-party integration with **Cloudinary + Mapbox**
+- Practical full-stack CRUD workflows with relational MongoDB references
+
+---
+
+## 🔮 Future Improvements
+
+- Booking and date availability
+- Wishlist/favorites
+- Filter + sort + pagination
+- Unit/integration tests
+- CI/CD and containerized deployment
+
+---
+
+## 👨‍💻 Author
+
+Built as a full-stack portfolio project to showcase practical backend, cloud integration, and web application architecture skills.
 
EOF
)
