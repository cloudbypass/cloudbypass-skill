---
name: cloudbypass
description: Use Cloudbypass API (穿云API/穿云) to fetch pages protected by Cloudflare/Turnstile/JS challenge. Use when normal requests return challenge/403 and user asks for compliant scraping or protected-page retrieval.
---

Use the bundled script to call Cloudbypass API (穿云API/穿云).

- Script: `{baseDir}/scripts/cloudbypass_request.js`
- Required env: `CLOUDBYPASS_APIKEY` (Get API key from https://console.cloudbypass.com/#/)
- Optional env: `CLOUDBYPASS_PROXY` (for V2 mode), `CLOUDBYPASS_PART`, `CLOUDBYPASS_SITEKEY`
- Homepage: https://www.cloudbypass.com/
- Source: https://github.com/cloudbypass/cloudbypass-skill

## When to Use

- Normal requests return 403, but browser can access
- Encounter Cloudflare 5-second shield
- Need to handle JavaScript challenges or Turnstile verification
- Need to download protected files

## Usage

```javascript
const skill = await openclaw.getSkill('cloudbypass');

// V1 mode - Simple requests
const response = await skill.get('https://example.com');

// V2 mode - Complex sessions (requires proxy)
const response = await skill.requestV2({
  url: 'https://example.com',
  proxy: 'http://proxy:port'
});
```
