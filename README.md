# graphity-collaboration-server
This repository provides a simple **docker-compose** setup for the [graphity realtime collaboration server](https://www.graphity.com/collaborative-editing.html).

The compose stack is based on the official [Collaboration Server Docker image](https://hub.docker.com/r/yworksgmbh/graphity-collaboration-server) and adds a SSL terminating reverse proxy based on the [jwilder/nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy) NGINX image in front.

## Usage

### Prerequisites

You have generated a **TOKEN** on the Graphity admin page in confluence and determined where the server should be hosted.

### Clone the repository

```bash
git clone https://github.com/yWorks/graphity-collaboration-server
```

This will pull the latest version of the stack.

### Adjust configuration

1. Make necessary adjustments to `docker-compose.yml`. At the very least, you need to provide the correct **server token** and the **hostname** where the clients can reach the collaboration server. All other variables are optional:

    | Variable       | Meaning     |Default     | Required? |
    | :------------- | :---------- | ----------- | :-----------: |
    | VIRTUAL_HOST | The **host component** of the endpoint URL   | | **YES** |
    | SERVER_TOKEN | Identification **token** from the Graphity admin page   | | **YES** |    
    | SERVER_PORT   | The **port** of the endpoint | 9093 | No |
    | SERVER_CONTEXT   | The **path component** of the endpoint URL | /graphity/rtc | No |
    | LOGLEVEL   | **Verbosity** of the logging output.<br> One of:<br> ALL, FINE, FINER, FINEST, INFO, WARNING, SEVERE, OFF | WARNING | No |

2. Place your SSL certificates in `proxy/volumes/certs`. If you have chosen `<myserver>` for the **VIRTUAL_HOST**, they must be named `<myserver>.crt` for the certificate and `<myserver>.key` for the private key. 

3. Optionally adjust other parts of the stack. The proxy component of the stack is based on  [jwilder/nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy). Consult the documentation there
        for more advanced scenarios.

### Start the stack

```bash
docker-compose up
```

# Maintainers:

**Maintained by:** [yWorks GmbH](https://www.yworks.com/)

**Where to get help:** [The yWorks Graphity Team](https://www.graphity.com/)


