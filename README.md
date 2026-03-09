# Stock Seller

A Next.js application for stock price monitoring, analysis, and automated trading recommendations with real-time notifications.

## Features

- **Stock Price Monitoring**: Real-time stock price tracking for both Indian (NSE) and US markets
- **DMA Analysis**: Dynamic Moving Average analysis for stock trends
- **Volatility Stop Analysis**: Calculate volatility-based stop losses for risk management
- **Watchlist Management**: Create and manage personalized stock watchlists
- **Smart Recommendations**: Automated buy/sell recommendations based on technical analysis
- **Real-time Notifications**: Push notifications via Firebase Cloud Messaging and WhatsApp
- **Batch Processing**: Automated batch jobs for price updates and analysis
- **Market Status**: Real-time market open/close status tracking

## Tech Stack

- **Frontend**: Next.js 14, React, TypeScript, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: MongoDB
- **Authentication**: Custom auth implementation
- **Notifications**: Firebase Cloud Messaging, WhatsApp API
- **Data Sources**: NSE, Yahoo Finance, Alpha Vantage, Finnhub, Twelve Data
- **Testing**: Jest

## Prerequisites

- Node.js 18+ and npm/yarn
- MongoDB instance
- Firebase project with Cloud Messaging enabled
- API keys for stock data providers (optional, based on requirements)

## Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd stock-seller
```

2. Install dependencies:

```bash
npm install
# or
yarn install
```

3. Create a `.env.local` file in the root directory with the following variables:

```env
# MongoDB
MONGODB_URI=your_mongodb_connection_string

# Firebase
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_auth_domain
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_storage_bucket
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=your_sender_id
NEXT_PUBLIC_FIREBASE_APP_ID=your_app_id
NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=your_measurement_id
FIREBASE_SERVICE_ACCOUNT_KEY=your_service_account_key_json

# WhatsApp (optional)
WHATSAPP_API_KEY=your_whatsapp_api_key

# Stock Data APIs (optional)
ALPHA_VANTAGE_API_KEY=your_alpha_vantage_key
FINNHUB_API_KEY=your_finnhub_key
TWELVE_DATA_API_KEY=your_twelve_data_key

# Auth
JWT_SECRET=your_jwt_secret
```

4. Run the development server:

```bash
npm run dev
# or
yarn dev
```

5. Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
├── src/
│   ├── app/                    # Next.js app directory
│   │   ├── api/               # API routes
│   │   │   ├── auth/          # Authentication endpoints
│   │   │   ├── batch/         # Batch processing
│   │   │   ├── cron/          # Scheduled jobs
│   │   │   ├── market/        # Market status
│   │   │   ├── notifications/ # Push notifications
│   │   │   ├── stock/         # Stock data and analysis
│   │   │   └── watchlist/     # Watchlist management
│   │   └── [pages]/           # Application pages
│   ├── components/            # React components
│   ├── hooks/                 # Custom React hooks
│   ├── lib/                   # Utility libraries and services
│   │   └── services/          # External API services
│   └── models/                # Database models
├── public/                    # Static assets
└── scripts/                   # Build and utility scripts
```

## API Endpoints

### Authentication

- `POST /api/auth/login` - User login

### Stock Data

- `GET /api/stock/price` - Get current stock price
- `GET /api/stock/price/batch` - Get multiple stock prices
- `GET /api/stock/recommendations` - Get buy/sell recommendations
- `GET /api/stock/recommendations/batch` - Batch recommendations
- `GET /api/stock/volatility` - Calculate volatility stop
- `POST /api/stock/dma/batch` - Batch DMA calculations

### Watchlist

- `GET /api/watchlist` - Get user watchlist
- `POST /api/watchlist` - Add stock to watchlist
- `DELETE /api/watchlist` - Remove stock from watchlist
- `GET /api/watchlist/user` - Get watchlist for specific user

### Market

- `GET /api/market/status` - Get current market status

### Notifications

- `POST /api/notifications/fcm/send` - Send FCM notification
- `POST /api/notifications/fcm/token` - Register FCM token
- `POST /api/notifications/whatsapp` - Send WhatsApp notification
- `POST /api/notifications/test` - Test notification

### Batch Processing

- `POST /api/batch/run` - Trigger batch processing

### Cron

- `GET /api/cron/check-prices` - Run price check cron job

## Key Features Explained

### DMA Analysis

The Dynamic Moving Average (DMA) analyzer helps identify trends by comparing short-term and long-term moving averages. The system automatically generates buy/sell signals based on DMA crossovers.

### Volatility Stop

Volatility-based stop loss calculation helps protect against significant market downturns by setting dynamic stop losses based on recent price volatility.

### Batch Processing

Automated batch jobs run periodically to:

- Update stock prices
- Calculate DMA values
- Generate recommendations
- Send alerts to users

### Notifications

Real-time notifications keep users informed about:

- Price targets reached
- Buy/sell signals
- Stop loss triggers
- Market events

## Development

### Running Tests

```bash
npm test
# or
yarn test
```

### Building for Production

```bash
npm run build
# or
yarn build
```

### Linting

```bash
npm run lint
# or
yarn lint
```

## Environment Setup

### Firebase Setup

1. Create a Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Enable Cloud Messaging
3. Add your web app and copy the configuration
4. Generate a service account key for server-side operations

### MongoDB Setup

1. Create a MongoDB Atlas cluster or use a local MongoDB instance
2. Create a database for the application
3. Add the connection string to `.env.local`s
