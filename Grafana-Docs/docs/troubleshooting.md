# Troubleshooting

## Common Issues

- **Grafana Server Not Starting:**
    - Check the logs located at `/var/log/grafana/grafana.log`.
    - Ensure the service is running: `sudo systemctl status grafana-server`.

- **Datasource Not Connecting:**
    - Verify the URL and credentials.
    - Check the datasource service is running.
    - Check Grafana logs for errors.
