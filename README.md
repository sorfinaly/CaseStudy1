# Case Study 1 Report

## i. Group Name
- Group Name: Blue

## ii. Group Member Details
1. **Nadirah Binti Ros Liza** - Matric No: 2027832
2. **Sorfina Alyia Binti Jazrry** - Matric No: 2017326

## iii. Assigned Tasks

| Name           | Task                 |
|----------------|----------------------|
| Nadirah        | Task 1               |
| Sorfina        | Task 2               |

# Table of Contents

1. [Brief Description of Air Selangor](#brief)
2. [Objectives of the Case Study](#objective)
3. [Identify Vulnerabilities](#identify)
4. [Evaluate Vulnerabilities](#evaluate)
5. [Prevent Vulnerabilities](#prevent)
6. [References](#reference)

## List of Figures
- [List of Figures goes here]

## List of Tables
- [List of Tables goes here]



## 1. Brief Description of Air Selangor <a id="brief"></a>

## 2. Objectives of the Case Study <a id="objective"></a>

## 3. Vulnerablities <a id="identify"></a>
### a. Server OS and Server-Side Scripting used<a id="identify"></a>
### b. Hash Disclosure
### c. CSRF
### d. Secured Cookies
### e. CSP
#### 1. Content Security Policy (CSP) Header Not Set
| Alert    	| CWE id: 693<br>WASC id : 15                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  	|
|----------	|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| Alert    	| CWE id: 693<br>WASC id : 15                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  	|
| Identify 	| Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files. 	|
| Evaluate 	| Risk: Medium <br>Confidence: High                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                	|
### f. JS Library
### g. HTTPS Implementation
### h. Cookie Poisoning
### i. Potential XSS
### j. Information Disclosure

## 6. References <a id="reference"></a>