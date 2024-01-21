# Prerequisites

## System Update

```bash
sudo apt update && sudo apt full-upgrade -y
```

## Curl Installation

```bash
sudo apt install curl -y
```

## Ansible Installation

```bash
sudo apt install ansible -y
```

## Package Software Properties Common Installation

```bash
sudo apt-get install software-properties-common -y
```

## Suricata Installation

### Add the Repository

```bash
sudo add-apt-repository ppa:oisf/suricata-stable
```

### Suricata Installation

```bash
sudo apt-get update
sudo apt-get install suricata -y
```
