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
<ol>
<li> a. Server OS and Server-Side Scripting used<a id="server"></a></i>
<li> b. Hash Disclosure <a id="hash"></a></li>
<li> c. CSRF <a id="csrf"></a><li>
<li> d. Secured Cookies <a id="securedcookie"></a></li>
<li> e. CSP <a id="csp"></a></li>
<ol>
<li> 1. Content Security Policy (CSP) Header Not Set </li>

|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 693<br>WASC id : 15      	|
| Identify 	| Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files. 	|
| Evaluate 	| Risk: Medium <br> Confidence: High                    	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header. |
</ol>

<li> f. JS Library <a id="js"></a> </li>

|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

<li> g. HTTPS Implementation <a id="https"></a> </li>

|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 315 <br>WASC id : 15      	|
| Identify 	| HTTP Strict Transport Security (HSTS) is a web security policy mechanism whereby a web server declares that complying user agents (such as a web browser) are to interact with it using only secure HTTPS connections (i.e. HTTP layered over TLS/SSL). HSTS is an IETF standards track protocol and is specified in RFC 6797. 	<br>**Evidence** <br> |
| Evaluate 	| Risk: Low <br> Confidence: High        	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to enforce Strict-Transport-Security. |

<li> h. Cookie Poisoning <a id="cookiepoison"></a> </li>

|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

<li> i. Potential XSS <a id="xss"></a> </li>

|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

<li> j. Information Disclosure <a id="info"></a> </li>

|    	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	| The response appears to contain suspicious comments which may help an attacker. Note: Matches made within script blocks or files are against the entire content not only comments. 	<br>**Evidence** <br> *Admin <br> The following pattern was used: \bADMIN\b and was detected 3 times, the first in the element starting with: "<script id="PopupBuilder.js-js-before">
var SGPB_POPUP_PARAMS = {"popupTypeAgeRestriction":"ageRestriction","defaultThemeImages"", see evidence field for the suspicious comment/snippet. <br>
*Query <br> The following pattern was used: \bQUERY\b and was detected in the element starting with: "<script type="application/ld+json" class="yoast-schema-graph">{"@context":"https://schema.org","@graph":[{"@type":"Organization"", see evidence field for the suspicious comment/snippet.|
| Evaluate 	| Risk: Informational<br> Confidence: Low         	|
| Prevent  	| Remove all comments that return information that may help an attacker and fix any underlying problems they refer to. |

</ol>

## 6. References <a id="reference"></a>