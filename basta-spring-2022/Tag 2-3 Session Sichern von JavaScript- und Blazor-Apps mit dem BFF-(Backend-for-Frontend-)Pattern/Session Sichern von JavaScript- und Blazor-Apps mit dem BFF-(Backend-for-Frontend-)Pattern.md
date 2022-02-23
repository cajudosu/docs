Session Sichern von JavaScript- und Blazor-Apps mit dem BFF-(Backend-for-Frontend-)Pattern
==========================================================================================

**TODO:** Slides angefragt

CSRF-Attacken verhindern
------------------------
- cross-site request forgery 
- add explicit credential on every request
  - VerificationToken
- IETF (internet engineering task force)
  - toke based API calls
- OAuth2 approach - Implicit Flow (deprecated)
- SPA muss Token irgendwo speichern
  - Liegt typischerweise im Session-Storage
- Autorization Code Flow
  - Token wird nicht mehr über URL übermittelt
  - Liegt aber trotzdem noch in einem Browser Storage
  - JavaScript kann auf Storage zugreifen
- Safari
  - kein Session Storage im Inkognito-Modus
- Session Storage ist wegen XSS ein Problem
- Same Site Cookies
  - Bsp. evil.com -> app.com
    - None
    - Lax
    - Strict
  - Second-Level Domain
- Session Riding
- CORS (cross-origin resource sharing)
- IDEE: Das Backend kümmert sich um Tokens
  - TMI BFF vs Full BFF
  - BFF (backend-for-frontend pattern)
- BFF mit ASP.NET Core
  - OpenID Connect/OAuth Client Lib
  - Session Management
  - Token Management
  - Local / Remote API Endpoints
  - UI Assets
- Es gibt fertige BFF Frameworks
- JavaScript darf per se keine Tokens handlen
- Sessions sind wieder da