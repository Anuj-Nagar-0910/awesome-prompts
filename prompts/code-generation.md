# Code Generation Prompts


## **Prompt1: Advance Python Prompt for Analyzing data**

Hey there! I've got a bit of a data puzzle on my hands, and I could really use your help to automate some of it.

Imagine I'm managing a small e-commerce business, and I regularly download sales data from our online platform. This data comes to me as an Excel file, and it's usually pretty messy – not ideal for quick analysis.

Specifically, I get a new Excel file every week named `weekly_sales_data_YYYY-MM-DD.xlsx` (where YYYY-MM-DD is the date of the report, for example, `weekly_sales_data_2025-07-04.xlsx`).

Inside this Excel file, there's always a sheet named 'Raw Sales Data.' This sheet contains several columns, but the most important ones for my immediate needs are:

* **'Order ID'**: A unique identifier for each order.
* **'Customer Name'**: The name of the customer who placed the order.
* **'Product SKU'**: The Stock Keeping Unit for the product sold.
* **'Quantity Sold'**: The number of units of that product sold in the order.
* **'Sale Price (USD)'**: The price of the product at the time of sale.
* **'Order Date'**: The date the order was placed.
* **'Delivery Status'**: The current status of the order (e.g., 'Processing', 'Shipped', 'Delivered', 'Cancelled').

My goal is to use Python to:

1.  **Read the latest weekly sales data Excel file.** It should automatically find the most recent file in a specified directory (let's say all these files are in a folder named `C:\SalesReports\`).
2.  **Clean up the 'Sale Price (USD)' column.** Sometimes, this column might have text like '$' signs or commas. I need to convert it to a pure numeric format (float). If there are any blank cells in this column, they should be treated as `0.0`.
3.  **Calculate the 'Total Revenue' for each line item.** This would be `Quantity Sold * Sale Price (USD)`. Add this as a new column to the DataFrame.
4.  **Sort the data.** I need to sort the entire dataset primarily by 'Order Date' in ascending order, and then secondarily by 'Total Revenue' in descending order. This helps me see recent orders and their highest-value items first.
5.  **Filter out cancelled orders.** I'm only interested in active or completed orders, so any rows where 'Delivery Status' is 'Cancelled' should be removed.
6.  **Create a summary report.** I want to group the data by 'Customer Name' and calculate the total 'Total Revenue' for each customer. This summary should then be sorted by 'Total Revenue' in descending order, so I can see my top customers.
7.  **Generate a visual representation of top customers.** Using Matplotlib, I want a bar chart showing the 'Total Revenue' for the **top 10 customers** from the customer summary report.
    * The X-axis should display the 'Customer Name'.
    * The Y-axis should represent 'Total Revenue (USD)'.
    * The chart title should be 'Top 10 Customers by Total Revenue'.
    * The bars should be clearly labeled or the customer names should be readable, potentially rotating labels if needed.
8.  **Save the results.**
    * The cleaned and sorted main sales data should be saved into a *new* Excel file named `cleaned_sorted_sales_YYYY-MM-DD.xlsx` (using the same date as the original file), in a sheet named 'Cleaned Sales Data'.
    * The customer summary report should be saved into the *same* new Excel file, but in a separate sheet named 'Customer Summary'.
    * The generated bar chart for top customers should be saved as an image file named `top_customers_bar_chart_YYYY-MM-DD.png` (again, using the same date as the original file) in the same directory.

Could you please provide the Python code to achieve this? I'm looking for a script that I can run regularly to automate this process. Thanks a ton for your help!"





Okay, this is a fun challenge\! Here are three distinct, in-depth data analytics prompts, each leveraging a different programming language and set of tools for a real-world use case.

-----

## **Prompt 2: R and SQL for Customer Segmentation and Product Affinity Analysis**

Alright team, I've got a crucial task for our marketing department. We need to better understand our customer base and identify key segments to tailor our marketing campaigns. Our e-commerce data lives in a PostgreSQL database, and I need a robust analysis using R.

**Here's the scenario:** I want to perform a deep dive into our customer purchasing behavior. Specifically, I'm interested in:

  * **Customer Lifetime Value (CLV) Calculation:** How much revenue does each customer generate over their history with us?
  * **Customer Segmentation:** Can we categorize customers into meaningful groups based on their CLV?
  * **Product Affinity per Segment:** What types of products are most popular within each customer segment? This will inform our targeted promotions.

**Our Database Structure:**
We have the following tables in a PostgreSQL database, and you'll need to connect to it using appropriate R packages:

  * `customers`:
      * `customer_id` (Primary Key)
      * `first_name`
      * `last_name`
      * `email`
      * `registration_date`
  * `orders`:
      * `order_id` (Primary Key)
      * `customer_id` (Foreign Key referencing `customers`)
      * `order_date`
      * `total_amount` (USD)
  * `order_items`:
      * `order_item_id` (Primary Key)
      * `order_id` (Foreign Key referencing `orders`)
      * `product_id` (Foreign Key referencing `products`)
      * `quantity`
      * `price_at_purchase`
  * `products`:
      * `product_id` (Primary Key)
      * `product_name`
      * `category` (e.g., 'Electronics', 'Apparel', 'Home Goods', 'Books')
      * `brand`
      * `unit_price`

**Your Task using R and SQL:**

1.  **Database Connection:** Establish a connection to the PostgreSQL database. Assume the connection details (host, port, database name, user, password) will be provided as variables.
2.  **Data Extraction & Transformation (SQL & R):**
      * Write SQL queries to extract all necessary data: customer details, all their orders, and the categories of products they've purchased. You'll likely need to join `customers`, `orders`, `order_items`, and `products` tables.
      * Bring this data into R as a data frame.
      * Ensure `order_date` is in a proper date format in R.
3.  **Calculate Customer Lifetime Value (CLV):**
      * For each unique `customer_id`, calculate the sum of all `total_amount` from their orders. This will be their CLV.
4.  **Customer Segmentation (using CLV):**
      * Divide customers into three segments based on their CLV. A simple approach would be using quantiles:
          * **'High Value'**: Top 25% of CLV.
          * **'Medium Value'**: Middle 50% of CLV.
          * **'Low Value'**: Bottom 25% of CLV.
      * Add a new column, `customer_segment`, to your customer data.
5.  **Product Category Affinity Analysis:**
      * For each `customer_segment`, determine the most frequently purchased `category` of products.
      * Calculate the percentage distribution of product categories within each segment. For example, 'High Value' customers spend X% on 'Electronics', Y% on 'Apparel', etc.
6.  **Data Visualization (using `ggplot2` or similar):**
      * **CLV Distribution:** Create a histogram or density plot showing the distribution of CLV across all customers. Clearly label axes and add a title.
      * **Segment Composition:** Create a bar chart (or pie chart, though bars are often better for comparison) showing the number of customers in each segment.
      * **Product Category Preference by Segment:** Generate a *stacked bar chart* or *faceted bar charts* (one for each segment) showing the proportion of spending on different product categories within each segment. This is critical for marketing.
7.  **Reporting:**
      * Save the final segmented customer data (including CLV and segment) as a CSV file: `customer_segments_report_YYYY-MM-DD.csv`.
      * Save each generated plot as a high-resolution PNG image (e.g., `clv_distribution.png`, `segment_composition.png`, `product_affinity_by_segment.png`).

Please provide the complete R script, including SQL query examples embedded or executed via an R database package, to perform this analysis."

-----

## **Prompt 3: Python (PySpark) for Large-Scale Log Anomaly Detection**

"Alright, operations team, we're facing a massive influx of web server log data, and manually sifting through it for anomalies is impossible. I need a scalable solution using PySpark to automatically detect unusual patterns that might indicate performance issues or security threats.

**Here's the challenge:** We receive hourly Apache web server log files, dumped into a Google Cloud Storage (GCS) bucket. These files are huge, and we need to process them efficiently to identify red flags.

**Data Source:**
Our log files are in a GCS bucket, e.g., `gs://my-company-logs/apache_access/access_log_YYYY-MM-DD-HH.log`. Each line in these files is a standard Apache Common Log Format entry, roughly like this:
`192.168.1.1 - - [05/Jul/2025:10:05:01 +0000] "GET /index.html HTTP/1.1" 200 1234 "http://referrer.com" "Mozilla/5.0 (...)"`

**Your Task using Python with PySpark:**

1.  **Environment Setup:** Assume a PySpark environment is available (e.g., Dataproc cluster or local Spark setup). You'll need to configure Spark to read from GCS.
2.  **Data Ingestion & Parsing:**
      * Read all log files from a specified date range (e.g., last 24 hours, or a specific day) from the GCS bucket into a PySpark DataFrame.
      * Parse each raw log line into structured columns: `ip_address`, `timestamp` (as a proper timestamp type), `http_method`, `url_path`, `status_code`, `response_size_bytes`, `referrer`, `user_agent`. Handle any potential parsing errors gracefully (e.g., by logging malformed lines or setting fields to null).
      * Filter out any rows that couldn't be fully parsed.
3.  **Basic Aggregations & Metrics:**
      * Calculate the total number of requests.
      * Count occurrences of each `status_code` (especially 4xx and 5xx errors).
      * Determine the top 10 most requested `url_path`s.
      * Find the top 10 IP addresses by total requests.
4.  **Time-Based Analysis:**
      * Calculate the number of requests per minute.
      * Identify the peak traffic hour(s) and minute(s).
5.  **Anomaly Detection (Simplified):**
      * **Error Rate Spike:** Identify `url_path`s or `ip_address`es that experienced a sudden, significant increase (e.g., \> 3 standard deviations from the hourly average) in 4xx or 5xx status codes within a short time window (e.g., 5-minute intervals).
      * **Unusual IP Activity:** Find `ip_address`es that made an unusually high number of requests to non-existent pages (404 errors) or very high total requests compared to their historical average (if that data were available, otherwise compare to the overall average for the period). A simple threshold or standard deviation approach is fine.
6.  **Reporting & Output:**
      * Save the parsed, structured log data (e.g., for a specific day) into a new Parquet file in a separate GCS bucket (e.g., `gs://my-processed-logs/apache_structured/YYYY-MM-DD/`).
      * Output the aggregated metrics (status code counts, top URLs, top IPs, peak traffic times) to a simple text file or small CSV in a GCS output folder (e.g., `gs://my-analysis-results/apache_metrics_YYYY-MM-DD.txt`).
      * Output the detected anomalies (IPs, URLs, timestamps of anomalous events) to a separate JSON or CSV file in the same output folder (e.g., `apache_anomalies_YYYY-MM-DD.json`).

Please provide the complete PySpark script, including necessary imports and comments explaining each step. Assume the GCS bucket and date range will be passed as arguments or defined as variables."

-----

## **Prompt 4: JavaScript (Node.js & D3.js) for Real-time IoT Sensor Dashboard**

"I need a dynamic, real-time dashboard to monitor environmental conditions within our smart warehouse. We have an array of IoT sensors constantly reporting temperature and humidity, and I want a web interface that visualizes this data live.

**The Scenario:**
Our IoT sensors push data to a backend API. I need a web page that continuously fetches the latest readings and updates interactive charts without requiring a page refresh.

**Data Source:**
We have a hypothetical REST API endpoint: `https://api.mywarehousesensors.com/latest-readings`.
When queried, it returns a JSON array of sensor data like this:

```json
[
  {
    "sensorId": "WH-TEMP-001",
    "location": "Warehouse Zone A",
    "timestamp": "2025-07-05T15:30:00Z",
    "temperature_celsius": 22.5,
    "humidity_percent": 55.2
  },
  {
    "sensorId": "WH-HUM-002",
    "location": "Loading Dock",
    "timestamp": "2025-07-05T15:30:01Z",
    "temperature_celsius": 28.1,
    "humidity_percent": 70.5
  },
  // ... more sensor data
]
```

The API is designed to always return the *latest* reading for each sensor. We expect about 5-10 unique sensors.

**Your Task using JavaScript (Node.js for serving, D3.js for visualization):**

1.  **Basic Web Server (Node.js - Optional but recommended):** Create a simple Node.js Express server to serve an `index.html` file and the necessary JavaScript/CSS files. This provides a more robust setup for a web dashboard. Alternatively, you can just provide the client-side HTML/JS if server-side is out of scope.
2.  **HTML Structure (`index.html`):**
      * Create a basic HTML page.
      * Include a `div` element for each sensor that will host its real-time data and chart. Assign unique IDs to these divs (e.g., `sensor-chart-WH-TEMP-001`).
      * Link to a main JavaScript file (`dashboard.js`) and any CSS.
3.  **Real-time Data Fetching (`dashboard.js`):**
      * Write JavaScript code (client-side, using `fetch` API) to call `https://api.mywarehousesensors.com/latest-readings` every **5 seconds**.
      * Implement basic error handling for API calls (e.g., `console.error` on network issues or non-200 responses).
      * Parse the JSON response.
4.  **Dynamic Data Display:**
      * For each sensor in the fetched data, update a dedicated area on the HTML page to show its `sensorId`, `location`, `temperature_celsius`, and `humidity_percent`.
5.  **D3.js Live Line Charts:**
      * For each unique `sensorId`, create and manage a D3.js line chart that visualizes the `temperature_celsius` over time.
      * **Rolling Window:** The chart should display the last **20 data points** (or approximately the last 100 seconds of data, given a 5-second interval). As new data comes in, older data should gracefully 'scroll' off the left of the chart.
      * **Axes:**
          * X-axis: Time (formatted to show minutes/seconds).
          * Y-axis: Temperature in Celsius.
      * **Dynamic Updates:** The line chart should update smoothly as new data points are added.
      * **Labels & Title:** Each chart should have a title like 'Sensor [sensorId] Temperature' and clear axis labels.
      * **Tooltips (Optional but Recommended):** On hover over the line, display a tooltip showing the exact temperature and timestamp for that point.
6.  **Initial Load:** Ensure the dashboard loads correctly and populates charts with initial data immediately upon a page load, then begins its polling cycle.

Please provide the `index.html`, `dashboard.js` (and optionally a simple `server.js` if you choose to include the Node.js server setup) files. Focus on clear, well-commented JavaScript code for the D3.js visualizations and data handling."