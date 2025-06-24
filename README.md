# Customer Management API

A RESTful API built with Node.js, Express, and MongoDB for managing customer data with comprehensive testing suite.

## 🚀 Features

- Create, Read, Update, Delete (CRUD) operations for customers
- MongoDB integration with Mongoose
- Comprehensive testing suite (Unit, Integration, API tests)
- Input validation and error handling
- 70%+ test coverage

## 🛠️ Tech Stack

- **Backend**: Node.js, Express.js
- **Database**: MongoDB with Mongoose ODM
- **Testing**: Jest, Supertest, MongoDB Memory Server
- **API Testing**: Postman (development), Automated tests (CI/CD)

## 📋 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/cus` | Get all customers |
| POST | `/cus/create` | Create a new customer |
| PATCH | `/cus/:id` | Update a customer by ID |
| DELETE | `/cus/:id` | Delete a customer by ID |

### Request/Response Examples

#### Create Customer
```bash
POST /api/customers
Content-Type: application/json

{
  "name": "John Doe",
  "email": "john@example.com",
  "age": 25
}
```

**Response:**
```json
{
  "success": true,
  "message": "Customer Has Been Added",
  "customer": {
    "name": "John Doe",
    "email": "john@example.com",
    "age": 25
  }
}
```

#### Get All Customers
```bash
GET /api/customers
```

**Response:**
```json
{
  "success": true,
  "message": "Customer are this",
  "count": 2,
  "customers": [
    {
      "id": "64f1a2b3c4d5e6f7g8h9i0j1",
      "name": "John Doe",
      "email": "john@example.com",
      "age": 25
    }
  ]
}
```

## 🏃‍♂️ Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local installation or MongoDB Atlas)
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd customer-api
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   Create a `.env` file in the root directory:
   ```env
   PORT=3000
   MONGODB_URI=url
   NODE_ENV=development
   ```

4. **Start the server**
   ```bash
   npm start
   ```

   The API will be available at `http://localhost:3000`

## 🧪 Testing

This project includes a comprehensive testing suite with three types of tests:

### Testing Frameworks Used

- **Jest**: Main testing framework
- **Supertest**: HTTP testing library
- **MongoDB Memory Server**: In-memory MongoDB for testing

### Test Types

#### 1. Unit Tests
Test individual functions in isolation with mocked dependencies.

```bash
npm run test:unit
```

**Location**: `tests/unit/`
**Coverage**: Tests controller logic with mocked database operations

#### 2. Integration Tests
Test the interaction between controllers and the database.

```bash
npm run test:integration
```

**Location**: `tests/integration/`
**Coverage**: Tests controller + database integration with real (in-memory) MongoDB

#### 3. API Tests
Test HTTP endpoints as a client would use them.

```bash
npm run test:api
```

**Location**: `tests/api/`
**Coverage**: Tests complete HTTP request/response cycle

### Running Tests

```bash
# Run all tests
npm test

# Run tests with coverage report
npm run test:coverage

# Run tests in watch mode (re-runs on file changes)
npm run test:watch

# Run specific test types
npm run test:unit
npm run test:integration
npm run test:api
```

### Test Coverage

Our testing strategy achieves **70%+ code coverage** across:

- **Unit Tests**: Controller logic and business rules
- **Integration Tests**: Database operations and data persistence
- **API Tests**: HTTP endpoints and error handling

#### Current Test Coverage

![Test Coverage Screenshot](./coverage-screenshot.png)

*Screenshot showing test coverage results from `npm run test:coverage`*

**Coverage Breakdown:**
- **Statements**: 85%+
- **Branches**: 80%+
- **Functions**: 90%+
- **Lines**: 85%+

### Test Database Strategy

#### Non-Mocking Approach (Integration & API Tests)
- Uses MongoDB Memory Server
- Creates real database operations
- Tests actual data persistence
- Ensures database schema validation

#### Mocking Approach (Unit Tests)
- Mocks MongoDB operations
- Tests controller logic in isolation
- Faster test execution
- Focuses on business logic

## 📁 Project Structure

```

├── controller.js       # Business logic for CRUD operations
├── customerModel.js     # Mongoose schema and model for Customer
├── Db.js               # MongoDB connection setup
├── routes.js           # Express router for endpoints
├── server.js           # Express server configuration
├── .env                # Environment variables
├── .gitignore          # Git ignore rules
├── tests/
│   ├── unit/                    # Unit tests with mocked dependencies
│   │   └── customerController.test.js
│   ├── integration/             # Integration tests with real database
│   │   └── customerController.integration.test.js
│   ├── api/                     # API endpoint tests
│   │   └── customer.api.test.js
│   └── setup/                   # Test configuration and utilities
│       ├── database.js          # Test database setup
│       └── jest.setup.js        # Jest configuration
├── coverage/                    # Test coverage reports (generated)
├── package.json                 # Dependencies and scripts
└── README.md                    # Project documentation
```

## 🔧 Development

### Adding New Features

1. **Create the feature** 
2. **Write tests first** (TDD approach recommended)
   - Unit tests for business logic
   - Integration tests for database operations
   - API tests for endpoints
3. **Implement the feature** to make tests pass
4. **Run tests** to ensure coverage remains above 70%

### Testing Best Practices

1. **Test Structure**: Follow AAA pattern (Arrange, Act, Assert)
2. **Test Isolation**: Each test should be independent
3. **Clear Test Names**: Describe what the test does
4. **Edge Cases**: Test both success and failure scenarios
5. **Mock External Dependencies**: Use mocks for external services

### Example Test Structure

```javascript
describe('Feature Name', () => {
  describe('specific function', () => {
    test('should do something when condition is met', async () => {
      // Arrange
      const input = { /* test data */ };
      
      // Act
      const result = await functionUnderTest(input);
      
      // Assert
      expect(result).toEqual(expectedOutput);
    });
  });
});
```

## 🚀 Deployment

### Environment Variables for Production

```env
NODE_ENV=production
PORT=3000
MONGODB_URI=url
```

### Running Tests in CI/CD

```bash
# Install dependencies
npm ci

# Run tests with coverage
npm run test:coverage

# Check if coverage meets requirements
npm run test:coverage -- --coverageThreshold='{"global":{"branches":70,"functions":70,"lines":70,"statements":70}}'
```

## 📊 API Testing with Postman

During development, you can test the API endpoints using Postman:

1. Import the provided Postman collection (if available)
2. Set up environment variables for base URL
3. Test each endpoint manually
4. Verify responses match the documented format

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Write tests for your changes
4. Implement your changes
5. Ensure all tests pass (`npm test`)
6. Commit your changes (`git commit -m 'Add amazing feature'`)
7. Push to the branch (`git push origin feature/amazing-feature`)
8. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Troubleshooting

### Common Issues

#### Tests Failing to Connect to Database
```bash
# Make sure MongoDB Memory Server is installed
npm install --save-dev mongodb-memory-server
```

#### Coverage Not Meeting Requirements
```bash
# Run coverage report to see which lines are missing
npm run test:coverage
# Open coverage/lcov-report/index.html in browser for detailed report
```

#### Port Already in Use
```bash
# Kill process using port 3000
lsof -ti:3000 | xargs kill -9
```

## 📞 Support

If you encounter any issues or have questions:

1. Check the troubleshooting section above
2. Look through existing issues in the repository
3. Create a new issue with detailed description and error logs

---

**Happy Testing!** 🎉
