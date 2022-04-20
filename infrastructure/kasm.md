# KASM Cheat-Sheet
## Custom Images


### Add Images in KASM
> [!attention]
> You need to pass in a "tag" in the Docker Image. Otherwise kasm won't pull and start the image correctly.

### Docker Run Config
**Example**
```
{
	"cap_add":["NET_ADMIN"],
	"devices":["dev/net/tun","/dev/net/tun"],
	"sysctls":{"net.ipv6.conf.all.disable_ipv6":"0"}
}
```