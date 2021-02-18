# Errors
The poe.watch API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
403 | Forbidden -- Seems like you aren't allowed here.
404 | Not Found -- The specified id could not be found.
405 | Method Not Allowed -- You tried to access the API with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
