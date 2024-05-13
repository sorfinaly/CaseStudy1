# Case Study 1 Report

## Group Name: Blue

## Group Member and Assigned Tasks Details

| Name           | Task                 |
|----------------|----------------------|
| Nadirah Binti Ros Liza (2027832)       | Hash Disclosure, Secured Cookies, JS Library, Cookie Poisoning, Potential XSS.               |
| Sorfina Alyia Binti Jazrry (2017326)       | Server OS and Server-Side Scripting used, CSRF, CSP, HTTPS implementation, Information Disclosure.               |

# Table of Contents

1. [Brief Description of Air Selangor](#brief)
2. [Objective of the Case Study](#objective)
3. [Vulnerabilities](#vuln)
    - [Server OS and Server-Side Scripting](#server)
        - Server OS and Server-Side Scripting used

    - [Hash Disclosure](#hash)
    
    - [CSRF](#csrf)
        - Absence of Anti-CSRF Tokens
        - Cookie with SameSite Attribute None
        - Cross-Domain Misconfiguration

    - [Secured Cookies](#securedcookie)
        - Session ID in URL Rewrite
        - Retrieved from Cache
        - Loosely Scoped Cookie
    - [CSP](#csp)
        - Content Security Policy (CSP) Header Not Set
        - Missing Anti-clicking Header

    - [JS Library](#js)
        - Cross-Domain JavaScript Source File Inclusion
        - Vulnerable JS LIbrary 

    - [HTTPS Implementation](#https)
        - Strict-Transport-Security Header Not Set

   - [Cookie Poisoning](#cookiepoison)
        - Cookie no HTTPOnly Flag
        - Cookie without Secure Flag 

    - [Potential XSS](#xss)
        - User Controllable HTML Element Attribute

    - [Information Disclosure](#info)
        - Suspicious Comments
        - Sensitive Information in URL
        - Re-examine Cache-control Directives
        - X-Content-Type-Options Header Missing
        - Timestamp Disclosure - Unix
        - PII Disclosure
4. [References](#reference)

## List of Figures
- [List of Figures goes here]

## List of Tables
- [List of Tables goes here]



## 1. Brief Description of Air Selangor <a id="brief"></a>
Syarikat Bekalan Air Selangor (SYABAS) is the water supply company responsible for providing treated water to Selangor, Kuala Lumpur, and Putrajaya in Malaysia. It manages the treatment and distribution of water to households, businesses, and industries in the region. SYABAS ensures the availability of clean and safe water for consumption, sanitation, and various other purposes. It also manages projects to improve water infrastructure and efficiency to meet the growing demands of the population.<br>

## 2. Objectives of the Case Study <a id="objective"></a>
The objective of this case study is to evaluate and address the vulnerabilities found on the Air Selangor website. We aim to identify any flaws that could jeopardize the website's security through extensive analysis by using the OWASP ZAP scan. By examining these vulnerabilities, we can determine the level of risk and impact. This allows us to prioritize remedies in order to minimize risks while ensuring the dependability and integrity of Air Selangor's website in providing water services to the community.
The vulnerablities that need to be observed are:
1. Server OS and Server-Side Scripting used
2. Hash Disclosure
3. CSRF
4. Secured Cookies
5. CSP
6. JS Library
7. HTTPS implementation
8. Cookie Poisoning
9. Potential XSS
10. Information Disclosure<br>

## 3. Vulnerablities <a id="vuln"></a>
<ol>
<li>Server OS and Server-Side Scripting used <a id="server"></a></li> <br>

<ol>

<li>Server Leaks Version Information via "Server" HTTP Response Header Field</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:200 <br>WASC id : 13      	|
| Identify 	| The web/application server is leaking version information via the "Server" HTTP response header. Access to such information may facilitate attackers identifying other vulnerabilities your web/application server is subject to. 	<br><br>**Evidence** <br><br> Content-Type: text/plain <br>Cross-Origin-Resource-Policy: cross-origin<br>**Server: Golfe2**<br>Content-Length: 2|
| Evaluate 	| Risk: Low <br> Confidence:     High    	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to suppress the "Server" header or provide generic details. |
</ol>

<li>Hash Disclosure <a id="hash"></a></li><br>

<ol> 
    
|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 200<br>WASC id : 13      	|
| Identify 	|  	A hash was disclosed by the web server. - MD4 / MD5 <br>|
| Evaluate 	| Risk:  Low <br>	|
| Prevent  	|  Ensure that hashes that are used to protect credentials or other resources are not leaked by the web server or database. There is typically no requirement for password hashes to be accessible to the web browser.|



</ol>

<li>CSRF <a id="csrf"></a></li><br>
<ol>

<li>Absence of Anti-CSRF Tokens</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 352<br>WASC id : 9       	|
| Identify 	|  No Anti-CSRF tokens were found in a HTML submission form. <br><br> A cross-site request forgery is an attack that involves forcing a victim to send an HTTP request to a target destination without their knowledge or intent in order to perform an action as the victim. The underlying cause is application functionality using predictable URL/form actions in a repeatable way. The nature of the attack is that CSRF exploits the trust that a web site has for a user. By contrast, cross-site scripting (XSS) exploits the trust that a user has for a web site. Like XSS, CSRF attacks are not necessarily cross-site, but they can be. Cross-site request forgery is also known as CSRF, XSRF, one-click attack, session riding, confused deputy, and sea surf.<br><br>CSRF attacks are effective in a number of situations, including:<br><br>* The victim has an active session on the target site.<br><br>* The victim is authenticated via HTTP auth on the target site.<br><br>* The victim is on the same local network as the target site.<br><br>CSRF has primarily been used to perform an action against a target site using the victim's privileges, but recent techniques have been discovered to disclose information by gaining access to the response. The risk of information disclosure is dramatically increased when the target site is vulnerable to XSS, because XSS can be used as a platform for CSRF, allowing the attack to operate within the bounds of the same-origin policy. <br><br>**Evidence** <br><br> form data-sf-form-id="7462" data-is-rtl="0" data-maintain-state data-results-url="https://www.airselangor.com/?sfid=7462" data-ajax-form-url="https://www.airselangor.com/?sfid=7462&amp;sf_action=get_data&amp;sf_data=form" data-display-result-method="archive" data-use-history-api="1" data-template-loaded="0" data-lang-code="en" data-ajax="0" data-init-paged="1" data-auto-update="1" action="https://www.airselangor.com/?sfid=7462" method="post" class="searchandfilter" id="search-filter-form-7462" autocomplete="off" data-instance-count="2"><br><br>No known Anti-CSRF token [anticsrf, CSRFToken, __RequestVerificationToken, csrfmiddlewaretoken, authenticity_token, OWASP_CSRFTOKEN, anoncsrf, csrf_token, _csrf, _csrfSecret, __csrf_magic, CSRF, _token, _csrf_token] was found in the following HTML form: [Form 2: "_sf_search[]" ]. |
| Evaluate 	| Risk:  Medium<br> Confidence: Low         	|
| Prevent  	| Phase: Architecture and Design<br><br>Use a vetted library or framework that does not allow this weakness to occur or provides constructs that make this weakness easier to avoid <br><br>For example, use anti-CSRF packages such as the OWASP CSRFGuard.<br><br>Phase: Implementation<br><br>Ensure that your application is free of cross-site scripting issues, because most CSRF defenses can be bypassed using attacker-controlled script.<br><br>Phase: Architecture and Design<br><br>Generate a unique nonce for each form, place the nonce into the form, and verify the nonce upon receipt of the form. Be sure that the nonce is not predictable (CWE-330).<br><br>Note that this can be bypassed using XSS.<br><br>Identify especially dangerous operations. When the user performs a dangerous operation, send a separate confirmation request to ensure that the user intended to perform that operation.<br><br>Note that this can be bypassed using XSS.<br><br>Use the ESAPI Session Management control.<br><br>This control includes a component for CSRF.<br><br>Do not use the GET method for any request that triggers a state change.<br><br>Phase: Implementation<br><br>Check the HTTP Referer header to see if the request originated from an expected page. This could break legitimate functionality, because users or proxies may have disabled sending the Referer for privacy reasons.|

<li>Cookie with SameSite Attribute None</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 1275<br>WASC id : 13      	|
| Identify 	| A cookie has been set with its SameSite attribute set to "none", which means that the cookie can be sent as a result of a 'cross-site' request. The SameSite attribute is an effective counter measure to cross-site request forgery, cross-site script inclusion, and timing attacks. 	<br><br>**Evidence** <br><br> X-XSS-Protection: 0 **Set-Cookie: test_cookie=CheckForPermission;** expires=Thu, 09-May-2024 15:31:15 GMT; |
| Evaluate 	| Risk: Low <br> Confidence:  Medium       	|
| Prevent  	| Ensure that the SameSite attribute is set to either 'lax' or ideally 'strict' for all cookies. |

<li>Cross-Domain Misconfiguration</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 	264<br>WASC id :  	14     	|
| Identify 	| Web browser data loading may be possible, due to a Cross Origin Resource Sharing (CORS) misconfiguration on the web server <br> The CORS misconfiguration on the web server permits cross-domain read requests from arbitrary third party domains, using unauthenticated APIs on this domain. Web browser implementations do not permit arbitrary third parties to read the response from authenticated APIs, however. This reduces the risk somewhat. This misconfiguration could be used by an attacker to access data that is available in an unauthenticated manner, but which uses some other form of security, such as IP address white-listing. <br><br>**Evidence** <br><br>Access-Control-Allow-Origin: * |
| Evaluate 	| Risk: Medium <br> Confidence:     Medium    	|
| Prevent  	|Ensure that sensitive data is not available in an unauthenticated manner (using IP address white-listing, for instance). Configure the "Access-Control-Allow-Origin" HTTP header to a more restrictive set of domains, or remove all CORS headers entirely, to allow the web browser to enforce the Same Origin Policy (SOP) in a more restrictive manner. |

</ol>

<li>Secured Cookies <a id="securedcookie"></a></li><br>

<ol>
<li>Session ID in URL Rewrite</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 200 <br>WASC id : 13      	|
| Identify 	| URL rewrite is used to track user session ID. The session ID may be disclosed via cross-site referer header. In addition, the session ID might be stored in browser history or server logs. 	<br><br>**Evidence** <br><br> ...frm=0&pscdl=noapi&_s=1&**sid=1715267737**&sct=1&seg=0&dl=https%3A%2... |
| Evaluate 	| Risk: Medium <br> Confidence:   High      	|
| Prevent  	| For secure content, put session ID in a cookie. To be even more secure consider using a combination of cookie and URL rewrite. |

<li>Retrieved from Cache</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: N/A <br>WASC id : N/A     	|
| Identify 	| The content was retrieved from a shared cache. If the response data is sensitive, personal or user-specific, this may result in sensitive information being leaked. In some cases, this may even result in a user gaining complete control of the session of another user, depending on the configuration of the caching components in use in their environment. This is primarily an issue where caching servers such as "proxy" caches are configured on the local network. This configuration is typically found in corporate or educational environments, for instance. 	<br><br>**Evidence** <br><br> expires: Tue, 09 Apr 2024 21:12:36 GMT <br>last-modified: Tue, 02 Nov 2021 10:02:33 GMT<br>vary: Accept-Encoding <br> CF-Cache-Status: HIT <br> **Age: 7180** <br>Accept-Ranges: bytes <br>Server: cloudflare <br>CF-RAY: 8812a64049e99f8c-SIN Age: 14867 ... <br><br>The presence of the 'Age' in the response header indicates that that a HTTP/1.1 compliant caching server is in use.|
| Evaluate 	| Risk: Informational <br> Confidence:   Medium      	|
| Prevent  	| Validate that the response does not contain sensitive, personal or user-specific information. If it does, consider the use of the following HTTP response headers, to limit, or prevent the content being stored and retrieved from the cache by another user: <br><br>Cache-Control: no-cache, no-store, must-revalidate, private <br><br>Pragma: no-cache<br><br>Expires: 0 <br><br>This configuration directs both HTTP 1.0 and HTTP 1.1 compliant caching servers to not store the response, and to not retrieve the response (without validation) from the cache, in response to a similar request. |

<li>Loosely Scoped Cookie</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:565 <br>WASC id :  	15     	|
| Identify 	| Cookies can be scoped by domain or path. This check is only concerned with domain scope.The domain scope applied to a cookie determines which domains can access it. For example, a cookie can be scoped strictly to a subdomain e.g. www.nottrusted.com, or loosely scoped to a parent domain e.g. nottrusted.com. In the latter case, any subdomain of nottrusted.com can access the cookie. Loosely scoped cookies are common in mega-applications like google.com and live.com. Cookies set from a subdomain like app.foo.bar are transmitted only to that domain by the browser. However, cookies scoped to a parent-level domain may be transmitted to the parent, or any subdomain of the parent.	<br><br>**Evidence** <br><br> The origin domain used for comparison was: googleads.g.doubleclick.net test_cookie=CheckForPermission|
| Evaluate 	| Risk: 565 <br> Confidence:   Low      	|
| Prevent  	| Always scope cookies to a FQDN (Fully Qualified Domain Name). |

</ol>

<li>CSP <a id="csp"></a></li><br>
<ol>
<li>Content Security Policy (CSP) Header Not Set </li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 693<br>WASC id : 15      	|
| Identify 	| Content Security Policy (CSP) is an added layer of security that helps to detect and mitigate certain types of attacks, including Cross Site Scripting (XSS) and data injection attacks. These attacks are used for everything from data theft to site defacement or distribution of malware. CSP provides a set of standard HTTP headers that allow website owners to declare approved sources of content that browsers should be allowed to load on that page — covered types are JavaScript, CSS, HTML frames, fonts, images and embeddable objects such as Java applets, ActiveX, audio and video files. <br><br>**Evidence** <br><br> The following directives either allow wildcard sources (or ancestors), are not defined, or are overly broadly defined:<br>style-src, img-src, connect-src, frame-src, frame-ancestors, font-src, media-src, manifest-src, worker-src, form-action. <br>The directive(s): frame-ancestors, form-action are among the directives that do not fallback to default-src, missing/excluding them is the same as allowing anything. <br> script-src 'report-sample' 'nonce-RIEsIj30XDI5NhyoOFEvIQ' 'unsafe-inline' 'strict-dynamic' https: http: 'unsafe-eval';object-src 'none';base-uri 'self';report-uri https://csp.withgoogle.com/csp/recaptcha/1 	|
| Evaluate 	| Risk: Medium <br> Confidence: High                    	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to set the Content-Security-Policy header. |

<li>Missing Anti-clicking Header </li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 1021 <br>WASC id : 15       	|
| Identify 	| The response does not include either Content-Security-Policy with 'frame-ancestors' directive or X-Frame-Options to protect against 'ClickJacking' attacks. 	<br> |
| Evaluate 	| Risk: Medium <br> Confidence: Medium        	|
| Prevent  	| Modern Web browsers support the Content-Security-Policy and X-Frame-Options HTTP headers. Ensure one of them is set on all web pages returned by your site/app. If you expect the page to be framed only by pages on your server (e.g. it's part of a FRAMESET) then you'll want to use SAMEORIGIN, otherwise if you never expect the page to be framed, you should use DENY. Alternatively consider implementing Content Security Policy's "frame-ancestors" directive. |



</ol>

<li>JS Library <a id="js"></a> </li><br>

<ol>
<li>Cross-Domain JavaScript Source File Inclusion</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:  829<br>WASC id : 15       	|
| Identify 	|  The page includes one or more script files from a third-party domain	<br><br>**Evidence** <br><br> <ol><li><script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js?ver=02fc163323d2ee7aa277411bbc10e1e7" id="gsap-js-js"></script></li><li><script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-4300098778201117" crossorigin="anonymous"></script></li><li><script async src="https://www.googletagmanager.com/gtag/js?id=G-HC8HNVJVEZ"></script></li><li><script async src="https://www.googletagmanager.com/gtag/js?id=UA-150747362-1"></script></li><li><script src="https://cdn.jsdelivr.net/npm/jquery-validation@1.19.2/dist/jquery.validate.js"></script></li></ol>|
| Evaluate 	| Risk:  Low <br> Confidence:   Medium        	|
| Prevent  	| Ensure JavaScript source files are loaded from only trusted sources, and the sources can't be controlled by end users of the application. |


<li>Vulnerable JS LIbrary </li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:  829 <br>WASC id : N/A     	|
| Identify 	| The identified library jquery-ui, version 1.12.1 is vulnerable. 	<br><br>**Evidence** <br><br> /*! jQuery UI - v1.12.1 |
| Evaluate 	| Risk: Medium <br> Confidence:    Medium     	|
| Prevent  	| Please upgrade to the latest version of jquery-ui. |


</ol>

<li>HTTPS Implementation <a id="https"></a> </li><br>

<ol>
<li>Strict-Transport-Security Header Not Set</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 315 <br>WASC id : 15      	|
| Identify 	| HTTP Strict Transport Security (HSTS) is a web security policy mechanism whereby a web server declares that complying user agents (such as a web browser) are to interact with it using only secure HTTPS connections (i.e. HTTP layered over TLS/SSL). HSTS is an IETF standards track protocol and is specified in RFC 6797. 	 |
| Evaluate 	| Risk: Low <br> Confidence: High        	|
| Prevent  	| Ensure that your web server, application server, load balancer, etc. is configured to enforce Strict-Transport-Security. |

</ol>

<li>Cookie Poisoning <a id="cookiepoison"></a> </li><br>

<ol>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 565 <br>WASC id : 20       	|
| Identify 	| This check looks at user-supplied input in query string parameters and POST data to identify where ookie parameters might be controlled. An attacker may be able to poison cookie values through URL parameters by injecting a semicolon to see if they can add cookie values, example: name=controlledValue;name=anotherValue; This was identified at: https://example.com/transact <br>User-input was found in the following cookie: value=poison; SameSite=Strict The user input was: place=poison <br>|
| Evaluate 	| Risk: Informational <br>    	|
| Prevent  	| Do not allow user input to control cookie names and values. If some query string parameters must be set in cookie values, be sure to filter out semicolon's that can serve as name/value pair delimiters.  |

<li>Cookie No HTTPOnly Flag</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 1004 <br>WASC id : 13       	|
| Identify 	| A cookie has been set without HTTPOnly flag, which means that the cookie can be accessed by JavaScript. If a malicious script can be run on this page then the cookie will be accessible and can be transmitted to another site. If this is a session cookie then session hijacking may be possible.<br><br> **Evidence**<br><br> set-cookie: PHPSESSID=mbseevnqh4r62o6atqoi7aq86; path=/ expires: Thu 19 Nov 1981 08:52:00 GMT |
| Evaluate 	| Risk: Low <br> Confidence: Medium   	|
| Prevent  	| Ensure that the HttpOnly Flag is set for all cookies.  |

<li>Cookie without Secure Flag</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 614 <br>WASC id : 13       	|
| Identify 	| A cookie has been set without the secure flag, which means that the cookie can be accessed via unencrypted connections.<br><br> **Evidence**<br><br> set-cookie: PHPSESSID=mbseevnqh4r62o6atqoi7aq86; path=/ expires: Thu 19 Nov 1981 08:52:00 GMT |
| Evaluate 	| Risk: Low <br> Confidence: Medium   	|
| Prevent  	| Whenever a cookie contains sensitive information or a session token, then it should always be passed using an encrypted channel. Ensure that the secure flag is set for cookies containing such sensitive information.  |

</ol>

<li>Potential XSS <a id="xss"></a> </li><br>

<ol>
<li>User Controllable HTML Element Attribute (Potential XSS)</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 20 <br>WASC id : 20       	|
| Identify 	| This check looks at user-supplied input in query string parameters and POST data to identify where certain HTML attribute values might be controlled. This provides hot-spot detection for cross-site scripting (XSS) that will require further review by a security analyst to determine exploitability. <br>|
| Evaluate 	| Risk: Informational <br> Confidence: Low         	|
| Prevent  	| Validate all input and sanitize output before writing to any HTML attributes.  |

</ol>

<li>Information Disclosure <a id="info"></a> </li><br>
<ol>
<li>Suspicious Comments</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:  200 <br>WASC id : 13      	|
| Identify 	| The response appears to contain suspicious comments which may help an attacker. Note: Matches made within script blocks or files are against the entire content not only comments. 	<br><br>**Evidence** <br><br> - Admin <br> The following pattern was used: \bADMIN\b and was detected 3 times, the first in the element starting with: "<script id="PopupBuilder.js-js-before"> var SGPB_POPUP_PARAMS = {"popupTypeAgeRestriction":"ageRestriction","defaultThemeImages"", see evidence field for the suspicious comment/snippet. <br><br> - Query <br> The following pattern was used: \bQUERY\b and was detected in the element starting with: "<script type="application/ld+json" class="yoast-schema-graph">{"@context":"https://schema.org","@graph":[{"@type":"Organization"", see evidence field for the suspicious comment/snippet.|
| Evaluate 	| Risk: Informational<br> Confidence: Low         	|
| Prevent  	| Remove all comments that return information that may help an attacker and fix any underlying problems they refer to. |

<li> Sensitive Information in URL </li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:200 <br>WASC id :   13    	|
| Identify 	|  The request appeared to contain sensitive information leaked in the URL. This can violate PCI and most organizational compliance policies. You can configure the list of strings for this check to add or remove values specific to your environment. <br><br>**Evidence** <br><br> The URL appears to contain credit card information. <br> https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-4300098778201117 |
| Evaluate 	| Risk: Informational <br> Confidence:  Medium      	|
| Prevent  	| Do not pass sensitive information in URIs. |

<li>Re-examine Cache-control Directives</li><br>

|       	| Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 525 <br>WASC id :   13    	|
| Identify 	|  The cache-control header has not been set properly or is missing, allowing the browser and proxies to cache content. For static assets like css, js, or image files this might be intended, however, the resources should be reviewed to ensure that no sensitive content will be cached.	<br><br>**Evidence** <br><br> Connection: keep-alive <br>ccess-Control-Allow-Origin: * <br>**Cache-Control: max-age=315360000, immutable** <br>referrer-policy: strict-origin-when-cross-origin|
| Evaluate 	| Risk: Informational <br> Confidence:  Low       	|
| Prevent  	| For secure content, ensure the cache-control HTTP header is set with "no-cache, no-store, must-revalidate". If an asset should be cached consider setting the directives "public, max-age, immutable". |

<li>X-Content-Type-Options Header Missing</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id: 693 <br>WASC id : 15        	|
| Identify 	| The Anti-MIME-Sniffing header X-Content-Type-Options was not set to 'nosniff'. This allows older versions of Internet Explorer and Chrome to perform MIME-sniffing on the response body, potentially causing the response body to be interpreted and displayed as a content type other than the declared content type. Current (early 2014) and legacy versions of Firefox will use the declared content type (if one is set), rather than performing MIME-sniffing. 	<br><br>**Evidence** <br><br> This issue still applies to error type pages (401, 403, 500, etc.) as those pages are often still affected by injection issues, in which case there is still concern for browsers sniffing pages away from their actual content type.<br> GET https://www.airselangor.com/wp-content/plugins/contact-form-7/includes/css/styles.css?ver=5.5.2 |
| Evaluate 	| Risk: Low <br> Confidence: Medium        	|
| Prevent  	|Ensure that the application/web server sets the Content-Type header appropriately, and that it sets the X-Content-Type-Options header to 'nosniff' for all web pages. If possible, ensure that the end user uses a standards-compliant and modern web browser that does not perform MIME-sniffing at all, or that can be directed by the web application/web server to not perform MIME-sniffing. |

<li>Timestamp Disclosure - Unix</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:200 <br>WASC id : 13      	|
| Identify 	|  A timestamp was disclosed by the application/web server - Unix	<br><br>**Evidence** <br><br> 1659364840, which evaluates to: 2022-08-01 22:40:40|
| Evaluate 	| Risk: Low <br> Confidence: Low        	|
| Prevent  	| Manually confirm that the timestamp data is not sensitive, and that the data cannot be aggregated to disclose exploitable patterns. |

<li>PII Disclosure</li><br>

|    	    | Description      	|
|----------	|----------------------------------	|
| Alert    	| CWE id:359 <br>WASC id : 13      	|
| Identify 	|  The response contains Personally Identifiable Information, such as CC number, SSN and similar sensitive data	<br><br>**Evidence** <br><br> 376574821370814 found in </image:loc>https://www.airselangor.com/wp-content/upload/elementor/thumbs/3985444548_376574821370814_313752166118313748_n-qfff4di9rre33x5uf18b31k1j7cjvuaca3syssmhmg.jpg</image:loc>|
| Evaluate 	| Risk: High <br> Confidence: Medium        	|
| Prevent  	| Check the response for the potential presence of personally identifiable information(PII), ensure nothing sensitive is leaked by the application . |

</ol>
</ol>

## 6. References <a id="reference"></a>
<ol>
    - ZAP Documentation. Retrieved on 9 May 2024 from [https://www.zaproxy.org/docs/alerts/10029/](https://www.zaproxy.org/)<br>
    - OWASP Cheat Sheet Series. Retrieved on 9 May 2024 from https://cheatsheetseries.owasp.org/<br>
</ol>
