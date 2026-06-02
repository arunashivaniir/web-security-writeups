WebVerse Pro — Sundial Observatory

Challenge Link:https://dashboard.webverselabs-pro.com/learning-paths/junior-web-hacker/01/occultation

Reconnaissance
Upon opening the sundial observatory page, I explored all the tabs ,did some inspection.

Testing
When I scrolled down to the bottom of the home page, I found “robots.txt” listed.
The robots.txt file is intended for search engine crawlers and should not be used to protect sensitive resources. Any user can access it directly and discover hidden application endpoints.
Directing to robots.txt, I read the contents
The robots.txt file contained three disallowed directories. I manually browsed to each path to determine whether any exposed content was accessible without authentication,
where only one was found to be accessible— /members-only-2026

Discovery
At the bottom of the page, I located the challenge flag.
The challenge demonstrates information disclosure through robots.txt, where sensitive endpoints can be exposed to unauthenticated users.
