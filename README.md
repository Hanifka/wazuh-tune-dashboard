# Wazuh Noisy Alerts Dashboard

A Wazuh dashboard to find which rules create the most noise and which ones are safe to tune.

<img width="1901" height="622" alt="Screenshot 2026-09-17 204757" src="https://github.com/user-attachments/assets/575f87f5-e010-43d6-bf7c-e7de6c8591cb" />


## What's inside

| Panel | Type | What it shows |
|---|---|---|
| Noise Pareto: Tuning Impact | Vega | Rules ranked by volume, with cumulative share of all alerts |
| Top 10 alerts by description | Pie | Share of the top 10 rules |
| Table Most Triggered | Table | Rule ID, description, level and count |
| Top Noisy Agents | Bar | Agents with the most alerts |
| Top Noisy Agents with rule levels | Bar | Agent volume split by rule level |
| Alerts grouped by hours | Histogram | Alert volume per hour of day |
| Rule Burst Heatmap (z-score) | Vega | Volume spikes against each rule's own baseline |
| Noise vs Severity: Tuning Quadrant | Vega | Rules split into keep, investigate, tune first and low priority |

## Requirements

- Wazuh dashboard with Vega visualizations enabled
- Index pattern `wazuh-alerts-*` with time field `timestamp`

## Install

1. Open **Dashboards Management > Saved objects**
2. Click **Import** and select `export.ndjson`
3. If asked about conflicts, choose **Overwrite**
4. Open the dashboard **Detecting Noisy Alerts**

The export includes its own `wazuh-alerts-*` index pattern. If you already have one, remap the visualizations to it during import.

## How to read it

- **Level 6 and below with high volume:** tuning candidate
- **Level 7 and above:** review before tuning
- **Bright cells in the heatmap:** a burst, check it before silencing the rule
- Prefer tuning by field (process path, user, agent) or frequency over disabling a rule

## Tested on

Wazuh `4.*`


