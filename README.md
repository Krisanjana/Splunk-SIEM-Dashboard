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

- Total SSH Events
- Click on Add Panel
- Under New, choose Single Value
- Use Shared Time Picker time_range
- Set Content Title to "Total SSH Events"
- Enter the Search String as below


  markdown
  source="ssh_logs.json" host="LinuxServer" sourcetype="_json"
 | stats count AS "Total SSH Events"




