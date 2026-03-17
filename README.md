# 📊 Manufacturing Process Monitoring with SQL
![manufacturing](https://github.com/user-attachments/assets/1d8be185-ef5d-4fe2-8ef8-86e4552d820b)

## Project Summary

Manufacturing processes require consistent monitoring to maintain product quality. Small variations in measurements are expected, but values outside an acceptable range may indicate process instability.

In this project, I used SQL window functions and Statistical Process Control (SPC) techniques to analyze manufacturing data and identify potential anomalies in product height measurements.

By calculating rolling statistics and control limits for each machine operator, the analysis detects when the manufacturing process may require adjustment.

## 🎯 Business Problem

Manufacturing teams need a systematic way to monitor product quality and detect deviations early.

The objective of this project is to:

Monitor height measurements of manufactured parts

Establish acceptable control limits

Identify measurements outside the normal variation range

Flag potential production issues using automated alerts

## 🗂 Dataset

The analysis uses the manufacturing_parts dataset.

Column	Description:
item_no	Unique identifier for each manufactured item
length	Length measurement of the part
width	Width measurement of the part
height	Height measurement of the part
operator	Machine/operator producing the part

The focus of this analysis is on height variation, which can indicate production inconsistencies.

## ⚙️ Analytical Approach
1️⃣ Rolling Process Monitoring

A rolling window of five recent observations was used to monitor short-term process variation.

ROWS BETWEEN 4 PRECEDING AND CURRENT ROW

This allows the analysis to capture the most recent production behavior for each operator.

2️⃣ Moving Statistics

Using SQL window functions:

Moving Average (avg_height)
Represents the expected product height within the window.

Moving Standard Deviation (stddev_height)
Measures variability in product height.

These statistics describe the current stability of the production process.

3️⃣ Control Limits

Using Statistical Process Control formulas:

UCL = avg_height + 3 * stddev_height / sqrt(5)
LCL = avg_height - 3 * stddev_height / sqrt(5)

Where:

UCL (Upper Control Limit) = highest acceptable measurement

LCL (Lower Control Limit) = lowest acceptable measurement

Values outside this range indicate potential anomalies.

4️⃣ Automated Alert Detection

A boolean alert flag identifies out-of-control measurements:

height NOT BETWEEN lcl AND ucl

If the condition is met:

alert = TRUE

This highlights potential production issues that may require investigation.

## 🧠 SQL Skills Demonstrated

This project demonstrates practical SQL skills used in real analytics work:

Window functions (OVER, PARTITION BY)

Rolling statistical calculations

Nested queries

Conditional logic (CASE)

Data filtering and transformation

Operational anomaly detection

## 📈 Example Output

operator	row_number	height	avg_height	stddev_height	ucl	lcl	alert

A	5	10.2	10.1	0.08	10.23	9.97	FALSE

A	6	10.5	10.15	0.09	10.27	10.03	TRUE

Rows where alert = TRUE represent potential process anomalies.

## 📌 Key Insights

Rolling statistical monitoring allows early detection of production instability.

Control limits provide a clear framework for identifying abnormal measurements.

SQL can be used not only for querying data but also for operational monitoring and quality control analysis.

## 🚀 Potential Improvements

Future extensions of this project could include:

Creating control charts using Python or visualization tools

Monitoring additional dimensions such as length and width

Integrating the analysis into a real-time monitoring dashboard

Automating alerts for manufacturing teams

## 🛠 Tools Used

SQL

Window Functions

Statistical Process Control (SPC)

## 👩‍💻 About This Project

This project is part of my Data Analyst portfolio, where I apply SQL and analytical methods to real-world datasets to extract insights and support data-driven decision-making.
