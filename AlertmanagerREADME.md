# Run alertmanager As A Service

# Download alertmanager using below link
    cd /opt
    wget https://github.com/prometheus/alertmanager/releases/download/v0.21.0/alertmanager-0.21.0.linux-amd64.tar.gz
# Extract tar file
    tar xvzf alertmanager-0.21.0.linux-amd64.tar.gz
# Rename file name
    mv alertmanager-0.21.0.linux-amd64/ alertmanager-0.21.0

# Create a file "/etc/systemd/system/alertmanager.service":
    [Unit]
    Description=alertmanager
    After=network-online.target

    [Service]
    User=root
    Restart=on-failure

    #Change this line if you download the alertmanager on different path user
    ExecStart=/opt/alertmanager-0.21.0/alertmanager \
      --config.file=/opt/alertmanager-0.21.0/alertmanager.yml \

    [Install]
    WantedBy=multi-user.target
# Reload the Systemctl Daemon:
    systemctl daemon-reload
# Start the Prometheus service:
    service alertmanager start
# Check status of Prometheus:
    service alertmanager status
# Stop the alertmanager service:
    service alertmanager stop
