# Smart Home Cyber-Attack Detection

## Introduction  
This project is a **Smart Home Cyber-Attack Detection System** built using **Python**, designed to identify anomalous behavior in a smart building environment based on predefined rules and event logs. 

The project was developed for **EN4720 - Security in Cyber-Physical Systems** and includes detection mechanisms for failed logins, toggle spam, power anomalies, session hijacking, and flagged source monitoring. 

📄 **Report PDF**: `Cyber_Milestone_IV.pdf`  
📓 **Simulation Code**: `anomalydet_realistic1.ipynb`  
📆 Available since **June 1st, 2025**

## Features
- **Anomaly Detection**
  - Failed login attempts
  - Geographically unrealistic logins
  - Toggle spam and device overload
  - Power usage spikes and invalid readings
  - Session hijacking and long-idle sessions
  - Detection of previously flagged users and IPs

## Detection Logic
### 1. Failed Login Detection
#### **Triggered when:**
- More than 5 failed logins in 60 seconds
- Logins from multiple countries with unrealistic time gaps

### 2. Toggle Spam & Device Overload
#### **Triggered when:**
- More than 10 toggles in 30 seconds
- Device accessed by >5 unique users (critical) or >10 (non-critical) in 10 seconds
- Conflicting toggle states (e.g., "on" to "off" rapidly)

### 3. Power Anomaly Detection
#### **Triggered when:**
- Reading is 0 or negative
- Reading exceeds 150% of recent 20-sample average during off-hours

### 4. Session Hijacking & Duration
#### **Triggered when:**
- A session is accessed from >1 IP in 60 seconds
- Sessions idle for over 12 hours and running over allowed duration

### 5. Flagged User/IP Detection
#### **Triggered when:**
- Any action is initiated by a user or IP previously flagged

## Simulation Functions
Testing was done via Python simulations using the following:

```python
sim_normal_use(user_id, user_ip)
sim_failed_login(user_id, user_ip)
sim_location_anomaly(user_id, [ip1, ip2])
sim_toggle_spam(user_id, role, user_ip)
sim_power_spike(user_id, user_ip, base=1000, spike=2000)
sim_admin_behavior(admin_id, admin_ip, hour=22)
sim_session_hijack("sesh_hijack")
sim_flagged_source(user_id, user_ip) 
```
## Sample Log Output

```pgsql
Too many failed login attempts for malicious
Device toggled too frequently by spammer
Power spike (2500) exceeds 150% of avg (1187.50)
Session hijacking suspected for session ‘sesh_hijack’ used from multiple IPs
Unrealistic login locations for geo_user: US to UK in 0.00 hours
Activity from previously flagged source: flagged_user / 192.168.13.69
```
## Repository
🔗 **GitHub Repository:** [https://github.com/thisariii01/Cyber-Attack-Detection](https://github.com/thisariii01/Cyber-Attack-Detection)

## Contributors
- 🧙‍♀️**Amarasekara A.T.P.** ([https://github.com/thisariii01](https://github.com/thisariii01))
- 🧙‍♂️**Bandara D.M.D.V.** ([https://github.com/D-Vinod](https://github.com/D-Vinod))
- 🧙‍♂️**Samarasekera A.M.P.S.** ([https://github.com/PaSe-Sam](https://github.com/PaSe-Sam))
- 🧙‍♂️**Wijetunga W.L.N.K.** ([https://github.com/namiwijeuom](https://github.com/namiwijeuom})
  
## License `WTFPL`
Feel free to use, modify, and share this code however you like!

---
**Appare Vestigium! 🧙‍♂️✨** Let every anomaly leave a trace — and may none go unnoticed.

