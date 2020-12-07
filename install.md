https://stackoverflow.com/questions/54295980/nifi-from-overwriting-values-in-nifi-properties


# Docker Swarm

# Create Swarm manager
```bash
docker swarm init --advertise-addr <host ip>
```

# Add nodes to cluster
```bash
docker swarm join --token <token>
```

# Add labels to each node for placement restrictions (This has to be done on master node)
```bash
docker node update --label-add name=node1 node1
docker node update --label-add name=node2 node2
docker node update --label-add name=node3 node3
```

# Create file system structure (Must be done in all nodes)
```bash
mkdir -p /opt/nifi/flow
mkdir -p /opt/nifi/work
mkdir -p /opt/nifi/logs
mkdir -p /opt/nifi/content_repository
mkdir -p /opt/nifi/database_repository
mkdir -p /opt/nifi/flowfile_repository
mkdir -p /opt/nifi/provenance_repository
mkdir -p /tmp/data
mkdir -p /opt/nifi
git clone https://github.com/m4rb3n/NiFiClusterSwarm.git
cd NiFiClusterSwarm
cp -r * /opt/nifi/ 
```

# Start swarm cluster
```bash
cd /opt/nifi
docker stack deploy --compose-file docker-compose.swarm.yml nificluster
```