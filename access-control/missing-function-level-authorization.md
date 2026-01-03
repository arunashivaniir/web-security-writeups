VULNERABILITY TYPE
Broken Access Control - Missing Function-Level Authorisation

Affected Endpoint
GET /api/Challenges

Intended Behaviour
This API(Challenges) can only be viewed/accessed by an admin, A normal customer should not be able to access the challenge metadata

Actual Behaviour
A user with the customer role can access the Challenges API and check sensitive metadata.

Steps to Reproduce
1.Login as normal user
2.Send the request:
	GET /api/Challenges
3.Returns 304 not modified, hence delete the “If-None-Match”, to avoid caching and send the request to server.

Evidence
Api returned metadata of Challenges which should be accessed as a customer,should be restricted to privileged user only.

Root Cause
Endpoint performs authentication but doesnt enforce funtion-level authorisation.

Recommended Fix
Apply role-based access control
	authorise('admin')
	
Prevention
Sensitive metadata must validate user permissions and not always rely on authentication.
