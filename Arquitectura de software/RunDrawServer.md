Quick Start
Run the container.

docker run -it --rm --name="draw" -p 8080:8080 -p 8443:8443 jgraph/drawio

### Runnig in local machine

Create docker compose file, use volumes to persist data and use environment variables to configure the server.

```yaml
version: '3.7'
services:
  draw:
    image: jgraph/drawio
    container_name: draw
    ports:
        - 8080:8080
        - 8443:8443
```    