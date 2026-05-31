# Integration Guide • Sovereign Shield – Zero‑Trust Anti‑Fraud Kernel

This document describes how to integrate Sovereign Shield into existing API infrastructures, including NGINX, Kong, Envoy, and generic API Gateway environments. The goal is to ensure that **all traffic** is evaluated by the Edge Enforcement Layer before reaching upstream services.

---

## 1. Integration Overview

Sovereign Shield is deployed as a **mandatory enforcement hop** between clients and your API gateway. It can operate in three modes:

- **Inline Mode (Strict)** – All traffic must pass through Sovereign Shield.  
- **Sidecar Mode** – Sovereign Shield runs next to the gateway and intercepts traffic.  
- **Plugin Mode** – Gateway plugins call Sovereign Shield for enforcement decisions.

The recommended production setup is **Inline Mode** for maximum security.

---

## 2. Integration Requirements

- Sovereign Shield must be reachable by the gateway with low latency.  
- Gateway must be configured to **reject any request** that bypasses Sovereign Shield.  
- Internal communication between Sovereign Shield and the gateway must be authenticated (HMAC or mTLS).  
- Kafka Revocation Mesh must be reachable from all Sovereign Shield nodes.

---

## 3. Integration Architecture

