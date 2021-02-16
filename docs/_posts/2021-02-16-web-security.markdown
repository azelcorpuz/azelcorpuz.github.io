---
layout: post
title:  "Web Security"
date:   2021-02-16 12:19:00 +0800
categories: notes
---

## Session/Cookie Based
* stored in the server
* cookie is automatically sent to server together with the request
* prone to CSRF  ??? - *to confirm*
* prone to XSS - not without the HTTPOnly flag ??? *to confirm*
  * HTTPOnly flag is the cookie only accessible to HTTP requests
* scaling 

## Token Based
* stored in the client
* send to each and every request -- in the header
* CSRF Safe?
* Prone to XSS - *why?*
* can scale because nothing is stored on the server

## CSRF
* a user will be lured to click something, and this link normally sends a request to the server
* can be solved by: same site cookie
* CSRF token - *how it works?*

## XSS
* inject script and so it looks lke the request came from the same website, and can stole your cookie or token
* read - https://academind.com/learn/javascript/localstorage-vs-cookies-xss/

## NOT TRUE:
* can be solved by: Same Origin Policy --> it prevents scripts running under one origin to read data from another origin
  * because SOP only prevents to read the response, but the request can still be successful
  * In short SOP only prevents reading data which was served from a different origin. It does not cover cross-domain form submissions which are used to carry out   a  CSRF attack.
  * Some sites says it prevents CSRF because 
  * Pre flight requests --> Cross-site requests are preflighted like this since they may have implications to user data. 
* can be solved by (???): CORS - Cross-origin resource sharing --> control which servers can read your responses -- just relaxing the SOP
https://www.nccgroup.com/us/about-us/newsroom-and-events/blog/2017/september/common-csrf-prevention-misconceptions/ 

