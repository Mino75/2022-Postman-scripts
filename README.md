# 📦 Postman Scripts

## 📋 Table of Contents
- [📖 About](#-about)
- [🚀 Getting Started](#-getting-started)
- [🔨 How to Build / How to Run](#-how-to-build--how-to-run)
- [🏗️ Project Structure](#️-project-structure)
- [🎯 Features](#-features)
- [📚 Dependencies](#-dependencies)
- [🌐 GitHub Pages](#-github-pages)
- [💡 Usage](#-usage)
- [📄 License](#-license)

## 📖 About
Postman Scripts is an open-source repository containing useful JavaScript scripts and test collections for API testing with Postman. Created by Mino Rand, this project provides ready-to-use templates and automated testing collections specifically designed for the Swagger Pet Store API, making API testing more efficient and standardized.

## 🚀 Getting Started

### Prerequisites
- Postman application (Desktop or Web)
- Basic knowledge of JavaScript
- Understanding of REST API concepts
- Access to Swagger Pet Store API

### 📦 Installation
```bash
git clone https://github.com/Mino75/postman-scripts.git
cd postman-scripts
```

## 🔨 How to Build / How to Run

### Import Collections to Postman
1. **Manual Collection**: Import `Swagger_Test_collection_manual.postman_collection.json`
2. **Automated Collection**: Import `Swagger_Test_collection_Automated.postman_collection.json`
3. **Set up Environment**: Configure variables for pet testing

### Running Tests
```bash
# For automated testing with Newman (Postman CLI)
npm install -g newman
newman run Swagger_Test_collection_Automated.postman_collection.json
```

### GitHub Pages Deployment
The repository automatically deploys to GitHub Pages via GitHub Actions:
- **Live Demo**: Available at repository's GitHub Pages URL
- **Auto-deploy**: Triggered on pushes to main branch

## 🏗️ Project Structure
```
postman-scripts/
├── README.md                                           # Project documentation
├── LICENSE                                            # MIT License
├── Template.js                                        # JavaScript templates for Postman
├── Swagger_Test_collection_manual.postman_collection.json     # Manual testing collection
├── Swagger_Test_collection_Automated.postman_collection.json  # Automated testing collection
├── index.html                                         # GitHub Pages interface
└── .github/workflows/
    └── static.yml                                     # GitHub Pages deployment workflow
```

## 🎯 Features

### JavaScript Templates
- **Variable Management**: Store and retrieve test data
- **HTTP Status Validation**: Verify response codes (200, 404, 500)
- **Response Time Checks**: Performance testing capabilities
- **Dynamic Data Generation**: Timestamps and random values
- **JSON Response Validation**: Field-specific assertions
- **Unique Value Creation**: Prevent duplicate test data

### Test Collections
- **Manual Collection**: Step-by-step API testing workflow
- **Automated Collection**: Pre-configured with test scripts and assertions
- **CRUD Operations**: Complete Create, Read, Update, Delete cycle
- **Environment Variables**: Dynamic pet ID and data management

### API Test Flow
1. **Authenticate**: OAuth authorization endpoint
2. **Create Pet**: POST request with validation
3. **Retrieve Pet**: GET request by ID
4. **Update Pet**: PUT request with modified data
5. **Verify Update**: Confirm changes were applied
6. **Delete Pet**: Remove test data
7. **Verify Deletion**: Ensure pet no longer exists

## 📚 Dependencies

### Postman Features Used
- **Environment Variables**: Dynamic data storage
- **Pre-request Scripts**: Setup and data preparation
- **Test Scripts**: Automated validation and assertions
- **Collection Variables**: Shared data across requests

### JavaScript Libraries
- **Moment.js**: Date and time manipulation
- **Built-in Postman Libraries**: pm.* APIs for testing

### Swagger Pet Store API
- **Base URL**: `https://petstore3.swagger.io/api/v3/`
- **Authentication**: OAuth 2.0 support
- **Operations**: Full CRUD operations on pets
- **Response Formats**: JSON responses with pet data

## 🌐 GitHub Pages
The repository includes a modern, responsive web interface showcasing all project files:

### Features
- **Dynamic File Loading**: Fetches files from GitHub API
- **Interactive File Browser**: Click to view files on GitHub
- **Responsive Design**: Works on desktop and mobile
- **File Type Icons**: Visual indicators for different file types
- **Repository Statistics**: File count and total size information

### Analytics Integration
- **Umami Analytics**: Privacy-focused usage tracking
- **Custom Domain Support**: Configurable for custom domains

## 💡 Usage

### Template Scripts (`Template.js`)
```javascript
// Status code validation
pm.test("Status code is 200", function () { 
    pm.response.to.have.status(200);
});

// Save response data
var jsonData = pm.response.json();
pm.environment.set("petId", jsonData.id);

// Field validation
pm.test("the id is 30", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(30);
});

// Response time check
pm.test("Response time is less than 800ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(800);
});
```

### Environment Variables
- **petId**: `30` - Test pet identifier
- **petName**: `"MinLion"` - Initial pet name
- **petNewName**: `"MinLion2"` - Updated pet name
- **petStatus**: `"available"` - Pet availability status

### Collection Workflow
1. **Import Collection**: Choose manual or automated version
2. **Configure Environment**: Set up required variables
3. **Run Tests**: Execute entire collection or individual requests
4. **Review Results**: Check test results and response data
5. **Iterate**: Modify scripts as needed for your API

### Best Practices
- **Environment Separation**: Use different environments for dev/staging/prod
- **Dynamic Data**: Use timestamps and random values to avoid conflicts
- **Error Handling**: Include validation for error scenarios
- **Documentation**: Comment your scripts for team collaboration

## 📄 License
MIT License

Copyright (c) 2022 Mino

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
