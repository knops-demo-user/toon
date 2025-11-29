# Scaling & Performance Limits: Mercur

## Current Limits
Known scaling thresholds for Mercur are primarily determined by server capacity and database limitations. The system can support up to 10,000 concurrent users before requiring additional resources or adjustments. For data storage, the system effectively manages up to 2 TB in its current configuration, beyond which database performance may degrade without optimization.

## Performance Bottlenecks
Identified constraints include:
- **Database Load:** High read and write operations during peak usage can lead to latency.
- **Network Bandwidth:** Limited bandwidth in certain regions can affect data transfer rates.
- **CPU and Memory Usage:** During intensive computation tasks, CPU spikes can cause delays in response times.

## Rate Limits & Quotas
API rate limits are set to 1000 requests per minute per user to ensure fair resource allocation and prevent abuse. User quotas include a maximum of 5 concurrent connections to the API and a daily data retrieval cap of 10 GB.

## Caching Strategy
Mercur employs a multi-layer caching strategy:
- **In-memory Caching:** Frequently accessed data is stored in-memory using Redis to minimize database queries.
- **Content Delivery Network (CDN):** Static assets are cached at the edge to reduce server load and improve load times.

## Scaling Approach
Mercur utilizes both horizontal and vertical scaling.
- **Horizontal Scaling:** Primarily used to manage increasing user loads by adding more servers, particularly during peak usage times.
- **Vertical Scaling:** Implemented by upgrading existing server resources (e.g., CPU, RAM) to maintain performance without adding complexity.

## Monitoring & Alerts
Performance monitoring is set up using a combination of tools:
- **Prometheus:** For real-time metrics collection and monitoring system health.
- **Grafana:** To visualize metrics and track performance trends over time.
- **Alertmanager:** Configured to send alerts via email and SMS in case of critical performance issues, such as server downtime or threshold breaches.