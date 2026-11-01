# Machine Learning Layer for al akhawayin University SIEM

An anomaly detection layer that sits next to an existing SIEM built on the Elastic Stack (Elasticsearch and Kibana). It reads firewall logs every 30 minutes, scores how unusual each source address behaves, and shows analysts a short, explained list of cases in Kibana.

This is my final-year capstone (B.S. Computer Science, Big Data Analytics). It is built for a real university IT team, so the code and data stay private. This page describes the project only.

## The problem

Rule-based detection misses behavior that no rule describes, and a noisy rule can bury analysts in alerts. The goal is to highlight what an analyst might miss, and to support their decision with reasons, without adding to the noise.

## What it does

- Reads each completed 30-minute window of firewall traffic (read-only).
- Builds a behavior profile per source address: connections, distinct destinations and ports, bytes sent, blocked connections.
- Scores how unusual each profile is against recent normal traffic, with no labeled attacks needed.
- Keeps only a limited number of new cases per day, one case per address per day.
- Explains each alert by showing unusual values next to their usual values.
- Keeps a score history per address and flags scores that keep rising.
- Retrains weekly, and only switches to a new model if it passes quality checks.
- Writes its own health report after every run.
- Never blocks traffic. A person always decides.

## Approach

1. Start with a simple statistical baseline (robust z-score).
2. Compare it against Isolation Forest, and keep the model only if it does better on known attacks.
3. Measure recall of known attacks, precision of the daily top alerts, and reliability over a full week.

## Status

In development, November 2026. Requirements are written and being validated with the client. The pipeline is being built step by step on invented data, then connected to the real SIEM. No results yet.

## Planned stack

Python, pandas, scikit-learn, Elasticsearch, Kibana.

## Author

Mohamed Riad Lahrichi
