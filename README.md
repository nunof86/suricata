# Documentation

## See the full documentation on https://documentation-com.gitbook.io/suricata-installation/

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

# Suricata Configuration

## Suricata.yaml Configuration File

1. First you need to go to <mark style="color:red;">`/etc/suricata/suricata.yaml`</mark> and edit the <mark style="color:red;">`HOME_NET`</mark> and the <mark style="color:red;">`interface`</mark>.

```yaml
vars:
    address-groups:
        HOME_NET: "[network/prefix]" 
```

```yaml
af-packet:
    - interface: your_interface
```

## Rules Update

```bash
sudo suricata-update
```

## Restart Suricata Service

```bash
sudo systemctl restart suricata
```

## Rule Creation

1. The <mark style="color:red;">**suricata rules**</mark> are stored in the <mark style="color:red;">`/usr/share/suricata/rules`</mark>.
2. To create a <mark style="color:red;">**rule**</mark> you can create a file with the extension <mark style="color:red;">`.rule`</mark>,  for example <mark style="color:red;">`test.rule`</mark> and add the following:

```firestore-security-rules
alert ip any any -> any any (msg:"GPL ATTACK_RESPONSE id check returned root"; content:"uid=0|28|root|29|"; classtype:bad-unknown; sid:2100498; rev:7; metadata:created_at 2010_09_23, updated_at 2010_09_23;)
```
