# windows-dfir-lab35-print-spooler-forensic-investigation

## Overview

Windows Print Spooler is responsible for managing print jobs by temporarily storing documents in the spool directory before they are sent to a printer. In addition to generating Windows Event Logs, the Print Spooler creates spool artifacts that can provide valuable forensic evidence during incident response.

In this hands-on DFIR lab, controlled print activity was generated using Microsoft Print to PDF. Native Windows tools were then used to examine PrintService Operational logs, inspect spool files, and correlate multiple artifacts to reconstruct document printing activity.

---

# Executive Summary

This investigation demonstrates how Windows Print Spooler artifacts can be analyzed using only native Windows tools. By generating controlled print jobs, investigators examined Windows Event Logs alongside temporary spool files to identify printed documents, determine the user responsible, identify the printer used, and reconstruct the overall printing timeline.

The workflow mirrors a real-world DFIR investigation by generating activity, preserving evidence, validating forensic artifacts, correlating multiple evidence sources, and documenting findings.

---

# Investigation Objectives

- Generate controlled document printing activity.
- Verify Windows Print Spooler service status.
- Examine PrintService Operational logs.
- Analyze print-related Event IDs.
- Inspect Windows spool directory artifacts.
- Correlate Event Viewer evidence with spool files.
- Reconstruct document printing activity.
- Document forensic findings.

---

# Skills Demonstrated

- Windows Print Spooler Forensics
- Windows Event Log Analysis
- Host-Based DFIR Investigation
- Native Windows Artifact Analysis
- Print Job Reconstruction
- PowerShell Enumeration
- Windows Service Verification
- Evidence Correlation
- Timeline Reconstruction
- Incident Reporting

---

# Tools Used

- Windows 10
- PowerShell
- Event Viewer
- File Explorer
- Microsoft Print to PDF

---

# Lab Environment

| Component | Details |
|-----------|---------|
| Operating System | Windows 10 |
| Investigation Type | Host-Based DFIR |
| Analysis Method | Native Windows Tools |
| Primary Artifact | Windows Print Spooler |
| Secondary Artifact | PrintService Operational Log |
| Shell | Windows PowerShell |
| Privileges | Administrator |

---

# Investigation Workflow

1. Create investigation workspace.
2. Generate sample documents.
3. Verify Print Spooler service.
4. Produce controlled print activity.
5. Examine PrintService Operational logs.
6. Inspect spool directory artifacts.
7. Correlate Event Logs with spool files.
8. Document findings.
9. Remove lab artifacts.

---

# MITRE ATT&CK Mapping

| Technique | Description |
|-----------|-------------|
| T1005 | Data from Local System |
| T1083 | File and Directory Discovery |
| T1070 | Indicator Removal on Host |
| T1020 | Automated Collection (Potential Follow-on Investigation) |

---

# Evidence Collected

- PowerShell outputs
- PrintService Operational logs
- Event IDs 800, 801, 805, 842, 307
- Print dialog screenshots
- Print Spooler service status
- `.SPL` spool files
- `.SHD` spool metadata files

---

# Evidence Correlation

The investigation correlated multiple Windows forensic artifacts to validate printing activity:

- Successful print jobs generated corresponding PrintService Operational events.
- Event ID 307 identified the document name, user account, printer, pages printed, and print timestamp.
- Temporary `.SPL` and `.SHD` files confirmed that Windows created spool artifacts during printing.
- Event Viewer logs and spool directory artifacts together reconstructed the complete print workflow.

---

# Investigation Findings

The investigation confirmed that Windows Print Spooler preserves valuable forensic evidence during document printing. PrintService Operational logs recorded detailed information about each completed print job, while temporary spool files demonstrated how Windows stages documents before printing. Correlating both artifact sources allowed accurate reconstruction of user printing activity using only native Windows forensic evidence.

---

# Key Takeaway

Windows Print Spooler artifacts are an important source of forensic evidence during host-based investigations. By combining PrintService Operational logs with spool directory artifacts, investigators can determine what was printed, who initiated the print job, when it occurred, and which printer was used, enabling reliable reconstruction of printing activity without specialized forensic software.
