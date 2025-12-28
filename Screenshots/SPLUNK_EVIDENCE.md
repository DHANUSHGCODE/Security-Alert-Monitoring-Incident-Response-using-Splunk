# Splunk Evidence & Screenshots

## Overview
This directory contains screenshots of the Splunk Enterprise security monitoring and log analysis activities performed during the FUTURE_CS_02 project.

---

## Screenshot Categories

### 1. **Log Ingestion Phase**
- **File:** `01-log-upload.png`
- **Description:** Apache.log file successfully uploaded to Splunk platform
- **Details:** Shows the "Select Source" upload interface with Apache.log selected and confirmed upload status

### 2. **Source Type Configuration**
- **File:** `02-set-sourcetype.png`
- **Description:** Source type configuration for Apache logs (DMMOP sourcetype)
- **Details:** Displays event preview with correct timestamp extraction and field identification

### 3. **Input Settings Review**
- **File:** `03-input-review.png`
- **Description:** Final review of input configuration before indexing
- **Details:** Shows:
  - Input Type: Uploaded File
  - File Name: Apache.log
  - Source Type: khh
  - Host: DSP
  - Index: Default

### 4. **Search & Analysis Results**
- **File:** `04-splunk-search-results.png`
- **Description:** Main Splunk search displaying Apache log events (8,661 events indexed)
- **Details:** Shows:
  - Query: `source="Apache.log" sourcetype="DMMOP"`
  - Time range: All time (before 28/12/2025 17:21:54.000)
  - Event breakdown with timestamps and log levels
  - Multiple 403 Forbidden errors indicating unauthorized access attempts

### 5. **Threat Detection - Directory Index Forbidden**
- **File:** `05-threat-detection.png`
- **Description:** Highlighted suspicious activities in Apache logs
- **Details:** Shows repeated "Directory index forbidden" errors (HTTP 403)
  - Multiple client IP addresses attempting access: 211.92.56.72, 222.166.160.57, 194.63.235.157, 222.166.160.74, 194.207.237.21
  - Attack pattern: Systematic probing of `/var/www/html/` directory
  - Error messages formatted with [error] tags

### 6. **Splunk App Dashboard**
- **File:** `06-splunk-apps.png`
- **Description:** Splunk Enterprise home page and available apps
- **Details:** Shows:
  - Search & Reporting app (primary analysis tool)
  - Audit Trail app
  - Discover Splunk Observability Cloud
  - Common tasks for security monitoring
  - Alert management capabilities

### 7. **Evidence of Multiple Attacks**
- **File:** `07-multiple-attacks.png`
- **Description:** Detailed view of Apache server logs showing various attack patterns
- **Details:** Shows multiple log entries with:
  - [Notice] LDAP SDK initialization messages
  - [Error] mod_jk initialization failures
  - [Error] Script not found errors (CGI-bin probing)
  - Repeated pattern suggesting automated reconnaissance

---

## Key Findings Summary

Based on screenshot analysis:

✅ **Total Events Indexed:** 8,661 events  
✅ **Primary Threat:** HTTP 403 (Directory Index Forbidden) errors  
✅ **Attack Sources:** Multiple IP addresses from different subnets  
✅ **Attack Type:** Reconnaissance/Probing Activity  
✅ **Severity:** Medium (No confirmed compromise)  
✅ **Detection Method:** Splunk SIEM log analysis  

---

## How to Use These Screenshots

1. **Presentation:** Use these screenshots in security reports and presentations
2. **Evidence:** Document incident response activities
3. **Training:** Train SOC team members on Splunk threat detection
4. **Portfolio:** Demonstrate practical SIEM monitoring experience

---

## File Naming Convention

```
Sequence-Description.png
Example: 01-log-upload.png, 02-set-sourcetype.png
```

---

**Last Updated:** December 28, 2025  
**Project:** FUTURE_CS_02 - Security Alert Monitoring & Incident Response
