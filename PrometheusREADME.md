# Run Prometheus As A Service

# Download Prometheus using below link
    wget https://github.com/prometheus/prometheus/releases/download/v2.23.0/prometheus-2.23.0.linux-amd64.tar.gz
# Extract tar file
    tar xvzf prometheus-2.23.0.linux-amd64.tar.gz
# Rename file name
    mv prometheus-2.23.0.linux-amd64/ prometheus-2.23.0

# Create a file prometheus.service:
    vi /etc/systemd/system/prometheus.service
    ---------------------------------------------------------------------
    [Unit]
    Description=Prometheus
    Documentation=https://prometheus.io/docs/introduction/overview/
    After=network-online.target
		
    [Service]
    User=root
    Restart=on-failure
		
    #Change this line if you download the
    #Prometheus on different path user
    ExecStart=/opt/prometheus-2.23.0/prometheus \
	--config.file=/opt/prometheus-2.23.0/prometheus.yml \
	--storage.tsdb.path=/opt/prometheus-2.23.0/data \
	--web.console.templates=/opt/prometheus-2.23.0/consoles \
	--web.console.libraries=/opt/prometheus-2.23.0/console_libraries
	
    [Install]
    WantedBy=multi-user.target
# Reload the Systemctl Daemon:
    systemctl daemon-reload
# Start the Prometheus service:
    service prometheus start
# Check status of Prometheus:
    service prometheus status
# Stop the Prometheus service:
    service prometheus stop
# Make Less secure app access: ON
  Login to Gmail.
  Access the URL as https://www.google.com/settings/security/lesssecureapps
  
  ![image](https://user-images.githubusercontent.com/58024415/100221905-53c81a00-2f3f-11eb-8edd-2e7f6c1e218c.png)
# DisplayUnlockCaptcha need to be continue
  URL: https://accounts.google.com/DisplayUnlockCaptcha
  Before:
  
  ![image](https://user-images.githubusercontent.com/58024415/100222050-8d992080-2f3f-11eb-8db1-f47c39f172e4.png)

  After:
  
  ![image](https://user-images.githubusercontent.com/58024415/100222121-a3a6e100-2f3f-11eb-8d52-9b8f1c8a9b23.png)
# Configure Node-Exporter and Alert Manager with prometheus
Pre-Requisites:
  
    Run Node-Exporter
    Run Alert Manager
  step1: Create prometheus.yml and rules.yml files in side /opt/prometheus-2.23.0
  step2: Restart prometheus 
  
    service prometheus restart
  Check alerts in prometheous UI: <ip-address>:9090
  
  ![image](https://user-images.githubusercontent.com/58024415/100535236-2334f880-323d-11eb-9155-bec99c1c406f.png)
  
  Check alerts status in prometheous UI: <ip-address>:9090
	
  ![image](https://user-images.githubusercontent.com/58024415/100535151-4c08be00-323c-11eb-89d3-314156f914d1.png)
  
  Again check alerts status in prometheous UI: <ip-address>:9090
	
  ![image](https://user-images.githubusercontent.com/58024415/100535156-53c86280-323c-11eb-8c2f-0d67f6b7f9bb.png)
 
  Check alert manager in UI: <ip-address>:9093
	
  ![image](https://user-images.githubusercontent.com/58024415/100535171-6fcc0400-323c-11eb-9760-c755779e1bac.png)
  
  Check mail which we gave in alertmanager.yml
  
  ![image](https://user-images.githubusercontent.com/58024415/100535302-aa826c00-323d-11eb-88de-59d6d004ecbb.png)
  
  
  
