# Grafana Documentation 
Welcome to the Grafana documentation. Here you will find all the necessary information to install and configure grafana. 
For full documentation visit [grafana.com](https://grafana.com/docs/grafana/latest/).

## Project layout

    grafana docs/
        - index.md  # The documentation homepage.
        - installation.md
        - configuration.md
        - datasources.md
        - dashboards.md
  

## What is Grafana ?
   Grafana is a multi-platform open source analystics and interactive visualization web application.It provides

   - **Charts**
   - **Graphs**
   - **Alerts**
![image not available](image.png)
## Features 
   - **Visualize**: Grafana has a plethora of visualization options to help you understand your data beautifully.
   - **Alert** : Seamlessly define alerts where it makes sense- while you're in data 
   - **Unify** : Grafana supports dozens of databases,natively.Mix them together in the same Dashboard 
   - **Open Source**: Grafana is completely open source, and backed by a vibrant community.
   - **Extend** : Discover hundreds of dashboards and plugins in the ooficial library

# Steps for installation

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


# Datasource


**- Adding a Prometheus Datasource**

1. Go to `Configuration > Data Sources`.

2. Click on `Add data source`.

3. Select `Prometheus` from the list.

4. Configure the following settings:
    - **Name:**  Prometheus
    - **URL:**  http://localhost:9090   



5. Click `Save & Test`.


# Dashboards

**Creating a New Dashboard**

1. Click on the `+` icon in the sidebar and select `Dashboard`.
2. Click `Add new panel`.
3. Click `Save` and give your dashboard a name.


# Troubleshooting

## Common Issues

- **Grafana Server Not Starting:**
    - Check the logs located at `/var/log/grafana/grafana.log`.
    - Ensure the service is running: `sudo systemctl status grafana-server`.

- **Datasource Not Connecting:**
    - Verify the URL and credentials.
    - Check the datasource service is running.
    - Check Grafana logs for errors.
