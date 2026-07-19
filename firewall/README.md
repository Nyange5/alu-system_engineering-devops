# Firewall

Securing a server with UFW (Uncomplicated Firewall) by allowing only the network traffic required for essential services, such as SSH, HTTP, and HTTPS. All other incoming traffic is blocked by default.

## Tasks

- **0-block_all_incoming_traffic_but** — Installs UFW on `web-01`, allows TCP ports `22` (SSH), `80` (HTTP), and `443` (HTTPS), and sets the default incoming policy to deny all other traffic. Outgoing traffic remains allowed, and the firewall is then enabled.

- **100-port_forwarding** — Uses a modified copy of `/etc/ufw/before.rules` from `web-01` to add a NAT PREROUTING rule that redirects incoming TCP traffic on port `8080` to port `80`. It also allows TCP port `8080` through UFW so the traffic can pass through the firewall's filter table.

## Notes

- Port `22` must be allowed before enabling UFW. Otherwise, the current SSH connection may be blocked, preventing you from reconnecting to the server.

- Since the school network filters outgoing connections, testing whether a port is open on `web-01` must be done from outside the school network. For example, you can first SSH into `web-02` and then run `telnet <web-01 IP> <port>`. This ensures that the connection originates from `web-02` rather than from the school network.
