# Steps for Installing Grafana:

1) **Add Grafana GPG key and repository:**

     ```sh
    sudo wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
    sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
    ```

2) **Install Grafana:**

    ```sh
    sudo apt-get update
    sudo apt-get install grafana
    ```
3) **Start and enable Grafana service:**

    ```sh
    sudo systemctl start grafana-server
    sudo systemctl status grafana-server
    sudo systemctl enable grafana-server
    ```
4) **Access Grafana:**

    Open your browser and go to `http://localhost:3000`. The default login is `admin` and password is `admin`.

    ( Note: Grafana by default runs on port no: 3000 )
    