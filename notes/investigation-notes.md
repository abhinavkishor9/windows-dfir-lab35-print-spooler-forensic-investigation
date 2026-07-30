# Investigation Notes

## Lab Summary

**Objective:**

Investigate Windows Print Spooler forensic artifacts by generating print activity, examining PrintService Operational logs, analyzing spool files, and correlating artifacts to reconstruct document printing events.

---

## Analyst Methodology

The investigation followed a standard host-based DFIR methodology:

1. Prepare investigation workspace.
2. Generate sample documents.
3. Verify Print Spooler service.
4. Produce controlled print activity.
5. Examine Windows Event Logs.
6. Inspect spool directory artifacts.
7. Correlate forensic evidence.
8. Document findings.
9. Produce investigation timeline.

---

## Investigation Steps

### Step 1

Created investigation workspace.

Evidence:

- PrintSpoolLab
- Documents folder

---

### Step 2

Created sample documents.

Evidence:

- Payroll.txt
- Employees.txt
- IncidentReport.txt

---

### Step 3

Verified the Windows Print Spooler service.

PowerShell:

```powershell
Get-Service Spooler
```

Observation:

- Service Status: Running

---

### Step 4

Printed each sample document using **Microsoft Print to PDF**.

Observation:

Multiple print jobs were successfully generated.

---

### Step 5

Opened Event Viewer.

Navigated to:

```

Applications and Services Logs
→ Microsoft
→ Windows
→ PrintService
→ Operational

```

Observation:

Multiple PrintService events were recorded.

---

### Step 6

Examined PrintService Operational events.

Important Event IDs observed:

- 800
- 801
- 805
- 842
- 307

Observation:

Event ID 307 contained detailed forensic evidence including:

- Document name
- User account
- Printer used
- Port information
- Number of pages printed
- Print timestamp

---

### Step 7

Inspected the Print Spool directory.

Location:

```

C:\Windows\System32\spool\PRINTERS

```

Observed artifacts:

- .SPL files
- .SHD files

---

### Step 8

Correlated forensic artifacts.

| Artifact | Evidence |
|----------|----------|
| Event ID 307 | Successful print event |
| PrintService Log | Printing workflow |
| .SPL File | Print job spool data |
| .SHD File | Print job metadata |

Confirmed successful reconstruction of print activity.

---

## Evidence Summary

Collected:

- PowerShell outputs
- PrintService Operational logs
- Event ID 307 details
- Print dialog screenshots
- Spool directory artifacts (.SPL / .SHD)

---

## Analyst Observations

The investigation demonstrated that:

- Windows logs every print job through PrintService Operational events.
- Event ID 307 provides valuable forensic information about completed print jobs.
- Print Spooler temporarily stores print artifacts inside the PRINTERS directory.
- Event logs and spool artifacts together enable investigators to reconstruct document printing activity accurately.

---

## Conclusion

The investigation successfully demonstrated Windows Print Spooler forensic analysis by generating controlled print activity, examining Event Viewer logs, inspecting spool artifacts, and correlating multiple forensic evidence sources to reconstruct printing events.
