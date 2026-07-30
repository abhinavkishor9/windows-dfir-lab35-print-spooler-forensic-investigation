# windows-dfir-lab35-print-spooler-forensic-investigation
## Overview

Windows Print Spooler maintains forensic evidence whenever documents are printed. Besides generating Windows Event Logs, it temporarily stores spool files that contain information about pending print jobs.

During incident response, Print Spooler artifacts can help investigators determine:

- Whether documents were printed
- Which document was printed
- Which user initiated printing
- Which printer was used
- When the print occurred
- Whether spool files still exist

This investigation demonstrates how native Windows artifacts can be used to reconstruct printing activity.

---

## Objectives

- Generate controlled printing activity
- Verify Print Spooler service status
- Examine PrintService Operational logs
- Analyze Event IDs related to printing
- Inspect spool directory artifacts
- Correlate Event Viewer evidence with spool files
- Document forensic findings

---

## Environment

- Windows 10 VM
- PowerShell
- Event Viewer
- Microsoft Print to PDF
- Windows Print Spooler Service

---

## Tools Used

- PowerShell
- Event Viewer
- File Explorer
- Microsoft Print to PDF

---

## Windows Artifacts Investigated

### PrintService Operational Log

```

Applications and Services Logs
└── Microsoft
└── Windows
└── PrintService
└── Operational

```

### Spool Directory

```

C:\Windows\System32\spool\PRINTERS

```

---

## Key Findings

- Print Spooler service was running normally.
- Sample documents were successfully printed.
- PrintService Operational logs recorded multiple print events.
- Event ID 307 contained detailed forensic evidence.
- Temporary `.SPL` and `.SHD` spool files were created.
- Event logs and spool artifacts correlated successfully.

---

## Skills Practiced

- Windows DFIR
- Print Spooler Forensics
- Event Log Analysis
- Artifact Correlation
- Timeline Reconstruction
- Native Windows Forensic Analysis

---

## MITRE ATT&CK Context

Although printing itself is legitimate, attackers sometimes print sensitive documents before exfiltration or insider theft.

Relevant techniques include:

- T1005 – Data from Local System
- T1020 – Automated Collection
- T1070 – Indicator Removal (if spool files are deleted)

---

## Outcome

This lab demonstrated how Windows Print Spooler artifacts can be leveraged during DFIR investigations to reconstruct document printing activity using only native Windows forensic evidence.
