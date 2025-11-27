# 🍔 Foodie - Food Delivery App

A complete production-ready MERN stack food delivery application with Razorpay payment integration, user authentication, cart management, order tracking, and admin dashboard.

## 🚀 Features

### User Features
- ✅ User Registration & Login with JWT Authentication
- ✅ Browse Menu with Category Filtering
- ✅ Add Items to Cart (stored in MongoDB)
- ✅ Real-time Cart Updates
- ✅ Secure Checkout with Razorpay Payment Gateway
- ✅ Order History & Tracking
- ✅ Responsive Design for Mobile & Desktop

### Admin Features
- ✅ Admin Dashboard with Statistics
- ✅ Menu Management (Add, Edit, Delete Items)
- ✅ Order Management (View & Update Order Status)
- ✅ Real-time Order Statistics

## 🛠️ Tech Stack

### Frontend
- **React 18** - UI Library
- **Vite** - Build Tool
- **Redux Toolkit** - State Management
- **React Router** - Routing
- **Tailwind CSS** - Styling
- **Axios** - HTTP Client

### Backend
- **Node.js** - Runtime
- **Express** - Web Framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **Razorpay** - Payment Gateway
- **bcryptjs** - Password Hashing

## 📁 Project Structure

```
Foodie/
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   ├── MenuItem.js
│   │   ├── Cart.js
│   │   └── Order.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── menu.js
│   │   ├── cart.js
│   │   ├── order.js
│   │   └── admin.js
│   ├── middleware/
│   │   └── auth.js
│   ├── scripts/
│   │   └── seedData.js
│   ├── server.js
│   ├── package.json
│   └── .env.example
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   └── Layout/
│   │   │       └── Navbar.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   ├── Menu.jsx
│   │   │   ├── Cart.jsx
│   │   │   ├── Checkout.jsx
│   │   │   ├── Orders.jsx
│   │   │   ├── OrderDetails.jsx
│   │   │   └── Admin/
│   │   │       ├── AdminDashboard.jsx
│   │   │       ├── AdminMenu.jsx
│   │   │       └── AdminOrders.jsx
│   │   ├── store/
│   │   │   ├── store.js
│   │   │   └── slices/
│   │   │       ├── authSlice.js
│   │   │       ├── cartSlice.js
│   │   │       └── menuSlice.js
│   │   ├── utils/
│   │   │   └── ProtectedRoute.jsx
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── postcss.config.js
└── README.md
```

## 🔧 Installation & Setup

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local or MongoDB Atlas)
- Razorpay Account (for payment integration)

### Backend Setup

1. **Navigate to backend directory**
   ```bash
   cd backend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Create `.env` file**
   ```bash
   cp .env.example .env
   ```

4. **Configure environment variables**
   Edit `.env` file with your values:
   ```env
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/foodie
   JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
   RAZORPAY_KEY_ID=your_razorpay_key_id
   RAZORPAY_KEY_SECRET=your_razorpay_key_secret
   ```

5. **Start MongoDB**
   Make sure MongoDB is running on your system. If using MongoDB Atlas, update `MONGODB_URI` in `.env`.

6. **Seed test data (optional)**
   ```bash
   npm run seed
   ```
   This will create:
   - Admin user: `admin@foodie.com` / `admin123`
   - Test user: `user@foodie.com` / `user123`
   - 15 sample menu items

7. **Start the server**
   ```bash
   npm run dev
   ```
   Server will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory**
   ```bash
   cd frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```
   Frontend will run on `http://localhost:3000`

## 🔑 Razorpay Setup

**⚠️ Important**: You need valid Razorpay API keys for payment functionality to work.

See **[RAZORPAY_SETUP.md](./RAZORPAY_SETUP.md)** for detailed step-by-step instructions.

### Quick Setup:
1. Create account at [Razorpay Dashboard](https://dashboard.razorpay.com/)
2. Go to **Settings → API Keys**
3. Generate **Test Keys** (for development)
4. Copy `Key ID` (starts with `rzp_test_...`) and `Key Secret`
5. Update `backend/.env`:
   ```env
   RAZORPAY_KEY_ID=rzp_test_xxxxxxxxxxxxx
   RAZORPAY_KEY_SECRET=xxxxxxxxxxxxxxxxxxxx
   ```
6. Restart your backend server

**Test Card** (Test Mode Only):
- Card: `4111 1111 1111 1111`
- Expiry: Any future date
- CVV: Any 3 digits

## 📝 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user (Protected)

### Menu
- `GET /api/menu` - Get all menu items
- `GET /api/menu?category=main-course` - Get items by category
- `GET /api/menu/:id` - Get single menu item

### Cart (Protected)
- `GET /api/cart` - Get user's cart
- `POST /api/cart/add` - Add item to cart
- `PUT /api/cart/update/:itemId` - Update cart item quantity
- `DELETE /api/cart/remove/:itemId` - Remove item from cart
- `DELETE /api/cart/clear` - Clear cart

### Orders (Protected)
- `POST /api/orders/create` - Create order
- `POST /api/orders/verify` - Verify payment
- `GET /api/orders/my-orders` - Get user orders
- `GET /api/orders/:id` - Get order details

### Admin (Protected, Admin Only)
- `GET /api/admin/stats` - Get dashboard statistics
- `GET /api/admin/menu` - Get all menu items (including unavailable)
- `POST /api/admin/menu` - Create menu item
- `PUT /api/admin/menu/:id` - Update menu item
- `DELETE /api/admin/menu/:id` - Delete menu item
- `GET /api/admin/orders` - Get all orders
- `PUT /api/admin/orders/:id/status` - Update order status

## 🧪 Test Credentials

After running the seed script:

**Admin Account:**
- Email: `admin@foodie.com`
- Password: `admin123`

**User Account:**
- Email: `user@foodie.com`
- Password: `user123`

## 🔒 Security Features

- JWT tokens stored in localStorage
- Password hashing with bcrypt
- Protected routes with authentication middleware
- Admin-only routes with role-based access control
- Razorpay payment signature verification

## 🎨 Features Implementation

### Protected Routes
- User must be logged in to access cart, checkout, and orders
- Admin routes require admin role
- Automatic redirect to login if not authenticated

### Cart Management
- Cart stored in MongoDB (persistent across sessions)
- Real-time updates with Redux
- Quantity management
- Automatic total calculation

### Payment Flow
1. User fills delivery information
2. Order created in database
3. Razorpay order created
4. Payment gateway opens
5. Payment verification on success
6. Order status updated
7. Cart cleared

### Admin Dashboard
- Real-time statistics
- Menu CRUD operations
- Order status management
- Filter orders by status

## 🚀 Production Deployment

### Backend
1. Set production MongoDB URI
2. Use strong JWT_SECRET
3. Use Razorpay Live keys
4. Enable CORS for production domain
5. Deploy to services like Heroku, Railway, or AWS

### Frontend
1. Update API URLs in production
2. Build for production: `npm run build`
3. Deploy to Vercel, Netlify, or AWS S3

## 📱 Responsive Design

The application is fully responsive and works seamlessly on:
- Desktop (1920px+)
- Laptop (1024px+)
- Tablet (768px+)
- Mobile (320px+)

## 🐛 Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running
- Check MONGODB_URI in .env
- Verify network connectivity for MongoDB Atlas

### Razorpay Payment Issues
- Verify API keys in .env
- Check Razorpay dashboard for webhook logs
- Ensure correct currency (INR) is used

### JWT Token Issues
- Clear localStorage and login again
- Check JWT_SECRET in backend .env
- Verify token expiration (7 days)

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Development

### Running in Development Mode

**Backend:**
```bash
cd backend
npm run dev
```


## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Development

### Running in Development Mode

**Backend:**
```bash
cd backend
npm run dev
```

**Frontend:**
```bash
cd frontend
npm run dev
```

### Building for Production

**Frontend:**
```bash
cd frontend
npm run build
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

For issues and questions, please open an issue on the repository.

---

**Made with ❤️ using MERN Stack**

**Frontend:**
```bash
cd frontend
npm run dev
```

### Building for Production

**Frontend:**
```bash
cd frontend
npm run build
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

For issues and questions, please open an issue on the repository.

---

**Made with ❤️ using MERN Stack**

