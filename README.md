### Real Time Event Processing platform
A system that ingests, processes, and monitors real-time user activity events through a streaming pipeline.

You simulate user-generated events (e.g., logins, page views), which are:

Published to Kafka topics

Consumed by backend services (Node.js)

Processed (validated, transformed)

Cached (temporarily in Redis if needed)

Stored in PostgreSQL for durability

Monitored via Prometheus + Grafana

Deployed with Docker on AWS EC2 using GitHub Actions

## Why This Project Matters to Businesses
  Real-World Applications:
  User behavior tracking (analytics, personalization)
  Monitoring app usage in real-time
  Security auditing (login patterns, anomalies)
  Business insights (what users do most often)
  Real-time alerting (e.g., too many failed logins)

## Business Impact:
Increases customer intelligence

Powers real-time dashboards for stakeholders

Improves system reliability and monitoring

Enhances security and fraud detection

## Event Types & JSON Schemas
 Here's starter schema for 5 event types:
 Base Event Structure
 
# Template
Copy code
{
  "eventId": "uuid-v4",
  "type": "login",  // or logout, page_view, etc.
  "timestamp": "ISO8601-UTC",
  "payload": { ... }
}
# Event Type: login


{
  "eventId": "a1b2c3",
  "type": "login",
  "timestamp": "2025-05-18T14:00:00Z",
  "payload": {
    "userId": "u123",
    "ip": "203.0.113.45",
    "device": "Chrome on macOS"
  }
}
# Event Type: logout


{
  "type": "logout",
  "payload": {
    "userId": "u123",
    "duration": 3600,  // in seconds
    "ip": "203.0.113.45"
  }
}
# Event Type: page_view

{
  "type": "page_view",
  "payload": {
    "userId": "u456",
    "page": "/dashboard",
    "referrer": "/login",
    "device": "Firefox on Linux"
  }
}
# Event Type: button_click

{
  "type": "button_click",
  "payload": {
    "userId": "u456",
    "buttonId": "download-report",
    "page": "/dashboard"
  }
}
# Event Type: form_submit

{
  "type": "form_submit",
  "payload": {
    "userId": "u789",
    "formId": "feedback-form",
    "fields": {
      "rating": "5",
      "comment": "Great app!"
    }
  }
## Architecture Diagram (Simplified View)
![output-onlinepngtools](https://github.com/user-attachments/assets/23260b62-0edb-43b1-a8ea-df44a1a914ed)



