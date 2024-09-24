# **Introduction to Grafana and Prometheus**

This document serves as a beginner's guide to understanding Grafana and Prometheus, how they work together, and how to perform queries using Grafana and PromQL. It is tailored for developers working with Spring Boot applications but is applicable to a broader audience interested in application monitoring and data visualization.

---

## **Table of Contents**

1. [What is Grafana?](#what-is-grafana)
2. [What is Prometheus?](#what-is-prometheus)
3. [Integrating Spring Boot with Prometheus](#integrating-spring-boot-with-prometheus)
4. [Setting Up Grafana with Prometheus](#setting-up-grafana-with-prometheus)
5. [Basics of PromQL (Prometheus Query Language)](#basics-of-promql)
6. [Creating Queries in Grafana](#creating-queries-in-grafana)
7. [Visualizing Data in Grafana](#visualizing-data-in-grafana)
8. [Advanced Features and Best Practices](#advanced-features-and-best-practices)
9. [Additional Resources](#additional-resources)

---

## **1. What is Grafana?**

Grafana is an open-source platform for data visualization, monitoring, and analysis. It allows you to create interactive and dynamic dashboards to visualize metrics from various data sources.

**Key Features:**

- **Customizable Dashboards:** Create dashboards with panels that display data in graphs, charts, and other visualizations.
- **Data Source Agnostic:** Supports various data sources like Prometheus, InfluxDB, MySQL, and more.
- **Alerting:** Set up alerts to notify you when certain conditions are met.
- **Templating:** Use variables to create dynamic and reusable dashboards.

**Official Website:** [https://grafana.com](https://grafana.com)

---

## **2. What is Prometheus?**

Prometheus is an open-source systems monitoring and alerting toolkit. It collects and stores metrics as time-series data, recording information with a timestamp.

**Key Features:**

- **Multidimensional Data Model:** Uses key/value pairs called labels to identify data.
- **Powerful Query Language (PromQL):** Allows for flexible and accurate querying.
- **Service Discovery:** Automatically discovers targets to scrape metrics from.
- **Alerting Integration:** Works with Alertmanager for handling alerts.


---

## **3. Integrating Spring Boot with Prometheus**

To monitor a Spring Boot application using Prometheus, you need to expose the application's metrics in a format Prometheus can scrape.

### **3.1. Add Dependencies**

Add the following dependencies to your `pom.xml` (for Maven) or `build.gradle` (for Gradle):

```xml
<!-- Micrometer Prometheus Registry -->
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>

<!-- Spring Boot Actuator -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

### **3.2. Configure Actuator Endpoints**

Enable the Prometheus endpoint in your `application.properties` or `application.yml`:

```properties
management.endpoints.web.exposure.include=prometheus
management.endpoint.prometheus.enabled=true
```

### **3.3. Expose Metrics**

With Micrometer and Actuator, your application now exposes metrics at `/actuator/prometheus`.

### **3.4. Create Custom Metrics (Optional)**

You can create custom metrics using the `MeterRegistry` provided by Micrometer.

**Example:**

```java
import io.micrometer.core.instrument.Counter;
import io.micrometer.core.instrument.MeterRegistry;
import org.springframework.stereotype.Component;

@Component
public class CustomMetrics {

    private final Counter customCounter;

    public CustomMetrics(MeterRegistry registry) {
        customCounter = registry.counter("custom_metric_counter");
    }

    public void incrementCounter() {
        customCounter.increment();
    }
}
```

---

## **4. Setting Up Grafana with Prometheus**

### **4.1. Install Prometheus**

Download and install Prometheus from the [official download page](https://prometheus.io/download/).

### **4.2. Configure Prometheus**

Create a `prometheus.yml` configuration file:

```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'spring_boot_app'
    metrics_path: '/actuator/prometheus'
    static_configs:
      - targets: ['localhost:8080']
```

**Note:** Adjust `targets` based on your application's host and port.

### **4.3. Run Prometheus**

Start Prometheus using the configuration file:

```bash
./prometheus --config.file=prometheus.yml
```

### **4.4. Install Grafana**

Download and install Grafana from the [official download page](https://grafana.com/get).

### **4.5. Start Grafana**

Start Grafana and access it via `http://localhost:3000`.

### **4.6. Add Prometheus as a Data Source in Grafana**

1. Log in to Grafana (default credentials are **admin/admin**).
2. Click on the **gear icon** (⚙️) in the sidebar and select **Data Sources**.
3. Click **Add data source** and choose **Prometheus**.
4. Set the **URL** to `http://localhost:9090`.
5. Click **Save & Test** to verify the connection.

---

## **5. Basics of PromQL**

PromQL (Prometheus Query Language) is a powerful query language used to retrieve and manipulate time-series data stored in Prometheus.

### **5.1. Data Types in Prometheus**

- **Instant Vector:** A set of time-series data at a single point in time.
- **Range Vector:** A set of time-series data over a range of time.

### **5.2. Basic Query Structure**

- **Metric Names:** The name of the metric you want to query (e.g., `http_requests_total`).
- **Labels:** Key-value pairs used to filter metrics (e.g., `{method="GET"}`).

**Example:**

```promql
http_requests_total{method="GET", status="200"}
```

### **5.3. Operators**

- **Arithmetic Operators:** `+`, `-`, `*`, `/`, `%`, `^`
- **Comparison Operators:** `==`, `!=`, `>`, `<`, `>=`, `<=`
- **Logical Operators:** `and`, `or`, `unless`

### **5.4. Functions**

- **Aggregation Functions:**

  - `sum()`: Sum of values across labels.
  - `avg()`: Average of values.
  - `max()`: Maximum value.
  - `min()`: Minimum value.
  - `count()`: Count of elements.

- **Time Functions:**

  - `rate()`: Calculates the per-second average rate of increase.
  - `irate()`: Calculates the instantaneous rate of increase.

**Example:**

```promql
sum(rate(http_requests_total[5m])) by (method)
```

---

## **6. Creating Queries in Grafana**

### **6.1. Create a New Dashboard and Panel**

1. Click on the **plus icon** (+) in the sidebar and select **Dashboard**.
2. Click **Add new panel**.

### **6.2. Configure the Query**

1. In the **Query** tab, ensure your Prometheus data source is selected.
2. Enter your PromQL query.

**Example:**

```promql
rate(http_requests_total[1m])
```

3. Use the **Legend** field to name your series.

### **6.3. Apply Time Filters**

Grafana automatically uses the dashboard's time range, but you can override it in the panel settings if needed.

---

## **7. Visualizing Data in Grafana**

### **7.1. Choose Visualization Type**

Select the visualization type that best represents your data:

- **Graph:** For time-series data.
- **Stat:** For single number summaries.
- **Table:** For tabular data.
- **Gauge/Bar Gauge:** For showing current values relative to thresholds.

### **7.2. Customize Panel Appearance**

- **Axes:** Adjust scales, units, and labels.
- **Visualization Options:** Modify line styles, point sizes, and fill options.
- **Thresholds:** Set thresholds to highlight critical values.

### **7.3. Save and Organize Dashboards**

- Click **Apply** to save the panel.
- Use folders to organize dashboards.
- Set dashboard permissions if needed.

---

## **8. Advanced Features and Best Practices**

### **8.1. Using Variables in Dashboards**

Variables make your dashboards dynamic and reusable.

**Steps:**

1. Click on the **gear icon** (⚙️) and select **Variables**.
2. Click **Add variable**.
3. Choose the variable type (e.g., **Query**, **Custom**).
4. Use the variable in queries with `$variableName`.

**Example:**

```promql
rate(http_requests_total{method="$method"}[5m])
```

### **8.2. Setting Up Alerts**

1. In the panel editor, navigate to the **Alert** tab.
2. Define alert conditions and thresholds.
3. Configure notification channels (e.g., email, Slack).

### **8.3. Dashboard Annotations**

Annotations help you correlate data with events.

- Add annotations manually or query-based.
- Display them on graphs as markers.

### **8.4. Best Practices**

- **Label Management:** Use consistent and meaningful labels to avoid high cardinality.
- **Data Retention:** Configure Prometheus retention policies based on storage and requirements.
- **Performance Optimization:** Use recording rules in Prometheus to precompute frequently used queries.
