---
title: Trinity API Documentation

toc_footers:
  - Made by <a href='https://trinity-apparel.com'>Trinity Apparel</a>

includes:
  - errors
  - pagination
  - orders
  - measurements
  - options
  - fabrics
  - materials
  - customers
  - manufacturers
  - shipping
  - changelog

search: true
---

# Introduction

Welcome to the Trinity Apparel API!

Our RESTful API is used for our internal apps, dealers, and manufacturers.  Here is an overview of our sections:

| API Name                            | Description                                 |
| ----------------------------------- | ------------------------------------------- |
| Orders API <br> <span>readonly</span> | Dealers can review their orders and all garments in those orders |
| Measurements API <br> <span>readonly</span> | Explore Options |
| Options API <br> <span>readonly</span> | Explore Options |
| Fabrics API <br> <span>readonly</span> | Search and Explore Fabrics |
| Materials API <br> <span>readonly</span> | Explore buttons, threads, felts, etc |
| Customers API <br> <span>write</span> | Explore your customers and add basic customer records |
| Manufacturers API <br> <span>write</span> | Manage orders at a factory |
| Shipping API <br> <span>write</span> | Receive and manage shipments at a factory |

# Authorization

> To authorize, use this code:

```shell
# Pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization Bearer: swaledale"
```

> Make sure to replace `swaledale` with your JWT.

All routes require a valid JSON Web Tokens (JWT) token. JSON Web Tokens are an open, industry standard RFC 7519 method for representing claims securely between two parties. Learn more at <a href='https://jwt.io/'>https://jwt.io/</a>

You'll pass the JWT in the header like this:

`Authorization Bearer: eyJhbGciOiJSUzI1NiJ9.eyJzdWIiOjg4LCJleHAiOjE1Njc4NDY5MTksImlhdCI6MTUzNjMxMDkxOSwiaXNzIjoiVHJpbml0eSBBUEkgVjEiLCJqdGkiOiIwYmUxY2IzNTY4NGVkYzhiYTY3YjM0YmRiMTUyZTlkMiJ9.UP7T1J0OM4lBWT3eB6s18qfo1XYI45-w5XIyd94LKlbIRsu1EzGyJrCm6sCwzBi3f3a-4I3wwxAUlt-t7NJP9rCSkWMOMzEOCNOU-waML0tU2dnh_mptxDJCE4GlY8JSTFVXbVGv1r6xDYi0xmy3UJHpW4rsoSUgLBPnTIzsZiE`

<aside class="notice">
You must replace <code>swaledale</code> with your personal JWT token. 
</aside>
