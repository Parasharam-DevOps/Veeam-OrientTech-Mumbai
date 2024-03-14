# AWS S3 IP Range Extraction

## Introduction

This script is designed to extract the IP ranges associated with AWS S3 (Simple Storage Service). This issue arises when connecting Veeam to an S3 object storage repository job in AWS, and the network team has blocked the traffic. They require specific ports, prompting the need for IP ranges. Security concerns dictate that not all traffic can be allowed, hence the need for specific IP ranges.

## How to Use

### Prerequisites
- Python3
- Jq   [Link](https://www.scaler.com/topics/linux-jq/)
       [Link](https://github.com/jqlang/jq/releases/tag/jq-1.6)

### Steps
1. Download the latest `ip-ranges.json` file from AWS.
2. Run the `extract_ips.py` script to extract the IPv4 and IPv6 prefixes.
3. Use the extracted IP ranges for configuring security rules and policies.

### Script

**ip-ranges.json**

```
import requests

url = "https://ip-ranges.amazonaws.com/ip-ranges.json"
response = requests.get(url)

if response.status_code == 200:
    with open('ip-ranges.json', 'w') as f:
        f.write(response.text)
else:
    print("Failed to download the IP ranges file")


```

**extract_ips.py**

```

import json
import requests

# Download the latest ip-ranges.json file
url = "https://ip-ranges.amazonaws.com/ip-ranges.json"
response = requests.get(url)

if response.status_code == 200:
    with open('ip-ranges.json', 'w') as f:
        f.write(response.text)
else:
    print("Failed to download the IP ranges file")

# Load the JSON file
with open('ip-ranges.json', 'r') as f:
    data = json.load(f)

# Extract IPv4 addresses
ipv4_prefixes = data['prefixes']
for prefix in ipv4_prefixes:
    ip_prefix = prefix['ip_prefix']
    print("IPv4 Prefix:", ip_prefix)

# Extract IPv6 addresses
ipv6_prefixes = data['ipv6_prefixes']
for prefix in ipv6_prefixes:
    ipv6_prefix = prefix['ipv6_prefix']
    print("IPv6 Prefix:", ipv6_prefix)

```
# Note
AWS IP ranges are dynamic and subject to change. Regularly update the ip-ranges.json file.
IP ranges for S3 cover the entire service, not specific to individual buckets. Use IAM policies or bucket policies for bucket-specific restrictions.

# Resource

- **Blog I Refer**: [Link](https://docs.aws.amazon.com/vpc/latest/userguide/aws-ip-ranges.html)
