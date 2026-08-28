# WPF App Health & Crash Monitor

A personal project to help better understand how to use Grafana, built around a multi-view WPF dashboard tool that monitors application health and crash events in real time.

## Project Overview

This project combines a **WPF desktop application** with a **Grafana observability stack** to demonstrate end-to-end crash monitoring and diagnostics.

### WPF Application

- A multi-view WPF dashboard (e.g., a system monitor or file sync manager) that simulates real-world workloads.
- Intentionally triggers specific exceptions to generate meaningful telemetry:
  - **Network dropouts** – simulated connectivity failures.
  - **IO errors** – file read/write failures and permission errors.
- Structured logs are emitted for every event (normal operations, warnings, and exceptions) and shipped to a log aggregation backend (e.g., Loki).

### Grafana Dashboard

A Grafana dashboard visualises:

| Panel | Description |
|-------|-------------|
| **Crash Rate** | Rate of unhandled exceptions over time, broken down by exception type. |
| **System Resource Usage** | CPU, memory, and disk metrics collected from the host while the WPF app runs. |
| **LogQL Alerts** | Targeted LogQL queries that fire alerts when error thresholds are exceeded (e.g., > N IO errors per minute). |

## Tech Stack

- **Frontend:** WPF (.NET / C#)
- **Logging:** Structured logging shipped to Grafana Loki
- **Metrics:** Prometheus (or Windows Exporter) → Grafana
- **Visualisation:** Grafana dashboards with LogQL and PromQL queries
- **Alerting:** Grafana Alerting with LogQL-based alert rules 
