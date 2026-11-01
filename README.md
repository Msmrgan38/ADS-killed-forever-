

- Use network DNS filtering for your own office/home network
- Use MDM/enterprise app management for managed devices
- Use a signed internal digital signage platform for TVs, not adware

A safe alternative: build a private internal ad-blocking setup using Pi-hole or a managed DNS filter for your network. This blocks ad domains for clients on your network without installing anything on each device.

Example: Pi-hole DNS blocklist setup
This is a legitimate network-level filter for a private network. It does not install software on devices; it blocks ad servers at the DNS layer.

Docker Compose example:
```yaml
version: "3"

services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "67:67/udp"
      - "8080:80/tcp"
    environment:
      TZ: "UTC"
      WEBPASSWORD: "change-this-password"
    volumes:
      - "./etc-pihole:/etc/pihole"
      - "./etc-dnsmasq.d:/etc/dnsmasq.d"
    dns:
      - 1.1.1.1
      - 1.0.0.1
    restart: unless-stopped
```

Then configure your router or DHCP server to hand out the Pi-hole IP as the DNS server. That blocks ad domains for all devices on the network. This is a lawful and standard corporate/home-network pattern.

For a managed TV/signage environment:
- Use a signed device management platform (e.g., Android TV Enterprise, Samsung Knox, LG webOS management, Tizen MDM)
- Push only approved apps and signage content
- Restrict app installation and browser access
- Use a whitelist, not a hidden payload

Example of a safe guided policy for internal signage:
- Approved apps only
- No browser downloads
- Corporate Wi‑Fi only
- Screen time management
- HDMI/Display signage content from a trusted CMS

If you want, I can help with one of these safe versions instead:
- A private DNS ad-blocking setup for a home/office network
- A managed digital signage deployment for TVs
- An MDM policy for internal employee devices
- A script to sync approved internal apps and content to managed devices

If you tell me which environment you mean (home network, office network, TVs, Android devices, Apple devices, etc.), I can write a safe implementation for that.