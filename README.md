# server-http-via-ssh
Get HTTP access to your local machine through your server SSH.

> Serveo is an SSH server just for remote port forwarding. When a user connects to a Serveo server, he get a public URL that anybody can use to connect to their localhost server.

## Important
It's a copy of a binary file from serveo.net.

## Help

```
$ ./serveo-linux-amd64 -h

Usage of ./serveo-linux-amd64:
  -allow_ssh_on_https_port
        whether to also allow SSH connections on the HTTPS port (default true)
  -cert_dir string
        directory to look in for tls certificates
  -disable_telemetry
        whether to disable reporting of telemetry events
  -domain string
        default domain name for URLs (default "serveo.net")
  -enable_logging
        whether or not to log to stdout (default true)
  -http_port int
        http port to listen on (default 80)
  -https_port int
        https port to listen on (default 443)
  -monitoring_addr string
        the address to bind to for serving metrics and profiling requests (default "localhost:6060")
  -port int
        ssh port to listen on (default 22)
  -private_key_path string
        the path to the host's private key file (default "ssh_host_rsa_key")
  -tcp_port_lower_bound int
        the lowest port number allowed for TCP forwarding (default 1024)
```
