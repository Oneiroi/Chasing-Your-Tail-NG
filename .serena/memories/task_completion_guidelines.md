# Task Completion Guidelines

## When Task is Complete

### Security Verification (ALWAYS)
Before considering any task complete:
```bash
# Verify security hardening still works
python3 chasing_your_tail.py
# Should show: "🔒 SECURE MODE: All SQL injection vulnerabilities have been eliminated!"
```

### Code Quality Checks
- **No formal linting setup** - Manual code review required
- **No automated testing** - Manual testing with demo data recommended
- **Security First**: Ensure all database queries use parameterized statements
- **Credential Safety**: Never expose API keys or master passwords

### Testing Approach
Since no formal testing framework:
```bash
# Test core functionality
python3 chasing_your_tail.py  # Should start monitoring

# Test GUI
python3 cyt_gui.py  # Should open GUI interface

# Test surveillance analysis with demo data
python3 surveillance_analyzer.py --demo

# Test probe analysis (local only, safe)
python3 probe_analyzer.py --days 1
```

### File Organization Check
After making changes, verify files are in correct locations:
- **Core scripts**: Main directory
- **Security modules**: Main directory (secure_*.py)
- **Output files**: Appropriate subdirectories (./surveillance_reports/, ./kml_files/, etc.)
- **Configuration**: config.json in main directory
- **Broken/old code**: Should be in archive directories

### Security Validation
- All SQL queries must use parameterized statements
- No exec() calls in production code
- Credentials must be encrypted
- Input validation must be comprehensive
- Security events must be logged

### Documentation Updates
- Update relevant sections in CLAUDE.md if architecture changes
- Maintain clear comments for security-critical code
- Document any new configuration options in config.json format

## Darwin System Considerations
- Use `ps aux | grep kismet` instead of Linux-specific commands
- File paths use forward slashes
- Shell scripts use bash (#!/bin/bash)
- Permissions may require sudo for Kismet operations