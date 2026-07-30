# Investigation Timeline

| Time | Activity | Evidence |
|------|----------|----------|
| 06:35 | Created PrintSpoolLab workspace | Investigation directory |
| 06:38 | Created Payroll.txt | Sample document |
| 06:38 | Created Employees.txt | Sample document |
| 06:39 | Created IncidentReport.txt | Sample document |
| 06:45 | Verified Print Spooler service | Get-Service Spooler |
| 06:50 | Printed documents using Microsoft Print to PDF | Print dialog |
| 06:50 | Spool files created | .SPL / .SHD artifacts |
| 07:03 | PrintService Operational events generated | Event IDs 800, 801, 805, 842, 307 |
| 07:03 | Examined Event ID 307 | Document name, user, printer, timestamp |
| 07:05 | Correlated Event Logs with spool artifacts | Successful forensic reconstruction |
| 07:08 | Removed investigation workspace | Lab cleanup |
