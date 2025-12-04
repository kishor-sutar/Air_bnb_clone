# 🏠 Airbnb Clone - Full Stack Web Application

A feature-rich Airbnb clone built with Node.js, Express, MongoDB, and EJS. This application allows users to browse, book, and manage property listings with a complete authentication system.

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

## ✨ Features

### 🔐 Authentication & Authorization
- User registration and login with secure password hashing (bcrypt)
- Session-based authentication with MongoDB session store
- Role-based access control (Guest/Host)
- Protected routes for authenticated users

### 🏡 Property Management
- **For Guests:**
  - Browse all available properties
  - View detailed property information
  - Book properties
  - Manage bookings (view and cancel)
  - Add properties to favourites
  - Remove properties from favourites

- **For Hosts:**
  - Add new property listings
  - Edit existing properties
  - Delete properties
  - Upload property images
  - Manage all hosted properties

### 📸 Image Upload
- Secure image upload with Multer
- File type validation (PNG, JPG, JPEG)
- Automatic file naming with random strings
- Image storage in dedicated uploads directory

### 🎨 User Interface
- Responsive design with TailwindCSS
- Clean and modern UI
- Dynamic EJS templates
- Real-time form validation
- Error handling and user feedback

## 🛠️ Tech Stack

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database
- **Mongoose** - MongoDB object modeling

### Frontend
- **EJS** - Templating engine
- **TailwindCSS** - Utility-first CSS framework
- **HTML5** - Markup language

### Authentication & Security
- **bcryptjs** - Password hashing
- **express-session** - Session management
- **connect-mongodb-session** - MongoDB session store
- **express-validator** - Input validation

### File Upload
- **Multer** - Multipart/form-data handling

## 📁 Project Structure

```
airbnb-clone/
├── controllers/          # Request handlers
│   ├── authController.js
│   ├── storeController.js
│   ├── hostController.js
│   └── errors.js
├── models/              # Database schemas
│   ├── user.js
│   └── home.js
├── routes/              # Route definitions
│   ├── authRouter.js
│   ├── storeRouter.js
│   └── hostRouter.js
├── views/               # EJS templates
│   ├── auth/           # Authentication pages
│   ├── store/          # Guest pages
│   ├── host/           # Host pages
│   └── partials/       # Reusable components
├── public/              # Static files
│   └── output.css      # Compiled TailwindCSS
├── uploads/             # Uploaded images
├── utils/               # Utility functions
├── app.js              # Application entry point
├── package.json        # Dependencies
└── tailwind.config.js  # TailwindCSS configuration
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (v4.4 or higher)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd airbnb-clone
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up MongoDB**
   - Make sure MongoDB is running on `mongodb://127.0.0.1:27017`
   - The application will create a database named `airbnb`

4. **Create uploads directory**
   ```bash
   mkdir uploads
   ```

5. **Start the application**
   ```bash
   npm start
   ```
   This will:
   - Start the Express server on port 3003
   - Watch and compile TailwindCSS automatically

6. **Access the application**
   ```
   http://localhost:3003
   ```

## 📝 Environment Variables

Create a `.env` file in the root directory (optional):

```env
PORT=3003
MONGODB_URI=mongodb://127.0.0.1:27017/airbnb
SESSION_SECRET=your-secret-key
```

## 🔑 API Routes

### Authentication Routes
- `GET /login` - Login page
- `POST /login` - Login user
- `GET /signup` - Signup page
- `POST /signup` - Register new user
- `POST /logout` - Logout user

### Guest Routes
- `GET /` - Home page with all listings
- `GET /homes` - Browse all properties
- `GET /homes/:homeId` - View property details
- `GET /bookings` - View user bookings
- `POST /bookings` - Book a property
- `POST /bookings/remove/:homeId` - Cancel booking
- `GET /favourites` - View favourite properties
- `POST /favourites` - Add to favourites
- `POST /favourites/delete/:homeId` - Remove from favourites

### Host Routes (Protected)
- `GET /host/add-home` - Add new property page
- `POST /host/add-home` - Create new property
- `GET /host/edit-home/:homeId` - Edit property page
- `POST /host/edit-home` - Update property
- `POST /host/delete-home/:homeId` - Delete property
- `GET /host/host-home-list` - View all hosted properties

## 💾 Database Models

### User Model
```javascript
{
  firstName: String (required),
  lastName: String,
  email: String (required, unique),
  password: String (required, hashed),
  userType: String (enum: ['guest', 'host']),
  favourites: [ObjectId] (ref: Home),
  bookings: [ObjectId] (ref: Home)
}
```

### Home Model
```javascript
{
  houseName: String (required),
  price: Number (required),
  location: String (required),
  rating: Number (required),
  photo: String,
  description: String
}
```

## 🎯 Key Features Implementation

### Session Management
- Sessions stored in MongoDB for persistence
- Automatic session cleanup
- Secure session configuration

### File Upload
- Image validation (PNG, JPG, JPEG only)
- Random filename generation
- Organized file storage

### Security Features
- Password hashing with bcrypt
- Session-based authentication
- Protected routes middleware
- Input validation and sanitization

## 🧪 Development Scripts

```bash
# Start development server with auto-reload
npm start

# Run TailwindCSS compiler only
npm run tailwind
```

## 📦 Dependencies

### Production
- express - ^4.21.0
- mongoose - ^8.12.1
- ejs - ^3.1.10
- bcryptjs - ^3.0.2
- express-session - ^1.18.1
- connect-mongodb-session - ^5.0.0
- multer - ^1.4.5-lts.2
- express-validator - ^7.2.1

### Development
- nodemon - ^3.1.7
- tailwindcss - ^3.4.13
- autoprefixer - ^10.4.20
- postcss - ^8.4.47

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the ISC License.

## 👨‍💻 Author

Built with ❤️ by kishor sutar

## 🙏 Acknowledgments

- Inspired by Airbnb
- Built as part of Complete Coding NodeJS Course
- TailwindCSS for the amazing utility-first framework

---

**Note:** This is a learning project and not intended for production use without proper security audits and enhancements.
