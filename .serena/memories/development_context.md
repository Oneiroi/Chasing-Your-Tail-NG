# Development Context & Guidelines

## Project Status
- **Security Hardened**: All critical vulnerabilities fixed (SQL injection, credential exposure, RCE)
- **Production Ready**: Real-world deployment with auto-start capability
- **Clean Architecture**: Code reorganization completed July 23, 2025
- **Enhanced Visualization**: Professional KML generation with Google Earth integration

## Development Priorities
1. **Security First**: All changes must maintain security posture
2. **Defensive Purpose Only**: Tool designed for legitimate security research and personal safety
3. **User Experience**: Maintain "Fisher Price" GUI usability while looking professional
4. **Performance**: Real-time monitoring with 60-second intervals

## Code Style & Conventions
- **Python 3.6+ compatibility** required
- **Logging**: Extensive use of logging module with different levels
- **Error Handling**: Graceful degradation and security-focused error boundaries
- **Documentation**: Clear docstrings for security-critical functions
- **Comments**: Minimal but meaningful comments

## File Naming Conventions
- **Core modules**: descriptive names (surveillance_analyzer.py)
- **Security modules**: secure_ prefix (secure_database.py) 
- **Output files**: Timestamped with YYYYMMDD_HHMMSS format
- **Configuration**: JSON format for data, Python for complex logic

## Security Guidelines
- **No exec() calls** - Use secure_ignore_loader.py instead
- **Parameterized queries only** - Use secure_database.py
- **Encrypted credentials** - Use secure_credentials.py
- **Input validation** - Use input_validation.py
- **Audit logging** - Log all security events

## Testing Philosophy
- **Demo mode** available for safe testing without real data
- **Manual testing** preferred due to security sensitivity
- **Real-world validation** with actual Kismet data
- **API-safe defaults** (no WiGLE calls unless explicit --wigle flag)

## Integration Points
- **Kismet**: SQLite database interface with real-time queries
- **WiGLE API**: Optional SSID geolocation (encrypted credentials required)
- **Google Earth**: KML export for professional visualization
- **System Integration**: Auto-start via crontab on boot