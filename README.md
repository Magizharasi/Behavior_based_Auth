# Behavior Based Continuous Authentication System
## 🛡️ Advanced Behavioral Authentication System

A sophisticated real-time continuous authentication system using behavioral biometrics, powered by machine learning and designed with modern web technologies.

## 🌟 Features

### 🔐 Core Security Features
- **Continuous Authentication** - Real-time user verification throughout active sessions
- **Behavioral Biometrics** - Keystroke dynamics and mouse behavior analysis
- **Multi-Model ML Ensemble** - GRU, Autoencoder, One-Class SVM, k-NN, Passive-Aggressive, and Isolation Forest
- **Drift Detection** - Adaptive learning that handles behavioral changes over time
- **Anomaly Detection** - Real-time identification of suspicious activities
- **Session Management** - Secure session handling with automatic cleanup

### 🧠 Machine Learning Models
- **GRU (Gated Recurrent Unit)** - Sequential pattern analysis
- **Autoencoder** - Anomaly detection through reconstruction loss
- **One-Class SVM** - Outlier detection for genuine user patterns
- **Incremental k-NN** - Adaptive classification with sliding windows
- **Passive-Aggressive Classifier** - Online learning for real-time updates
- **Isolation Forest** - Anomaly detection for rare behavioral patterns

### 🎨 Modern UI/UX
- **Dark Theme Design** - Professional cybersecurity aesthetic
- **Responsive Layout** - Mobile-friendly adaptive interface
- **Real-time Monitoring** - Live behavioral analytics dashboard
- **Interactive Calibration** - Engaging setup process with visual feedback
- **Animated Components** - Smooth transitions and micro-interactions

## 🏗️ Architecture

```
continuous-auth-backend/
├── app.py                          # Main Flask application
├── config.py                       # Configuration settings
├── requirements.txt                # Python dependencies
│
├── models/                         # ML models and algorithms
│   ├── behavioral_models.py        # Ensemble classifier implementation
│   └── saved/{user_id}/            # Per-user trained models
│       ├── model_gru.h5
│       ├── model_autoencoder.h5
│       └── sklearn_models.pkl
│
├── utils/                          # Utility modules
│   ├── feature_extractor.py        # Behavioral feature extraction
│   └── drift_detector.py           # Behavioral drift detection
│
├── database/                       # Database management
│   ├── db_manager.py               # SQLite database operations
│   └── auth_system.db              # SQLite database file
│
├── static/                         # Frontend assets
│   ├── css/
│   │   └── styles.css              # Modern dark theme styles
│   └── js/
│       ├── login.js                # Authentication interface
│       ├── calib.js                # Calibration process
│       └── challenge.js            # Real-time monitoring dashboard
│
└── templates/                      # HTML templates
    ├── login.html                  # Login and registration
    ├── calib.html                  # Behavioral calibration
    └── challenge.html              # Secure dashboard
```

## 🚀 Quick Start

### Prerequisites
- Python 3.8 and not more than 3.11
- Node.js (for development tools, optional)
- Modern web browser (Chrome, Firefox, Safari, Edge)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Magizharasi/Behavior_based_Auth
   cd continuous-auth-backend
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   
   # Windows
   venv\Scripts\activate
   
   # macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

5. **Initialize the database**
   ```bash
   python -c "from app import create_app; app, socketio = create_app(); print('Database initialized!')"
   ```

6. **Run the application**
   ```bash
   python run.py
   ```

7. **Access the application**
   - Open your browser to `http://localhost:5000`
   - Create a new account or use demo credentials
   - Complete the behavioral calibration process
   - Experience real-time authentication monitoring

## 📖 Usage Guide

### 1. User Registration & Login
- Navigate to the login page
- Create a new account with username, email, and secure password
- Password strength is validated in real-time
- Login with your credentials

### 2. Behavioral Calibration
- **Typing Calibration**: Complete 5 typing passages to establish keystroke patterns
- **Mouse Calibration**: Complete 4 interactive mouse exercises
- The system analyzes timing, rhythm, pressure, and movement patterns
- Calibration takes 5-10 minutes for optimal accuracy

### 3. Real-time Monitoring
- Access the secure dashboard after calibration
- Behavioral patterns are continuously monitored
- Authentication scores update in real-time
- Security alerts notify of potential threats
- View behavioral analytics and drift analysis

### 4. Dashboard Features
- **Security Overview**: Real-time authentication status
- **Behavioral Analytics**: Pattern visualization and trends
- **Activity Log**: Comprehensive security event history
- **Settings**: Customize sensitivity and alert preferences
- **Drift Detection**: Monitor behavioral changes over time

## ⚙️ Configuration

### Environment Variables
Create a `.env` file with the following variables:

```env
# Security
SECRET_KEY=your-secret-key-here
JWT_SECRET_KEY=your-jwt-secret-here

# Database
DATABASE_PATH=database/auth_system.db

# Model Configuration
MODELS_BASE_PATH=models/saved
CONFIDENCE_THRESHOLD=0.7
ANOMALY_THRESHOLD=0.8

# Development
DEBUG=True
FLASK_ENV=development
```

### Model Parameters
Adjust these in `config.py`:

```python
# Authentication Thresholds
CONFIDENCE_THRESHOLD = 0.7          # Minimum confidence for authentication
ANOMALY_SCORE_THRESHOLD = 0.8       # Threshold for anomaly detection
CONSECUTIVE_ANOMALIES_LIMIT = 3      # Max consecutive anomalies before alert

# Behavioral Analysis
WINDOW_SIZE = 30                     # Analysis window in seconds
MIN_CALIBRATION_TIME = 300           # Minimum calibration time (5 minutes)
DRIFT_DETECTION_WINDOW = 100         # Window size for drift detection

# Model Training
GRU_SEQUENCE_LENGTH = 50             # Sequence length for GRU model
AUTOENCODER_ENCODING_DIM = 32        # Autoencoder compressed dimension
```

## 🔧 Development

### Project Structure Details

#### Backend Components
- **`app.py`**: Main Flask application with WebSocket support
- **`config.py`**: Centralized configuration management
- **`database/db_manager.py`**: Database operations and user management
- **`utils/feature_extractor.py`**: Behavioral feature extraction algorithms
- **`utils/drift_detector.py`**: Statistical drift detection methods
- **`models/behavioral_models.py`**: Machine learning model ensemble

#### Frontend Components
- **Modern CSS**: Dark theme with glassmorphism effects
- **Responsive Design**: Mobile-first approach with breakpoints
- **WebSocket Integration**: Real-time behavioral data streaming
- **Chart.js Visualizations**: Interactive behavioral analytics
- **Progressive Enhancement**: Works without JavaScript for basic functionality

### Adding New Features

#### New Behavioral Features
1. Add feature extraction logic to `utils/feature_extractor.py`
2. Update model training in `models/behavioral_models.py`
3. Modify frontend data collection in JavaScript files

#### New ML Models
1. Implement model class in `behavioral_models.py`
2. Add to ensemble in `EnsembleBehavioralClassifier`
3. Update training and prediction workflows

#### UI Enhancements
1. Modify templates in `templates/`
2. Update styles in `static/css/styles.css`
3. Add JavaScript functionality in `static/js/`

### Testing

#### Manual Testing
```bash
# Run with debug mode
DEBUG=True python run.py

# Test different user scenarios
# 1. New user registration and calibration
# 2. Existing user login and monitoring
# 3. Behavioral drift simulation
# 4. Anomaly detection testing
```

#### Security Testing
- Test with different typing patterns
- Simulate mouse behavior variations
- Verify session management security
- Test drift detection sensitivity

## 📊 Behavioral Features Analyzed

### Keystroke Dynamics
- **Timing Features**: Hold time, flight time, typing speed
- **Rhythm Analysis**: Consistency, bursts, pauses
- **N-gram Patterns**: Digraph and trigraph timing
- **Pressure Dynamics**: Key force variations (if supported)
- **Typing Style**: Speed variance, error patterns

### Mouse Behavior
- **Movement Patterns**: Velocity, acceleration, jerk
- **Click Dynamics**: Duration, pressure, timing
- **Navigation Style**: Trajectory efficiency, curvature
- **Behavioral Signatures**: Dwell time, scroll patterns
- **Precision Metrics**: Target accuracy, movement smoothness

### Advanced Analytics
- **Temporal Patterns**: Time-of-day behavior variations
- **Context Awareness**: Application-specific patterns
- **Stress Indicators**: Behavioral changes under pressure
- **Device Adaptation**: Multi-device behavioral profiles
- **Environmental Factors**: External influence detection

## 🛡️ Security Features

### Authentication Layers
1. **Primary Authentication**: Username/password login
2. **Behavioral Verification**: Continuous pattern matching
3. **Anomaly Detection**: Real-time threat identification
4. **Drift Monitoring**: Behavioral change adaptation
5. **Session Security**: Encrypted token management

### Privacy Protection
- **Local Processing**: Behavioral analysis on-device when possible
- **Data Encryption**: All stored data is encrypted
- **Minimal Storage**: Only essential features are retained
- **User Control**: Complete data deletion capabilities
- **Transparency**: Clear data usage policies

### Threat Detection
- **Session Hijacking**: Detect unauthorized access attempts
- **Credential Theft**: Identify behavior inconsistencies
- **Insider Threats**: Monitor for behavioral anomalies
- **Device Compromise**: Detect unusual input patterns
- **Social Engineering**: Identify stressed/coerced behavior

## 🔍 Troubleshooting

### Common Issues

#### Installation Problems
```bash
# TensorFlow installation issues
pip install tensorflow==2.13.0 --no-cache-dir

# Socket.IO connection problems
pip install python-socketio[client]==5.8.0
```

#### Database Issues
```bash
# Reset database
rm database/auth_system.db
python -c "from app import create_app; app, socketio = create_app()"
```

#### Model Training Failures
- Ensure sufficient calibration data (minimum 5 minutes)
- Check feature extraction output for valid data
- Verify model save directory permissions
- Monitor memory usage during training

#### WebSocket Connection Issues
- Check firewall settings for port 5000
- Verify browser WebSocket support
- Test with different browsers
- Check network proxy configurations

### Performance Optimization

#### Backend Performance
- Use Redis for session storage in production
- Implement model caching for faster predictions
- Optimize database queries with indexing
- Use background tasks for heavy processing

#### Frontend Performance
- Minimize JavaScript bundle size
- Implement virtual scrolling for large datasets
- Use Web Workers for intensive computations
- Cache static assets with service workers

#### Model Performance
- Implement model quantization for faster inference
- Use batch processing for multiple predictions
- Cache feature extraction results
- Optimize ensemble weights based on accuracy

## 🚀 Production Deployment

### Environment Setup
```bash
# Production environment
export FLASK_ENV=production
export DEBUG=False
export SECRET_KEY="your-production-secret"

# Database configuration
export DATABASE_PATH="/secure/path/to/database.db"

# SSL/TLS configuration
export SSL_CERT_PATH="/path/to/cert.pem"
export SSL_KEY_PATH="/path/to/key.pem"
```

### Security Hardening
- Enable HTTPS with valid SSL certificates
- Implement rate limiting and DDoS protection
- Use secure session configuration
- Enable CSRF protection
- Implement content security policies
- Regular security audits and updates

### Scaling Considerations
- Use load balancer for multiple instances
- Implement database connection pooling
- Use Redis for shared session storage
- Consider microservices architecture for large deployments
- Implement horizontal scaling for ML inference

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines
- Follow PEP 8 for Python code style
- Use ESLint for JavaScript code consistency
- Write comprehensive tests for new features
- Update documentation for API changes
- Ensure backward compatibility when possible

## 🔮 Future Enhancements

### Planned Features
- **Mobile Applications**: Native iOS and Android apps
- **Biometric Integration**: Fingerprint and face recognition
- **Voice Analysis**: Speech pattern authentication
- **Advanced ML**: Deep learning and transformer models
- **Cloud Integration**: AWS/Azure/GCP deployment options
- **API Extensions**: RESTful API for third-party integration

### Research Areas
- **Federated Learning**: Privacy-preserving model training
- **Adversarial Robustness**: Defense against spoofing attacks
- **Cross-Device Learning**: Behavioral sync across devices
- **Contextual Authentication**: Environment-aware security
- **Quantum-Safe Cryptography**: Post-quantum security

## 🎯 Quick Demo

1. **Start the system**: `python app.py`
2. **Open browser**: Navigate to `http://localhost:5000`
3. **Register**: Create account with strong password
4. **Calibrate**: Complete 10-minute behavioral training
5. **Monitor**: Watch real-time authentication in dashboard
6. **Test**: Try different typing/mouse patterns to see anomaly detection

*Thank you*
