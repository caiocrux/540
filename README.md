# 540

Este repositório contém uma stack utilizada no curso 540 da 4Linux.

---

Criar a rede do traefik:

```bash
docker network create -d overlay traefik-net
```

Criar serviço

```bash
docker service create --name traefik \
--constraint 'node.role==manager' \
--publish 80:80 --publish 8080:8080 \
--mount type=bind,source=/var/run/docker.sock,target=/var/run/docker.sock \
--network traefik-net traefik:1.7 \
--docker --docker.swarmMode --docker.domain=4labs.example \
--docker.watch --web
```

---

Ordem de subida das stacks para melhor entendimento (lembrando de remover a stack antes de subir a próxima):

1. prometheus.yml
2. node-exporter.yml
3. cadvisor.yml
4. grafana.yml

---

ID dos dashboards para importação no Grafana

- 1860 - Node Exporter Full 
- 10566 - Docker and OS metrics ( cadvisor, node_exporter )
