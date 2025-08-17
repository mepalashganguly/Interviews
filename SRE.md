## SRE's

<a name="SRE's"></a>

<details>

<summary>1.1 - SLA Vs SLOs Vs SLI?</summary><br><b>
1. SLA – Service Level Agreement
What it is: A formal, legally binding contract between a service provider and a customer that specifies measurable service commitments (e.g., 99.9% uptime, 1-hour ticket response, etc.) and the consequences if they’re not met (like service credits or penalties).

Audience: Customers, legal/business teams, service provider.

Implication: SLA violations usually result in financial or contractual penalties and affect trust.

2. SLO – Service Level Objective
What it is: A specific, measurable internal goal set by the service provider to help ensure SLA commitments are met. An SLO is generally a target percentage or threshold (e.g., “99.95% of requests in a month must complete under 300ms”).

Audience: Engineering/operations teams.

Implication: SLOs guide operations, reliability engineering, and trigger corrective actions when not met—no direct legal penalty, but often prompt process reviews or feature freezes.

3. SLI – Service Level Indicator
What it is: A quantitative metric or measure of service performance; it’s the actual value recorded (e.g., measured uptime for the past 30 days or average response time).

Audience: Technical/development teams, monitoring, and operations.

Implication: SLIs are the raw data points that show if SLO targets (and thus SLA obligations) are being met. For example, if SLO is 99.9% availability, SLI might record actual availability of 99.87% for last month.

<img width="739" height="347" alt="Screenshot 2025-08-13 at 1 14 15 AM" src="https://github.com/user-attachments/assets/ebecd80f-fc7e-4dc8-a170-8738f412aac7" />
