# Exploring Consul ⚙️

Consul is a powerful tool for services and machines management. Here it was used to explore Service Discovery concepts

### Technologies

[![Docker](.markdown/docker.png "Docker")](https://docs.docker.com/)
[![Consul](.markdown/consul.png "Consul")](https://developer.hashicorp.com/consul)

---

### How to run

Start by creating Docker containers with
```bash
docker compose up -d
```

Now, you can bind all servers by accessing each one and running consul commands:
```bash
docker exec -it consul-server-<id> sh # For access container (replace <id> by server id)
consul agent -config-dir=/etc/consul.d # To setup consul server
``` 

Finally to check if everything is ok, you can run:
```bash
docker exec -it consul-server-<id> sh # For access container (replace <id> by server id)
consul members # To show all servers subscribed in cluster
``` 

You could do the same for client, however you must have attention when running ```consul members``` command, because it's configured to do a health checking in a NGINX service, which is not up, then no services will appear in the output list.
