# Install grafana-server

# Create grafana.repo in "/etc/yum.repos.d/" path
    vi /etc/yum.repos.d/grafana.repo
    ---------------------------------------------
    [grafana]
    name=grafana
    baseurl=https://packages.grafana.com/oss/rpm
    repo_gpgcheck=1
    enabled=1
    gpgcheck=1
    gpgkey=https://packages.grafana.com/gpg.key
    sslverify=1
    sslcacert=/etc/pki/tls/certs/ca-bundle.crt
# Install grafana
    yum install grafana -y
# Start grafana server
    service grafana-server start
# Check status of grafana server
    service grafana-server status
# Check grafana in UI
  ![image](https://user-images.githubusercontent.com/58024415/100535883-c9373180-3242-11eb-8e7e-6dbd6f768929.png)

    username: admin
    password: admin
  
  Change Password:
  
  ![image](https://user-images.githubusercontent.com/58024415/100535904-f388ef00-3242-11eb-8342-6ccbed5a1687.png)
  
  Grafana UI:
  
  ![image](https://user-images.githubusercontent.com/58024415/100535908-03083800-3243-11eb-8672-321d8bc670e4.png)
# Stop status of grafana server
    service grafana-server stop
