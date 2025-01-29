# Stacks Cybersentinel Anti-Phishing Smart Contract

## Overview
This smart contract is designed to provide a comprehensive security framework for detecting, monitoring, and reporting phishing threats on decentralized platforms. The contract enables the registration of secure websites, submission of threat alerts by trusted sentinels, and validation of threat reports by the system administrator. The system maintains robust data structures to track sentinel performance, malicious sites, and registered web properties.

## Features
- **Secure Site Registration:** Site proprietors can register their secure websites by providing collateral and a security endorsement.
- **Threat Reporting:** Sentinels can submit phishing threat alerts with proof documentation.
- **Threat Validation:** The system allows validation of submitted threats by trusted entities.
- **Sentinel Performance Tracking:** Logs sentinel activities and credibility scores.
- **Risk Management:** Adjusts the risk level for registered websites based on threat validation.
- **Protection Level Control:** The system controller can modify protection intensity and manage the operational state of the contract.

---

## Constants
- **Error Codes:**
  - `ACCESS_FORBIDDEN`: Unauthorized access error.
  - `DUPLICATE_ENTRY_ERROR`: Attempt to register an already existing site.
  - `ENTRY_MISSING_ERROR`: Data not found.
  - `OPERATION_BLOCKED_ERROR`: System is paused.
  - `COLLATERAL_MISSING_ERROR`: Insufficient collateral.
  - `TIME_RESTRICTION_ERROR`: Operation attempted within restricted time.
  - `LIMIT_BREACH_ERROR`: Limit breach detected.
  - `INVALID_WEB_IDENTIFIER`, `INVALID_SECURITY_ENDORSEMENT`, `INVALID_PROOF_DOCUMENTATION`, etc.: Input validation errors.

- **System Constants:**
  - `INACTIVITY_WINDOW`: 24-hour inactivity window.
  - `BASE_COLLATERAL_REQUIREMENT`: Base collateral requirement set at 1,000,000 microSTX.
  - `TRUSTWORTHINESS_BASELINE`: Minimum credibility score for trusted sentinels.
  - `EVIDENCE_STRING_LIMIT`: Maximum length for proof documentation.

---

## Data Structures
- **Registered Sites:** Tracks site information, authentication levels, threat metrics, and security endorsements.
- **Sentinel Performance Log:** Logs sentinel submissions, credibility scores, and activity.
- **Site Inspection Records:** Keeps track of inspection frequencies and compliance status.
- **Malicious Site Registry:** Stores information about detected phishing sites.
- **Sentinel Registry:** Manages sentinel status, collateral, and performance metrics.

---

## Core Functions
### **Public Functions**
- **`register_secure_site(web_identifier, security_endorsement)`**
  - Registers a secure site with collateral and endorsement.
  - **Parameters:**
    - `web_identifier`: ASCII string (max 255 characters).
    - `security_endorsement`: ASCII string (max 50 characters).
  - **Errors:** `INVALID_WEB_IDENTIFIER`, `INVALID_SECURITY_ENDORSEMENT`, `ACCESS_FORBIDDEN`, `DUPLICATE_ENTRY_ERROR`, etc.

- **`submit_threat_alert(web_identifier, proof_documentation, threat_magnitude)`**
  - Submits a threat alert for a registered website.
  - **Parameters:**
    - `web_identifier`: ASCII string.
    - `proof_documentation`: ASCII string (max 500 characters).
    - `threat_magnitude`: Integer between 1 and 100.
  - **Errors:** `INVALID_WEB_IDENTIFIER`, `INVALID_PROOF_DOCUMENTATION`, etc.

- **`validate_threat_report(web_identifier, is_valid)`**
  - Validates a threat report submitted by a sentinel.
  - **Parameters:**
    - `web_identifier`: ASCII string.
    - `is_valid`: Boolean flag.
  - Adjusts site threat metrics based on validation result.

- **`modify_protection_level(new_level)`**
  - Changes the system's protection intensity level.

- **`toggle_system_state(pause_state)`**
  - Pauses or resumes system operations.

- **`reassign_system_control(new_controller)`**
  - Transfers control to a new system administrator.

- **`initialize_system(admin)`**
  - Initializes the system with an administrator.

- **`enlist_sentinel(collateral_amount)`**
  - Registers a new sentinel with collateral.

### **Read-Only Functions**
- **`check_threat_status(web_identifier)`**: Checks if a site is marked as malicious.
- **`fetch_sentinel_rating(sentinel_id)`**: Fetches the credibility score of a sentinel.
- **`fetch_site_status(web_identifier)`**: Retrieves the status of a registered site.

---

## Input Validation Functions
- **`validate-web-identifier`**: Ensures web identifiers meet format requirements.
- **`validate-security-endorsement`**: Checks the validity of security endorsements.
- **`validate-proof-documentation`**: Ensures proof documentation is within limits.
- **`validate-threat-magnitude`**: Confirms threat magnitude is within range.
- **`validate-protection-level`**: Validates protection levels.

---

## Security Considerations
- **Collateral Requirements:** Ensures participants have a financial stake.
- **System Controller Checks:** Only the system controller can modify system-critical states.
- **Input Validation:** Extensive checks for web identifiers, endorsements, and proof documentation.
- **Pause Mechanism:** Allows the system to be paused during emergencies.

---

## Usage Guidelines
1. **Initialization:**
   - Call `initialize_system(admin)` to set up the system.
2. **Register a Site:**
   - Call `register_secure_site(web_identifier, security_endorsement)` with appropriate parameters.
3. **Submit a Threat Alert:**
   - Use `submit_threat_alert(web_identifier, proof_documentation, threat_magnitude)` to report phishing threats.
4. **Validate a Threat Report:**
   - Invoke `validate_threat_report(web_identifier, is_valid)` to confirm or dismiss alerts.
5. **Modify Protection Level:**
   - Adjust the protection level using `modify_protection_level(new_level)`.
6. **Toggle System State:**
   - Use `toggle_system_state(pause_state)` to pause or resume operations.

---

## Conclusion
This Anti-Phishing Smart Contract provides a robust framework for monitoring, reporting, and mitigating phishing threats on decentralized platforms. With secure site registration, sentinel participation, and validation processes, it ensures a proactive approach to online security.

