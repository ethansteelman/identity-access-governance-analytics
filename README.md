# Identity & Access Governance Analytics

> **End-to-end access governance and threat-detection project** utilizing Python for ETL and Power BI for role-based access modeling (RBAC), privilege-creep remediation, and maintenance prioritization.

*A semester-long data analytics project analyzing physical and logical access datasets provided by OG&E to the University of Oklahoma.*

---

## Executive Summary & Problem Context

* **The Challenge:** Enterprise infrastructure systems often struggle with fragmented physical security logs and sprawling logical access rights. Over time, role changes and lack of centralized auditing lead to security vulnerabilities, operational inefficiencies, and significant privilege creep.
* **The Solution & Key Outcomes:**
  * **Unified Access Model:** Architected a standardized Role-Based Access Control (RBAC) model covering **80% of the employee population** under least-privilege profiles.
  * **Privilege Creep Mitigation:** Flagged anomalous accounts, lingering elevated privileges, and disconnected user-role assignments for immediate auditing.
  * **Physical Security & Maintenance:** Pinpointed high-traffic physical access points requiring prioritized preventive maintenance and identified redundant card-swipe points for decommissioning.
  * **Anomaly Detection:** Isolated unusual access attempts, after-hours physical entries, and logical permission outliers using statistical flags.

---

## Architecture & Workflow

### 1. Extraction & Preparation (Python / Pandas)
* Cleaned, formatted, and reconciled multi-source physical badge swipe logs and Active Directory/HR records using **Python (pandas)** in Google Colab.
* Handled missing timestamps, deduplicated access records, and standardized role/department nomenclature.

### 2. Semantic Modeling (Power BI)
* Ingested processed datasets into **Power BI** to construct an optimized **Star Schema**.
* Established relational integrity between fact tables (access logs) and dimension tables (users, physical locations, logical systems, and entitlement levels).

### 3. Analysis & Metrics (DAX)
* Engineered custom **DAX measures** to quantify profile overlap, flag inactive high-privilege credentials, and calculate least-privilege coverage percentages.
* Built threshold alerts to dynamically classify accounts into tiered risk profiles.

### 4. Executive Delivery & Stakeholder Presentation
* Built an interactive, role-based dashboard suite delivering targeted, drill-through insights for security administrators and infrastructure executives.
* Formally presented analytical findings and strategic policy recommendations to an audience of over **50 OG&E analysts, executives, and University of Oklahoma faculty**.

---

## Visual Portfolio: Physical Infrastructure & Reader Analytics

The dashboard suite was built around modular, recommendation-driven report pages designed to give stakeholders immediate, actionable insights on specific recommendations.

While the overall team deliverable encompassed both physical and logical access layers, the dashboards below highlight my direct analytical deliverables. Throughout the project, I focused on physical security, foot-traffic distribution, and hardware maintenance prioritization.

### 1. Badge Reader Usage By Population & Density
![Reader Usage by Population](dashboards/screenshots/reader_usage_by_population.png)
* **Business Objective:** Identify badge readers accessed by a disproportionate share of the employee base to evaluate operational redundancy, recommend preventative maintenance or targeted security improvements, and pinpoint physical security choke points.
* **Key Analytical Insights:** Isolated the top 20 most commonly utilized access points across the enterprise footprint, discovering that the single highest-traffic reader processed badge events for over 16% of the entire employee base. These 20 readers represent prime single-point-of-failure risks, primary targets for physical tailgating/camouflage vulnerabilities, and candidates for throughput optimization.
* **Technical Implementation & Core Metrics:** Engineered DAX measures calculating distinct employee counts per physical reader `DISTINCTCOUNT` divided by the total active population to calculate the usage rate of each badge reader, displaying reader traffic via `Top-N` visual filters in Power BI.

### 2. Most Active Badge Readers
![Most Active Readers](dashboards/screenshots/most_active_readers.png)
* **Business Objective:** Analyze physical access event volumes across devices and operating hours to identify readers subject to high levels of wear-and-tear, detect potential volume-based security attacks (such as brute-force entry attempts, credential flooding, or denial-of-service disruptions), and strip away anomaly camouflage.
* **Key Analytical Insights:** Isolated the top 10 readers by sheer volume of access events as potential targets for maintenance and security reinforcements. Additionally, analyzed aggregate access events by time of day to uncover a baseline for standard business hours.
* **Technical Implementation & Core Metrics:** Aggregated raw access event logs using `COUNTROWS` to rank hardware utilization across a Top-10 bar chart, paired with a temporal line chart binning event timestamps by time of day (hh:mm). Configured dynamic KPI cards to display aggregate event volume and isolate the highest-throughput reader.

### 3. Redundant Badge Readers
![Most Active Readers](dashboards/screenshots/redundant_readers.png)
* **Business Objective:** 
* **Key Analytical Insights:**
* **Technical Implementation & Core Metrics:**

### 4. Anomalous Usage/Threat Identification
![Most Active Readers](dashboards/screenshots/anomalous_usage.png)
* **Business Objective:**
* **Key Analytical Insights:**
* **Technical Implementation & Core Metrics:**

