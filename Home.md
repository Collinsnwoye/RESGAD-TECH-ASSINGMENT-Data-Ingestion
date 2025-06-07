# Data Ingestion

Once you’ve assessed your data sources—their structure, origin, and storage format—the next step is bringing that data into your system. This stage, called **data ingestion**, is where raw data begins its journey into your analytics ecosystem.

From real-world practice, ingestion and source systems often present some of the **greatest challenges** in a data pipeline. These systems are often external and may behave unpredictably—slowing down, failing to respond, or providing inconsistent or low-quality data. Similarly, your ingestion processes might break due to configuration issues, schema drift, or infrastructure problems. When ingestion fails, it can delay or completely halt data movement, which impacts downstream processing and insights.

---

###  **Key Considerations for Building an Ingestion Layer**

When planning or implementing ingestion pipelines, keep these engineering questions in mind:

- **What is the intended use of this data?**  
  Can a single version of the data serve multiple needs, reducing duplication?

- **How dependable are the source and ingestion mechanisms?**  
  Is the data available when required, and are failures gracefully handled?

- **Where is the data headed?**  
  Identify the destination system or data store that will receive the ingested data.

- **How often is the data needed?**  
  Is this a real-time use case or a batch scenario?

- **How much data should I expect?**  
  Estimate the volume and velocity of incoming data to ensure scalability.

- **What format does the data arrive in?**  
  Ensure compatibility with downstream systems and their format requirements.

- **Is the data ready for use immediately after ingestion?**  
  If yes, for how long will that remain true, and what factors might change it?

- **Do streaming inputs require pre-processing?**  
  In some cases, it may be useful to apply transformations *in-flight*, directly within the data stream before it lands in your system.

---
### Data Ingestion Patterns: Batch vs. Streaming

Understanding how data enters your systems is foundational to designing scalable, efficient pipelines. Two major paradigms influence ingestion architecture: **batch vs. streaming**

Most data is naturally generated as a continuous stream, even if we often process it in larger segments called batches. 

**Batch ingestion** collects and transfers data at scheduled intervals or once a certain volume is reached. This method has long been the standard, especially for reporting and training machine learning models, due to its simplicity and reliability.

**Streaming ingestion**, by contrast, delivers data in near real-time—within seconds or milliseconds of creation. This approach supports more immediate insights and reactions, enabling use cases like fraud detection, real-time dashboards, or continuous model training.

