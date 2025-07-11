# AVEROX CRM System

A comprehensive AI-powered business solution platform that provides modular, scalable infrastructure for enterprise management with intelligent insights.

## Features

- User management and authentication
- Customer relationship management
- Lead tracking and management
- Opportunity pipeline management
- Product and inventory management
- Proposals and document generation
- Invoicing and billing
- AI-powered business insights
- Social media integration
- Communication hub

## Technology Stack

- **Frontend**: React, TypeScript, Tailwind CSS, Shadcn UI components
- **Backend**: Node.js, Express.js, Drizzle ORM
- **Database**: PostgreSQL
- **Authentication**: Passport.js, Express Session
- **Security**: AES-256 encryption with Averox CryptoSphere SDK
- **AI Integration**: OpenAI API
- **Payment Processing**: Stripe

## Project Structure

The project follows a modular domain-driven architecture with these key components:

```
/
├── client/                # React frontend application
├── server/                # Express.js backend
├── shared/                # Shared code and models
├── scripts/               # Database and utility scripts
├── docker/                # Docker configuration files
└── migrations/            # Database migration files
```

## Getting Started

### Local Development

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Set up environment variables (copy `.env.example` to `.env` and fill in required values)
4. Start the development server:
   ```bash
   npm run dev
   ```

### Using Docker

For containerized deployment, we provide Docker support:

1. Make sure Docker and Docker Compose are installed
2. Run the setup script:
   ```bash
   chmod +x docker/setup.sh
   ./docker/setup.sh
   ```
3. Start the containers:
   ```bash
   docker-compose up -d
   ```
4. Access the application at http://localhost

Detailed Docker instructions are available in the [docker/README.md](docker/README.md) file.

## Database Setup

The application uses PostgreSQL with Drizzle ORM. To initialize the database:

```bash
npm run db:push
```

To create demo data:

```bash
npx tsx scripts/create-demo-accounts-simple.ts
```

## Security Implementation

The system implements advanced security measures to protect sensitive data:

### AES-256 Encryption

The application uses the Averox CryptoSphere SDK to provide AES-256 encryption for sensitive data:

- **Selective Field Encryption**: Only sensitive fields are encrypted, maintaining performance
- **Transparent Middleware**: Automatic encryption/decryption via Express middleware
- **Database Security**: Support for encrypted database connection strings
- **Key Management**: Integrated with the Averox key monitoring system
- **Performance Optimization**: Encryption monitoring to identify bottlenecks

To enable encryption, set the following environment variables:

```
ENABLE_ENCRYPTION=true
CRYPTOSPHERE_API_KEY=your_api_key
CRYPTOSPHERE_KEY_ID=your_key_id
```

You can test the encryption functionality with:

```bash
node scripts/test-encryption.js
```

## API Documentation

API endpoints follow RESTful conventions and are organized by domain:

- `/api/auth` - Authentication endpoints
- `/api/users` - User management
- `/api/contacts` - Contact management
- `/api/leads` - Lead management
- `/api/opportunities` - Sales pipeline
- `/api/products` - Product catalog
- `/api/invoices` - Billing and invoicing
- `/api/encryption-test` - Test endpoint for encryption functionality

## Contributing

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details.