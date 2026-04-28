# 💬 Copilot Chat and Agent Intelligence Reports

<p style="font-size:small; font-weight:normal;">
This repository contains two distinct reports: <strong>Chat Intelligence</strong> and <strong>Agent Intelligence</strong>. Please select the appropriate template based on your specific use case. This enables more precise analysis of user behaviors, trends, and licensing/readiness across Copilot surfaces.
</p>

---

<details>
<summary>⚠️ **Important usage & compliance disclaimer - this is not official reporting for Chat or Agents**</summary>

Please note:  
The audit logs from Microsoft Purview are intended to support security and compliance use cases. While they provide visibility into Copilot interactions, they are **not intended** to serve as the sole source of truth for licensing or full-fidelity reporting on Copilot activity.  
For the most accurate and reliable usage insights, users are encouraged to refer to data from the **Microsoft 365 Admin Center** and **Viva Insights**. Insights from this report are intended to highlight organic usage trends, not replace official reporting or enforce licensing requirements.

While the tool helps customers better understand their data, Microsoft has **no visibility** into the data that customers input into this template/tool, nor does Microsoft have any control over how it is used or processed.  
Customers are solely responsible for ensuring that their use of the template tool complies with all applicable laws and regulations, including those related to data privacy and security.  
**Microsoft disclaims any and all liability** arising from or related to customers' use of the template tool.

</details>

---

## 🔑 Permissions Required

For Graph API access to Entra user information and mac licensing, you must assign the following Microsoft Graph permissions:

- `User.Read.All`
- `Organization.Read.All`

For Purview data, you will need one of the following roles:

 - `View-Only Audit Logs role (read-only, recommended for production)`
 - `Audit Logs role (if write operations needed elsewhere)`
 - `Member of appropriate role groups in Microsoft Purview compliance portal`

These permissions are required for both user info and mac licensing data (the latter is technically in Entra as well).

---

## 📊 What This Report Provides

- **Visibility into Copilot Chat usage** across prompts, sessions, agents, and surfaces.  
- **Breakdown of user engagement levels** to track progression from light to habitual use.  
- **Insights into agent adoption** across licensed vs. free experiences.  
- **Segmented views by org, quartile, and surface** to identify adoption hotspots and gaps.

---

## 🚀 How This Helps Leaders

- **Inform smarter Copilot licensing decisions** using real usage signals—maximize ROI by targeting high-readiness users.  
- **Accelerate AI readiness** by identifying where skills are organically developing, even before formal rollout.  
- **Connect usage across platforms** (Chat, M365, agents) to get a unified view of adoption trends and surface-specific value.  
- **Prioritize enablement efforts** based on actual usage patterns—focus resources where they’ll have the most impact.

<details closed>
  <summary>▶️ <b>Preview Chat Intelligence (GIF) </b></summary>

  <br>

  <img src="https://raw.githubusercontent.com/microsoft/CopilotChatAnalytics/refs/heads/main/Images/ChatIntelGIG.gif" alt="GitHub Copilot Engagement Preview" width="100%" />

</details>

<details open>
  <summary>▶️ <b>Preview Agent Intelligence (GIF) </b></summary>

  <br>

  <img src="https://raw.githubusercontent.com/microsoft/CopilotChatAnalytics/refs/heads/main/Images/AgentIntelGif.gif" alt="GitHub Copilot Engagement Preview" width="100%" />

</details>

> 📧 **Before you begin, your IT admin needs to export data from Purview and Entra.**
> These pre-written emails cover all required data sources, field names, admin roles, permissions, and export steps.
>
> **[📨 Chat Intelligence — Email Prerequisites to IT Admin](mailto:?subject=Action%20Required%3A%20Data%20Export%20Fields%20Needed%20for%20Chat%20Intelligence%20Report%20%28Power%20BI%29&body=To%3A%20IT%20Admin%20%2F%20Global%20Admin%0ARe%3A%20Copilot%20Chat%20Intelligence%20%E2%80%93%20Power%20BI%20Report%20Setup%0A%0A%0AWHAT%20THIS%20REPORT%20DOES%0A%0AThe%20Chat%20Intelligence%20Report%20is%20a%20Power%20BI%20report%20that%20analyzes%20Microsoft%20365%20Copilot%20Chat%20usage%20across%20your%20organization.%20It%20segments%20users%20by%20engagement%20level%20%28light%20to%20habitual%29%2C%20tracks%20session%20and%20prompt%20volume%20over%20time%2C%20and%20identifies%20adoption%20hotspots%20and%20licensing%20readiness%20signals%20by%20surface%2C%20org%20unit%2C%20and%20quartile.%0A%0A%0ADATA%20SOURCES%20REQUIRED%0A%0A1.%20Microsoft%20Purview%20%E2%80%93%20Copilot%20Audit%20Logs%0A%20%20%20Export%3A%20Purview%20portal%20%28security.microsoft.com%29%20-%3E%20Audit%20-%3E%20Activities%3A%20%22Interacted%20with%20Copilot%22%20-%3E%20Export%2C%20or%20PAX%20PowerShell%20script%0A%20%20%20Format%3A%20CSV%0A%0A2.%20Microsoft%20Entra%20ID%20%E2%80%93%20User%2FOrg%20Data%20%28includes%20license%20data%29%0A%20%20%20Export%3A%20entra.microsoft.com%20-%3E%20Identity%20-%3E%20Users%20-%3E%20Download%20users%2C%20or%20PAX%20script%20with%20-IncludeUserInfo%0A%20%20%20Format%3A%20CSV%0A%0A3.%20%28if%20not%20using%20PAX%29%20Microsoft%20365%20Admin%20Center%20%E2%80%93%20Licensed%20Users%0A%20%20%20Export%3A%20admin.microsoft.com%20-%3E%20Reports%20-%3E%20Usage%20-%3E%20M365%20Copilot%20-%3E%20Readiness%20tab%20-%3E%20Export%0A%20%20%20Format%3A%20CSV%0A%0ANote%20on%20license%20data%3A%20The%20report%20requires%20a%20hasLicense%20flag%20to%20separate%20licensed%20from%20unlicensed%20Copilot%20Chat%20usage.%20The%20PAX%20script%20automatically%20adds%20this%20column%20to%20the%20Entra%20user%20export%20%E2%80%94%20no%20separate%20file%20needed.%20If%20you%20are%20exporting%20manually%20from%20Entra%2C%20you%20will%20also%20need%20the%20M365%20Admin%20Center%20licensed%20users%20file%20%28source%20%233%29%20provided%20as%20a%20separate%20input.%0A%0A%0AREQUIRED%20FIELDS%20%E2%80%94%20DO%20NOT%20REMOVE%0A%0AIMPORTANT%3A%20If%20you%20are%20running%20a%20PAX%20Purview%20agent%20extract%20or%20manually%20exporting%20from%20Purview%2C%20do%20not%20remove%20or%20rename%20any%20columns%20from%20the%20output.%20Missing%20fields%20cause%20blank%20visuals%20with%20no%20error%20message.%0A%0APurview%20Audit%20Log%20%28CopilotInteraction%20%E2%80%93%20Record%20Type%2061%29%3A%0ACreationDate%2C%20UserId%2C%20Operations%2C%20AppHost%2C%20ThreadId%2C%20AgentId%2C%20Message_isPrompt.%0A%0AMicrosoft%20Entra%20ID%20%E2%80%93%20User%20Export%3A%0AUserPrincipalName%2C%20Department%2C%20hasLicense%20%28added%20automatically%20by%20PAX%3B%20or%20use%20the%20M365%20Admin%20Center%20licensed%20users%20file%20if%20exporting%20manually%29.%0A%0AM365%20Admin%20Center%20%E2%80%93%20Licensed%20Users%20%28manual%20export%20path%20only%29%3A%0AUserPrincipalName%2C%20Has%20Copilot%20License%20Assigned.%0A%0A%0AINSIGHTS%20YOU%20WILL%20GAIN%0A%0A-%20User%20engagement%20segmentation%3A%20light%2C%20moderate%2C%20regular%2C%20habitual%20Copilot%20Chat%20users%0A-%20Week-over-week%20session%20and%20prompt%20volume%20trends%0A-%20Surface%20breakdown%3A%20where%20chat%20usage%20is%20concentrated%20%28BizChat%2C%20Teams%2C%20M365%20apps%29%0A-%20Licensed%20vs.%20unlicensed%20chat%20usage%20patterns%0A-%20Agent-assisted%20vs.%20standard%20chat%20session%20split%0A-%20Org-level%20adoption%20comparison%20by%20department%20or%20quartile%0A%0A%0AROLES%20%26%20PERMISSIONS%20REQUIRED%0A%0AExport%20Purview%20audit%20logs%3A%20Audit%20Reader%20or%20Compliance%20Administrator%0AExport%20Entra%20user%20data%20%28includes%20hasLicense%20via%20PAX%29%3A%20User%20Administrator%20or%20Global%20Reader%0AExport%20M365%20Admin%20Center%20licensed%20users%20%28manual%20path%20only%29%3A%20Global%20Administrator%20or%20Reports%20Reader%0ARun%20PAX%20script%20%28optional%20automation%29%3A%20Audit%20Reader%20%2B%20AuditLog.Read.All%2C%20User.Read.All%20%28Microsoft%20Graph%29%0A%0A%0ASOFTWARE%20REQUIREMENTS%0A%0A-%20Power%20BI%20Desktop%20%E2%80%94%20required%20to%20open%20the%20.pbit%20template%20file%0A-%20PowerShell%205.1%2B%20%E2%80%94%20required%20only%20if%20using%20the%20PAX%20automated%20export%20script%0A-%20Access%20to%3A%20security.microsoft.com%2C%20admin.microsoft.com%2C%20entra.microsoft.com%0A%0A%0ANote%20on%20Usernames%3A%0AEnsure%20user%20display%20names%20are%20not%20concealed%20in%20M365%20Admin%20Center%20reports%20before%20exporting.%20Go%20to%20Settings%20-%3E%20Org%20Settings%20-%3E%20Services%20-%3E%20Reports%20and%20uncheck%20%22Display%20concealed%20user%2C%20group%2C%20and%20site%20names%20in%20all%20reports.%22%0A%0ANote%20on%20Hash%20String%3A%0AWhen%20opening%20the%20Power%20BI%20template%2C%20you%20will%20be%20prompted%20for%20a%20hash%20string.%20Provide%20any%20text%20string%20%E2%80%94%20this%20is%20used%20to%20de-identify%20sensitive%20user%20identifiers%20in%20the%20report%20output%20before%20sharing.)** · **[📨 Agent Intelligence — Email Prerequisites to IT Admin](mailto:?subject=Action%20Required%3A%20Data%20Export%20Fields%20Needed%20for%20Agent%20Intelligence%20Report%20%28Power%20BI%29&body=To%3A%20IT%20Admin%20%2F%20Global%20Admin%0ARe%3A%20Copilot%20Agent%20Intelligence%20%E2%80%93%20Power%20BI%20Report%20Setup%0A%0A%0AWHAT%20THIS%20REPORT%20DOES%0A%0AThe%20Agent%20Intelligence%20Report%20is%20a%20Power%20BI%20report%20that%20tracks%20adoption%20of%20Microsoft%20365%20Copilot%20agents%20across%20your%20organization.%20It%20ranks%20agents%20by%20usage%20and%20unique%20user%20reach%2C%20shows%20which%20M365%20surfaces%20agents%20are%20deployed%20on%2C%20and%20distinguishes%20licensed%20vs.%20free-tier%20agent%20interactions.%20Designed%20for%20organizations%20deploying%20custom%20or%20third-party%20Copilot%20agents%20at%20scale.%0A%0A%0ADATA%20SOURCES%20REQUIRED%0A%0A1.%20Microsoft%20Purview%20%E2%80%93%20Copilot%20Audit%20Logs%0A%20%20%20Export%3A%20Purview%20portal%20%28security.microsoft.com%29%20-%3E%20Audit%20-%3E%20Activities%3A%20%22Interacted%20with%20Copilot%22%20-%3E%20Export%2C%20or%20PAX%20PowerShell%20script%0A%20%20%20Format%3A%20CSV%0A%0A2.%20Microsoft%20Entra%20ID%20%E2%80%93%20User%2FOrg%20Data%20%28includes%20license%20data%29%0A%20%20%20Export%3A%20entra.microsoft.com%20-%3E%20Identity%20-%3E%20Users%20-%3E%20Download%20users%2C%20or%20PAX%20script%20with%20-IncludeUserInfo%0A%20%20%20Format%3A%20CSV%0A%0A3.%20%28if%20not%20using%20PAX%29%20Microsoft%20365%20Admin%20Center%20%E2%80%93%20Licensed%20Users%0A%20%20%20Export%3A%20admin.microsoft.com%20-%3E%20Reports%20-%3E%20Usage%20-%3E%20M365%20Copilot%20-%3E%20Readiness%20tab%20-%3E%20Export%0A%20%20%20Format%3A%20CSV%0A%0ANote%20on%20license%20data%3A%20The%20report%20requires%20a%20hasLicense%20flag%20to%20split%20licensed%20vs.%20free-tier%20agent%20interactions.%20The%20PAX%20script%20automatically%20adds%20this%20column%20to%20the%20Entra%20user%20export%20%E2%80%94%20no%20separate%20file%20needed.%20If%20you%20are%20exporting%20manually%20from%20Entra%2C%20you%20will%20also%20need%20the%20M365%20Admin%20Center%20licensed%20users%20file%20%28source%20%233%29%20provided%20as%20a%20separate%20input.%0A%0A%0AREQUIRED%20FIELDS%20%E2%80%94%20DO%20NOT%20REMOVE%0A%0AIMPORTANT%3A%20Agent-related%20fields%20%28AgentId%2C%20AgentName%2C%20AISystemPlugin_Name%29%20are%20nested%20inside%20the%20AuditData%20JSON%20in%20raw%20Purview%20exports%20and%20are%20flattened%20by%20the%20PAX%20script.%20If%20these%20columns%20are%20removed%20from%20a%20PAX%20output%20file%2C%20all%20agent%20analytics%20visuals%20will%20be%20blank.%20Do%20not%20prune%20these%20columns.%0A%0APurview%20Audit%20Log%20%28CopilotInteraction%20%E2%80%93%20Record%20Type%2061%29%3A%0ACreationDate%2C%20UserId%2C%20Operations%2C%20AppHost%2C%20AgentId%2C%20AgentName%2C%20AISystemPlugin_Id%2C%20AISystemPlugin_Name.%0A%0AMicrosoft%20Entra%20ID%20%E2%80%93%20User%20Export%3A%0AUserPrincipalName%2C%20Department%2C%20hasLicense%20%28added%20automatically%20by%20PAX%3B%20or%20use%20the%20M365%20Admin%20Center%20licensed%20users%20file%20if%20exporting%20manually%29.%0A%0AM365%20Admin%20Center%20%E2%80%93%20Licensed%20Users%20%28manual%20export%20path%20only%29%3A%0AUserPrincipalName%2C%20Has%20Copilot%20License%20Assigned.%0A%0A%0AINSIGHTS%20YOU%20WILL%20GAIN%0A%0A-%20Top%20agents%20by%20interaction%20volume%20and%20unique%20user%20reach%0A-%20Agent%20adoption%20trend%20over%20time%0A-%20Deployment%20surface%20breakdown%3A%20which%20M365%20surfaces%20%28Teams%2C%20BizChat%2C%20Outlook%29%20agents%20are%20invoked%20on%0A-%20Licensed%20vs.%20unlicensed%20user%20split%20for%20agent%20interactions%0A-%20Plugin%2Fagent-type%20categorization%20and%20inventory%20view%0A-%20Department-level%20agent%20adoption%20comparison%0A%0A%0AROLES%20%26%20PERMISSIONS%20REQUIRED%0A%0AExport%20Purview%20audit%20logs%3A%20Audit%20Reader%20or%20Compliance%20Administrator%0AExport%20Entra%20user%20data%20%28includes%20hasLicense%20via%20PAX%29%3A%20User%20Administrator%20or%20Global%20Reader%0AExport%20M365%20Admin%20Center%20licensed%20users%20%28manual%20path%20only%29%3A%20Global%20Administrator%20or%20Reports%20Reader%0ARun%20PAX%20script%20%28optional%20automation%29%3A%20Audit%20Reader%20%2B%20AuditLog.Read.All%2C%20User.Read.All%20%28Microsoft%20Graph%29%0A%0A%0ASOFTWARE%20REQUIREMENTS%0A%0A-%20Power%20BI%20Desktop%20%E2%80%94%20required%20to%20open%20the%20.pbit%20template%20file%0A-%20PowerShell%205.1%2B%20%E2%80%94%20required%20only%20if%20using%20the%20PAX%20automated%20export%20script%0A-%20Access%20to%3A%20security.microsoft.com%2C%20admin.microsoft.com%2C%20entra.microsoft.com%0A%0A%0ANote%20on%20Usernames%3A%0AEnsure%20user%20display%20names%20are%20not%20concealed%20before%20exporting%20from%20M365%20Admin%20Center.%20Go%20to%20Settings%20-%3E%20Org%20Settings%20-%3E%20Services%20-%3E%20Reports%20and%20uncheck%20%22Display%20concealed%20user%2C%20group%2C%20and%20site%20names%20in%20all%20reports.%22%0A%0ANote%20on%20Hash%20String%3A%0AThe%20Power%20BI%20template%20prompts%20for%20a%20hash%20string%20on%20open.%20Provide%20any%20text%20string%20%E2%80%94%20this%20de-identifies%20user%20identifiers%20before%20the%20report%20is%20shared.)**

---

## ✅ What You’ll Do

<details open>
<summary>📤 Step 1: Export 3 Files</summary>

- **Copilot interactions audit log** from Microsoft Purview  
- **Copilot licensed user list** from Microsoft 365 Admin Center  
- **Org data** from Microsoft Entra Admin Center  

</details>

<details open>
<summary>🔐 Step 2: Provide Hash String & Connect Files</summary>

- Supply a text string to be used for hashing and de-identifying sensitive identifiers  
- Paste full file paths for each CSV into the Power BI (PBI) template:
  
</details>

## 📁 Detailed Steps

<details>
<summary>🔍 Copilot Audit Logs from Purview</summary>

- Go to: [security.microsoft.com](https://security.microsoft.com)  
  - In the left pane, scroll down and click **Audit**  
  - Ensure you have appropriate compliance roles (e.g., **Audit Reader**). If not, contact your IT admin  
- In **Activities > Friendly Names**, select:  
  `Copilot Activities – Interacted with Copilot`  
- Set a **Date Range** (recommended: 3–6 months)  
- Give your search a name and click **Search**  
  - Once the status changes to **Completed**, click into it  
- Select **Export > Download all results**

📖 Learn more: [Export, configure, and view audit log records – Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/compliance/audit-log-search)

</details>

<details>
<summary>👤 Licensed User List from MAC</summary>

- Go to: [admin.microsoft.com](https://admin.microsoft.com)  
  - Log in as a **Microsoft 365 Global Administrator**  
- To unhide usernames in MAC reports:  
  - Go to **Settings > Org Settings**, then under the **Services** tab, choose **Reports**  
  - Deselect **Display concealed user, group, site names in all reports**  
  - Click **Save changes**  
- Navigate to: **Reports > Usage > Microsoft 365 Copilot**  
- In the **Readiness** tab, scroll to **Copilot Readiness Details**  
  - Select column: `Has Copilot license assigned`  
- Click the ellipsis (`...`) and choose **Export** to download the file as `.csv`

📖 Learn more: [Microsoft 365 Copilot Readiness Report – Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-readiness)

</details>

<details>
<summary>📥 User and Org Data from Entra</summary>

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com)  
2. In the left-hand navigation, go to: `Identity ➝ Users`  
3. Select **All users**  
4. Click the **“Download users”** button (in the toolbar or under the `...` menu)  
5. In the download dialog:  
   - Select the attributes to include in the CSV  
   - **Required fields**:  
     - `UserPrincipalName`  
     - `Department`  
   - **Optional fields**:  
     - Choose as appropriate  
6. Choose **CSV format** and click **Download**

📖 Learn more: [Download a list of users – Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity/users/users-bulk-download)  
💡 _Note: Avoid downloading non-essential attributes as it can degrade performance._

</details>

<details>
<summary>📊 Open Power BI Template & Set File Paths</summary>

- Download the provided Power BI report template (`.PBIT`)
- Select Agent Usage template for analyzing agents and Chat Intelligence for deep analysis on Chat interactions  
- Open the `.pbit` file in **Power BI Desktop**  
- When prompted, paste in the full file paths for the three CSVs you downloaded:  
   - `Copilot_Activities.csv`  
   - `Copilot_Licensed_Users.csv`  
   - `Org_Data.csv`  
- Provide a text string to hash and obfuscate identifiers. This will deidentify sensitive data and makes it easier to share.
- This will connect the template to your data and begin processing

</details>

---

## 🤓 Nerd Corner (for Claude Code users)
If you're into automation and allergic to manual decks — try this:

👉 https://github.com/shailendrahegde/pbi-to-exec-deck

It turns raw outputs into exec-ready PPTs with insights pre-baked.
All you do: verify, tweak, ship.
