# Carbon-Jar---SaaS-Technical-Test

# Question 10 - Caching DB Reads

I added Redis caching to avoid hitting the DB every time.  

I used a simple cache-aside pattern:
- First check Redis.
- If value is cached → return it.
- If not → read from DB → store in Redis with 60s TTL → return result.
Note: Redis server is not available in Colab, this is meant to be tested locally with Redis running.

# Question 14 - Log Anomaly Detection

I built a simple prototype for log anomaly detection:
- Used a rolling mean + std deviation.
- If response_time > mean + 3 * std → flagged as anomaly.

Printed alerts for any anomalies found.  
In real systems, I would add Isolation Forest or streaming pipeline.

Metrics and alerts can be sent to Grafana, Slack, etc.

# Question 15 - Lazy Loading

I used `React.lazy` and `Suspense` to lazy-load the HeavyAnalyticsDashboard.

This improves first page load time since the dashboard code is only loaded when needed.  
This also helps Lighthouse score.

Web Vitals I would monitor:
- LCP
- FID
- CLS

# Question 16 - Accessibility Fixes

I improved the HTML for accessibility:
- Added proper `<label>` for inputs.
- Replaced `<div>` with a real `<button>`, so it is keyboard-friendly.
- Added `aria-label` for better screen reader support.

This makes the form easier to use for everyone and compliant with WCAG 2.1.

# Question 18 - Adding Retries

I added retries to `call_flaky_service()` using the `tenacity` library with exponential backoff.

This helps the system handle temporary DB failures gracefully.

I also explained the circuit breaker pattern:
- If service is failing too often, block further requests temporarily.
- After cooldown, try again.

This prevents overload during big outages.


# Question 6 - API Observability

I added:
- A Prometheus counter `carbon_calculations_total` to track requests.
- An OpenTelemetry span on `/calculate` endpoint for tracing.

I would also use:
- Sentry for error reporting.
- Logs to Loki.
- Dashboards with Prometheus + Grafana.

# Question 5 - Secure Hybrid Cloud Connectivity

I compared VPN, Direct Connect, and VPC Peering.

For this case, I would use VPN as it is flexible and quick to set up.

Original security group was too permissive:
- Allowed all ports and all protocols.
- No logging.

I fixed it to allow only port 5432 (Postgres), limited CIDR range, and added VPC flow logs for audit.






