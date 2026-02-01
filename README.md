# FUTURE_CS_02 – Security Alert Monitoring & Incident Response using Splunk

---

## 📋 Project Overview

This repository documents a **Security Information and Event Management (SIEM)** case study focused on monitoring Apache web server logs using **Splunk Enterprise**. This project is **Task 2** of the **Future Interns Cyber Security Internship** and simulates real-world **Security Operations Center (SOC)** operations, including log ingestion, event analysis, threat detection, and structured incident response.

---

## 🛠️ Tools & Environment

| Component | Details |
|-----------|----------|
| **SIEM Platform** | Splunk Enterprise |
| **Operating System** | Windows |
| **Log Source** | Apache HTTP Server (access & error logs) |
| **Sourcetype** | DMMOP |
| **Analysis Tool** | Splunk Search & Reporting |

---

## 📂 Data Ingestion & Preparation

Apache log files were ingested into Splunk following these steps:

1. **Source Upload:** Apache log files exported from the web server
2. **File Upload:** Used Splunk's **Upload File** option from the interface
3. **Source Configuration:** Assigned proper source identification and sourcetype (**DMMOP**)
4. **Indexing:** Logs were indexed for full-text search capability
5. **Validation:** Event timestamps, host information, and fields were verified in Search & Reporting

---

## 🔍 Log Analysis & Detection

### Suspicious Activities Identified

During comprehensive analysis of Apache logs using the query below, the following security events were detected:

```spl
source="Apache.log" sourcetype="DMMOP"
```

### Key Findings:

| Finding | Details | Risk Level |
|---------|---------|------------|
| **Directory Index Forbidden (403)** | Multiple requests to restricted directories without proper permissions | Medium |
| **Repeated Failed Access Attempts** | Multiple client IP addresses attempting unauthorized access | Medium |
| **Abnormal Error Patterns** | Spike in server error and notice messages | Medium |
| **Reconnaissance Activity** | Systematic probing of server resources | Medium |

### Attack Indicators:
- HTTP 403 (Forbidden) responses for directory listing attempts
- Multiple source IPs targeting the same restricted resources
- Temporal clustering of failed authentication/authorization events
- Lack of legitimate user-agent headers in suspicious requests

---

## 🚨 Incident Classification & Response

### Incident Summary

| Attribute | Value |
|-----------|-------|
| **Incident Type** | Unauthorized Access Attempts |
| **Classification** | Probing/Reconnaissance |
| **Severity Level** | Medium |
| **Affected Component** | Apache Web Server |
| **Detection Method** | SIEM Log Analysis (Splunk) |
| **Status** | Contained & Monitored |

### Response Actions Implemented

1. **IP Monitoring & Filtering**
   - Identified suspicious source IP addresses from logs
   - Configured monitoring rules for repeated offenders
   - Recommended blocking or rate-limiting suspicious IPs at firewall level

2. **Access Control Review**
   - Audited Apache directory permissions and configurations
   - Verified .htaccess restrictions are properly configured
   - Recommended principle of least privilege for web directories

3. **Logging & Monitoring Enhancements**
   - Implemented continuous Splunk dashboard monitoring
   - Created saved searches for unauthorized access patterns
   - Set up alerts for repeated 403 errors and suspicious patterns

4. **Security Recommendations**
   - Deploy Web Application Firewall (WAF) for additional protection
   - Implement IP allowlisting for sensitive directories
   - Enable detailed request logging for forensic analysis
   - Conduct regular log reviews and threat hunting

---

## 📊 Skills Demonstrated

✅ **SIEM Platform Mastery**
- Log ingestion and onboarding into Splunk
- Index management and sourcetype configuration

✅ **Security Event Analysis**
- Pattern recognition in log data
- Correlation of suspicious activities
- Threat indicator identification

✅ **Incident Management**
- Event classification and prioritization
- Severity assessment and response planning
- Documentation of incident lifecycle

✅ **SOC Operations**
- Alert monitoring and triage
- Real-time threat detection
- Incident response workflow

✅ **Splunk Expertise**
- SPL (Splunk Processing Language) query crafting
- Field extraction and manipulation
- Dashboard creation and saved searches
- Alert configuration

---

## 📸 Repository Contents

This repository includes:

- **README.md** – Comprehensive project documentation (this file)
- 
- **Screenshots/** – Evidence of log analysis and detection:
  - Log ingestion process and configuration
  - Splunk search queries and results
  - Detected security events and alerts dashboard snapshots
  - See [Screenshots/SPLUNK_EVIDENCE.md](Screenshots/SPLUNK_EVIDENCE.md) for detailed documentation
  - 
  - **INCIDENT_RESPONSE_REPORT.md** – Comprehensive incident response documentation:
  - Executive summary of findings
  - Detailed threat analysis and classification
  - Incident response procedures and recommendations
  - Log examples and evidence documentation
  - See [INCIDENT_RESPONSE_REPORT.md](INCIDENT_RESPONSE_REPORT.md) for full report
- **Screenshots/** – Evidence of log analysis and detection:
  - Log ingestion process
  - Splunk search queries and results
  - Detected security events and alerts
  - Dashboard snapshots
- **Documentation/** – Detailed incident response reports
- **Queries/** – SPL search queries used in analysis

---

## 🎯 Key Achievements

✓ Successfully ingested and indexed Apache logs into Splunk  
✓ Identified and classified unauthorized access attempts  
✓ Documented comprehensive incident response procedures  
✓ Created reusable detection rules and alerts  
✓ Demonstrated real-world SOC monitoring capabilities  
✓ Gained practical SIEM and log analysis expertise  

---

## 📚 Future Enhancements

- Integration with threat intelligence feeds for IP reputation analysis
- Machine learning-based anomaly detection
- Automated incident ticket generation
- Integration with ticketing systems (Jira, ServiceNow)
- Enhanced correlation with network and endpoint logs
- Development of custom Splunk dashboards for executive reporting

---

## 📝 Conclusion

This project provided hands-on, practical experience in **security alert monitoring and incident response** using industry-standard SIEM tools. By analyzing real log data, detecting suspicious patterns, and documenting comprehensive incident response procedures, this task successfully simulated **real-world SOC operations** and built foundational cyber security skills essential for security operations professionals.

---

## 👤 Author

**DHANUSHGCODE**  
Future Interns Cyber Security Internship – Task 2  
December 2025

---

## 📄 License


#Mit license
---

**Last Updated:** December 28, 2025
