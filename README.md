# Splunk-SIEM-Dashboard
A custom-built Security Information and Event Management (SIEM) dashboard designed to monitor, visualize, and analyze system logs, potential vulnerabilities, and security events in real time. Devel...



# 🔧 Features
- 🌙 Dark/Light Mode — Seamless toggle between light and dark UI for better accessibility and UX.
- 🌍 Geo-IP Blocking — Automatically blocks suspicious IPs based on geolocation data.
- 🛡️ Vulnerability Detection — Detects potential system vulnerabilities using pattern matching and custom scripts.
- 📈 Access Log Visualization — Displays real-time logs, source IPs, actions, and threat levels.
- 📊 Interactive Charts & Dashboard — Graphs and tables powered by Chart.js for visual security analytics.
- 🔐 Secure Salt Authentication — Login system protected using salted password hashing.

# Objective

# Lab Set up

# Task0: Setting up Time Range
- Add Time Range Button
- Click on Add Input
- Select Time and click on pencil icon
- Set Label to Time Range and Token time_range
- Again Add Input
- Select Submit
- Note: For all future panel, set the time to time_range for consistency.

# Project Demo
https://github.com/user-attachments/assets/3b7b162e-32b1-4a19-8005-bd6fb0a951a6

# Task1: Authentication Overview Panels

## Goal: Give a quick summary of SSH activity.

### 1. Total SSH Events
- Click on Add Panel
- Under New, choose Single Value
- Use Shared Time Picker time_range
- Set Content Title to "Total SSH Events"
- Enter the Search String as below

  `source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json"
  | stats count AS "Total SSH Events"`
## Lad Img
<img width="1915" height="706" alt="image" src="https://github.com/user-attachments/assets/9a40522f-b8ce-4e86-a94d-6f9d10350188" />


### 2.Successful Logins
- Click on Add Panel

- Under New, choose Single Value

- Use Shared Time Picker time_range

- Set Content Title to "Successful Logins"

- Enter the Search String as below:

`source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json"  event_type="Successful SSH Login" | stats count AS "Successful Logins"`

## Lab Img
<img width="1911" height="715" alt="image" src="https://github.com/user-attachments/assets/09deedcb-675e-4b5a-8bf2-7ab30554bcec" />



### 3. Failed Logins
- Click on Add Panel
- Under New, choose Single Value
- Use Shared Time Picker time_range
- Set Content Title to "Failed Logins"
- Enter the Search String as below:

`source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json" event_type="Failed SSH Login" | stats count AS "Failed Login"`

## Lab Ing
<img width="1911" height="757" alt="image" src="https://github.com/user-attachments/assets/8395c68c-973c-40a4-9e00-190ec1e76c76" />

### 4. Connection without Authentication
- Click on Add Panel

- Under New, choose Single Value

- Use Shared Time Picker time_range

- Set Content Title to "Invalid User Attempts"

- Enter the Search String as below:

`source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json"  event_type="Connection Without Authentication" | stats count as "Connection Without Authentication"`

## Lab Img

<img width="1911" height="627" alt="image" src="https://github.com/user-attachments/assets/6adcdaa3-572d-4e42-8363-138cfd75cc35" />



# Task2: Login Activity Trends 

## Goal: Visualize login behavior over time and detect spikes.

### 1. Failed Logins by username
- Click on Add Panel

- Under New, choose Bar Chart

- Use Shared Time Picker time_range

- Set Content Title to "Failed Logins by username"

- Enter the Search String as below:

`source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json" event_type="Failed SSH Login" | top username`

## Lab Img

<img width="1910" height="881" alt="image" src="https://github.com/user-attachments/assets/c21afca4-210d-49f4-8ca5-e4291489a2c7" />


### 2. Possible Brute Force
- Click on Add Panel

- Under New, choose Statstics Table

- Use Shared Time Picker time_range

- Set Content Title to Possible Brute Force b IP Address

- Enter the Search String as below:

`source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json" event_type="Multiple Failed Authentication Attempts" | top id.orig_h`

## Lab Img

<img width="1910" height="930" alt="image" src="https://github.com/user-attachments/assets/fe538a48-4388-4884-a05a-1f218d1799e4" />


# Task3: Visualizing Brute Force attack in geo-location

### 1. Visualizing Brute Force attack with geo-location
- Click on Add Panel

- Under New, choose Choropleth Map

- Use Shared Time Picker time_range

- Set Content Title to Brute Force attack with geo-location

- Enter the Search String as below:

`source="ssh_logs_new.json" host="Krisan_Jana" sourcetype="_json" event_type="Multiple Failed Authentication Attempts" 
| table id.orig_h
| iplocation id.orig_h
| stats count by Country
| geom geo_countries featureIdField="Country"`

## Lab Img

<img width="1912" height="968" alt="Screenshot 2026-08-29 160124" src="https://github.com/user-attachments/assets/c9011a40-a743-46e6-995c-00c31ce6c49c" />

# Over View All Dashboard Img

<img width="1912" height="972" alt="image" src="https://github.com/user-attachments/assets/cdcfd274-87b1-4e58-bcd9-70118ea234d1" />


