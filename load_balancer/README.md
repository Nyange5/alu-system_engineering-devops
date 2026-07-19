# Load Balancing

Improving the web infrastructure by adding redundancy through two identical web servers, **web-01** and **web-02**, placed behind an **HAProxy load balancer (lb-01)**. The load balancer distributes incoming requests between the two servers using a **round-robin algorithm**.

## Tasks

- **0-custom_http_response_header** — Configures a new Ubuntu server to match the setup of **web-01**, including Nginx, a `/redirect_me` endpoint that returns a **301 redirect**, and a custom **404 error page**. It also adds an `X-Served-By` response header containing the server's hostname, making it possible to identify which web server handled each request. This configuration should be applied to both **web-01** and **web-02**.

- **1-install_load_balancer** — Installs and configures **HAProxy** on **lb-01** to distribute incoming traffic between **web-01** and **web-02** using the **round-robin method**, with the service managed through an init script.
