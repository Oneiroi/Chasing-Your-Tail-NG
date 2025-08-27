# Essential Commands for Chasing Your Tail Development

## Security Setup (REQUIRED FIRST TIME)
```bash
# Install dependencies
pip3 install -r requirements.txt

# Migrate credentials from insecure config.json (CRITICAL)
python3 migrate_credentials.py

# Verify security hardening
python3 chasing_your_tail.py
# Should show: "🔒 SECURE MODE: All SQL injection vulnerabilities have been eliminated!"
```

## Primary Application Commands
```bash
# Start enhanced GUI interface (recommended)
python3 cyt_gui.py

# Run core monitoring (command line)
python3 chasing_your_tail.py

# Start Kismet (ONLY working script)
./start_kismet_clean.sh

# Check Kismet status
ps aux | grep kismet

# Kill Kismet if needed
for pid in $(pgrep kismet); do sudo kill -9 $pid; done
```

## Analysis Commands
```bash
# Analyze collected data (past 14 days, local only - default, API-safe)
python3 probe_analyzer.py

# Analyze past 7 days only
python3 probe_analyzer.py --days 7

# Analyze ALL logs (may be slow)
python3 probe_analyzer.py --all-logs

# Analyze WITH WiGLE API calls (consumes API credits!)
python3 probe_analyzer.py --wigle
```

## Surveillance Detection & GPS Analysis
```bash
# Automatic GPS extraction with spectacular KML visualization
python3 surveillance_analyzer.py

# Run analysis with demo GPS data (testing)
python3 surveillance_analyzer.py --demo

# Analyze specific Kismet database
python3 surveillance_analyzer.py --kismet-db /path/to/kismet.db

# Focus on stalking detection with high persistence threshold
python3 surveillance_analyzer.py --stalking-only --min-persistence 0.8

# Export results to JSON
python3 surveillance_analyzer.py --output-json analysis_results.json
```

## System Status & Monitoring
```bash
# Check auto-start configuration
sudo crontab -l  # Kismet auto-start
crontab -l      # GUI auto-start

# Monitor logs
tail -f logs/cyt_log_*
tail -f analysis_logs/surveillance_analysis.log
tail -f cyt_security.log
```

## Development Notes
- No formal testing framework setup (pytest commented in requirements.txt)
- No linting/formatting tools configured
- Security is paramount - all database queries use parameterized statements
- Credentials are encrypted and require master password or test mode