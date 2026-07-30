# PM Internship Recommendation Engine

An AI-based internship recommendation system for the PM Internship Scheme that helps candidates find the most relevant internship opportunities based on their profile, skills, education, and location preferences.

## 🌟 Features

- **AI-Powered Recommendations**: Rule-based ML-light recommendation engine
- **Resume Parsing**: Automatically extract education, skills, and location from uploaded resumes
- **Multi-language Support**: Regional language support using Indic NLP library
- **Mobile-Responsive**: Touch-friendly interface optimized for mobile devices
- **Simple UI/UX**: Designed for users with low digital literacy
- **Personalized Results**: Top 3-5 tailored internship suggestions

## 🏗️ Architecture

### Backend (Flask)
- **Framework**: Flask with Python
- **Resume Parsing**: PyPDF2, python-docx, spaCy
- **Recommendation Engine**: Rule-based matching algorithm
- **Translation**: Indic NLP library for regional language support
- **API**: RESTful endpoints for all operations

### Frontend (React)
- **Framework**: React 18 with functional components
- **Routing**: React Router for navigation
- **Styling**: Mobile-first responsive CSS
- **State Management**: React hooks and context
- **File Upload**: Drag-and-drop resume upload

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- Node.js 16+
- npm or yarn

### 🎨 Automated Setup (Recommended)

**One-command setup and run:**
```bash
python setup.py
```

This will:
1. ✅ Set up both backend and frontend automatically
2. ✅ Create virtual environment and install all dependencies
3. ✅ Download required spaCy models
4. ✅ Ask if you want to start the servers immediately
5. ✅ Run both Flask backend (port 5000) and React frontend (port 3000)

### 🚀 Alternative Setup Commands

```bash
# Setup and automatically start servers (no prompt)
python setup.py --start

# Setup only, don't start servers
python setup.py --no-start

# Skip setup, just start servers (if already set up)
python setup.py --run-only

# Or use the quick run script
python run.py
```

### 🛠️ Manual Setup (Advanced Users)

#### Backend Setup

1. **Navigate to backend directory:**
```bash
cd pm-internship-recommendation/backend
```

2. **Create virtual environment:**
```bash
python -m venv venv
venv\Scripts\activate  # On Windows
# source venv/bin/activate  # On macOS/Linux
```

3. **Install dependencies:**
```bash
pip install -r requirements.txt
```

4. **Download spaCy model:**
```bash
python -m spacy download en_core_web_sm
```

5. **Run the Flask server:**
```bash
python app.py
```

The backend will be available at `http://localhost:5000`

#### Frontend Setup

1. **Navigate to frontend directory:**
```bash
cd pm-internship-recommendation/frontend
```

2. **Install dependencies:**
```bash
npm install
```

3. **Start the React development server:**
```bash
npm start
```

The frontend will be available at `http://localhost:3000`

## 📊 API Endpoints

### Core Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/health` | GET | Health check |
| `/api/recommend` | POST | Get personalized recommendations |
| `/api/parse-resume` | POST | Parse uploaded resume |
| `/api/internships` | GET | Get all available internships |
| `/api/translate` | POST | Translate text to regional languages |
| `/api/profile` | POST | Create/update user profile |

### Example API Usage

**Get Recommendations:**
```bash
curl -X POST http://localhost:5000/api/recommend \
  -H "Content-Type: application/json" \
  -d '{
    "education": "B.Tech Computer Science",
    "skills": ["Python", "JavaScript", "React"],
    "location": "Bangalore",
    "interests": ["Technology", "Software Development"]
  }'
```

**Parse Resume:**
```bash
curl -X POST http://localhost:5000/api/parse-resume \
  -F "file=@resume.pdf"
```

## 🎯 User Journey

### 1. Landing Page
Choose between manual profile creation or resume upload.

<p align="center">
  <img width="550" alt="Landing Page" src="https://github.com/user-attachments/assets/0f1b755d-6384-4502-bd7f-7d0043fb5a39" />
</p>

### 2. Profile Creation
Fill form with education, skills, location, and interests.

<p align="center">
  <img width="550" alt="Profile Creation" src="https://github.com/user-attachments/assets/43f280cd-73b7-4c7b-bc1e-b37ebc6061ba" />
</p>

### 3. Resume Upload & Data Extraction
Drag-and-drop resume for automatic data extraction and skill mapping.

|<p align="center"><img width="450" alt="Resume Drag and Drop" src="https://github.com/user-attachments/assets/6d7e3c67-9bcf-41e5-8a58-9196f18ca7cc" /></p> | <p align="center"><img width="450" alt="Data Extraction Result" src="https://github.com/user-attachments/assets/3b63a5d7-b850-4662-8139-27dbb318b97f" /></p> |
| :---: | :---: |

### 4. Recommendations
View top personalized internship matches calculated by the AI engine.

|<p align="center"><img width="450" alt="Recommendations View 1" src="https://github.com/user-attachments/assets/40221255-5177-4329-b56a-2fbca82b03cd" /></p> | <p align="center"><img width="450" alt="Recommendations View 2" src="https://github.com/user-attachments/assets/04eaab9f-deec-4c0c-b943-dd5fa5d9c294" /></p> |
| :---: | :---: |

### 5. Application & Details
View complete vacancy details and apply directly to recommended internships.

|<p align="center"><img width="380" alt="Application View 1" src="https://github.com/user-attachments/assets/c47ee842-4799-48c6-803b-3e6aea1df72d" /></p> | <p align="center"><img width="380" alt="Application View 2" src="https://github.com/user-attachments/assets/984c6a13-f68b-4318-8a38-cdb3f50bb6de" /></p> |
| :---: | :---: |

## 🌐 Multi-language Support

Supported Languages:
- English
- Hindi (हिंदी)
- Telugu (తెలుగు)
- Tamil (தமிழ்)
- Bengali (বাংলা)

The system supports basic UI translation and can be extended with more comprehensive Indic NLP integration.

## 📱 Mobile Optimization

- **Touch-friendly buttons** (minimum 48px height)
- **Responsive grid layouts**
- **Optimized forms** for mobile input
- **Progressive enhancement** for low-bandwidth scenarios
- **Visual cues** and minimal text for low digital literacy users

## 🧠 Recommendation Algorithm

The system uses a weighted scoring approach:

- **Education Match (20%)**: Alignment between user education and internship requirements
- **Skills Match (30%)**: Overlap between user skills and required skills
- **Location Preference (30%)**: Geographic proximity and remote work options
- **Interest Alignment (20%)**: Match between user interests and internship sector

## 📁 Project Structure

```
pm-internship-recommendation/
├── backend/
│   ├── app.py                 # Main Flask application
│   ├── services/
│   │   ├── recommendation_engine.py
│   │   ├── resume_parser.py
│   │   └── translation_service.py
│   ├── data/
│   │   └── sample_data.py     # Sample internship data
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── context/          # Language context
│   │   ├── services/         # API service
│   │   └── App.js
│   ├── package.json
│   └── public/
└── README.md
```

## 🔧 Configuration

### Backend Configuration (.env)

```env
FLASK_ENV=development
FLASK_DEBUG=True
SECRET_KEY=your-secret-key-here
CORS_ORIGINS=http://localhost:3000
```

### Frontend Configuration

The frontend automatically proxies API requests to the backend during development.

## 🧪 Testing

### Backend Testing
```bash
cd backend
python -m pytest tests/  # If tests are implemented
```

### Frontend Testing
```bash
cd frontend
npm test
```

## 🚀 Deployment

### Backend Deployment

1. **Production Setup:**
```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

2. **Docker (Optional):**
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:5000", "app:app"]
```

### Frontend Deployment

1. **Build for Production:**
```bash
npm run build
```

2. **Serve Static Files:**
Use any static file server (nginx, Apache, or CDN)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For support and questions:
- Create an issue in the GitHub repository
- Contact the development team
- Refer to the API documentation

## 🔮 Future Enhancements

- **Database Integration**: PostgreSQL/MongoDB for data persistence
- **Advanced ML Models**: Deep learning for better recommendations
- **Real-time Chat**: Support system integration
- **Analytics Dashboard**: Admin panel for tracking usage
- **Enhanced Translation**: Full content translation using advanced NLP
- **Offline Mode**: PWA capabilities for limited connectivity scenarios
