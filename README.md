# AI-Powered Ad Campaign Reporting with n8n

An automated reporting workflow that processes ad campaign data, identifies campaigns with low click-through rates (CTR), generates AI-powered insights using a local Ollama model, and delivers a CSV report with an email summary.

## Overview

Marketing reports often involve repetitive tasks such as retrieving campaign data, calculating KPIs, filtering underperforming campaigns, preparing reports, and emailing stakeholders.

This project explores how **n8n workflow automation and local AI** can streamline that process, reducing manual reporting effort while making campaign insights easier to review.

## Workflow Architecture

![n8n Ad Campaign Reporting Workflow](https://github.com/Maira-Nawaz/Automate-Ad-Campaign-Reporting-with-n8n/blob/main/Automate%20Ad%20Campaign%20Reporting%20Workflow.jpg)

**Workflow:** Data Source → Data Transformation → CTR Filtering → AI-Generated Summary → CSV Report → Email Delivery

## Key Features

- **Automated data processing:** Retrieve campaign performance data and prepare it for analysis.
- **CTR calculation:** Calculate click-through rates using clicks and impressions.
- **Performance filtering:** Identify campaigns below a configurable CTR threshold.
- **AI-powered insights:** Use a locally hosted Ollama model to generate a concise summary of campaign performance.
- **CSV report generation:** Convert processed data into a downloadable report.
- **Automated email delivery:** Send the AI-generated summary alongside the CSV attachment.

## Technology Stack

| Technology | Purpose |
|---|---|
| n8n | Workflow automation and orchestration |
| Google Sheets | Campaign data source |
| Ollama | Local LLM inference |
| Gmail | Email report delivery |
| CSV | Structured report export |

## How It Works

### 1. Retrieve Campaign Data

The workflow reads ad campaign performance data from Google Sheets.

### 2. Calculate CTR

A new field is created to calculate the click-through rate:

`CTR = Clicks / Impressions`

The resulting ratio can be multiplied by 100 when displaying CTR as a percentage.

### 3. Filter Low-Performing Campaigns

Campaigns are filtered using a configurable CTR threshold so the report focuses on records that need further investigation.

The threshold is a configurable business rule, not a universal benchmark.

### 4. Generate AI Insights

The selected campaign data is passed to a local Ollama model, which generates a concise summary of the findings.

Using a local model provides an opportunity to experiment with LLM-powered reporting without relying on a paid hosted-model API. Local execution still requires appropriate hardware and configuration.

### 5. Generate a CSV Report

The processed campaign data is converted into CSV format for further analysis and sharing.

### 6. Merge and Deliver the Report

The workflow combines the AI-generated content with the report output and sends an email containing the summary and CSV attachment.

## Example Use Case

A marketing analyst needs to review campaign performance regularly.

Instead of manually calculating metrics, filtering campaigns, preparing a spreadsheet, and writing an email, this workflow automates the main reporting steps.

The result is a report designed to help stakeholders identify campaigns that may need attention and review the supporting data.

## Setup and Configuration

1. Set up an n8n instance.
2. Connect your Google Sheets account and configure the campaign data source.
3. Configure the CTR calculation and filtering logic.
4. Install and run Ollama, then download a compatible local model.
5. Configure the Ollama connection in your workflow.
6. Connect Gmail using n8n credentials.
7. Configure the CSV attachment and email fields.
8. Test each node and then run the complete workflow.

**Ollama connection note:** If n8n and Ollama run on the same machine, `http://localhost:11434` may be the appropriate API base URL. If n8n runs inside Docker or another environment, `localhost` may refer to that environment rather than the host machine, so the connection address may need to change.

## Current Status

The workflow has been built and tested in stages. A test email was successfully sent with an AI-generated summary and CSV attachment.

Further work is needed to improve AI email formatting and complete end-to-end validation across different inputs and failure scenarios.

## Potential Improvements

- Improve the structure and HTML formatting of AI-generated emails.
- Validate AI-generated claims against the source data.
- Handle missing values and zero impressions.
- Add error notifications and retry logic where appropriate.
- Schedule recurring reports.
- Test empty inputs, model timeouts, and email delivery failures.
- Add more campaign KPIs and configurable reporting thresholds.

## Key Learning Outcomes

- Designing multi-step workflows in n8n.
- Applying data transformation and conditional filtering.
- Integrating a locally hosted LLM into an analytics workflow.
- Combining structured data with AI-generated text.
- Generating CSV files and automating email delivery.
- Testing and validating AI-powered reporting workflows.

## Notes

This project is a learning and portfolio project. AI-generated summaries should be reviewed for accuracy before being used for business decisions or sent to stakeholders automatically.

---

**Built to explore the intersection of Data Analytics, Workflow Automation, and Generative AI.**
