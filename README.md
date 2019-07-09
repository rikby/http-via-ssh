# HTTP via SSH
Get HTTP access to your local machine through your server SSH.

> Serveo is an SSH server just for remote port forwarding. When a user connects to a Serveo server, he get a public URL that anybody can use to connect to their localhost server.

## Important
It's a copy of a binary file from serveo.net (now it's down).

## Usage


The server's behavior is configured using command line arguments. Use `-h` to see all options.

```./serveo -h```

**`-private_key_path`**

At the very least, you must specify the path to an encoded private key used for establishing SSH connections. You may be able to use `/etc/ssh/ssh_host_rsa_key` or `$HOME/.ssh/id_rsa`, but it's recommended that you generate a private key for Serveo's use (using `ssh-keygen`, for example: `ssh-keygen -t rsa -f ssh_host_rsa_key`).

```
./serveo -private_key_path=/etc/ssh/ssh_host_rsa_key
./serveo -private_key_path=$HOME/.ssh/id_rsa
```

**`-port, -http_port, -https_port`**

These options tell Serveo on which ports, respectively, to listen for SSH, HTTP, and HTTPS connections.

```
./serveo -private_key_path=ssh_host_rsa_key -port=22 -http_port=80 -https_port=443
./serveo -private_key_path=ssh_host_rsa_key -port=2222 -http_port=8080 -https_port=8443
```

**`-cert_dir`**

This is necessary for HTTPS support. The directory it specifies should contain TLS certificates and keys. For example, a cert_dir might contain the following files:
```
    abc.crt      abc.key      foo.crt      foo.key
```

Certificate files must end in .crt, and keys in .key. The basename for certificate files doesn't matter, but must match the corresponding key file (i.e. `abc.{crt,key}` should both exist). Wildcard certificates and certificates with multiple DNS names are supported.

```
./serveo -cert_dir=certs
```

**`-domain`**

This option specifies the default domain in case no domain is specified.
```
./serveo -domain=example.com
```

**`-disable_telemetry`**

A few basic events are reported for my analytical use (process startup and the start of port forwarding). Invoke this flag to disable telemetry.

## Help from CLI

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
