Threat Investigation Report
Incident ID: SOC-004 Date:11/03/2026 Analyst: Joshua Sigley

VirusTotal Analysis

1. Alert Summary
Suspicious URL was identified and submitted for threat analysis using VirusTotal.

The URL returned a compressed ZIP file hosted on a direct IP adress rather than a domain name, which is commonly associated with malicious infrastructure used for malware deliery.

The purpose of this investigation is to determine whether the URL is potentioally malicious and identify indicators of compromise.

Example: A suspicious phishing email containing a malicious link was identified.

2. Initial Indicators
Indicator | Type http://115.60.252.46:35776/i | suspicious URL 115.60.252.46 | IP address application/zip | File type

200 OK | status
3. Investigation Process
URL Analysis
the suspicious URL was submitted to VirusTotal for secuirty analysis URL analysed: http://115.60.252.46:35776/i

Observations:

Resource returns a ZIP archive
the server reponds successfully with HTTP 200
the file appears to be directly downloadable
Using an IP address instead of a domain name is commonly used by attacker to bypass domain reputation filtering.

Sandbox Analysis55454545454545454545455454545
Tool Used: ANY.RUN / Hybrid Analysis

Observed behaviour:

process creation
network connections
file downloads
Threat Intelligence
Tools used:

VirusTotal
Results: 1/95 security vendrs flagged the URL as malicious community score: -11

Vendor classification:

Malicious / Suspicious

GreyNoise: Malicious
SOCRadar: Suspicious
URLQery: suspicious
Clean detections from multiple vendors

Although the detection ratio is low, the negative community score and suspicious infrastructure indicators increase the likelyhood of malicious activity.
4. MITRE ATT&CK Mapping
Technique | Description T1205 | Ingress tool transfer T1566 | Phishing T1204 | User execution Explanation: attackers frequently distribute malware through compressed files delivered via malicious URLs that require the user to download and execute payload.
5. Indicators of Compromise
IOC | Type 115.60.252.46|IP adress http://115.60.252.46:35776/i | URL

6. Remediation Actions
Recommended defensive actions:

• blocked outbound traffic to IP 115.60.252.46 • scan endpoints for doanloaded ZIP files associated with this URL • alert users regarding suspicious file downloads

7. Conclusion
The analysed URL demonstrates serveral characteristics associated with malicious infrastrucure including direct IP hosting and compressed payload delivery.

while only one vendor currently flags the resource malicous, the behaviour indicators suggest the link could be user for malware distribution.

blocking the IP address and monitoring related traffic is recommended as a precautionary defensive measure.


