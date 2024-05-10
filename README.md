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

1. [Brief](#brief)
2. [Objective](#objective)
3. [Vulnerabilities](#vuln)
    - [Server OS and Server-Side Scripting](#server)
        - Timestamp Disclosure - Unix
    - [Hash Disclosure](#hash)
    - [CSRF](#csrf)
        - Absence of Anti-CSRF Tokens
        - Missing Anti-clicking Header

    - [Secured Cookies](#securedcookie)
    - [CSP](#csp)
        - Content Security Policy (CSP) Header Not Set
        - Missing Anti-clicking Header
        - X-Content-Type-Options Header Missing

    - [JS Library](#js)
        - Cross-Domain JavaScript Source File Inclusion
        - Vulnerable JS LIbrary 

    - [HTTPS Implementation](#https)
        - Strict-Transport-Security Header Not Set
    - [Cookie Poisoning](#cookiepoison)
    - [Potential XSS](#xss)
    - [Information Disclosure](#info)
        - Suspicious Comments
4. [References](#reference)

## List of Figures
- [List of Figures goes here]

## List of Tables
- [List of Tables goes here]



## 1. Brief Description of Air Selangor <a id="brief"></a>

## 2. Objectives of the Case Study <a id="objective"></a>

## 3. Vulnerablities <a id="vuln"></a>
<ol>
<li>Server OS and Server-Side Scripting used<a id="server"></a></i>

<ol>
<li>Timestamp Disclosure - Unix</li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:200 <br>WASC id : 13      	|
| Identify 	|  A timestamp was disclosed by the application/web server - Unix	<br>**Evidence** <br> 1659364840, which evaluates to: 2022-08-01 22:40:40|
| Evaluate 	| Risk: Low <br> Confidence: Low        	|
| Prevent  	| Manually confirm that the timestamp data is not sensitive, and that the data cannot be aggregated to disclose exploitable patterns. |

</ol>

<li>Hash Disclosure <a id="hash"></a></li>

<ol>
<li></li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

</ol>

<li>CSRF <a id="csrf"></a><li>

<ol>
<li>Absence of Anti-CSRF Tokens</li>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 352<br>WASC id :       	|
| Identify 	|  No Anti-CSRF tokens were found in a HTML submission form. <br><br> A cross-site request forgery is an attack that involves forcing a victim to send an HTTP request to a target destination without their knowledge or intent in order to perform an action as the victim. The underlying cause is application functionality using predictable URL/form actions in a repeatable way. The nature of the attack is that CSRF exploits the trust that a web site has for a user. By contrast, cross-site scripting (XSS) exploits the trust that a user has for a web site. Like XSS, CSRF attacks are not necessarily cross-site, but they can be. Cross-site request forgery is also known as CSRF, XSRF, one-click attack, session riding, confused deputy, and sea surf.<br><br>CSRF attacks are effective in a number of situations, including:<br><br>* The victim has an active session on the target site.<br><br>* The victim is authenticated via HTTP auth on the target site.<br><br>* The victim is on the same local network as the target site.<br><br>CSRF has primarily been used to perform an action against a target site using the victim's privileges, but recent techniques have been discovered to disclose information by gaining access to the response. The risk of information disclosure is dramatically increased when the target site is vulnerable to XSS, because XSS can be used as a platform for CSRF, allowing the attack to operate within the bounds of the same-origin policy. <br><br>**Evidence** <br><br> <form data-sf-form-id="7462" data-is-rtl="0" data-maintain-state data-results-url="https://www.airselangor.com/?sfid=7462" data-ajax-form-url="https://www.airselangor.com/?sfid=7462&amp;sf_action=get_data&amp;sf_data=form" data-display-result-method="archive" data-use-history-api="1" data-template-loaded="0" data-lang-code="en" data-ajax="0" data-init-paged="1" data-auto-update="1" action="https://www.airselangor.com/?sfid=7462" method="post" class="searchandfilter" id="search-filter-form-7462" autocomplete="off" data-instance-count="2"><br><br>No known Anti-CSRF token [anticsrf, CSRFToken, __RequestVerificationToken, csrfmiddlewaretoken, authenticity_token, OWASP_CSRFTOKEN, anoncsrf, csrf_token, _csrf, _csrfSecret, __csrf_magic, CSRF, _token, _csrf_token] was found in the following HTML form: [Form 2: "_sf_search[]" ]. |
| Evaluate 	| Risk:  Medium<br> Confidence: Low         	|
| Prevent  	| Phase: Architecture and Design<br><br>Use a vetted library or framework that does not allow this weakness to occur or provides constructs that make this weakness easier to avoid <br><br>For example, use anti-CSRF packages such as the OWASP CSRFGuard.<br><br>Phase: Implementation<br><br>Ensure that your application is free of cross-site scripting issues, because most CSRF defenses can be bypassed using attacker-controlled script.<br><br>Phase: Architecture and Design<br><br>Generate a unique nonce for each form, place the nonce into the form, and verify the nonce upon receipt of the form. Be sure that the nonce is not predictable (CWE-330).<br><br>Note that this can be bypassed using XSS.<br><br>Identify especially dangerous operations. When the user performs a dangerous operation, send a separate confirmation request to ensure that the user intended to perform that operation.<br><br>Note that this can be bypassed using XSS.<br><br>Use the ESAPI Session Management control.<br><br>This control includes a component for CSRF.<br><br>Do not use the GET method for any request that triggers a state change.<br><br>Phase: Implementation<br><br>Check the HTTP Referer header to see if the request originated from an expected page. This could break legitimate functionality, because users or proxies may have disabled sending the Referer for privacy reasons.|

</ol>

<li>Secured Cookies <a id="securedcookie"></a></li>

<ol>
<li></li>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

</ol>

<li>CSP <a id="csp"></a></li>
<ol>
<li>Content Security Policy (CSP) Header Not Set </li>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 693<br>WASC id : 15      	|
| Identify 	| Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files. 	|
| Evaluate 	| Risk: Medium <br> Confidence: High                    	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header. |

<li>Missing Anti-clicking Header </li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 1021 <br>WASC id : 15       	|
| Identify 	| The response does not include either Content-Security-Policy with 'frame-ancestors' directive or X-Frame-Options to protect against 'ClickJacking' attacks. 	<br>**Evidence** <br> |
| Evaluate 	| Risk: Medium <br> Confidence: Medium        	|
| Prevent  	| Modern Web browsers support the Content-Security-Policy and X-Frame-Options HTTP headers. Ensure one of them is set on all web pages returned by your site/app. If you expect the page to be framed only by pages on your server (e.g. it's part of a FRAMESET) then you'll want to use SAMEORIGIN, otherwise if you never expect the page to be framed, you should use DENY. Alternatively consider implementing Content Security Policy's "frame-ancestors" directive. |

<li>X-Content-Type-Options Header Missing</li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 693 <br>WASC id : 15        	|
| Identify 	| The Anti-MIME-Sniffing header X-Content-Type-Options was not set to 'nosniff'. This allows older versions of Internet Explorer and Chrome to perform MIME-sniffing on the response body, potentially causing the response body to be interpreted and displayed as a content type other than the declared content type. Current (early 2014) and legacy versions of Firefox will use the declared content type (if one is set), rather than performing MIME-sniffing. 	<br>**Evidence** <br> This issue still applies to error type pages (401, 403, 500, etc.) as those pages are often still affected by injection issues, in which case there is still concern for browsers sniffing pages away from their actual content type. At "High" threshold this scan rule will not alert on client or server error responses. |
| Evaluate 	| Risk: Low <br> Confidence: Medium        	|
| Prevent  	|Ensure that the application/web server sets the Content-Type header appropriately, and that it sets the X-Content-Type-Options header to 'nosniff' for all web pages. If possible, ensure that the end user uses a standards-compliant and modern web browser that does not perform MIME-sniffing at all, or that can be directed by the web application/web server to not perform MIME-sniffing. |

</ol>

<li>JS Library <a id="js"></a> </li>

<ol>
<li>Cross-Domain JavaScript Source File Inclusion</li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:  829<br>WASC id : 15       	|
| Identify 	|  The page includes one or more script files from a third-party domain	<br>**Evidence** <br> <ol><li><script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js?ver=02fc163323d2ee7aa277411bbc10e1e7" id="gsap-js-js"></script></li><li><script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-4300098778201117" crossorigin="anonymous"></script></li><li><script async src="https://www.googletagmanager.com/gtag/js?id=G-HC8HNVJVEZ"></script></li><li><script async src="https://www.googletagmanager.com/gtag/js?id=UA-150747362-1"></script></li><li><script src="https://cdn.jsdelivr.net/npm/jquery-validation@1.19.2/dist/jquery.validate.js"></script></li></ol>|
| Evaluate 	| Risk:  Low <br> Confidence:   Medium        	|
| Prevent  	| Ensure JavaScript source files are loaded from only trusted sources, and the sources can't be controlled by end users of the application. |


<li>Vulnerable JS LIbrary </li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:  829 <br>WASC id : (n/a)      	|
| Identify 	| The identified library jquery-ui, version 1.12.1 is vulnerable. 	<br>**Evidence** <br> /*! jQuery UI - v1.12.1 |
| Evaluate 	| Risk: Medium <br> Confidence:    Medium     	|
| Prevent  	| Please upgrade to the latest version of jquery-ui. |


</ol>

<li>HTTPS Implementation <a id="https"></a> </li>

<ol>
<li>Strict-Transport-Security Header Not Set</li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 315 <br>WASC id : 15      	|
| Identify 	| HTTP Strict Transport Security (HSTS) is a web security policy mechanism whereby a web server declares that complying user agents (such as a web browser) are to interact with it using only secure HTTPS connections (i.e. HTTP layered over TLS/SSL). HSTS is an IETF standards track protocol and is specified in RFC 6797. 	<br>**Evidence** <br> |
| Evaluate 	| Risk: Low <br> Confidence: High        	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to enforce Strict-Transport-Security. |

</ol>

<li>Cookie Poisoning <a id="cookiepoison"></a> </li>

<ol>
<li></li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

</ol>

<li>Potential XSS <a id="xss"></a> </li>

<ol>
<li></li>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: <br>WASC id :       	|
| Identify 	|  	<br>**Evidence** <br> |
| Evaluate 	| Risk:  <br> Confidence:         	|
| Prevent  	|  |

</ol>

<li>Information Disclosure <a id="info"></a> </li>
<ol>
<li>Suspicious Comments</li>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:  200 <br>WASC id : 13      	|
| Identify 	| The response appears to contain suspicious comments which may help an attacker. Note: Matches made within script blocks or files are against the entire content not only comments. 	<br>**Evidence** <br> *Admin <br> The following pattern was used: \bADMIN\b and was detected 3 times, the first in the element starting with: "<script id="PopupBuilder.js-js-before"> var SGPB_POPUP_PARAMS = {"popupTypeAgeRestriction":"ageRestriction","defaultThemeImages"", see evidence field for the suspicious comment/snippet. <br> *Query <br> The following pattern was used: \bQUERY\b and was detected in the element starting with: "<script type="application/ld+json" class="yoast-schema-graph">{"@context":"https://schema.org","@graph":[{"@type":"Organization"", see evidence field for the suspicious comment/snippet.|
| Evaluate 	| Risk: Informational<br> Confidence: Low         	|
| Prevent  	| Remove all comments that return information that may help an attacker and fix any underlying problems they refer to. |

</ol>

</ol>

## 6. References <a id="reference"></a>