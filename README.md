<div align="center">
    <a href="https://github.com/softspiders/softspiders">
      <img src="https://avatars.githubusercontent.com/u/47006425?v=4"width="100" height="100"/>
    </a>
</div> 

# Spring application starter exporting metrics for Prometheus


## Feature tags

- actuator
- maven
- prometheus
- spring
- starter
- swagger
- template

---

## Direct ancestor

[- prometheus](https://github.com/AlexanderLapygin/spring-actuator#readme)

---

## Author

[Alexander Lapygin](https://github.com/AlexanderLapygin) <<alexanderlapygin@gmail.com>>

---

## Run

```sh
mvnw spring-???:run
```

# Check Swagger

Take a look at http://localhost:8080/swagger-ui.html.

# Check Actuator

Take a look at actuator endpoints at http://localhost:8080/actuator.

# Check how the actuator exports metrics for Prometheus 

Take a look at actuator endpoints at http://localhost:8080/actuator/prometheus.

# Setting up and running Prometheus

To set up Prometheus for monitoring your Spring application, follow these steps:

1. Download the [latest release](https://prometheus.io/download/) of Prometheus for your operating system.
2. Extract the files from the archive.
3. Open the `prometheus.yml` configuration file in a text editor.
4. Add the following job to the `scrape_configs` section:
```yaml
- job_name: 'spring'
  metrics_path: '/actuator/prometheus'
  static_configs:
    - targets: ['localhost:8080']
```
This configuration tells Prometheus to scrape metrics from the `/actuator/prometheus` endpoint of your Spring application running on `localhost:8080`.
5. Save the `prometheus.yml` file and start Prometheus locally by running the `prometheus` executable:
```shell
prometheus --config.file=prometheus.yml
```
6. Open Prometheus in your web browser by going to `http://localhost:9090`.
7. In the query field ("Expression"), enter the name of the metric associated with the /hello query. For example, if you used the following configuration to enable /hello monitoring:
```
http_server_requests_seconds_bucket{uri="/hello"}
```
8. Select "Graph" from the top menu.
9. Click the "Execute" button.

That's it! Now you have Prometheus set up to monitor your Spring application and collect metrics.

# Setting up and running Grafana locally

To set up Grafana for monitoring your Spring application, follow these steps:

1. Download the [latest release](https://grafana.com/grafana/download) of Grafana for your operating system.
2. Run the installer and follow the instructions on the screen. Select the installation path and other settings as needed.
3. Start Grafana located in the bin directory from the command line:
```sh
grafana-server
```
4. Open a browser and enter http://localhost:3000/ to open the Grafana web interface.
5. On first launch, you will be prompted to log in. The default administrator username and password is *admin*.
6. After logging in, you can set up data sources and create dashboards to visualize metrics.

### License

Licensed under the [MIT license](./LICENSE)

---

[SOFTSPIDERS](https://github.com/softspiders/softspiders)
