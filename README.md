
# Real-Time Threat Detection SIEM on the Elastic Stack

A small-scale Security Information and Event Management (SIEM) system that detects network attacks in near real time, combining rule-based detection with a machine learning layer, and ranking attackers by risk on a live dashboard.

## Overview
Security teams need to catch attacks hidden inside large volumes of network data. This project builds an end-to-end SIEM using the free Elastic Stack (Elasticsearch, Logstash, Kibana, Filebeat), running in Docker. It ingests data from two sources, detects attacks using both threshold rules and a trained Random Forest model, and combines all detections into a risk score per attacker IP.

## Status
Early-stage proposal. Development in progress.

## Author
Mohamed Riad Lahrichi — B.S. Computer Science (Big Data Analytics), Al Akhawayn University
Supervisor: Dr. Driss Kettani
