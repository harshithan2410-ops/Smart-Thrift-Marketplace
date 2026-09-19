# Thriftify 🛒

Thriftify is an online marketplace platform for buying and selling second-hand items, promoting sustainability through reuse and reducing waste.



## 🚀 Demo

[Live Demo](https://thriftify.onrender.com/)

### Sandbox Credentials
For testing and demo purposes, you can use the following sandbox credentials:

- **Email:** sb-pzckc40679934@business.example.com
- **Password:** hYM*t^i4

## ✨ Features

- **User Authentication:** Secure registration and login system with JWT
- **Product Listings:** Create, view, update, and delete listings with image uploads
- **Categories:** Browse items by categories (electronics, furniture, clothing, books, others)
- **Search & Filters:** Find items by location, category, price, etc.
- **Bookmarks:** Save favorite items for later
- **Messaging:** Real-time chat between buyers and sellers
- **Payment Integration:** Secure checkout with PayPal
- **Order Management:** Track purchases and sales
- **User Profiles:** Customizable user profiles with profile pictures

## 💻 Tech Stack

### Backend
- Node.js
- Express.js
- MongoDB (Mongoose)
- JWT for authentication
- Cloudinary for image storage
- PayPal API for payment integration
- Swagger for API documentation

### Frontend
- EJS templates
- JavaScript
- CSS
- Responsive design components

## 🔧 Installation

### Prerequisites
- Node.js (v14+)
- MongoDB
- npm or yarn

### Setup Steps

1. Clone the repository
```bash
git clone https://github.com/yourusername/thriftify.git
cd thriftify
```

2. Install dependencies
```bash
npm install
```

3. Create a `.env` file in the root directory with the following variables:
```
PORT=3000
MONGODB_URI=mongodb://localhost:27017/thriftify
ACCESS_TOKEN_SECRETE=your_jwt_secret_key
CLOUDINARY_CLOUD_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_key
CLOUDINARY_API_SECRET=your_cloudinary_secret
PAYPAL_CLIENT_ID=your_paypal_client_id
PAYPAL_CLIENT_SECRET=your_paypal_client_secret
```

4. Start the server
```bash
npm start
```

5. For development with auto-reload:
```bash
npm run dev
```

6. Visit `http://localhost:3000` in your browser

## 📚 API Documentation

Thriftify provides comprehensive API documentation using Swagger UI.

### Accessing Swagger Documentation

When running the application locally, you can access the Swagger documentation at:
```
http://localhost:3000/api-docs
```

You can also access the Swagger documentation on the deployed version:
```
https://thriftify.onrender.com/api-docs
```

### Key Endpoints

#### User Endpoints

- **POST /api/v1/user/register** - Register a new user
- **POST /api/v1/user/login** - Login and receive authentication token
- **GET /api/v1/user/profile** - Get current user profile
- **PUT /api/v1/user/profile** - Update user profile

#### Listing Endpoints

- **GET /api/v1/listings** - Get all listings with optional filters
- **POST /api/v1/listings** - Create a new listing
- **GET /api/v1/listings/:id** - Get specific listing details
- **PUT /api/v1/listings/:id** - Update a listing
- **DELETE /api/v1/listings/:id** - Delete a listing

#### Bookmark Endpoints

- **GET /api/v1/bookmarks** - Get all bookmarks for current user
- **POST /api/v1/bookmarks/:listingId** - Add a listing to bookmarks
- **DELETE /api/v1/bookmarks/:listingId** - Remove a listing from bookmarks

#### Order Endpoints

- **POST /api/v1/orders/create** - Create a new order
- **GET /api/v1/orders** - Get all orders for current user
- **GET /api/v1/orders/:id** - Get specific order details

#### Category Endpoints

- **GET /api/v1/category/:category** - Get listings by category

#### Support Endpoint

- **POST /api/v1/support/submit** - Submit a support request

## 🗄️ Database Schema

### User

- `username`: String (unique)
- `email`: String (unique)
- `fullname`: String
- `password`: String (hashed)
- `profilepic`: String
- `createdAt`: Date
- `updatedAt`: Date

### Listing

- `title`: String
- `description`: String
- `price`: Number
- `category`: String (enum: electronics, furniture, clothing, books, others)
- `location`: String
- `images`: [String]
- `postedBy`: ObjectId (reference to User)
- `status`: String (available, sold)
- `createdAt`: Date
- `updatedAt`: Date

### Bookmark

- `user`: ObjectId (reference to User)
- `listing`: ObjectId (reference to Listing)
- `createdAt`: Date

### Order

- `buyer`: ObjectId (reference to User)
- `listing`: ObjectId (reference to Listing)
- `seller`: ObjectId (reference to User)
- `paymentId`: String
- `shippingInfo`: Object
- `paymentMethod`: String
- `status`: String (pending, completed, cancelled)
- `createdAt`: Date
- `updatedAt`: Date

## 📁 Project Structure

```
thriftify/
├── DataBase/
│   └── connect.js
├── Routes/
│   ├── bookmark.router.js
│   ├── category.router.js
│   ├── listing.router.js
│   ├── orders.router.js
│   └── user.router.js
├── Schemas/
│   ├── bookmark.schemas.js
│   ├── category.schemas.js
│   ├── listings.schemas.js
│   ├── order.schemas.js
│   └── user.schemas.js
├── utils/
│   └── asynchandler.js
├── views/
│   ├── chat.ejs
│   ├── home.ejs
│   ├── index.ejs
│   ├── payment-cancel.ejs
│   └── payment-success.ejs
├── public/
│   ├── css/
│   ├── js/
│   └── images/
├── app.js
├── swagger.js
├── .env.example
├── package.json
└── README.md
```

## 🚀 Deployment

Thriftify can be easily deployed on Render with both backend and frontend services.

### Quick Deploy to Render

**Option 1: Blueprint Deployment (Recommended)**

The easiest way to deploy the entire application at once:

1. Push your code to GitHub
2. Go to [Render Dashboard](https://dashboard.render.com/)
3. Click "New +" → "Blueprint"
4. Connect your repository (Render will auto-detect `render.yaml`)
5. Configure environment variables
6. Click "Apply"

📖 **Step-by-step guide:** See [RENDER_DEPLOY.md](./RENDER_DEPLOY.md) for quick start

✅ **Deployment checklist:** Use [DEPLOYMENT_CHECKLIST.md](./DEPLOYMENT_CHECKLIST.md) to ensure nothing is missed

📚 **Detailed documentation:** See [DEPLOY.md](./DEPLOY.md) for comprehensive instructions

### Required Services

1. **MongoDB Atlas** (Database) - Free tier available
2. **Cloudinary** (Image uploads) - Free tier available
3. **Render** (Hosting) - Free tier available

### Environment Variables Required

**Backend:**
- `MONGODB_URI` - MongoDB connection string
- `JWT_SECRET` - JWT secret key (auto-generated)
- `JWT_REFRESH_SECRET` - JWT refresh secret (auto-generated) 
- `CLOUDINARY_CLOUD_NAME` - Cloudinary cloud name
- `CLOUDINARY_API_KEY` - Cloudinary API key
- `CLOUDINARY_API_SECRET` - Cloudinary API secret
- `FRONTEND_URL` - Frontend URL (for CORS)

**Frontend:**
- `VITE_API_URL` - Backend API URL

### Features Included in Deployment Config

✅ Automatic builds and deployments  
✅ Health checks configured  
✅ CORS properly configured  
✅ WebSocket support for real-time chat  
✅ Static file serving for frontend  
✅ Environment-based configuration  

### Production URL

- **Demo**: [https://thriftify.onrender.com](https://thriftify.onrender.com)

### Free Tier Notes

- Services sleep after 15 minutes of inactivity on free tier
- First request after sleep takes 30-60 seconds to wake up
- Consider upgrading to paid tier for production use

## 🔒 Authentication

Thriftify uses JSON Web Tokens (JWT) for authentication:
- Tokens are stored in HTTP-only cookies for security
- Protected routes require valid authentication
- User sessions expire after a configured period

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Contact

Project Link: [https://github.com/viraj-gavade/thriftify](https://github.com/viraj-gavade/Thriftify)

### Connect with Me
- 📸 Instagram: [@_viraj.js]([https://instagram.com/yourinstagram](https://www.instagram.com/_viraj.js/))
- 🐦 Twitter: [@viraj_gavade]([https://twitter.com/yourtwitter](https://x.com/viraj_gavade))
- 💼 LinkedIn: [Viraj Gavade]([https://linkedin.com/in/yourlinkedin](https://www.linkedin.com/in/viraj-gavade-dev/))

## 📷 Screenshots

Here are some screenshots of the Thriftify application:

### Homepage
![Homepage](./Backend/screenshots/homepage.png)

### Product Listing
![Product Listing](./Backend/screenshots/product-listing.png)

### Payment Gateway
![payment View](./Backend/screenshots/payment-view.png)
