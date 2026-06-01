WebVerse Pro — Header Hunt

Difficulty:Easy

Reconnaissance
Upon opening the shipment tracking page, a tracking ID parameter was visible in the request:

GET /track?id=ARC-7842-XRC HTTP/2

Since the tracking ID was user-controlled, I tested whether changing it would reveal additional information or trigger unintended functionality.

Testing
The website has an input field to search for a particular tracking ID.
Using Burp we send a GET request with the tracking ID.
Then send this GET request to Repeater Tab.

Discovery
Previously we have given the tracking ID to be:ARC-7842-XRC

In the Repeater Tab modify id query parameter.
(for .e.g. ARC-7842-XOC)

After modifying the tracking ID, I inspected the response headers and noticed an unexpected internal debugging header:

X-Internal-Order-Ref: WEBVERSE{************}

The exposed header contained the challenge flag.

Vulnerability
The issue is an Information Disclosure vulnerability caused by an exposed debugging header.
Sensitive internal information should never be exposed to external users through HTTP response headers. In this case, an internal debugging header was left accessible in the production environment, leaking information that should remain hidden from users.

