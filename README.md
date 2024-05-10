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

## 3. Vulnerablities <a id="vuln"></a>
### a. Server OS and Server-Side Scripting used<a id="server"></a>
### b. Hash Disclosure <a id="hash"></a>
### c. CSRF <a id="csrf"></a>
### d. Secured Cookies <a id="securedcookie"></a>
### e. CSP <a id="csp"></a>

   #### 1. Content Security Policy (CSP) Header Not Set
|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 693<br>WASC id : 15      	|
| Identify 	| Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files. 	|
| Evaluate 	| Risk: Medium <br> Confidence: High                    	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header. |
### f. JS Library <a id="js"></a>
### g. HTTPS Implementation <a id="https"></a>
### h. Cookie Poisoning <a id="cookiepoison"></a>
### i. Potential XSS <a id="xss"></a>
### j. Information Disclosure <a id="info"></a>

## 6. References <a id="reference"></a>