## ✅ What You’ll Do

- Export **Copilot interactions audit log** from Microsoft Purview.
- Export **licensed user list** from Microsoft 365 Admin Center.
- **Paste your file paths** into Power BI when prompted:
  - One for the **Copilot_Activities** file
  - One for the **Copilot Licensed Users** file
- Merge both datasets in Power BI.

---

## 📁 Files You’ll Download

### 1. 🔍 Copilot Audit Logs

- Go to: [security.microsoft.com](https://security.microsoft.com)
  - On the left pane, scroll down and click **Audit**.
  - Ensure you have appropriate **Compliance roles** (e.g., Audit Reader). If not, contact your IT admin.
- In **Activities > Friendly Names**, select:  
  `Copilot Activities – Interacted with Copilot`
- Set a **Date Range** (recommended: 3–6 months).
- Give your search a name and click **Search**.
  - Once the status changes to **Completed**, click into it.
- Select **Export > Download all results**.

This will download a `.csv` file containing an `AuditData` JSON column.

📖 Learn more:  
[Export, configure, and view audit log records – Microsoft Learn](https://learn.microsoft.com/en-us/purview/audit-log-export-records)

---

### 2. 👤 Licensed User List

- Go to: [admin.microsoft.com](https://admin.microsoft.com)
  - Log in as a **Microsoft 365 Global Administrator**.
- Navigate to **Reports > Usage**.
- Select the **Microsoft 365 Copilot** tab.
- On the **Readiness** tab, select:  
  `Has Copilot license assigned`
- Select only these columns:
  - `Username`, `Display name`, `Email`
- Click the ellipsis (**...**) and choose **Export** to download the file as `.csv`.

📖 Learn more:  
[Microsoft 365 Copilot Readiness Report – Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-readiness?view=o365-worldwide)

---

## 💡 Tips

- The `AuditData` column contains nested JSON. Power BI will automatically flatten this using the provided report template.
- Ensure the **audit log date range** is wide enough (3–6 months) to capture meaningful usage data.
- Use **email address** as the key when merging datasets in Power BI.
- When prompted in Power BI, paste the **full file paths** for both CSVs:  
  - `Copilot_Activities.csv`  
  - `Copilot_Licensed_Users.csv`
