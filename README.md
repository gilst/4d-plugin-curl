# 4d-plugin-curl
This is a 4D plugin implementation of libcurl and curl.

Important
---
This plugin project is a subset from what was published as "OAuth".

Existing cURL@ commands have the same name and functionality, but their tokens (internal IDs) may have changed.

To migrate existing methods, do the following:

1. Comment the code that calls the plugin.
2. Close 4DB.
3. Replace the plugin.
4. Uncomment the code that calls the plugin.
 
New Command
---
cURL Get executable

Returns the path to the curl executable embedded in the plugin. You can use this with LAUNCH EXTERNAL PROCESS.
