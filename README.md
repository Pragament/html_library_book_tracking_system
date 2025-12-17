# html_library_book_tracking_system
https://chat.deepseek.com/share/cpj65ndtb6qrv29b8o
```
// Your web app's Firebase configuration
  // For Firebase JS SDK v7.20.0 and later, measurementId is optional
  const firebaseConfig = {
    apiKey: "AIzaSyDQ1SY4lQ9CtaW_Fr_YD1-HJjMzUrmnCRQ",
    authDomain: "library-management-2d1fa.firebaseapp.com",
    projectId: "library-management-2d1fa",
    storageBucket: "library-management-2d1fa.firebasestorage.app",
    messagingSenderId: "874629417122",
    appId: "1:874629417122:web:e747713799610e81952ffb",
    measurementId: "G-80ED6ME7FR"
  };
```

# Library Book Tracking System

A comprehensive library management web application built with vanilla JavaScript and Firebase. This system allows librarians to track book borrowing and returns using QR code scanning or manual entry, with Google authentication for secure access.

## Features

### 🔐 Authentication
- Google Sign-In for secure librarian access
- User profile display with avatar
- Session management

### 📚 Book Management
- **QR Code Scanning**: Scan book QR codes for quick identification
- **Manual Entry**: Enter book details when QR codes aren't available
- **Add New Books**: Add books to catalog that aren't in the system
- **Real-time Catalog**: View all books with current status

### 📖 Borrowing & Returning
- **Quick Actions**: Borrow or return books with minimal steps
- **Borrower Identification**: Scan borrower QR codes or enter details manually
- **Due Date Management**: Set and track return dates
- **Overdue Detection**: Automatic overdue status calculation

### 📊 Dashboard & Reporting
- **Library Statistics**: Real-time counts of total, available, borrowed, and overdue books
- **Searchable Catalog**: Filter books by status or search by title/author/ID
- **Quick Actions**: Direct borrow/return from the catalog table
- **Transaction Logging**: All actions are recorded with timestamps

## Technology Stack

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Authentication**: Firebase Authentication (Google Sign-In)
- **Database**: Firebase Firestore (NoSQL)
- **QR Scanning**: HTML5 QR Code Scanner library
- **Icons**: Font Awesome 6.4.0

## Setup Instructions

### 1. Firebase Project Setup

1. Go to the [Firebase Console](https://console.firebase.google.com/)
2. Click "Add project" and create a new project
3. Enable the following services:

#### Authentication
- Go to **Authentication** → **Sign-in method**
- Click **Google**
- Toggle "Enable"
- Add a project support email
- Click **Save**

#### Firestore Database
- Go to **Firestore Database**
- Click **Create database**
- Start in **test mode** (for development)
- Choose a location and click **Enable**

### 2. Get Firebase Configuration

1. From your Firebase project overview, click the **</>** icon to add a web app
2. Register your app with a nickname
3. Copy the configuration object:
```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

### 3. Update the Application

1. Open the `index.html` file
2. Replace the placeholder Firebase configuration (lines 394-401) with your actual configuration
3. Save the file

### 4. Security Rules (Development)

For development, use these Firestore rules:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```

For production, implement more restrictive rules based on your needs.

## How to Use

### First-Time Setup
1. Open the application in a web browser
2. Sign in with your Google account
3. The system will automatically create sample data if the database is empty

### Borrowing a Book
1. Click **"Scan Book QR Code"** or **"Enter Book Manually"**
2. Identify the book (scan QR or enter ID)
3. Select **"Borrow This Book"**
4. Identify the borrower (scan QR or enter details)
5. Set the due date and confirm

### Returning a Book
1. Click **"Scan Book QR Code"** or the **"Return Book"** button
2. Identify the book
3. Select **"Return This Book"**
4. Add any return notes and confirm

### Managing the Catalog
- Use the search box to find specific books
- Filter by status: All, Borrowed, Available, or Overdue
- Click the action buttons in the catalog table for quick borrow/return

### Adding New Books
If a book isn't found in the catalog:
1. Use the **"Enter Book Manually"** option
2. Fill in book details (Title and ISBN/ID are required)
3. Click **"Add to Catalog"**

## QR Code Format

The system supports two QR code formats:

### Book QR Codes
- Simple format: Just the book ID or ISBN (e.g., `978-0451524935`)
- URL format: `https://library.example.com/books/{BOOK_ID}`

### Borrower QR Codes
- Simple format: Just the borrower ID
- JSON format: `{"name": "John Doe", "class": "12A", "id": "S12345"}`

## File Structure

```
library-tracker/
│
├── index.html          # Main application file
│
├── (No separate CSS/JS files - all inline in index.html)
│
└── README.md           # This documentation
```

## Browser Compatibility

- Chrome 60+ (recommended for best QR scanning performance)
- Firefox 55+
- Safari 11+
- Edge 79+

**Note**: QR code scanning works best on mobile devices or laptops with front-facing cameras.

## Sample Data

On first login, the system creates sample books:
- 1984 by George Orwell (Available)
- To Kill a Mockingbird by Harper Lee (Borrowed)
- Pride and Prejudice by Jane Austen (Available)
- The Great Gatsby by F. Scott Fitzgerald (Borrowed)
- The Hobbit by J.R.R. Tolkien (Available)

## Troubleshooting

### QR Scanner Not Working
1. Ensure camera permissions are granted
2. Try a different browser (Chrome works best)
3. Use manual entry as an alternative

### Authentication Issues
1. Check Firebase Authentication is enabled
3. Verify your Google account has access

### Database Errors
1. Check Firestore security rules
2. Ensure internet connection is stable
3. Verify Firebase configuration is correct

## Production Considerations

1. **Security Rules**: Implement proper Firestore security rules
2. **Error Handling**: Add more comprehensive error handling
3. **Backup**: Regular database backups
4. **Monitoring**: Set up Firebase monitoring and alerts
5. **Custom Domain**: Configure a custom domain for the application

## Support

For issues or questions:
1. Check Firebase documentation
2. Review browser console for errors
3. Ensure all Firebase services are properly enabled

---

**Note**: This application runs entirely in the browser. No backend server is required beyond Firebase services.
