# minitor-prometheus
monitor linux server using prometheus

### Login to your aws and ssh the key into the perminal
<img width="1087" height="611" alt="Screenshot 2025-09-30 at 3 27 11 pm" src="https://github.com/user-attachments/assets/b88ff60c-cddc-409a-948e-d5c7122a5d4a" />

### install prometheus node exporter
run this command curl -LO https://github.com/prometheus/node_exporter/releases/latest/download/node_exporter-linux-amd64.tar.gz
<img width="1397" height="161" alt="Screenshot 2025-09-29 at 1 41 32 pm" src="https://github.com/user-attachments/assets/f3680ce8-c444-4378-8b08-211c36e813ca" />

### extract the downloaded terball
<img width="1440" height="549" alt="Screenshot 2025-09-29 at 1 45 04 pm" src="https://github.com/user-attachments/assets/161bc96d-e48d-4c59-b897-d27f3087c2a4" />
### extract the downloaded terball done
<img width="1053" height="103" alt="Screenshot 2025-09-29 at 1 45 45 pm" src="https://github.com/user-attachments/assets/5347d252-f921-4099-91a2-250f63c98c09" />
### move the binary to a directory in your PATH
<img width="899" height="67" alt="Screenshot 2025-09-29 at 1 47 24 pm" src="https://github.com/user-attachments/assets/989d4bbc-aeb9-4125-a1b1-ecbeea6f0103" />

### create a systemd service file for node exporter by running the command " sudo nano /etc/systemd/system/node_exporter.service
 past in the code inside the file 

 [Unit]
Description=Prometheus Node Exporter
After=network.target

[Service]
User=nobody
ExecStart=/usr/local/bin/node_exporter
Restart=always

[Install]
WantedBy=multi-user.target

 
 "<img width="996" height="852" alt="Screenshot 2025-09-29 at 1 49 57 pm" src="https://github.com/user-attachments/assets/a3eed4fe-5017-49a9-a0c6-dc7812bf0057" />

### Reload systemd and start the node exporter service to the following commands

sudo systemctl daemon-reload
sudo systemctl start node_exporter
sudo systemctl enable node_exporter

<img width="1323" height="124" alt="Screenshot 2025-09-29 at 1 52 35 pm" src="https://github.com/user-attachments/assets/4754357a-3c1b-4192-9ab5-8ec3862ab427" />

### verify that node exporter is runing with this command

 <img width="1434" height="395" alt="Screenshot 2025-09-29 at 2 00 58 pm" src="https://github.com/user-attachments/assets/7f39e919-94a8-4375-ad0b-64cf2f8400f8" />

### confirm node exporter is accessible by visiting http://http://18.215.150.215:9100/
<img width="1440" height="407" alt="Screenshot 2025-09-30 at 2 40 07 pm" src="https://github.com/user-attachments/assets/c9d60563-b4c2-46c5-ae89-b4ac81b8aead" />

 
