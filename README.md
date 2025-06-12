# Internship Application System

A comprehensive internship application system with a beautiful React frontend and Node.js/Express backend that integrates with Google Sheets API for secure data storage.

## Features

- **Beautiful UI**: Modern, responsive design with blue gradient theme
- **Comprehensive Form**: Collects all necessary applicant information
- **File Upload**: Resume upload with validation (PDF/Word, max 5MB)
- **Real-time Validation**: Client-side and server-side validation
- **Google Sheets Integration**: Secure storage using Google Sheets API
- **Rate Limiting**: Prevents spam and abuse
- **Error Handling**: Comprehensive error handling and user feedback
- **Security**: Helmet.js, CORS, input sanitization

## Prerequisites

- Node.js (v16 or higher)
- Google Cloud Console account
- Google Sheets API credentials

## Setup Instructions

### 1. Google Sheets API Setup

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the Google Sheets API
4. Create credentials (Service Account)
5. Download the JSON key file
6. Create a Google Sheet and share it with the service account email (found in the JSON file)
7. Copy the spreadsheet ID from the URL

### 2. Environment Configuration

1. Copy `.env.example` to `.env`
2. Fill in your Google Sheets configuration:
   ```
   GOOGLE_SPREADSHEET_ID=your_spreadsheet_id_here
   GOOGLE_SERVICE_ACCOUNT_KEY_FILE=path/to/your/service-account-key.json
   ```

### 3. Installation

```bash
# Install dependencies
npm install

# Start development server (both frontend and backend)
npm run dev

# Or run separately:
npm run client  # Frontend only
npm run server  # Backend only
```

### 4. Production Build

```bash
npm run build
```

## API Endpoints

### Health Check
- **GET** `/api/health` - Check server status

### Applications
- **POST** `/api/applications` - Submit internship application
  - Content-Type: `multipart/form-data`
  - Rate limited: 10 requests per 15 minutes per IP

## Form Fields

### Required Fields
- First Name
- Last Name
- Email
- Phone Number
- University
- Major
- Graduation Year
- Position Applied For
- Available Start Date
- Cover Letter (min 50 characters)
- Skills
- How did you hear about us?

### Optional Fields
- GPA
- LinkedIn URL
- GitHub URL
- Portfolio URL
- Previous Experience
- Resume File

## Security Features

- **Rate Limiting**: 10 applications per 15 minutes per IP
- **File Validation**: Only PDF and Word documents, max 5MB
- **Input Validation**: Comprehensive validation using Joi
- **CORS Protection**: Configured for specific origins
- **Helmet.js**: Security headers
- **Data Sanitization**: All inputs are validated and sanitized

## Google Sheets Schema

The application data is stored in a Google Sheet with the following columns:

1. Timestamp
2. First Name
3. Last Name
4. Email
5. Phone
6. University
7. Major
8. Graduation Year
9. GPA
10. Position Applied
11. Available Start Date
12. Cover Letter
13. LinkedIn URL
14. GitHub URL
15. Portfolio URL
16. Previous Experience
17. Skills
18. Referral Source
19. Resume File

## Error Handling

- **Client-side**: Real-time validation with user-friendly error messages
- **Server-side**: Comprehensive validation and error responses
- **Network errors**: Graceful handling of connection issues
- **File upload errors**: Clear feedback for file validation failures

## Development

The application uses:
- **Frontend**: React 18 + TypeScript + Tailwind CSS + Lucide React
- **Backend**: Node.js + Express + Google Sheets API
- **Validation**: Joi for server-side validation
- **File Upload**: Multer for handling multipart/form-data
- **Security**: Helmet, CORS, rate limiting

## License

MIT License