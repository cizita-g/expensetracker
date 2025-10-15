# Expense Tracker

A comprehensive expense tracking application that combines OCR technology with AI-powered categorization to help users manage their finances efficiently. The application allows users to scan receipts, automatically extract data, categorize expenses, and track budgets.

## 🌟 Features

### 📱 Core Functionality
- **Receipt Scanning**: Upload or capture receipt images using camera
- **OCR Text Extraction**: Automatically extract text from receipt images using EasyOCR
- **AI-Powered Data Processing**: Use LLM to structure and clean extracted receipt data
- **Smart Categorization**: Automatically categorize items using Naive Bayes machine learning
- **Budget Management**: Create and track monthly budgets by category
- **Expense Analytics**: Visualize spending patterns with interactive charts
- **User Authentication**: Secure login/signup with JWT tokens and password reset functionality

### 📊 Analytics & Visualization
- Monthly spending trends
- Category-wise expense breakdown
- Budget vs actual spending comparison
- Interactive charts and graphs using Chart.js and Recharts
- Receipt history with detailed item listings

### 🔧 Technical Features
- **Backend**: Flask REST API with SQLAlchemy ORM
- **Frontend**: React with modern UI components using Tailwind CSS
- **Database**: SQLite for development, easily configurable for production
- **Image Processing**: OpenCV for receipt preprocessing
- **OCR**: EasyOCR for text extraction from images
- **ML Integration**: Naive Bayes classifier for expense categorization

## 🏗️ Architecture

```
expensetracker/
├── backend/                 # Flask API server
│   ├── app.py              # Main Flask application
│   ├── models.py           # Database models
│   ├── config.py           # Configuration settings
│   ├── requirements.txt    # Python dependencies
│   ├── ocr/                # OCR processing modules
│   │   ├── ocr.py          # EasyOCR text extraction
│   │   └── llm.py          # LLM data structuring
│   ├── services/           # Business logic services
│   │   └── category_service.py
│   ├── uploads/            # Uploaded receipt images
│   └── ocr_output/         # OCR processed text files
└── client/                 # React frontend application
    ├── src/
    │   ├── components/     # Reusable UI components
    │   ├── pages/          # Application pages
    │   └── App.jsx         # Main application component
    ├── package.json        # Node.js dependencies
    └── tailwind.config.js  # Tailwind CSS configuration
```

## 🚀 Getting Started

### Prerequisites

- **Python 3.8+**
- **Node.js 16+**
- **npm or yarn**

### Backend Setup

1. **Navigate to backend directory**
   ```bash
   cd backend
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the backend directory:
   ```env
   SECRET_KEY=your-secret-key-here
   SQLALCHEMY_DATABASE_URI=sqlite:///app.db
   MAIL_SERVER=smtp.gmail.com
   MAIL_PORT=587
   MAIL_USE_TLS=True
   MAIL_USERNAME=your-email@gmail.com
   MAIL_PASSWORD=your-app-password
   ```

5. **Initialize database**
   ```bash
   python -c "from app import app, db; app.app_context().push(); db.create_all()"
   ```

6. **Populate categories**
   ```bash
   python prepopulate_categories.py
   ```

7. **Start the backend server**
   ```bash
   python app.py
   ```
   The backend will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to client directory**
   ```bash
   cd client
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   ```
   The frontend will run on `http://localhost:5173`

## 📱 Usage

### 1. User Registration & Login
- Create an account or login with existing credentials
- Reset password functionality available via email

### 2. Receipt Scanning
- **Upload Image**: Select receipt image from device
- **Camera Capture**: Use device camera to capture receipt
- **OCR Processing**: System automatically extracts text and structures data

### 3. Expense Management
- Review extracted receipt data
- Edit or confirm item details
- Items are automatically categorized using ML

### 4. Budget Tracking
- Set monthly budgets by category
- View budget vs actual spending
- Track spending trends over time

### 5. Analytics Dashboard
- View spending patterns with interactive charts
- Monthly expense breakdowns
- Category-wise analysis

## 🔧 API Endpoints

### Authentication
- `POST /api/register` - User registration
- `POST /api/login` - User login
- `POST /api/forgot-password` - Password reset request
- `POST /api/reset-password/<token>` - Reset password

### Receipt Management
- `POST /api/upload` - Upload receipt image for OCR
- `POST /api/save-receipt` - Save processed receipt data
- `GET /api/get-receipts` - Retrieve user's receipts
- `DELETE /api/receipts/<id>` - Delete receipt

### Budget Management
- `POST /api/budget` - Create/update budgets
- `GET /api/budget/<month>` - Get budgets for specific month
- `GET /api/budget/months` - Get all budgeted months

### Analytics
- `GET /api/expenses/<month>` - Get expenses for specific month
- `GET /api/expenses/monthly` - Get monthly expense totals
- `GET /api/expenses/total` - Get total expenses

## 🤖 Machine Learning Components

### OCR Processing Pipeline
1. **Image Preprocessing**: OpenCV for image enhancement
2. **Text Extraction**: EasyOCR for multilingual text recognition
3. **Data Cleaning**: LLM-based text structuring and cleaning
4. **Categorization**: Naive Bayes classifier for expense categorization

### Category Service
- Pre-trained model for expense categorization
- Automatic item classification based on item names
- Support for custom categories and training

## 🛠️ Technologies Used

### Backend
- **Flask**: Web framework
- **SQLAlchemy**: ORM for database operations
- **Flask-JWT-Extended**: JWT authentication
- **Flask-Bcrypt**: Password hashing
- **Flask-Mail**: Email functionality
- **EasyOCR**: Optical character recognition
- **OpenCV**: Image processing
- **Pandas**: Data manipulation
- **Scikit-learn**: Machine learning (Naive Bayes)

### Frontend
- **React 19**: UI framework
- **React Router**: Client-side routing
- **Tailwind CSS**: Utility-first CSS framework
- **Chart.js**: Data visualization
- **Recharts**: React charting library
- **Axios**: HTTP client
- **React Webcam**: Camera integration
- **Framer Motion**: Animation library

## 📁 Database Schema

### Tables
- **users**: User account information
- **receipts**: Receipt metadata and details
- **items**: Individual items from receipts
- **categories**: Expense categories
- **budgets**: Monthly budget allocations

### Relationships
- Users have many receipts and budgets
- Receipts have many items
- Items belong to categories
- Budgets are linked to users and categories

## 🔒 Security Features

- JWT-based authentication
- Password hashing with bcrypt
- CORS configuration
- Input validation and sanitization
- Secure file upload handling

## 🚀 Deployment

### Backend Deployment
1. Set up production database (PostgreSQL recommended)
2. Configure environment variables
3. Use production WSGI server (Gunicorn)
4. Set up reverse proxy (Nginx)

### Frontend Deployment
1. Build production bundle: `npm run build`
2. Serve static files with web server
3. Configure API endpoints for production

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For support and questions:
- Create an issue in the GitHub repository
- Check the documentation for common solutions

## 🔮 Future Enhancements

- [ ] Multi-language OCR support
- [ ] Advanced analytics and insights
- [ ] Export functionality (PDF, CSV)
- [ ] Mobile app development
- [ ] Integration with banking APIs
- [ ] Receipt storage optimization
- [ ] Advanced ML models for better categorization
- [ ] Social features and expense sharing

---


