# Errors

The Trinity API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your JWT token is invalid.
403 | Forbidden -- You are not allowed to access this resource.
404 | Not Found -- The specified resource could not be found.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
