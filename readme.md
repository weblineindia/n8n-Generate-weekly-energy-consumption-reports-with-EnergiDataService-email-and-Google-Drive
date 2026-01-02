# Generate Weekly Energy Consumption Reports with API, Email and Google Drive

This workflow automates the process of retrieving energy consumption data, formatting it into a CSV report, and distributing it every week via email and Google Drive.

---

## ⚡ Quick Implementation Steps

- Import the workflow into your n8n instance.
- Configure your API, email details and Google Drive folder.
- (Optional) Adjust the CRON schedule if you need a different time or frequency.
- Activate workflow — automated weekly reports begin immediately.

---

## Who’s It For

Energy providers, sustainability departments, facility managers, renewable energy operators.

---

## Requirements

- n8n instance
- Energy Consumption API access
- Google Drive account
- Email SMTP access

---

## ⚙️ How It Works

The workflow triggers every Monday at 8:00 AM, fetches energy consumption data, converts it into a CSV file, emails the report, and uploads a copy to Google Drive.

---

## Workflow Steps

### 1. Schedule Weekly (Mon 8:00 AM)

- **Type:** Cron Node
- Runs every Monday at 8:00 AM.
- Triggers the workflow execution automatically.

---

### 2. Fetch Energy Data

- **Type:** HTTP Request Node
- Makes a GET request to the Energi Data Service API.
- Returns JSON data with hourly electricity consumption.

Example API:

```
https://api.energidataservice.dk/dataset/ConsumptionDE35Hour
```

Sample Response:

```json
{
  "records": [
    {
      "HourDK": "2025-08-25T01:00:00",
      "MunicipalityNo": 101,
      "MunicipalityName": "Copenhagen",
      "ConsumptionkWh": 12345.67
    }
  ]
}
```

---

### 3. Normalize Records

- **Type:** Code Node
- Extracts the `records` array and converts each record into a separate item.

```javascript
const itemlist = $input.first().json.records;
return itemlist.map((r) => ({ json: r }));
```

---

### 4. Convert to File

- **Type:** Convert to File Node
- Converts JSON data into a CSV file.
- Stores the file in binary format.

---

### 5. Send Email Weekly Report

- **Type:** Email Send Node
- Sends the CSV file as an email attachment.
- Subject: **Weekly Energy Consumption Report**

---

### 6. Upload Report to Google Drive

- **Type:** Google Drive Node
- Uploads the CSV file to Google Drive.
- Example filename:

```
energy_report_{{ $now.format('yyyy_MM_dd_HH_mm_ss') }}
```

---

## ✨ How To Customize

- Change the schedule (daily, monthly).
- Modify email subject or body.
- Convert CSV to Excel or PDF.
- Add Slack or Teams notifications.

---

## ➕ Add-ons

- Power BI / Tableau integration
- PDF or Excel reports
- Slack alerts

---

## Use Case Examples

- Weekly compliance reports
- Energy usage tracking
- Forecasting and analytics

---

## Troubleshooting

| Issue          | Cause             | Solution                  |
| -------------- | ----------------- | ------------------------- |
| No data        | API issue         | Verify API URL            |
| Email not sent | SMTP config       | Check email credentials   |
| Upload failed  | Drive permissions | Check Google Drive access |

---

## Need Assistance?

Contact **WeblineIndia** for customization and support.
