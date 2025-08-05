# DocInsight

A comprehensive document analysis platform that extracts functional requirements from documents and generates automated test checklists using AI-powered analysis.

![Docker](https://img.shields.io/badge/Docker-Compose-blue?style=flat-square&logo=docker)
![RAGFlow](https://img.shields.io/badge/RAGFlow-API-green?style=flat-square)
![Angular](https://img.shields.io/badge/Angular-19.2-red?style=flat-square&logo=angular)
![FastAPI](https://img.shields.io/badge/FastAPI-Python-blue?style=flat-square&logo=fastapi)

## 🚀 What is DocInsight?

DocInsight is an AI-powered document analysis platform that:

- **📄 Processes Documents**: Upload DOCX/DOC files containing requirements specifications
- **🤖 AI Analysis**: Uses RAGFlow API with local LLM to understand document content
- **📋 Extracts Requirements**: Automatically identifies functional requirements from documents
- **✅ Generates Test Checklists**: Creates comprehensive test cases for each requirement
- **🌐 Web Interface**: Modern Angular frontend for easy document upload and results viewing

### Key Features
- **Intelligent Document Parsing** using RAGFlow and local LLM
- **Automatic Requirement Extraction** from technical specifications
- **Test Checklist Generation** in Thai/English languages
- **Real-time Processing** with cancellation support
- **Modern Web Interface** with responsive design

## 🏗️ Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Angular       │    │   FastAPI       │    │   RAGFlow       │
│   Frontend      │◄──►│   Backend       │◄──►│   + Local LLM   │
│   (Port 4200)   │    │   (Port 4444)   │    │   (Port 9380)   │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

## 📋 Prerequisites

Before running DocInsight, ensure you have:

- **Docker & Docker Compose** (recommended)
- **RAGFlow Server** running on `http://localhost:9380`
- **RAGFlow API Key** (for authentication)

### 🔧 RAGFlow Setup

1. **Install and start RAGFlow** following their [official documentation](https://ragflow.io/docs)
2. **Generate an API key** from your RAGFlow dashboard
3. **Ensure RAGFlow is accessible** at `http://localhost:9380`

## 🚀 Quick Start

### Option 1: Docker Compose (Recommended)

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd DocInsight
   ```

2. **Create environment file**
   ```bash
   cp example.env .env
   ```

3. **Configure your RAGFlow API key**
   ```bash
   # Edit .env file
   RAGFLOW_API_KEY="your-ragflow-api-key-here"
   RAGFLOW_BASE_URL=http://host.docker.internal:9380
   ```

4. **Start the entire stack**
   ```bash
   docker-compose up --build
   ```

5. **Access the application**
   - **Frontend**: http://localhost:4200
   - **Backend API**: http://localhost:4444

### Option 2: Run Services Separately

#### Backend Setup
```bash
cd backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
RAGFLOW_API_KEY="your-key" python main.py
```

#### Frontend Setup
```bash
cd frontend
npm install
npm start
```

## 📖 How to Use

1. **Start the application** using Docker Compose or manual setup
2. **Open your browser** to http://localhost:4200
3. **Upload a document** (.docx or .doc file with requirements)
4. **Wait for analysis** - the system will:
   - Upload and parse your document
   - Extract functional requirements
   - Generate test checklists for each requirement
5. **View results** in the interactive interface
6. **Use checkboxes** to track test completion

## 🔗 API Endpoints

The backend provides these main endpoints:

- `POST /main` - Upload document for analysis
- `GET /status/{task_id}` - Check analysis progress
- `POST /stop/{task_id}` - Cancel ongoing analysis

## 📁 Project Structure

```
DocInsight/
├── frontend/           # Angular web application
│   ├── src/
│   ├── package.json
│   └── README.md      # Frontend-specific documentation
├── backend/            # FastAPI server
│   ├── main.py
│   ├── ragflow.py
│   ├── requirements.txt
│   └── README.md      # Backend-specific documentation
├── docker-compose.yml  # Multi-service orchestration
└── README.md          # This file
```

## 🛠️ Development

### Individual Service Development

Each service has its own detailed README:
- **Frontend**: See [`frontend/README.md`](frontend/README.md) for Angular development
- **Backend**: See [`backend/README.md`](backend/README.md) for FastAPI development

### Environment Variables

Key configuration options:

```env
# RAGFlow Configuration
RAGFLOW_API_KEY="your-api-key"
RAGFLOW_BASE_URL=http://host.docker.internal:9380

# Development
NODE_ENV=development
```

## 🔍 Troubleshooting

### Common Issues

**❌ "You need to start the RAGFlow server first"**
- Ensure RAGFlow is running on http://localhost:9380
- Check your RAGFlow API key is valid
- Verify network connectivity

**❌ "Port already in use"**
```bash
# Use different ports
docker-compose -f docker-compose.yml up --build
# or modify ports in docker-compose.yml
```

**❌ "Invalid RAGFlow API key"**
- Check your API key in the `.env` file
- Regenerate API key from RAGFlow dashboard
- Ensure API key has proper permissions

## 📝 Supported File Types

- Microsoft Word documents (`.docx`, `.doc`)
- Requirements specifications
- Technical documentation
- Single file upload (up to 100MB)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (s`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **RAGFlow** - For the powerful document processing API
- **Angular Team** - For the robust frontend framework
- **FastAPI** - For the high-performance backend framework

---

For detailed service-specific documentation, please refer to:
- [Frontend Documentation](frontend/README.md)