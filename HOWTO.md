# HOW TOs

## Host sites and applications on Synology NAS
1. Add CNAME record to DNS: xyz.domain.com > domain.com
2. Serve the site / application
  - Virtual Host for static sites > Name based > xyz.domain.com > both 80/443
  - Docker: serve container on a specific port, eg. localhost:12345
3. Setup reverse proxy for port-based sites / containers:
  - Hostname: xyz.domain.com, select HTTP/HTTPS
  - Destination: localhost:12345
  - Select HTTP instead of HTTPS for optional SSL offloading on externally accessible URLs
  - For websockets: Custom Header > Create: websocket
    - Upgrade : $http_upgrade
    - Connection : $connection_upgrade
