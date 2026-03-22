## Architecture Recommendation

For a fast-growing food delivery startup managing a complex mix of GPS location logs, customer text reviews, payment transactions, and restaurant menu images, I strongly recommend implementing a **Data Lakehouse** architecture. 

A Data Lakehouse merges the flexible, low-cost storage capabilities of a Data Lake with the robust data management and ACID transactional features of a traditional Data Warehouse. Here are three specific reasons for this choice:

First, it natively supports **diverse data types**. The startup is collecting structured data (payments), semi-structured data (GPS logs), and completely unstructured data (text reviews and menu images). A traditional Data Warehouse cannot store images or raw text efficiently, whereas a Lakehouse uses cheap object storage to house all these formats in a single, unified repository.

Second, a Lakehouse provides **ACID transaction guarantees** (using open table formats like Delta Lake or Apache Iceberg). Payment transactions require absolute strictness and reliability. A pure Data Lake struggles with updates and data consistency, but a Lakehouse ensures that critical financial data is accurately recorded, updated, and queried without risking corruption.

Third, it enables **unified analytics and streaming**. The startup needs to ingest high-velocity GPS logs in real-time while simultaneously running analytical queries. A Lakehouse prevents the "data silo" problem by allowing data scientists to run machine learning models on text/images, while business analysts run SQL queries on payments—all directly on the same underlying storage architecture, drastically reducing ETL overhead.
