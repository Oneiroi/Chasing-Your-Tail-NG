# Code Architecture & Patterns

## Architecture Overview
The system follows a modular architecture with clear separation of concerns:

### Core Monitoring Pipeline
1. **Data Collection**: Kismet captures wireless frames → SQLite database
2. **Real-time Processing**: chasing_your_tail.py queries database every 60 seconds
3. **Time Window Tracking**: Maintains sliding windows (5, 10, 15, 20 minutes)
4. **Persistence Detection**: surveillance_detector.py analyzes device patterns
5. **GPS Correlation**: Automatic GPS extraction and location clustering
6. **Visualization**: Professional KML generation for Google Earth

### Security Architecture
- **Secure Database Layer**: secure_database.py with parameterized queries
- **Encrypted Credentials**: secure_credentials.py with cryptography lib
- **Input Validation**: input_validation.py with comprehensive sanitization
- **Safe Data Loading**: secure_ignore_loader.py (replaces dangerous exec())
- **Audit Logging**: Security events tracked in cyt_security.log

## Code Patterns & Conventions

### Class Structure
- **Main Classes**: SurveillanceAnalyzer, SurveillanceDetector, GPSTracker
- **Security Classes**: SecureKismetDB, SecureCredentialManager, SecureIgnoreLoader
- **Data Classes**: SuspiciousDevice, LocationSession (dataclasses/named tuples)

### Error Handling
- Extensive logging with different log levels
- Security-focused error boundaries
- Graceful degradation when optional features fail

### File Organization
- **Core Scripts**: Main directory (chasing_your_tail.py, etc.)
- **Security Modules**: secure_*.py files in main directory  
- **Output Directories**: Organized by type (./surveillance_reports/, ./kml_files/, etc.)
- **Configuration**: Centralized in config.json
- **Archive**: old_scripts/, docs_archive/, legacy/ for historical code

### Time Window Algorithm
```
Recent:  Past 5 minutes
Medium:  5-10 minutes ago
Old:     10-15 minutes ago  
Oldest:  15-20 minutes ago
```
Lists rotate every 5 cycles (5 minutes) with fresh database queries.

### GPS Integration Pattern
- Automatic extraction from Kismet Bluetooth GPS data
- Location clustering with 100m threshold
- Session management with timeout handling
- Device-to-location correlation with precise timing
- Professional KML generation with threat-level styling