# Logstash Project

## Overview
This project demonstrates my ability to configure Logstash for ingesting and parsing security log data. It includes a configuration to transform syslog-style FortiGate logs into structured JSON.
For this logstash project I have used Fortigate Firewall sample logs to demonstrate log normalization.

---

## Project Structure
- `input.log`: Contains the raw FortiGate syslog log samples.
- `parser.conf`: The Logstash configuration file used to parse and normalize logs.
- `output.json`: Sample output from Logstash showing the normalized JSON structure.
- `output_dhcplog.json`: Sample output from Logstash showing the normalized JSON DHCP log structure.
- `output_systemuser_log.json`: Sample output from Logstash showing the normalized SystemUser log JSON structure.
- `output_trafficlog.json`: Sample output from Logstash showing the normalized Traffic log JSON structure.
- `output_vpnlog.json`: Sample output from Logstash showing the normalized VPN log JSON structure.
- `README.md`: This file — describes the approach and configuration.

---

## How It Works

### Ingestion
- Input Plugin: The `file` input plugin reads from `input.log`.

### Filtering
- Filter Plugin: The `grok` plugin is used to match and extract key fields from the raw syslog format.
- Mutate Plugin: Removes unnecessary fields like `host`, `log`, etc., to keep the output clean.

### Output
- **Output Plugin**: The `file` output plugin writes the normalized JSON to `output.json`.

---

## Normalization Design
The configuration is designed to:
- Support any log line with the same format.
- Extract values like `source_ip`, `destination_ip`, `action`, `timestamp`, etc., into clearly defined fields.
- Maintain flexibility to adapt to new log values without changing the grok pattern drastically.
