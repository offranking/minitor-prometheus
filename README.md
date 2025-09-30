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

### on this part we need to open the prometheus configurations file called (prometheus.yml)
run this command sudo nano /etc/prometheus/prometheus.yml

<img width="936" height="28" alt="Screenshot 2025-09-30 at 3 59 25 pm" src="https://github.com/user-attachments/assets/aa507d33-dc8f-4300-910b-74e5c07085f1" />

### Add a new scrape job for node exporter

<img width="996" height="897" alt="Screenshot 2025-09-30 at 4 00 54 pm" src="https://github.com/user-attachments/assets/f9fbd07d-2ccb-42ef-a655-b5fa32060828" />

### Now we have to give permission to the file 

<img width="981" height="81" alt="Screenshot 2025-09-30 at 4 04 16 pm" src="https://github.com/user-attachments/assets/7436d3d3-9236-49d5-a03d-26376152e61b" />

### we need to save the file and restart the prometheus to apply the changes
run this command "sudo systemctl restart prometheus"

<img width="1035" height="864" alt="Screenshot 2025-09-30 at 4 05 02 pm" src="https://github.com/user-attachments/assets/db29be15-52c8-435f-933b-a123ba90846e" />

### verify the port  "sudo ss -tlnp | grep 9090"

<img width="961" height="62" alt="Screenshot 2025-09-30 at 4 09 21 pm" src="https://github.com/user-attachments/assets/d4645495-3997-4647-8adb-6227b95a812e" />

### Access the prometheus web interface http://18.215.150.215:9090/

<img width="1440" height="547" alt="Screenshot 2025-09-30 at 3 18 23 pm" src="https://github.com/user-attachments/assets/d593cbe2-8716-40e0-a120-be8e1ddd1478" />

### to view the CPU
<img width="996" height="815" alt="Screenshot 2025-09-30 at 3 21 27 pm" src="https://github.com/user-attachments/assets/79e59f6b-11e1-47e2-8a40-95b5ee9a3a66" />
