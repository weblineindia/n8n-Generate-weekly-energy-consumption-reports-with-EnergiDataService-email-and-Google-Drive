# Weekly Energy Consumption Reports with EnergiDataService, Email and Google Drive

### 📊 Automated Energy Reporting (n8n | API | Google Drive | Email)

This workflow automates the process of retrieving energy consumption data from the EnergiDataService API, formatting it into a professional report, and distributing it every week via email and Google Drive. It is designed to help energy managers and sustainability teams track consumption patterns without manual data exports.

---

## ⚡ Quick Implementation Steps

- **Import** the workflow JSON into your n8n instance.
- **Configure** your Gmail/Outlook and Google Drive credentials.
- **Adjust** the Schedule (Cron) node if you need a different reporting time (default is Monday morning).
- **Activate** the workflow to start receiving automated weekly reports.

---

## 🎯 Who's It For

- **Energy Providers & Utilities:** Automate reporting for end-users or internal teams.
- **Sustainability Departments:** Track weekly carbon footprints and usage.
- **Facility Managers:** Monitor building energy performance over time.
- **Renewable Energy Operators:** Log grid consumption alongside local production.

---

## 🛠 Requirements

| Tool                      | Purpose                                              |
| :------------------------ | :--------------------------------------------------- |
| **n8n Instance**          | To run and schedule the automation                   |
| **EnergiDataService API** | Source of energy consumption data (Public API)       |
| **Google Drive**          | To archive a permanent copy of the CSV/Excel reports |
| **Email Service**         | To distribute the weekly report (Gmail/Outlook/SMTP) |

---

## 🧠 How It Works

1.  **Schedule Weekly:** A Cron node triggers the workflow every Monday at 8:00 AM.
2.  **Fetch Energy Data:** An HTTP Request node pulls consumption data (e.g., `ConsumptionDE35Hour`) from the EnergiDataService API.
3.  **Normalize Records:** A Code node cleans and transforms the raw JSON into a flat structure.
4.  **Convert to File:** The data is converted into a downloadable CSV or binary file.
5.  **Distribute:** The report is sent to stakeholders via email and simultaneously uploaded to a specific folder in Google Drive.

---

## 🔧 How To Set Up – Step-by-Step

1.  **Import Workflow:** Upload the `.json` file into your n8n workspace.
2.  **Set Credentials:**
    - **Google Drive:** Connect via OAuth2 and select the target folder.
    - **Email:** Connect your Gmail, Outlook, or SMTP credentials.
3.  **Configure API:**
    - The workflow is pre-configured for `api.energidataservice.dk`.
    - If you need data for a specific region or meter, update the URL parameters in the **HTTP Request** node.
4.  **Test Run:** Click "Execute Workflow" to ensure the file is generated and sent correctly.
5.  **Activate:** Toggle the workflow to **Active**.

---

## ✨ How To Customise

| Customization        | Method                                                                            |
| :------------------- | :-------------------------------------------------------------------------------- |
| **Change Frequency** | Edit the **Cron** node to run Daily, Monthly, or at specific hours.               |
| **File Format**      | Change the **Convert to File** node settings to output `.xlsx` instead of `.csv`. |
| **Add Branding**     | Modify the HTML body in the **Email** node to include your company logo.          |
| **Threshold Alerts** | Add an **IF Node** to only send reports if consumption exceeds a certain limit.   |

---

## ➕ Add-ons (Advanced)

- **Analytics Integration:** Connect to Power BI or Tableau to visualize the stored Google Drive data.
- **Slack/Teams Notifications:** Send a summary of the report directly to a chat channel.
- **Multi-Source Reporting:** Merge data from solar inverters or IoT sensors alongside the grid data.

---

## 📈 Use Case Examples

- **Compliance Reporting:** Automatically generate records for environmental and regulatory audits.
- **Operational Analytics:** Identify peak usage hours to optimize machinery or heating schedules.
- **Forecasting:** Feed the historical CSV data into an AI model to predict next week’s energy costs.

---

## 🧯 Troubleshooting Guide

| Issue                 | Possible Cause             | Solution                                                              |
| :-------------------- | :------------------------- | :-------------------------------------------------------------------- |
| **API Error 404/500** | EnergiDataService downtime | Re-try the execution; check the API status page.                      |
| **No File in Drive**  | Permission issues          | Ensure the Google account has "Editor" access to the folder.          |
| **Email Not Sending** | Credential mismatch        | Re-authenticate your Gmail/Outlook node in the credentials tab.       |
| **Empty Report**      | No data for selected range | Ensure the API query dates are calculated correctly in the Code node. |

---

## 📞 Need Assistance?

Need help integrating this with a specific energy meter or building a custom dashboard?

👉 **Contact WeblineIndia** — Expert automation partners for energy, IoT, and enterprise workflows.
