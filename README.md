# 🩸 Blood Management System

A comprehensive web-based application designed to streamline blood bank operations, connecting donors, recipients, and healthcare administrators on a unified platform.

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://blood-management-system-omega.vercel.app)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🎯 Overview

The Blood Management System addresses critical challenges in blood donation and distribution by providing a digital platform that:

- Connects blood donors with those in need
- Manages blood inventory in real-time
- Streamlines the donation request and approval process
- Maintains comprehensive records of donations and transfusions
- Reduces response time in emergency situations

**Live Application:** [https://blood-management-system-omega.vercel.app](https://blood-management-system-omega.vercel.app)

## ✨ Features

### For Donors
- 🔐 Secure registration and login system
- 👤 Profile management (view, update, delete)
- 🩸 Blood donation scheduling
- 📊 Donation history tracking
- 🔔 Notifications for donation requests

### For Recipients
- 📝 Easy registration process
- 🔍 Search for available blood by type and location
- 📤 Submit blood requests
- 📈 Track request status
- 📜 View request history

### For Administrators
- 📊 Centralized dashboard for all operations
- 👥 Manage donor and recipient accounts
- 🏥 Blood inventory management across facilities
- ✅ Approve/reject donation and request submissions
- 📉 View analytics and reports
- 🩹 Update blood stock levels

### General Features
- 🔍 Advanced search functionality
- 📱 Responsive design for all devices
- 🔒 Secure authentication and authorization
- 📧 Email notifications
- 📊 Real-time blood availability tracking
- 🗺️ Location-based donor/blood bank search

## 🛠️ Tech Stack

### Frontend
- **HTML5** - Structure and semantic markup
- **CSS3** - Styling and responsive design
- **JavaScript** - Client-side interactivity
- **Bootstrap** - UI components and grid system (if applicable)

### Backend
- **Python** - Server-side programming
- **Flask/Django** - Web framework (based on your backend structure)
- **RESTful API** - API architecture

### Database
- **MySQL/SQLite** - Relational database management
- **SQL** - Database queries and operations

### Deployment
- **Vercel** - Frontend hosting
- **Cloud Database** - Database hosting

## 🏗️ System Architecture

```
┌─────────────────┐
│   Client/User   │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Frontend      │
│   (HTML/CSS/JS) │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Backend API   │
│   (Python)      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   Database      │
│   (MySQL)       │
└─────────────────┘
```

## 🚀 Installation

### Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.8 or higher
- pip (Python package manager)
- MySQL/SQLite
- Git
- A modern web browser

### Step-by-Step Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/Allanagari-Renuka/Blood-Management-System.git
   cd Blood-Management-System
   ```

2. **Set up the Backend**
   ```bash
   cd "Blood Management Backend"
   
   # Create a virtual environment
   python -m venv venv
   
   # Activate virtual environment
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   
   # Install dependencies
   pip install -r requirements.txt
   ```

3. **Configure the Database**
   ```bash
   # Create database
   mysql -u root -p
   CREATE DATABASE blood_management;
   
   # Import database schema
   mysql -u root -p blood_management < database/schema.sql
   ```

4. **Configure Environment Variables**
   
   Create a `.env` file in the backend directory:
   ```env
   DATABASE_HOST=localhost
   DATABASE_USER=root
   DATABASE_PASSWORD=your_password
   DATABASE_NAME=blood_management
   SECRET_KEY=your_secret_key_here
   FLASK_ENV=development
   ```

5. **Run Database Migrations** (if applicable)
   ```bash
   python manage.py migrate
   ```

6. **Start the Backend Server**
   ```bash
   python app.py
   # Server will run on http://localhost:5000
   ```

7. **Set up the Frontend**
   
   Open a new terminal window:
   ```bash
   cd "Blood Management front end"
   
   # If using a local server
   # Open index.html in your browser or use a local server:
   python -m http.server 8000
   # Access at http://localhost:8000
   ```

## 💻 Usage

### For First-Time Users

1. **Access the Application**
   - Navigate to [https://blood-management-system-omega.vercel.app](https://blood-management-system-omega.vercel.app)
   - Or access locally at `http://localhost:8000`

2. **Register an Account**
   - Click on "Register" button
   - Choose your role (Donor/Recipient/Admin)
   - Fill in required information
   - Submit the form

3. **Login**
   - Use your registered credentials
   - Access your personalized dashboard

### For Donors

1. Navigate to "Donate Blood" section
2. Fill in donation details
3. Submit and wait for approval
4. View donation history in your profile

### For Recipients

1. Go to "Request Blood" section
2. Specify blood type and quantity needed
3. Submit request
4. Track request status in dashboard

### For Administrators

1. Access admin dashboard
2. Manage users, blood inventory, and requests
3. Approve/reject submissions
4. Generate reports and analytics

## 📁 Project Structure

```
Blood-Management-System/
│
├── Blood Management Backend/
│   ├── app.py                 # Main application file
│   ├── models/                # Database models
│   ├── routes/                # API endpoints
│   ├── controllers/           # Business logic
│   ├── config/                # Configuration files
│   ├── utils/                 # Helper functions
│   ├── requirements.txt       # Python dependencies
│   └── database/              # Database scripts
│
├── Blood Management front end/
│   ├── index.html             # Home page
│   ├── login.html             # Login page
│   ├── register.html          # Registration page
│   ├── dashboard.html         # User dashboard
│   ├── css/                   # Stylesheets
│   │   └── styles.css
│   ├── js/                    # JavaScript files
│   │   └── main.js
│   └── assets/                # Images and resources
│
└── README.md                  # Project documentation
```

## 📡 API Documentation

### Authentication Endpoints

#### Register User
```http
POST /api/register
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "securePassword123",
  "role": "donor",
  "blood_type": "O+"
}
```

#### Login
```http
POST /api/login
Content-Type: application/json

{
  "email": "john@example.com",
  "password": "securePassword123"
}
```

### Donor Endpoints

#### Submit Donation
```http
POST /api/donations
Authorization: Bearer {token}
Content-Type: application/json

{
  "blood_type": "O+",
  "units": 1,
  "hospital_id": 123
}
```

#### Get Donation History
```http
GET /api/donations/history
Authorization: Bearer {token}
```

### Recipient Endpoints

#### Request Blood
```http
POST /api/requests
Authorization: Bearer {token}
Content-Type: application/json

{
  "blood_type": "A+",
  "units": 2,
  "urgency": "high",
  "reason": "Emergency surgery"
}
```

### Admin Endpoints

#### Get All Users
```http
GET /api/admin/users
Authorization: Bearer {admin_token}
```

#### Update Blood Stock
```http
PUT /api/admin/blood-stock
Authorization: Bearer {admin_token}
Content-Type: application/json

{
  "blood_type": "B+",
  "units": 50
}
```

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

1. **Fork the Repository**
   ```bash
   git clone https://github.com/your-username/Blood-Management-System.git
   ```

2. **Create a Feature Branch**
   ```bash
   git checkout -b feature/YourFeatureName
   ```

3. **Make Your Changes**
   - Write clean, documented code
   - Follow existing code style
   - Add tests if applicable

4. **Commit Your Changes**
   ```bash
   git commit -m "Add: Description of your feature"
   ```

5. **Push to Your Branch**
   ```bash
   git push origin feature/YourFeatureName
   ```

6. **Open a Pull Request**
   - Provide a clear description of changes
   - Reference any related issues

### Code of Conduct

- Be respectful and inclusive
- Write clear commit messages
- Document new features
- Test your code before submitting

## 🐛 Known Issues & Future Enhancements

### Current Limitations
- Real-time notifications not yet implemented
- Mobile app version in development
- Payment gateway integration pending

### Planned Features
- 🔔 Push notifications for urgent requests
- 📱 Native mobile applications (iOS/Android)
- 🗺️ Google Maps integration for donor location
- 📊 Advanced analytics dashboard
- 🌐 Multi-language support
- 🤖 AI-powered blood demand prediction

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

**Renuka Allanagari**
- GitHub: [@Allanagari-Renuka](https://github.com/Allanagari-Renuka)

## 🙏 Acknowledgments

- Thanks to all contributors who have helped improve this project
- Inspired by the need to save lives through efficient blood management
- Built with dedication to serve the community

## 📞 Support & Contact

- **Issues:** [GitHub Issues](https://github.com/Allanagari-Renuka/Blood-Management-System/issues)
- **Email:** [Your email address]
- **Website:** [https://blood-management-system-omega.vercel.app](https://blood-management-system-omega.vercel.app)

---

<div align="center">

**Made with ❤️ for saving lives**

⭐ Star this repository if you find it helpful!

[Report Bug](https://github.com/Allanagari-Renuka/Blood-Management-System/issues) · [Request Feature](https://github.com/Allanagari-Renuka/Blood-Management-System/issues)

</div>
