1	# WanderLust 🌍
     2	
     3	A full-stack travel accommodation platform where users can discover unique stays, publish listings, upload photos, and share trusted reviews.
     4	
     5	WanderLust is built as a production-style MVC Node.js application and demonstrates practical backend engineering skills recruiters look for: authentication, authorization, RESTful routing, schema validation, media storage, geocoding, session persistence, and clean project structure.
     6	
     7	---
     8	
     9	## Why this project stands out
    10	
    11	- **Real product flow:** browse listings, create/own listings, review stays, and manage account sessions.
    12	- **Security-focused fundamentals:** Passport auth, route protection, ownership checks, and Joi request validation.
    13	- **Cloud integrations:** image uploads via Cloudinary and geolocation support via Mapbox.
    14	- **Scalable patterns:** MVC architecture, middleware layering, reusable utilities, and Mongo-backed sessions.
    15	
    16	---
    17	
    18	## Core Features
    19	
    20	### 1) Listings Management
    21	- View all listings with card-based browsing.
    22	- Create new listings with title, description, pricing, location, and country.
    23	- Edit or delete listings (owner-only).
    24	- Server-side validation for all listing inputs.
    25	
    26	### 2) Image Upload Pipeline
    27	- Listing images are uploaded with **Multer**.
    28	- Files are stored in **Cloudinary** through `multer-storage-cloudinary`.
    29	- Optimized image URLs are used in edit previews.
    30	
    31	### 3) Geospatial Support
    32	- Uses **Mapbox Geocoding API** to convert listing locations into coordinates.
    33	- Stores GeoJSON `Point` data in MongoDB for map-ready listing records.
    34	
    35	### 4) Authentication & Authorization
    36	- User signup/login/logout using **Passport + passport-local-mongoose**.
    37	- Session-based auth with persistent storage in MongoDB (`connect-mongo`).
    38	- Access control middleware ensures:
    39	  - only authenticated users can create listings/reviews
    40	  - only listing owners can edit/delete listings
    41	  - only review authors can delete reviews
    42	
    43	### 5) Review System
    44	- Logged-in users can post ratings and comments.
    45	- Reviews are linked to both listing and user.
    46	- Review cleanup occurs automatically when a listing is deleted.
    47	
    48	### 6) Search
    49	- Case-insensitive location search with regex filtering for fast listing discovery.
    50	
    51	---
    52	
    53	## Tech Stack
    54	
    55	**Backend**
    56	- Node.js
    57	- Express.js
    58	- MongoDB + Mongoose
    59	
    60	**Frontend**
    61	- EJS templates
    62	- EJS-Mate layouts
    63	- Static CSS + JS
    64	
    65	**Authentication & Sessions**
    66	- Passport
    67	- passport-local
    68	- passport-local-mongoose
    69	- express-session
    70	- connect-mongo
    71	- connect-flash
    72	
    73	**Validation & Utilities**
    74	- Joi
    75	- method-override
    76	
    77	**Cloud / External Services**
    78	- Cloudinary (image hosting)
    79	- Mapbox SDK (geocoding)
    80	
    81	---
    82	
    83	## Project Structure
    84	
    85	```bash
    86	WanderLust/
    87	├── app.js
    88	├── cloudConfig.js
    89	├── controllers/
    90	│   ├── listings.js
    91	│   ├── reviews.js
    92	│   └── users.js
    93	├── models/
    94	│   ├── listing.js
    95	│   ├── review.js
    96	│   └── user.js
    97	├── routes/
    98	│   ├── listing.js
    99	│   ├── review.js
   100	│   └── user.js
   101	├── views/
   102	│   ├── listings/
   103	│   ├── users/
   104	│   ├── includes/
   105	│   └── layouts/
   106	├── public/
   107	│   ├── css/
   108	│   └── js/
   109	├── middleware.js
   110	├── schema.js
   111	└── init/
   112	    ├── data.js
   113	    └── index.js
   114	```
   115	
   116	---
   117	
   118	## Local Setup
   119	
   120	### 1) Clone and install
   121	
   122	```bash
   123	git clone <your-repo-url>
   124	cd WanderLust
   125	npm install
   126	```
   127	
   128	### 2) Create `.env`
   129	
   130	```env
   131	ATLASDB_URL=<your_mongodb_connection_string>
   132	SECRET=<your_session_secret>
   133	MAP_TOKEN=<your_mapbox_token>
   134	CLOUD_NAME=<your_cloudinary_cloud_name>
   135	CLOUD_API_KEY=<your_cloudinary_api_key>
   136	CLOUD_API_SECRET=<your_cloudinary_api_secret>
   137	NODE_ENV=development
   138	```
   139	
   140	### 3) Run the app
   141	
   142	```bash
   143	node app.js
   144	```
   145	
   146	Server starts at:
   147	
   148	```text
   149	http://localhost:8080
   150	```
   151	
   152	---
   153	
   154	## Seed Data (Optional)
   155	
   156	To populate the database with starter listings:
   157	
   158	```bash
   159	node init/index.js
   160	```
   161	
   162	> Note: the seeding script uses a local MongoDB URL by default. Update `init/index.js` if you want to seed a cloud database.
   163	
   164	---
   165	
   166	## API & Route Highlights
   167	
   168	- `GET /listings` → list all stays
   169	- `GET /listings/new` → create form (auth required)
   170	- `POST /listings` → create listing (auth + validation)
   171	- `GET /listings/:id` → listing detail page
   172	- `PUT /listings/:id` → update listing (owner only)
   173	- `DELETE /listings/:id` → delete listing (owner only)
   174	- `POST /listings/:id/reviews` → create review (auth)
   175	- `DELETE /listings/:id/reviews/:reviewId` → delete review (author only)
   176	- `GET /signup | POST /signup`
   177	- `GET /login | POST /login`
   178	- `GET /logout`
   179	
   180	---
   181	
   182	## Recruiter-Focused Engineering Highlights
   183	
   184	- Implemented **session-backed auth lifecycle** with redirect-after-login UX.
   185	- Applied **defensive backend validation** with Joi schemas before DB writes.
   186	- Designed **ownership-based authorization** to protect user-generated content.
   187	- Integrated **third-party cloud services** (Mapbox + Cloudinary) into core CRUD flow.
   188	- Structured code with **separation of concerns** (routes/controllers/models/middleware).
   189	- Built with maintainable conventions that support future upgrades (favorites, bookings, payments, maps filtering).
   190	
   191	---
   192	
   193	## Future Enhancements
   194	
   195	- Booking availability calendar
   196	- Wishlist/Favorites
   197	- Advanced geospatial filters (radius, price range, amenities)
   198	- Pagination + sorting + caching
   199	- CI/CD pipeline and test suite (unit/integration)
   200	- Dockerized deployment profile
   201	
   202	---
   203	
   204	## Author
   205	
   206	**WanderLust Project**  
   207	Built to demonstrate full-stack development capability, cloud integration, and production-minded backend design.
