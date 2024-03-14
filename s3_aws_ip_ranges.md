# To count aws s3 ips follow below scripts it will be give you all aws s3 ips

The issue you're facing is that the IP ranges for AWS services are not static and can change over time. The ip-ranges.json file you're using is a static snapshot of the IP ranges, which means it won't be updated automatically.

To get the latest IP ranges, you need to download the ip-ranges.json file from the AWS IP ranges URL:

import requests

url = "https://ip-ranges.amazonaws.com/ip-ranges.json"
response = requests.get(url)

if response.status_code == 200:
    with open('ip-ranges.json', 'w') as f:
        f.write(response.text)
else:
    print("Failed to download the IP ranges file")


After downloading the latest ip-ranges.json file, you can run your extract_ips.py script again to get the latest IPv4 and IPv6 prefixes.

Here's the complete code:


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



This will print out the latest IPv4 and IPv6 prefixes for all AWS services, including S3.

Note that the IP ranges for S3 are not specific to a particular bucket, but rather to the S3 service as a whole. If you want to restrict access to a specific S3 bucket, you should use an IAM policy or a bucket policy instead of IP-based restrictions.
