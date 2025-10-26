# ☁️ Automated Weather Report Workflow with n8n

This repository contains the workflow file and documentation for an automated system built with [n8n](https://n8n.io/) that fetches and distributes regular weather reports.

***

## ✨ Overview

This n8n workflow is designed to run automatically, fetching the latest weather forecast for a specified location and delivering a structured report to a chosen destination.

| Detail | Value |
| :--- | :--- |
| **Automation Platform** | n8n |
| **Trigger Frequency** | **[e.g., Daily at 7:30 AM]** |
| **Weather API Used** | **[e.g., OpenWeatherMap, AccuWeather]** |
| **Report Destination** | **[e.g., Gmail, Slack, Telegram, Google Sheets]** |
| **Report Content** | [e.g., Today's Forecast, Min/Max Temperature, Wind Speed, UV Index] |

***
![outputimage](https://github.com/Mukesh77-code/Weather_mail/blob/a25c8dbe2b4f2a29fc6ac10d638def2896f18113/Screenshot%202025-10-26%20183048.png)
## 🖼️ Visuals

Here are screenshots of the workflow setup and the final output:

### 1. The n8n Workflow

A visual representation of the node-based automation flow.

****
![workflow](https://github.com/Mukesh77-code/Weather_mail/blob/f0048cd409d0ffba481045af345996fbad2f45d9/Screenshot%202025-10-26%20235057.png)

### 2. Example Report Output

This shows what the final automated report looks like when delivered.

****

**Note:** The file path for this image is: (https://github.com/Mukesh77-code/Weather_mail/blob/a25c8dbe2b4f2a29fc6ac10d638def2896f18113/Screenshot%202025-10-26%20183048.png)

***

## ⚙️ Workflow Structure

The workflow is saved in the included JSON file: `weather_report_workflow.json`

The key steps (nodes) in the workflow are:

1.  **`Schedule`** / **`Webhook`**: The starting node that triggers the execution.
2.  **`HTTP Request`**: Calls the **[Weather API Used]** API endpoint to retrieve raw weather data.
3.  **`Function`** / **`Set`**: Processes the raw JSON response, extracts key data points, and formats it into a clean message (e.g., HTML or Markdown for the final report).
4.  **`[Reporting Service Node]`**: The final step, which sends the formatted report.

***

## 🚀 Getting Started (Setup Guide)

Follow these steps to import and configure the workflow in your n8n instance.

### Prerequisites

You must have the following accounts and credentials ready:

1.  A running **n8n instance** (Cloud or Self-Hosted).
2.  An API Key for **[Weather API Used]**. ([Link to API documentation/sign-up page])
3.  Credentials for your report destination (e.g., **Gmail OAuth2** or **Telegram Bot Token**).

### Step 1: Import the Workflow

1.  Navigate to your n8n UI.
2.  Go to the **Workflows** section and click **Import from JSON**.
3.  Upload the `weather_report_workflow.json` file.

### Step 2: Configure Credentials

Set up the required credentials in n8n's **Credentials** section and assign them to the corresponding nodes:

| Node | Credential Type | Action Required |
| :--- | :--- | :--- |
| **`HTTP Request`** | [e.g., HTTP Query Auth] | Enter your **[Weather API Used]** API Key. |
| **`[Reporting Service Node]`** | [e.g., OAuth2 / Token] | Connect your **[Reporting Service]** account. |

### Step 3: Customize Parameters

Open the workflow and edit these nodes to personalize the report:

| Node | Setting to Change | Your Custom Value |
| :--- | :--- | :--- |
| **`Schedule`** | Time & Frequency | [e.g., Every 3 Hours, Monday-Friday at 8 AM] |
| **`HTTP Request`** | **Location Parameter** | Change `city=London` to `city=[Your City]` |
| **`[Reporting Service Node]`** | **Recipient/Channel** | [e.g., Your Email Address, Slack Channel ID] |

### Step 4: Activate and Test

1.  Click **Save** in the n8n workflow editor.
2.  Toggle the workflow **ON** to enable scheduling.
3.  Click **Test Workflow** to run a manual check and verify the report is sent correctly.

***

## Troubleshooting

| Issue | Potential Cause | Solution |
| :--- | :--- | :--- |
| **No report is sent.** | Workflow is inactive or credentials failed. | Ensure the workflow is **ON**. Check credentials in the final node output. |
| **Data is not updating.** | API rate limit reached or wrong location set. | Check the API documentation for usage limits. Verify the location parameter in the `HTTP Request` node. |
