# Introduction

The **Onibex One Connect SAP Data Modeler** is a **low-code / no-code** tool designed to model SAP Entities (Foundational Data Products) by connecting SAP tables and CDS Views through Inner or Left Outer Joins, without requiring ABAP development or custom coding.

As a core component of the One Connect Connector for SAP, the Data Modeler pushes data and metadata to the Smart Gateway in either **batch** or **real-time** mode, leveraging SAP standard mechanisms such as **BOR**, **RAP**, **BTE**, and **PPF**. This enables enterprises to extend pre-packaged Data Products or build custom ones to feed downstream platforms, including Databricks, Snowflake, and ClickHouse, through Kafka.

The table below outlines key features of the **SAP Data Modeler**, showcasing out-of-the-box functionalities that support entity modeling, real-time replication, and seamless integration with the OneConnect platform.

| No | Function | Description |
|---|---|---|
| 1 | Low-Code / No-Code Modeling | SAP Data Modeler enables users to design SAP Entities visually by connecting tables and CDS Views, eliminating the need for ABAP coding or custom development. |
| 2 | Table and CDS View Joins | Build Foundational Data Products by joining SAP tables and CDS Views using **Inner Join** or **Left Outer Join** operations through an intuitive visual interface. |
| 3 | Table Format Replication | Converts each SAP table or CDS View into an individual Kafka topic in a CDC-like (Change Data Capture) pattern, ideal for granular, field-level downstream consumption. |
| 4 | Document Format Replication | Converts entire SAP documents (e.g., a complete Sales Order with header, items, partners, and schedule lines) into nested Kafka topics in an IDOC-like structure. |
| 5 | Real-Time Data Streaming | Pushes data and metadata to the Smart Gateway in real time using SAP standard event mechanisms: **BOR**, **RAP**, **BTE**, and **PPF**. |
| 6 | Batch Mode Replication | Supports batch extraction for initial loads, historical synchronization, or scheduled refreshes when real-time streaming is not required. |
| 7 | Metadata Propagation | Automatically extracts and propagates SAP metadata to the Smart Gateway, where it is translated into Kafka schemas and serialized in Avro format. |
| 8 | Extension of Pre-Packaged Data Products | Customers can extend any of the 150+ pre-packaged Foundational Data Products from the One Connect Data Market by adding custom tables, CDS Views, and fields. |
| 9 | Real-Time Inserts, Updates, and Deletes | Ensures every connected downstream system reflects the most accurate SAP information by propagating all data changes (INSERT, UPDATE, DELETE) in real time. |
| 10 | SAP-Verified Integration | The only SAP-verified technology for extracting real-time data and metadata, available in the SAP Store and compliant with SAP standards for security, scalability, and licensing. |
