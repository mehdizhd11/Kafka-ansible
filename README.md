
```markdown
# Kafka KRaft Cluster Deployment (Ansible)

Automated deployment of a Zookeeper-less Kafka cluster using KRaft consensus mode.  
Deploys Java, Kafka, and configures a production-ready KRaft cluster with:  
- Controller-broker colocation  
- Automatic cluster ID generation  
- Systemd service management  

## inv.ini
```ini
[kafka]
Node-3 ansible_host=192.168.1.10 node_id=3
Node-2 ansible_host=192.168.1.11 node_id=2
Node-1 ansible_host=192.168.1.12 node_id=1

[all:vars]
ansible_user=ubuntu
```

## Roles

### java
- Installs OpenJDK 11
- Sets JAVA_HOME

### kafka 
- Deploys Kafka from binary
- Configures listeners and logs
- Creates systemd service

### kraft
- Sets up KRaft consensus
- Configures controller nodes  
- Config the nodes in cluster

## Usage
```bash
ansible-playbook -i inv.ini java.yml
ansible-playbook -i inv.ini kafka.yml  
ansible-playbook -i inv.ini kraft.yml
```

> **Note**: Requires minimum 3 nodes for production KRaft deployment
