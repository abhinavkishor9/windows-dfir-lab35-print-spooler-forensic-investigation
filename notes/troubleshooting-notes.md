# Troubleshooting Notes

## Issue 1

PrintService Operational log showed no events.

### Cause

Operational logging was disabled.

### Resolution

Enable the Operational log in Event Viewer:

```

Applications and Services Logs
→ Microsoft
→ Windows
→ PrintService
→ Operational
→ Enable Log

```

---

## Issue 2

No print events appeared after printing.

### Cause

The document was not actually sent to the printer.

### Resolution

Complete the **Microsoft Print to PDF** save process before checking Event Viewer.

---

## Issue 3

Print Spooler service not running.

### Cause

The Print Spooler service was stopped.

### Resolution

Verify using:

```powershell
Get-Service Spooler
```

Start if necessary:

```powershell
Start-Service Spooler
```

---

## Issue 4

No `.SPL` or `.SHD` files found.

### Cause

The print job had already completed and temporary spool files were automatically removed.

### Resolution

Inspect the spool directory while the print job is active or immediately after printing.

---

## Issue 5

Unable to access the spool directory.

### Cause

Administrator permissions required.

### Resolution

Open File Explorer or PowerShell with administrative privileges.

---

## Issue 6

Unexpected file path errors during cleanup.

### Cause

Incorrect folder path or typo.

Example:

```
C:\Downloads\Archive
```

instead of

```
C:\Users\<User>\Downloads\Archive
```

### Resolution

Verify paths using:

```powershell
Get-ChildItem "$Env:USERPROFILE" -Recurse
```

before deleting files.

---

## Issue 7

Cleanup failed because the investigation folder did not exist.

### Cause

Folder had already been removed or the wrong path was used.

### Resolution

Verify the folder before deleting:

```powershell
Get-ChildItem C:\PrintSpoolLab
```

Then execute:

```powershell
Remove-Item C:\PrintSpoolLab -Recurse -Force
```
