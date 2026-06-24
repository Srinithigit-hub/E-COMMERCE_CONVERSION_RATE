# E-COMMERCE_CONVERSION_RATE
A modern, full-stack e-commerce platform designed for a seamless shopping experience. Features secure user authentication, product catalog filtering, integrated payment processing, and a comprehensive admin dashboard.

🔗 View Live Site | 🖥️ Admin Dashboard

✨ Key Features:


●🔒 Secure Authentication: JWT-based user login, registration, and password recovery via OAuth.


●🔍 Advanced Search & Filter: Dynamic product filtering by category, price range, ratings, and real-time text search.


●🛒 Shopping Cart & Checkout: Persistent local-storage cart, real-time inventory checks, and single-page checkout.


●💳 Payment Integration: Secure sandbox payment processing integrated via Stripe / PayPal.


●📊 Admin Analytics Panel: Management suite for updating stock, tracking revenue metrics, and handling order fulfillment statuses.


●📱 Fully Responsive UI: Optimized layout for desktop, tablet, and mobile devices using CSS Grid and Flexbox.


🛠️ Tech Stack:


Layer:	Technologies Used


Frontend:	React.js, Tailwind CSS, Redux Toolkit (State Management)


Backend	:Node.js, Express.js


Database	:MongoDB (Mongoose ORM) / PostgreSQL


Payments	:Stripe API


Hosting	:Vercel (Frontend), Render / AWS (Backend)


⚙️ Getting Started:


Follow these steps to set up the project locally on your machine.

Prerequisites:


●Node.js (v18.x or higher)
●npm or yarn
●A free MongoDB Atlas account (or local MongoDB setup)
●A Stripe Developer Account (for API keys)
Clone the Repository
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
cd your-repo-name
Installation & Local Run
You can run both client and server concurrently, or spin them up in separate terminals.

🗺️ API Endpoint Preview
Method	Endpoint	Description	Auth Required
GET	/api/products	Fetch all products with pagination	No
GET	/api/products/:id	Fetch details for a specific item	No
POST	/api/cart	Sync local cart to user profile	Yes
POST	/api/orders	Create a new order after checkout	Yes
GET	/api/admin/analytics	Fetch sales stats (Admin only)	Yes
AUTHOR : MADHUMITHA LOGANATHAN