> ⚠️ **Disclaimer**  
> Please note: The audit logs from Microsoft Purview are intended to support security and compliance use cases.  
>
> While they provide visibility into Copilot interactions, they are **not intended** to serve as the official source for Copilot usage reporting.  
>
> Metrics derived from this data—such as "prompt count" or "active user count"—**may differ** from the usage reports provided directly by Microsoft.  
>
> For the most accurate and reliable usage insights, users are encouraged to refer to data from the **Microsoft 365 Admin Center** and **Viva Insights**, which are purpose-built to deliver higher fidelity reporting.  
>
> Users should interpret audit log-based information with that context in mind.


## ✅ What You’ll Do

- Export **Copilot interactions audit log** from Microsoft Purview.
- Export **licensed user list** from Microsoft 365 Admin Center.
- Export **user list with org data** from Microsoft Entra Admin Center.

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
## 📥 Exporting User List from Microsoft Entra Portal (UI)

Follow these steps to export a list of users with specific attributes from the Microsoft Entra admin center:

### Prerequisites
- An account with sufficient permissions to view and export user data in Microsoft Entra.

### Steps

1. **Sign in** to the [Microsoft Entra admin center](https://entra.microsoft.com/).
2. In the **left-hand navigation**, go to:  
   `Identity` ➝ `Users`
3. Select **All users**.
4. Click the **“Download users”** button (found in the toolbar or under the `...` menu).
5. In the download dialog:
   - Select the **attributes** to include in the CSV.
   - **Required fields**:
     - `UserPrincipalName`
     - `Department`
   - **Optional fields**:
     - Choose as appropriate`
6. Choose **CSV format** and click **Download**.

📖 Learn more: https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-download

> 💡 Note: Avoid downloading non-essential attributes as it can degrade the performance


### 4. 📊 Open Power BI Template & Set File Paths

- Download the provided **Power BI report template (.PBIT)**.
- Open the `.pbit` file in Power BI Desktop.
- When prompted, paste in the **full file paths** for the three CSVs you downloaded:
  - `Copilot_Activities.csv`
  - `Copilot_Licensed_Users.csv`
  - `Org_Data.csv`

This will connect the template to your data and begin processing.

---

