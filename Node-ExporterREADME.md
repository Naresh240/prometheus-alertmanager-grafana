# Run Node Exporter As Service:

# Download The Binary File
    cd /opt
    wget https://github.com/prometheus/node_exporter/releases/download/v0.18.1/node_exporter-0.18.1.linux-amd64.tar.gz
# Extract tar file
    tar xvzf node_exporter-0.18.1.linux-amd64.tar.gz
# Rename file
    mv node_exporter-0.18.1.linux-amd64/ node_exporter-0.18.1
 # Create a file in "/etc/systemd/system/node-exporter.service" path:
    vi /etc/systemd/system/node-exporter.service
    -----------------------------------------------------------------
    [Unit]
    Description=Node exporter
    After=network-online.target

    [Service]
    User=root
    Restart=on-failure

    #Change this line if you download the node_exporter on different path user
    ExecStart=/opt/node_exporter-0.18.1/node_exporter

    [Install]
    WantedBy=multi-user.target
# Reload the systemctl daemon:
    systemctl daemon-reload
# Start the Prometheus service:
    service node-exporter start
# Check status of node-exporter:
    service node-exporter status
# Stop the Prometheus service:
    service node-exporter stop
