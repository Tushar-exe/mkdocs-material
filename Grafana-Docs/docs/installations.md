# Steps for Installing Grafana:

1) **Add Grafana GPG key and repository:**

     ```sh
    wget -q -O gpg.key https://rpm.grafana.com/gpg.key
    sudo rpm --import gpg.key
    ```

2) **Create a yum package manager to include the grafana repository:**

    ```sh
    Note: for creating this file we need a ROOT access for it, otherwise it will give us an error stating "/etc/yum.repos.d/grafana.repo" E212: Can't open file for 
    writing.
    "vi /etc/yum.repos.d/grafana.repo"
    [grafana]
    name=grafana
    baseurl=https://rpm.grafana.com
    repo_gpgcheck=1
    enabled=1
    gpgcheck=1
    gpgkey=https://rpm.grafana.com/gpg.key
    sslverify=1
    sslcacert=/etc/pki/tls/certs/ca-bundle.crt
    ```
3) **Start and enable Grafana service:**

    ```sh
    (please execute the following statements to configure grafana to start automatically using systemd)
    sudo systemctl daemon-reload
    sudo systemctl enable grafana-server.service
    sudo stemctl start grafana-server.service
    ```
4) **Access Grafana:**

    Open your browser and go to `http://10.208.34.9:3000`. The default login is `admin` and password is `admin`.

    ( Note: Grafana by default runs on port no: 3000 and why 10.208.34.9 because we have installed this on shreshta cluster)
    
## Steps for Uninstallating Grafana

1. sudo yum remove grafana

If you want to remove Grafana completely, you need to delete all the directories that Grafana creates during installation. To do this, you will need to run certain commands. However, make sure you only use these commands if you're certain you want to delete Grafana entirely.

2. sudo rm -rf /etc/grafana /var/lib/grafana /var/log/grafana