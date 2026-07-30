# Investigation Notes

## Lab Summary

This investigation focused on analyzing Windows Print Spooler forensic artifacts using native Windows tools.

The investigation reconstructed document printing activity by correlating Windows PrintService Operational logs, Print Spooler artifacts, Event Viewer, PowerShell, and the Windows spool directory while validating print-related Event IDs.

---

## Analyst Methodology

1. Create investigation workspace.
2. Generate sample documents.
3. Verify Print Spooler service.
4. Generate controlled print activity.
5. Review PrintService Operational logs.
6. Validate events using Event Viewer.
7. Verify Print Spooler service using PowerShell.
8. Examine spool directory artifacts.
9. Correlate event logs with spool files.
10. Document findings.

---

## Investigation Scenario

Several sample documents were created and printed using **Microsoft Print to PDF**.

The investigation aimed to determine:

- Which document was printed.
- Which user initiated the print job.
- Which printer was used.
- Whether Windows generated PrintService events.
- Whether spool files were created.
- How printing activity could be reconstructed.

---

## Evidence Collected

### Evidence 1 – Sample Documents

Collected:

- Payroll.txt
- Employees.txt
- IncidentReport.txt

Finding:

Established controlled printing activity for the investigation.

---

### Evidence 2 – Print Spooler Service

Command Used

```powershell
Get-Service Spooler
```

Finding:

Confirmed the Windows Print Spooler service was running successfully before generating print activity.

---

### Evidence 3 – Event Viewer

Collected:

- PrintService Operational Log
- Event IDs 800
- Event IDs 801
- Event IDs 805
- Event IDs 842
- Event ID 307

Finding:

Confirmed successful document printing and recorded detailed forensic information including document name, user, printer, timestamp, and pages printed.

---

### Evidence 4 – Print Spool Directory

Location

```text
C:\Windows\System32\spool\PRINTERS
```

Collected:

- `.SPL` files
- `.SHD` files

Finding:

Confirmed temporary spool artifacts were created during the print process.

---

## DFIR Analysis

The investigation demonstrated how Windows Print Spooler preserves valuable forensic evidence during document printing.

By correlating PrintService Operational logs with spool directory artifacts, the investigation successfully reconstructed document printing activity, identified the printed document, verified the responsible user, and confirmed successful print job execution using native Windows forensic artifacts.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Collection | Data from Local System | T1005 |
| Discovery | File and Directory Discovery | T1083 |
| Defense Evasion | Indicator Removal on Host (Potential Follow-on Investigation) | T1070 |

---

## Analyst Observations

- PrintService Operational logs provide detailed evidence of completed print jobs.
- Event ID 307 is the primary forensic artifact for successful document printing.
- Temporary `.SPL` and `.SHD` files provide additional print job evidence.
- PowerShell quickly verifies the operational status of the Print Spooler service.
- Correlating Event Viewer logs with spool artifacts significantly improves investigation confidence.

---

## Conclusion

The investigation demonstrated how Windows Print Spooler forensic artifacts can be used to reconstruct document printing activity using native Windows tools. By combining Event Viewer analysis, PowerShell validation, and spool directory artifacts, investigators can accurately determine what was printed, who initiated the print job, and when the activity occurred.
