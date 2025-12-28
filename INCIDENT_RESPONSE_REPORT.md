# Incident Response Report - FUTURE_CS_02
## Security Alert Monitoring & Incident Response using Splunk

---

## 📋 Report Header

- **Intern Name:** Dhanush G
- **Internship Program:** Future Interns Cyber Security
- **Task:** Task 02 - Security Alert Monitoring & Incident Response
- **Report Type:** Incident Response Report
- **Date:** December 28, 2025
- **Environment:** Windows (Splunk Enterprise)

---

## 📌 Executive Summary

This report documents the analysis of security events identified through Apache web server logs using **Splunk Enterprise**. The objective was to monitor logs, detect suspicious activity, classify incidents, and propose remediation steps. The analysis revealed repeated directory access forbidden errors and abnormal client activity, indicating potential **unauthorized access attempts**.

---

## 1️⃣ Introduction

### Objective
Monitor security events using a SIEM tool (Splunk Enterprise), analyze Apache web server logs, identify suspicious activities, classify incidents, and document an incident response process.

### Scope
Apache web server logs from the DSP host containing 8,661 events indexed with DMMOP sourcetype.

---

## 2️⃣ Environment Details

| Attribute | Value |
|-----------|-------|
| **SIEM Tool** | Splunk Enterprise |
| **Operating System** | Windows / Kali Linux |
| **Log Source** | Apache Web Server Logs |
| **Sourcetype** | DMMOP |
| **Host** | DSP |
| **Total Events Indexed** | 8,661 events |
| **Log Collection Period** | Multiple days (June 2005) |

---

## 3️⃣ Log Ingestion & Analysis Process

### Data Collection
- Apache log files were extracted from the web server
- Uploaded using Splunk's **Upload File** option
- Successfully indexed into the Default index

### Ingestion Steps
1. **Source Selection** → Selected Apache.log file
2. **Source Type Assignment** → Assigned DMMOP sourcetype
3. **Index Configuration** → Configured for Default index
4. **Timestamp Validation** → Verified correct event timestamps
5. **Field Extraction** → Confirmed proper field parsing

### Search Query Used
```spl
source="Apache.log" sourcetype="DMMOP"
```

**Results:** 8,661 events returned (before 28/12/2025 17:21:54.000)

---

## 4️⃣ Alert Event Analysis

### Detected Threats

#### Primary Threat: HTTP 403 - Directory Index Forbidden
- **Error Type:** [error] Directory index forbidden by rule
- **Error Code:** 403 Forbidden
- **Frequency:** Multiple occurrences
- **Path Targeted:** `/var/www/html/` directory

#### Suspicious Client IPs Identified
- 211.92.56.72
- 222.166.160.57
- 194.63.235.157
- 222.166.160.74
- 194.207.237.21

#### Attack Pattern Analysis
- **Type:** Reconnaissance / Directory Probing
- **Method:** Repeated HTTP requests to restricted directories
- **Indicators:** Multiple 403 errors from different source IPs
- **Temporal Pattern:** Clustered requests within short timeframes

### Additional Anomalies
- **[Notice] LDAP SDK** initialization messages
- **[Error] mod_jk** child initialization failures
- **[Error] Script not found** errors (CGI-bin probing)
- **[Error] Failed child processes** indicating abnormal server behavior

---

## 5️⃣ Incident Classification

### Incident Type
**Unauthorized Access Attempts / Reconnaissance Activity**

### Severity Assessment
| Factor | Assessment |
|--------|------------|
| **Severity Level** | MEDIUM |
| **Impact** | Contained (No confirmed breach) |
| **Urgency** | Medium |
| **Scope** | Apache Web Server only |
| **Data Risk** | Low (No data exfiltration detected) |

### Classification Details
- **Category:** Network Reconnaissance / Probing
- **Attack Vector:** Network-based HTTP requests
- **Attack Stage:** Early stage (Reconnaissance)
- **Threat Actor:** Unknown (multiple IPs suggest automated scanning or distributed activity)
- **Indicators of Compromise (IoCs):** Multiple 403 errors, repeated failed access attempts

---

## 6️⃣ Incident Response Actions

### Immediate Actions Taken

#### 1. **IP Monitoring & Filtering**
- Identified and documented suspicious source IP addresses
- Configured monitoring rules for repeated offenders
- **Recommendation:** Block or rate-limit suspicious IPs at firewall level

#### 2. **Access Control Review**
- Audited Apache directory permissions and configurations
- Verified .htaccess restrictions are properly configured
- **Recommendation:** Implement principle of least privilege

#### 3. **Logging & Monitoring Enhancements**
- Implemented continuous Splunk dashboard monitoring
- Created saved searches for unauthorized access patterns
- Set up alerts for repeated 403 errors and suspicious patterns
- **Recommendation:** Enable detailed request logging for forensic analysis

#### 4. **Security Hardening Recommendations**
- Deploy Web Application Firewall (WAF) for additional protection
- Implement IP allowlisting for sensitive directories
- Enable detailed request logging and retention
- Conduct regular log reviews and threat hunting
- Implement automated alerting for suspicious patterns

---

## 7️⃣ Key Findings Summary

✅ **Total Events Analyzed:** 8,661 events  
✅ **Primary Threat Detected:** HTTP 403 (Directory Index Forbidden)  
✅ **Attack Sources:** 5+ distinct IP addresses  
✅ **Attack Classification:** Reconnaissance/Probing  
✅ **Severity Level:** Medium (No confirmed compromise)  
✅ **Detection Method:** SIEM log analysis (Splunk)  
✅ **Response Status:** Contained & Monitored  

---

## 8️⃣ Conclusion

This incident response exercise successfully demonstrated:

1. **SIEM Log Ingestion** - Proper Apache log onboarding into Splunk
2. **Event Analysis** - Identification of suspicious patterns and threat indicators
3. **Incident Classification** - Categorization of attacks by type and severity
4. **Response Planning** - Structured incident response procedures
5. **SOC Operations** - Real-world security monitoring simulation

The task provided **hands-on, practical exposure** to SIEM-based log analysis and incident response, simulating real-world SOC operations. Key competencies gained include threat detection, event correlation, incident triage, and response documentation.

---

## 📊 Appendix: Log Examples

### Example 1: Directory Index Forbidden Error
```
[Sat Jun 11 07:06:50 2005] [error] [client 222.166.160.57] Directory index forbidden by rule: /var/www/html/
```

### Example 2: Multiple Failed Requests
```
[Sat Jun 11 03:04:01 2005] [notice] mod_jk Shutting down
[Sat Jun 11 03:03:59 2005] [notice] mod_jk Shutting down
[Sat Jun 11 03:03:58 2005] [notice] mod_jk Shutting down
```

### Example 3: Script Not Found (CGI Probing)
```
[Sat Jun 11 03:03:07 2005] [error] [client 202.133.98.6] script not found or unable to stat: /var/www/cgi-bin/awstats.pl
```

---

## 📝 Report Footer

- **Report Generated:** December 28, 2025
- **Analyst:** Dhanush G
- **Tool Used:** Splunk Enterprise
- **Data Source:** Apache.log
- **Classification:** Task 02 - Future Interns Cyber Security Internship
- **Status:** Completed ✓

---

**Document Control:**  
Version: 1.0  
Last Updated: December 28, 2025  
Next Review: Post-internship
