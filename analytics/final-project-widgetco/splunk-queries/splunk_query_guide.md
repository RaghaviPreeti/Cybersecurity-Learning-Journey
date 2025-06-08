# Splunk Query Guide – Final Project (WidgetCo)

This document summarizes and explains the `.spl` files used to extract and correlate data during the WidgetCo breach investigation. Each query was written to support timeline building, user behavior analysis, and IOC matching using Splunk.

<div align="center">

----- [ Section Break ] -----

</div>

> **Data Sources Used:**
> - `mfa.csv`
> - `vpn.csv`
> - `passwordvault.csv`
> - `widgetapp.csv`
> - `ticketing.csv`
> - `itadmin.csv`
> - `dns.csv`
> - `IOC_lookup_URL_file.csv`

<div align="center">

----- [ Section Break ] -----

</div>

## 📁 bdvrls_queries.spl

### 🎯 Focus:
Investigates the activity of user `BDRVLS` across:
- Multifactor authentication logs (`mfa.csv`)
- VPN connections (`vpn.csv`)
- Password vault activity (`passwordvault.csv`)
- Internal app access (`widgetapp.csv`)

### 🔍 Key Techniques:
- Parsing `Date` and `Time` fields into a single `Date_Time` field
- Sorting events chronologically
- Extracting critical metadata like source IP, authentication status, application name, and access results

<div align="center">

----- [ Section Break ] -----

</div>

## 📁 dddxub_queries.spl

### 🎯 Focus:
Tracks activity of user `DDDXUB` across a broader range of sources:
- Same logs as BDRVLS
- Additional files: `ticketing.csv` and `itadmin.csv`

### 🔍 Highlights:
- Deeper coverage into user behavior, including:
  - Sent tickets
  - System login/logout events
- Queries include multiple `eval` and `strptime` steps to normalize time formats for correlation

<div align="center">

----- [ Section Break ] -----

</div>

## 📁 dns_ioc_matching.spl

### 🎯 Focus:
Matches DNS activity logs against known malicious indicators of compromise (IOCs)

### 🔍 Key Logic:
- Normalizes DNS Hit values with `lower()`
- Joins with `IOC_lookup_URL_file.csv` via `lookup`
- Filters out null results to isolate confirmed matches
- Returns machine names and dates where known IOCs were contacted

<div align="center">

----- [ Section Break ] -----

</div>

## 📌 Notes:

- All timestamps were converted using `strptime()` and `strftime()` for consistent event correlation.
- Sorting by `Date_Time` ensures accurate timeline reconstruction.
- Splunk queries were structured to clearly reflect user roles and the stages of breach activity.

<div align="center">

--- 🔹🔹🔹 End of Section 🔹🔹🔹 ---

</div>

