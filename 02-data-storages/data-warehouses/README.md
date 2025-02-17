# Data Warehouses

## Objective

To learn the data warehouses tools and concepts

## Steps

1. [Snowflake](./snowflake/)
1. [BigQuery](./bigquery/)
1. [Redshift](./redshift/)
1. [Athena](./athena/)

## Note

> A central repository of information to make more informed decisions

Enterprises are becoming increasingly data driven, and a key component of any enterprise’s data strategy is a data warehouse—a central repository of integrated data from all across the company. Traditionally, the data warehouse was used by data analysts to create analytical reports. But now it is also increasingly used to populate real-time dashboards, to make ad hoc queries, and to provide decision-making guidance through predictive analytics. Because of these business requirements for advanced analytics and a trend toward cost control, agility, and self-service data access, many organizations are moving to cloud-based data warehouses such as Snowfkake, Amazon Redshift and Google BigQuery.

A data warehouse is a piece of technology that acts on 3 ideas: the data modeling, the data storage and processing engine.

In this cloud world where everything is serverless a good data modeling is still a key factor in the performance—which often mean cost—of a data platform. Modeling is often lead by the dimensional modeling but you can also do 3NF or data vault. When it comes to storage it's mainly a row-based vs. a column-based discussion, which in the end will impact how the engine will process data. Processing engines are mainly SMP (Symmetrical Multiprocessing) and MPP (Massively Parallel Processing).

### Speed vs Granularity tradeoff in data systems

You can do additional processing on top of dimensional data modeling to increase speed of access. Optimizing for speed does require sacrificing granularity, but as technology continues to improve, these tradeoffs become less consequential. Denormalized tables and OLAP cubes are the two ways to increase speed of access. Building denormalized tables, or summary tables, on top of your dimensional data models enables faster performance, but it does require some sacrifice of granularity. For example, you can save the “last 7 day purchases” on a per-user basis in a single data table for fast access, but you’ll lose the ability to get “last 8 day purchases”. For many usage patterns, the speed is worth the tradeoff because users would rather see pre-baked data in 3 seconds than wait 30 seconds for customization.

OLAP cubes are a more intensive option to increase speed of access. An OLAP cube pre-aggregates the data so much that lookup queries are near-instant. However, they require much more prep, and they sacrifice more granularity. Denormalized tables are a better way to satisfy performance for most use cases.

It's also worth noting that newer technologies such as Druid and Pinot can have extremely fast querying using a single table. This makes denormalized tables an appealing option if you choose to use these technologies since you don't have to pre-aggregate.

In addition to this, there are also in-memory implementations of data models that allow for fast data access. Tableau has Tableau Data Extract – first with the tde format and more recently hyper formats to enable fast access of large datasets. Arrow is another in-memory approach that allows for data systems to be built with interactive performance.

![](https://user-images.githubusercontent.com/62965911/214000302-c6e7373c-fd30-47ad-bfca-b7431d542ec6.png)

This graph provides a rough representation of the speed vs. granularity tradeoff that’s central to dimensional data modeling. As speed increases, granularity decreases, and vise-versa. But what’s exciting to note is that as technology improves, the graph shifts further to the right. That is, we’re able to maintain more granularity at higher speeds. As each step gets faster, all of a sudden you can use the more granular technique for certain workloads and still meet user time expectations. This means a simpler data pipeline and less loss of granularity to achieve the same goals.

To drive the point home, consider the OLAP cube. OLAP cubes have largely fallen out of favor because recent advancements make denormalized tables a pretty good balance of performance and flexibility for most teams today.

### Data Warehouse Options

#### Traditional Solutions for Data Warehouse

- SQL Server
- PostgreSQL
- MySQL

#### Cloud Data Warehouses

- BigQuery (Google Cloud)
- Redshift (AWS Cloud)
- Snowflake

#### Other Options

- AWS Athena
- Hadoop Hive

### Building a Data Warehouse/Lake solution on Cloud

#### 1. Data Warehouse Management (Strong SQL and Data Modeling Skills)

- Data Modeling
- Optimizing Queries
- Billing/Cost Management
- User/Access Management
- Enabling BI/Analytics for Query Management
- Data Governance and Security

#### 2. ETL/Data Movement (Strong Scripting/Coding skills along with understanding of cloud components)

- Writing Pipelines using Scala/Java/Python
- Data Orchestration Tools (Airflow/Step Functions)
- Deployment and Integration of Analytics/ML Models
- Know-how of best solutions for deploying scalable pipelines
- Logging, alerting and notifications

### Designing a data warehouse from the ground up

In general, the process of designing a data warehouse may involve the following steps:

1.  Identify the business requirements: The first step in designing a data warehouse is to understand the needs of the organization and the types of data that will be required to support the business. This may involve working with stakeholders to identify the specific goals and objectives of the data warehouse, as well as the types of data that will be needed to support these goals.
2.  Select the tools and technologies: The next step in designing a data warehouse is to choose the tools and technologies that will be used to build and manage the data warehouse. This may include selecting a database management system (DBMS), data integration and extraction tools, and analysis and visualization tools.
3.  Design the data model: After the tools and technologies have been selected, the next step is to design the data model for the data warehouse. This may involve identifying the data sources, defining the data structures and relationships, and establishing the data governance and security protocols that will be used to manage the data.
4.  Load and test the data: Once the data model has been designed, the final step is to load the data into the data warehouse and test it to ensure that it meets the business requirements and can be accessed and analyzed as needed. This may involve setting up ETL (extract, transform, load) processes to move data from the various sources into the data warehouse, and testing the data to ensure that it is accurate and up-to-date.

#### Select the tools and technologies

Tools and technologies, in today's world, can be influenced by many factors for example whether you prefer cloud or on-premise or if you go with cloud, then your existing cloud infrastructure.

For on-premises data warehousing (building the data warehouse on your own physical hardware), some popular tools include Oracle Database, Microsoft SQL Server, IBM Db2, Teradata, and SAP HANA. These tools offer advanced features like data compression, real-time analytics, support for unstructured data, and parallel processing.

There are also several popular cloud data warehousing tools that organizations can use to design and build their data warehouses in the cloud:

1.  Amazon Redshift: Amazon Redshift is a fully managed, cloud-based data warehousing service offered by Amazon Web Services (AWS). It offers fast querying and analysis of data using SQL and can handle petabyte-scale data warehouses.
2.  Google BigQuery: Google BigQuery is a fully managed, cloud-based data warehousing service offered by Google Cloud. It offers real-time analysis of large and complex datasets and can handle petabyte-scale data warehouses.
3.  Azure Synapse Analytics: Azure Synapse Analytics is a fully managed, cloud-based data warehousing service offered by Microsoft Azure. It offers integration with Azure Machine Learning and support for real-time analytics.
4.  Snowflake: Snowflake is a fully managed, cloud-based data warehousing platform that offers a range of features including support for semi-structured data, data sharing, and data lake integration.

#### Design the data model

There are multiple steps you need to take to design data modeling in your data warehouse.

1.  Identify the business process
2.  pick the right grain
3.  pick the right dimensions
4.  pick the right measures

**Identify the business process**

It's very important to focus on business process and not business departments as many departments share the same business process and if we focus on department, we might end up with multiple copies of models and have different sources of truth.

When the right business process is picked, then we should start with the most impactful model with the lowest risk. In other words, the models should be used frequently and be critical to the business and also it must be built accurately. If we don't have a high quality data for the model, it would impose a risk of inaccuracy and it would nullify its business impact.

For picking the impactful models, consult with the stakeholders and they can help you decide which models to start with.

**pick the right grain**

Grain refers to the level of granularity, or detail, at which the data in the data warehouse should be organized. The grain of a data warehouse is an important aspect of its design because it affects the types of questions that can be asked of the data and the efficiency with which queries can be answered. Since, it's not possible to predict the type of queries your analysts are interested in, it's better to pick the most atomic level for your model.

For example, if the grain of a data warehouse is set at the customer level, then it would be easy to answer questions about individual customers, such as their purchase history or demographic information. On the other hand, if the grain is set at the transaction level, then it would be easy to answer questions about individual transactions, such as the products purchased and the total amount spent.

In order to identify the right grain for a data warehouse, it is important to consider the types of questions that will be asked of the data and to design the data warehouse accordingly. This may involve trade-offs between the level of detail that is captured and the efficiency of querying the data. It is also important to consider the size and complexity of the data, as well as the resources available for storing and processing it.

If you don't pick a right grain, you need to spend a lot of time to redo your design. Moreover, if you don't pick the most granular grain, then you might lose the data, and it is sometimes not possible to go back. For example, if you pick a granularity of month for your data, if you hadn't stored the historical data, then it's impossible to go back to day granularity.

**pick the right dimensions**

Right dimensions are the relevant data attributes that will be used to organize and categorize the data in the warehouse. These dimensions provide a way to slice and dice the data, allowing users to analyze and understand the data from various perspectives.

For example, in a data warehouse for a retail business, some common dimensions might include time, location, product, and customer. Time might be used to track sales data over different time periods (e.g. daily, monthly, yearly). Location might be used to track sales data by store or region. Product might be used to track sales data by product category or specific product. Customer might be used to track sales data by customer demographics or customer loyalty status.

Choosing the right dimensions is important because it determines the level of detail and granularity of the data that can be analyzed in the warehouse. If the wrong dimensions are chosen, it may be difficult or impossible to get the insights that are needed from the data. On the other hand, if the right dimensions are chosen, it will be much easier to explore and analyze the data in meaningful ways.

**pick the right measures**

Choosing the right measures refers to selecting the appropriate metrics or quantities that you want to track and analyze in your data warehouse. These measures can be used to support business decision-making and help you understand trends and patterns within your data.

There are several factors to consider when selecting measures for your data warehouse:

1.  Relevance: The measures you choose should be relevant to your business goals and objectives. For example, if you are a retail company, you might want to track metrics like sales revenue and customer loyalty.
2.  Accuracy: It's important to choose measures that are accurate and reliable. If the data you are using to calculate a measure is incorrect or incomplete, the resulting measure will also be inaccurate.
3.  Timeliness: Choose measures that are up-to-date and timely. If you are tracking metrics that are out-of-date, they may not be useful for decision-making.
4.  Consistency: Make sure the measures you choose are consistent over time. If you are tracking a metric that fluctuates significantly from one time period to the next, it may be difficult to identify trends or patterns.
5.  Comparability: Consider whether the measures you choose can be compared to other data sources or to past performance. This can help you understand how your business is performing relative to other companies or to its own performance over time.

### Watch the video

#### Transactional databases versus data warehouses

Watch this video: https://www.youtube.com/watch?v=GIAEAzoclgU

#### The modern data warehouse

Watch this video: https://www.youtube.com/watch?v=EsvenuliSsc