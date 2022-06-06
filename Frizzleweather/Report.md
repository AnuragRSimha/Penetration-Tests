# Penetration Test Report
Date: 5<sup>th</sup> June, 2022.
## Title
Denial of Service (DOS) attack on frizzleweather.com

## Description
### The Issue
The website, frizzleweather.com is vulnerable to the Denial of Service attack. 

### About the attack
The DOS attack, made possible by _**Slowloris**_, is mighty enough to keep the website down, hence antagonising the users from browsing the website. With more than 500 sockets sent at once, partial (incomplete) HTTP requests are transmitted perenially, persuading the server to keep the connection open awaiting completion. Consequently, the server remains overwhelmed by the overflow of a plethora of these incompletely crafted HTTP requests and remains unavailable. This version of the attack is an _Application-layer attack_.

## Affected Component
The web server is scathingly affected by the severity of the attack.\
Affected URL: http://frizzleweather.com/

## Affected Users
The end users/clients of this website remain deliberately impacted by the unresponsive website.

## Steps to Reproduce
1. Analysing the network traffic
2. Monitoring traffic
3. Firewall
4. DMZ (**D**e**M**ilitarised **Z**one)
5. All requests processed over HTTPS only

## Criticality
### Impact
1. Loss of Availability: All services completely lost (Degree = 9)
2. Reputation Damage: Brand damage (Degree = 9)
### Likelihood
1. Likelihood = High (Degree = 7.375)
2. Severity = Critical

## Exploitation Complexity
It's facile to exploit the vulnerability with _Slowloris_. But, the attacker must gain the IP address to the website first, and keep Slowloris installed on the machine.

## Overall Severity
### Threat agent factors (TAF)
1. Skill Level = 9
2. Motive = 4
3. Opportunity = 7
4. Size = 9
### Vulnerability factors (VF)
1. Ease of discovery = 7
2. Ease of exploit = 9
3. Awareness = 6
4. Intrusion Detection = 8

> ∴ Overall Likelihood = \
![equation](https://latex.codecogs.com/svg.image?\bg{white}=\frac{\sum&space;TAF&space;&plus;&space;\sum&space;VF}{\sum&space;no.&space;of&space;factors})\
![equation](https://latex.codecogs.com/svg.image?\bg{white}=\frac{(9&plus;4&plus;7&plus;9)&plus;(7&plus;9&plus;6&plus;8)}{8})\
= 7.375 = High

### Technical Impact (TE)
1. Loss of Confidentity = 6
2. Loss of intergrity = 3
3. Loss of Availability = 9
4. Loss of Accountability = 7

### Business Impact (BE)
1. Financial Damage = 3
2. Reputation Damage = 9
3. Non-Compliance = 2
4. Privacy Violation = 0

> Overall Technical Impact (OTI) \
![equation](https://latex.codecogs.com/svg.image?\bg{white}=\frac{\sum&space;TE}{\sum&space;no.&space;of&space;factors}) 
![equation](https://latex.codecogs.com/svg.image?\bg{white}=\frac{(6&plus;3&plus;9&plus;7)}{4}) \
= 6.25 = High

> Overall Business Impact (OBI) \
![equation](https://latex.codecogs.com/svg.image?\bg{white}=\frac{\sum&space;BE}{\sum&space;no.&space;of&space;factors}) 
![equation](https://latex.codecogs.com/svg.image?\bg{white}=\frac{(3&plus;9&plus;2&plus;0)}{4}) \
= 3.5 = Medium

Hence,\
Severity (Technical Impact) = Likelihood $\times$ Risk = High × High = Critical\
Severity (Business Impact) = High × Medium = High 

## CVSS Score
**CVSS Base Score = 8.6**\
Impact Subscore = 4.7\
Exploitability Subscore = 3.9\
**CVSS Temporal Score = NA**\
CVSS Environmental Score = 9.7\
Modified Impact Subscore = 5.8\
**Overall CVSS Score = 9.7**\
(CVSS: AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:L/A:H/CR:X/IR:X/AR:H/MAV:N/MAC:L/MPR:N/MUI:N/MS:U/MC:L/MI:L/MA:H)

## Tools Used and Setup Required
1. Use ufw.
2. Setup a DMZ.
3. Keep Wireshark always on.
4. Monitor and analyse packets.

## Prerequisites
The attacker must have a well established internet connection, and Slowloris tool installed.

## Additional Information
Date of the attack: 9<sup>th</sup> May, 2022.\
Website IP: 65.1.190.134\
Weakness: CWE-400 (Uncontrolled Resource Management)\
Tool used: Slowloris\
Commands:\
_(Capture the IP)_\
`dig frizzleweather.com`\
_(Launch the attack simultaneously on four or more terminals)_\
`slowloris 65.1.190.134 -s 500`

## Suggested Fixes
1. Install a firewall.
2. Implement DMZ.
3. Upgrade to HTTPS.
