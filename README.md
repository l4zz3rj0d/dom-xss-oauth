# DOM-Based XSS OAuth Token Theft 
## What this script does

Reads the URL fragment `window.location.hash` where OAuth tokens are stored after login.

Removes the `#` and splits the fragment into key–value pairs.

Parses these values into a JavaScript object.

Extracts the `access_token` from the parsed data.

## Token Exfiltration

Creates a new `Image` object.

Sets its `src` to an attacker-controlled URL.

Appends the stolen access token as a query parameter.

Loading the image sends the token to the attacker’s server silently.

## What needs to be configured

Replace `TTACKBOX_IP` with your attacker machine IP.

Ensure a listener/web server is running on the specified port `(e.g. 8081)`.

OAuth flow must return tokens in the URL fragment `(Implicit Flow)`.

Victim must execute the injected JavaScript `(DOM XSS present)`.

## Key Points

Attack Type: DOM-based XSS

Why it works: OAuth token exposed in URL fragment

Impact: Access token theft

Common in: OAuth Implicit Flow (deprecated)

Reminder

Use Authorization Code `Flow + PKCE` to avoid this issue.
