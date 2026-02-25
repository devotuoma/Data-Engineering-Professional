# Data-Engineering-Professional


# Modern Data Architectures

2. What will we learn?

During this course, we will discuss what modern data architecture is, different types of architecture, key components from ingestion to serving, and also transversal components like data governance and orchestration. Finally, by the end of this course, we'll review some business cases and design data architectures for them, thus, providing experience with real-world scenarios.

3. Modern data architectures
Let's start by understanding what modern data architecture is and how it's different from the traditional architectures that we have seen as of today. The first difference is the volume and variety of data. Modern data architectures are required to handle massive amounts of data in different formats, both structured and unstructured. Moreover, we need to store such different formats and amounts while facilitating its processing for exploration and analysis. Additionally, nowadays, organizations need to analyze and act upon data arrival, thus requiring real-time processing approaches. Another characteristic of modern data architectures is the flexibility and scalability they offer. With current cloud providers, engineers can spend less time provisioning compute capacity and even delete it after it's not needed. Finally, one of the most important characteristics is data democratization. Modern architectures empower users with self-service tools for direct data access and analysis, minimizing IT involvement.

4. Modern data architectures requirements

Now let's focus on more specifics about modern data architectures. As we have already mentioned, modern architectures must be flexible, extensible, and scalable to be able to manage the variety and amounts of data of the current world. It's important to note that modern data architectures are not only about analytics. They are now used even for critical business paths. For instance, one of the customers I worked with in the past depended on their data platform to consolidate the information about the usage of their service to be able to bill their customers. However, they experienced a high peak of traffic for one month, and due to not properly configuring their auto-scaling policies, they were not able to process the usage data promptly, causing delays in their overall billing process. This is a great example of why flexibility and scalability are important in data architectures nowadays. Even more, data is not coming from a small set of sources anymore. Thus, we need to be able to integrate multiple domains, such as between departments or even geographies. And, finally, but not less importantly, the data governance role is crucial to ensure that all this data is useful and usable and that we can protect it from unauthorized entities while still enabling the organization to make decisions with it.

1 https://www.ibm.com/resources/the-data-differentiator/data-architecture
5. Components

Let's review the components we need in order to meet such requirements. Today, data is being generated almost everywhere; thus, we need to be able to consume it from several sources. Additionally, not all data sources are suitable for being consulted frequently, so we'll need mechanisms to replicate the data so we can access it at our convenience. We'll also need appropriate storage systems able to handle the volume and variety. Once we have the data, we'd like to enrich it and process it to gain even more value from it. Moreover, as we get more sources and data, we'll need to be able to orchestrate complex workflows, and, finally, we need to know and control all of our data. However, how we connect these components may vary depending on the business needs.

1 https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/big-data



Examples of Modern Data Architectures

1. Examples of the modern data architecture

Now that we understand the basics of what modern data architectures are, it's a great time to review some examples of known data architectures that could be used to implement modern data solutions.

2. Lambda architecture

Let's start by understanding what Lambda architecture is and how it fits into modern data architectures. Lambda is a data processing architecture designed to handle large-scale, real-time data. It combines batch and stream processing to provide a comprehensive and reliable solution. Lambda consists of three main layers: the batch layer, speed layer, and serving layer.

3. Lambda architecture layers: Batch

The batch layer handles the master dataset, which keeps the data immutable, and only appends new records as data keeps coming. To be able to provide value to the company, this layer has to pre-compute a set of views that will allow the data to have some meaning. For instance, if our data is related to bank accounts, the master dataset will contain the whole list of transactions, and we will need to use a view with all the transactions already applied and computed for precise information about the balance at a given point in time. It's important to know that this layer aims for perfect accuracy.

4. Lambda architecture layers: Speed

The batch approach sounds good so far. However, batch jobs usually run with daily schedules or, at best, hourly or every few minutes. Thus, there will be a gap between the data known by the batch layer and the current reality. The speed layer aims to close such a gap. This layer will not be as accurate as the batch layer, as its goal is to allow the business to use the most recent data. Eventually, the batch layer will override the possible imprecisions introduced by this layer.

5. Lambda architecture layers: Serving

Finally, there's the serving layer. This layer aims to merge batch and real-time views to provide a unified view of the data to support querying and analysis without having the delay of traditional batch-only approaches.

6. Complexity of Lambda architecture

Even if Lambda is a great alternative in modern data solutions, dealing with two layers for processing the same data may be really complicated. As this adds complexity around the systems to be maintained, the code bases, and the algorithms because we need to make them work in at least two stacks to support both the batch and streaming layers.

7. Kappa architecture

Here is where Kappa architecture comes into play. It is a simplified version of the lambda architecture that eliminates the need for a separate batch layer. However, it's not as simple as saying we do not need a batch layer anymore. Kappa deals with it by treating all the data as a single data stream, so we will be able to ingest and process all our data with the same streaming stack. Still, if we need to perform batch analysis or backfilling, we will depend on reprocessing the whole source of events again.

8. Lambda vs. Kappa

Let's summarize the key differences between both architectures. Lambda uses two layers: batch and stream. On the other hand, Kappa eliminates the need for a separate layer by treating all data as a single data stream. Lambda is still useful as we will have more flexibility at the time of ingesting the data and also may produce more complex outputs via the batch layer. However, the overall complexity of maintaining the system is greater than what with Kappa.


<img width="867" height="338" alt="Screenshot 2026-02-19 at 11 59 46" src="https://github.com/user-attachments/assets/4d24f9e4-e26a-41c6-ab4f-636a2d0c972a" />



1. Data Mesh and Data Fabric
00:00 - 00:06
Now, we'll explore two innovative approaches to managing data: Data Mesh and Data Fabric.

2. Data Mesh
00:06 - 00:39
Let's start with Data Mesh. It is an architectural approach that aims to decentralize data ownership and management within an organization. Let's review this definition. So, when we talk about ownership and management, we refer to taking full responsibility for the data. We will have the authority to determine who can access or use our data, as we're the ones with control over all decisions for such data assets. However, at the same time, it is our duty to keep data quality standards and ensure its security and privacy.

3. Data Mesh architecture
00:39 - 01:11
Thus, a Data Mesh looks for the proper owners for each data asset and exposes those assets as products while still sharing a common self-served infrastructure. It is similar to the Microservices concept as each team will have full responsibility for their service, data in our case, and have to expose a clear interface for others to consume it. This is a huge mindset shift, as in traditional architectures, data is often treated as a centralized asset owned by a dedicated team, for example, the IT department.

1 https://martinfowler.com/articles/data-monolith-to-mesh.html
4. How to process data then?
01:11 - 01:45
So far, Data Mesh is not describing how to process data as Lambda or Kappa does. That is because Data Mesh is more concerned with the organizational and cultural aspects of data management. It provides guidelines and principles for organizing teams, defining data domains, and promoting data autonomy within an organization but not tools directly. Thus, they address different aspects of a data platform and could be combined to produce a more robust solution. Something similar happens with Data Fabric that we'll review soon.

5. Data Mesh benefits and challenges
01:45 - 02:15
Finally, let's review some benefits and challenges of using Data Mesh. We're aiming to democratize our data through decentralization of data ownership, which provides us with a whole set of benefits like scalability, agility, and flexibility as each domain is independent. However, it also requires a huge cultural shift, really clear governance policies, efforts in coordination, and extra technical complexity for the same reasons.

6. Data Fabric
02:15 - 03:20
Moving on to Data Fabric. It is an architectural framework that aims to create an unified and integrated view of an organization's data assets. At first, it may sound different from Data Mesh, however, they both share a final goal which is data democratization. Nonetheless, in this scenario, we'll heavily rely on the metadata to be able to manage our data. A Data Fabric should be able to collect and analyze all types of metadata. The idea here is to be able to take this analysis to the point in which the Data Fabric itself could help us with the overall management and integration of our data. We'll leverage concepts like knowledge graphs, which is a representation of real word entities and their relationships in a graph structure, and machine learning algorithms to "activate" our metadata by making it available for end users, and enabling intelligent data management and integration; with the Data Fabric providing insights on how to cluster and manage assets, how to add them to the overall ecosystem.

1 https://www.gartner.com/smarterwithgartner/data-fabric-architecture-is-key-to-modernizing-data-management-and-integration
2 https://www.ibm.com/topics/data-fabric
7. A Data Fabric should support...
03:20 - 03:44
Finally, something that is commonly heard about Data Fabric is the usage of virtualization. Even though it is useful, we aim to be able to consume all sorts of data in all sorts of ways - from traditional ETLs to virtualization, without a particular focus. The idea is to be able to integrate sources of all shapes and support the delivery styles required by the business.






1. Data Storage: Storage types

Now, we'll review storage. A key component of a data architecture.

2. Blob storage
00:05 - 01:12
Let's start with blob storage. This is probably the most general type of storage we could use. Blob refers to binary large objects, which means we will be storing the data here as binary objects without much information about their content as we don't know much about its structure. That means blob storage will support all types of data. We could store tabular data using CSVs, Parquet, or Avro, or store pdfs, audio files, or whatever we need to store. Another great characteristic of blob storage is its scalability. This will actually depend on the provider, but most popular cloud providers offer virtually unlimited blob storage. Nonetheless, they normally limit the size of a single object. For instance, Amazon S3 has been keeping that limit up to 5TB per object. Still, this is easily overcome by partitioning such objects, so don't worry! Finally, a really attractive characteristic of blob storage is its cost. They're cheap! Surely cheaper than most data warehouses or databases.

3. Blob storage use cases
01:12 - 01:34
About use cases, blob storages are a really good choice for unstructured data, and also for backing up or archiving any type of data. Additionally, it is a good choice to be the first place you store your data when it arrives on your data platform. At the same time, you could use them to deliver content to end-users, like static website content or files.

4. SQL
<img width="847" height="306" alt="Screenshot 2026-02-24 at 11 23 55" src="https://github.com/user-attachments/assets/9125624d-660f-490d-a6a4-3a80dc0f7c03" />

Now we'll review storage solutions that actually require some sort of structure around the data, and in exchange it provides query capabilities to us. First, we have SQL-based storage. Here, we'll find relational database management systems or RDBMS like MySQL or PostgreSQL, which will be better suited for transactional applications with strong consistency and integrity. However, data warehouses may also fall into this category, obviously relaxing some conditions but still providing a SQL-based query engine. Thus, if we're looking to store structured data and query it in complex manners, we could consider using SQL-based storage. Some common offerings out there are the fully managed options by the top three cloud providers.

5. NoSQL

<img width="859" height="285" alt="Screenshot 2026-02-24 at 11 24 38" src="https://github.com/user-attachments/assets/b50f572a-0a6f-4489-b9cd-15cea272a785" />

On the NoSQL, or "not only SQL", side, we'll find solutions that are planned to support huge traffic loads and have really good response times. However, it's important to know that we'll pay for that by not being strongly but eventually consistent. NoSQL stores are non-tabular databases, providing flexibility in data types and structure, meaning we could store semi-structured data with really diverse formats like documents, key-value pairs, and graphs, among others. Another interesting thing about SQL and NoSQL-based storage is the query capability. For blob storage, we could only get a file by its identifier, not much about its actual content. That's not the case for these storages, we could actually get insights from the data due to its structured nature. So, they're pretty common as well in later layers within a data architecture that has end-users consumption.

6. Data warehouses and data lakes

<img width="541" height="179" alt="Screenshot 2026-02-24 at 11 25 28" src="https://github.com/user-attachments/assets/eaff97c7-69e1-46d8-b4d7-e8492dcba388" />

Even though data warehouses and data lakes are more complex systems, with current offerings like BigQuery, Redshift, or blob storages it is really common to consider them when deciding where and how to store our data. Most companies decide to get data directly from their operational databases into the data warehouse and have logical separation within it to be able to process the data to be better suited for analytical purposes. Actually, this is also known as ELT, which is a really common practice nowadays.




1. Data Ingestion
00:00 - 00:06
Data architecture is about data, and we normally need to be able to ingest it to work with it.

2. What is data ingestion?
00:06 - 00:48
So, what is data ingestion? Software systems are designed to meet specific functional requirements. Thus, they normally use storage solutions that help them to be functional, and that doesn't necessarily mean good for analytics. In modern data architectures, we'll generally need to replicate data coming from multiple sources, especially transactional systems, so we'll be able to perform analytics over our data without affecting the overall performance and functionality of our applications. In brief, ingestion is about getting our data from different sources into our data platform, so we can play with it and evolve it into a useful asset for the business.

3. Batch ingestion
00:48 - 01:39
Now, we need to consider how to ingest our data. This will happen through jobs that are simply scripts that define a set of tasks to be performed. Probably the most common approach is by using a batch job that will be triggered with some schedule and will gather the data from where it originally resides. Batch ingestion, however, has to deal with a huge decision: will we read all existing data every time we run the job, or will we read only data that has changed since the last time we ingest it? This depends on the size of our data, computing, network, and storage capacity. If we have infinite resources, bringing all data will be easier, then we could do analytics over the current state of the data or examine how the data changes over time as we also have such information.

4. Batch ingestion: Bring only what changed
01:39 - 02:20
Having infinite resources is impossible, so we'll depend on bringing what has changed most of the time. This is not an easy approach. We need to consider how we are going to determine whether something has changed from the previous time. We'll need a timestamp or a "was updated" flag. Then, the source system has to provide such capability for us. Additionally, after bringing the delta of data, we need to consolidate it with the previous data to get the latest state. So, we'll need more jobs. Finally, let's think about deletions: if a record was deleted, how would we know that? We'll probably need to read the whole data once every month or so.

5. Streaming ingestion
02:20 - 03:24
On the other hand, we can ingest our data in real-time! Nonetheless, this requires a mindset shift. For ingesting data here, also known as the push model, we'll depend on events. For instance, a change data capture will tell us whenever something happens to an entity in a database and what exactly happened. So, we'll get those events into a queue like Kafka or Pub/Sub and listen to the queue all the time. Finally, we need to store the events. It could be, for instance, by keeping the whole history plus a view or copy with the latest status of our data. Streaming is also really good for when you don't know when the events will happen or when external entities will send the data to you. The drawback is you need to listen 24/7. Finally, remember that no matter how we get our data, it's always a good idea to first store it in a dedicated zone for new data, also known as a landing zone, so we can explore and process it before our end-users get to know it.




1. Data Processing
00:00 - 00:04
Let's review how to get the best from our data by processing it.

2. What is data processing?
00:04 - 00:43
What exactly is data processing? Is it transformations? Well, processing is wider. It's the whole idea of working with data. By processing, we mean, for instance, exploring it or performing data quality reviews without necessarily transforming it. Another example of data processing is analytics itself. For example, aggregating the data to gain insights or connecting multiple sources to get a 360 view of our organization or area. Nonetheless, we're already partially describing transformations here, which is still an important part of data processing but not everything.

3. Batch processing
00:43 - 01:17
When processing data, we could execute our jobs in two different approaches: Batch and streaming. Batch processing is when we read our whole data universe and work on it. When we say universe, it means we have a clear understanding of where it starts and ends. For instance, a whole table or a subset of a table based on some condition. In batch, we'll work with that fixed data, and we can perform operations over the whole dataset. For instance, we could compute an average of the whole dataset and derive insights from it.

4. Streaming processing
01:17 - 02:01
Something completely different happens with streaming. Here, we'll keep getting new data all the time. We don't know when it ends; thus, we could not compute operations over the whole dataset. So, we'll need to define a window in which we could perform such operations. Windows could be defined by a fixed time. For instance, we could compute the average for data that arrives within a 30-minute timeframe, and events after that will be processed in the next window. There are other types of windows, for example, sliding, which could overlap multiple data items. So, it is a good option for computing moving averages. Nonetheless, what happens if an event arrives late but belongs to the previous window?

1 https://beam.apache.org/documentation/programming-guide/#windowing
5. Streaming processing concepts
02:01 - 02:32
That's why we consider two different times. Event time refers to the time when the event happens, while processing time is when the event is processed. However, how will we know a window is closed? Watermarks! They are the notion of when all data in a certain window can be expected to have arrived in the pipeline. If data arrives after that, it is considered late. And late data may trigger a new processing event that could be re-processing the whole window, but that's up to us.

6. Processing technologies
02:32 - 03:47
Finally, let's review some tools useful for processing. We have frameworks like Spark or Flink that allow us to do both batch and streaming processing. However, they require a cluster, which is a set of servers that work in a coordinated way to accomplish some tasks. Cloud providers abstract the complexity of clusters with services like EMR or Dataproc that provision the machines and packages we need to run our jobs, but we still need to manage the cluster. Although, Google even abstracts batch and streaming under a single unified model using Apache Beam under Dataflow. Dataflow goes further as it's known as serverless, meaning that the provider will fully manage the servers' life cycle. Overall, these are great alternatives for general big data processing. Our computing will run in commodity servers and scale horizontally, and those frameworks and cloud providers hide that complexity from us. However, not everything is big data. We'll also face individual operations that will not necessarily happen all the time. That's where we'd like to use function computing to process our data without servers running 24/7, but responding to events.




1. Data serving
00:00 - 00:05
Now, let's start by understanding what data serving and the serving layer is.

2. Serving layer
00:05 - 00:31
The serving layer normally refers to where we're going to store our processed data and the protocols or mechanisms we provide to our consumers to access such data. So, after our data is processed and has gone through data quality checks, enrichment, and other processes, we're ready to present it to our consumers. Thus, we will need to identify how it will be consumed to find a proper way to store and serve it.

3. What data do we have?
00:31 - 01:15
To create a good serving layer, we need to understand what data we have and how the business will consume it. For instance, is our data structured? If so, we could decide to use a data warehouse to take advantage of the structure itself and enable use cases like dashboarding, BI, or querying. Thus, a data warehouse as part of the serving layer is a great decision! However, what happens if we have unstructured data? Or if our data is a time series? There are better technologies for such use cases, such as blob storage, a time series database, or even a NoSQL database. It's important to note that a serving layer is not a single data store but a set of them.

4. How will data be consumed?
01:15 - 02:04
Now that we know our data, we need to understand how it's going to be consumed. Are we going to build machine learning models? Which applications will consume our data? And will these applications request summarized information? Or maybe request individual records? Not every data storage system is a good option for every query. That's why it's important to address these questions, as, for instance, if applications frequently request individual records, let's say, ask for just one specific user's data, a data warehouse may get exhausted and produce poor performance. Thus, we probably need to consider enabling an RDBMS, even if this means replicating data and exposing it via an API so it can handle such traffic.

5. Serving your data depending on your use case
02:04 - 02:58
Let's look at different systems and the use cases that better fit them. Starting with data warehouses. We already know that they are good with structured data and that we can use them for BI, reporting, and querying. Next, we have blob storages, which will allow us to store all types of data. They are also great for archiving data that we do not plan to access frequently, due to their lower cost. The next options, NoSQL and relational databases, are storages that we have already discussed in previous videos, so let's look at their role in the serving layer. For instance, creating a single source of truth that transactional applications will consume by searching for individual records. These applications may connect using an API that will expose the data via a defined protocol, usually HTTP, so applications can get data in a well-defined way.

6. Serving vs. Consuming
02:58 - 03:30
Finally, it's important to differentiate between serving and consuming. Even though we're considering how data is consumed to design our serving layer, we do not care how the consumption is actually happening. Thus, the serving layer does not care which exact dashboarding tool or machine learning model we will build. It cares about being able to get the data we need in the best possible way. Additionally, it can also help optimize performance by caching frequently accessed data and using indexing to speed up queries.



















1. Data governance
00:00 - 00:06
Data governance is present across our whole architecture. Let's dive into it!
<img width="766" height="451" alt="Screenshot 2026-02-25 at 10 16 37" src="https://github.com/user-attachments/assets/1e52be33-63d2-4ce8-8f15-2a273bf95fd7" />


2. What is data governance?
00:06 - 00:31
Data governance is a complex concept combining people, processes, and tools to appropriately control our data assets. Data governance helps companies understand what data they possess, where it originated, and its quality. At the same time, a well-defined data governance strategy allows them to secure their data, prevent unauthorized access, and meet industry regulations.

1 https://www.oreilly.com/library/view/data-governance-the/9781492063483/


3. The people

<img width="858" height="289" alt="Screenshot 2026-02-25 at 10 20 05" src="https://github.com/user-attachments/assets/eef220e3-ff47-465e-a82d-a45190e20d55" />


Let's start with the people and the different roles that exist here in data governance. We have three main categories, the first being governors or approvers. They are accountable for the data. Here we find roles like owner or steward that are the actual implementers of the data governance strategy. These roles have first-hand knowledge of the data assets, and they are also responsible for processes like classification and access control. Next, the users are the ones who consume the data. For instance, data analysts or data scientists. Finally, there are other actors like the legal team that helps to understand and adhere to industry regulations or C-executives that fund and lead the overall strategy.

4. The processes


<img width="528" height="348" alt="Screenshot 2026-02-25 at 10 22 15" src="https://github.com/user-attachments/assets/a8952c21-f5d1-43a2-8ccc-62793b6c6f2b" />

There's a wide variety of processes that companies need to implement to be able to properly govern their data. Our aim is to know our data, its quality, and when and where it originated, along with limiting access. One step is to classify our data, which allows us to understand what type of data we have. Is it sensitive? What exactly does that data represent? Additionally, processes like data lineage that aim to understand the origin of our data need to be implemented. And data quality as well. We need to define what we consider good data, how often we are going to validate that our data is good, or what we are going to do with bad data. Those are the kind of things that encompass the processes in a data governance strategy. And actually, these are the processes that governors normally are responsible for. That's why data governance needs the processes plus the people responsible for them and the data.



5. The tools

<img width="528" height="348" alt="Screenshot 2026-02-25 at 10 22 15" src="https://github.com/user-attachments/assets/e8975580-e5a3-4f2b-a3fe-1dcf4e8a5fb8" />

Now, we have the tools or technology that will facilitate the implementation of the processes described before. Probably the main tool around data governance is the enterprise dictionary. This dictionary will allow us to categorize our data into different information types. For instance, if a certain field is a phone number, or maybe a name or a salary. With such valuable information, we could start relying on data classes as well. For example, a class called PII or personally identifiable information will allow us to enforce policies on all fields marked as PII. Note that fields may be considered PII or not depending on regulations and company policies, but there are pretty common ones like names, passport numbers, or phones that are considered PII in most popular regulations. We could, for example, restrict access to PII data or only allow it under specific conditions. However, overall, this sounds like more processes. We need to consider how to automate these processes of classification and access management, and current cloud providers offer really good solutions like Data catalog from GCP or Glue data catalog from AWS. At the same time, we have IAM offerings to restrict and manage access to our data, and it normally integrates deeply with catalogs allowing us to ensure access in a granular manner. Finally, it's important to note that processes like data quality, lineage, or encryption are also candidates for automation, and we should pursue this.
















1. Metadata Management

The main enabler of any data governance strategy is the metadata. Let's check it out!

2. What is metadata?

<img width="858" height="289" alt="Screenshot 2026-02-25 at 10 20 05" src="https://github.com/user-attachments/assets/ce2d49f8-7a42-4fce-80c2-b149af097d5c" />


So, let's start with the basics - What is metadata? In its simplest form, metadata is 'data about data'. It provides information about our data, which can be used to organize, locate, and understand it more effectively. Imagine walking into a library and picking up a book. How do you know what it's about? You'd look at the title, maybe the author, and then take a look at the blurb on the back. All of this is metadata. It gives us context and helps us to understand what the book, or in our case, the data, is all about. Metadata is an essential part of data architecture because it allows for efficient data management and usage. It makes data discoverable and accessible, enhances its usability, and aids in maintaining data quality.

3. Metadata types

<img width="528" height="348" alt="Screenshot 2026-02-25 at 10 22 15" src="https://github.com/user-attachments/assets/a54949c5-3063-457e-904a-5b5e77c672a5" />


Now, let's get to know the different 'species' of metadata. First up, we've got technical metadata. This type of metadata relates to the data structure, including database schema, column names, data types, or relationships. Think of it as the blueprint of your data environment. In our book example, it could be, for instance, the number of pages or the ISBN. Next, business metadata provides context about the data, like business definitions and rules, or the owner of the data. An example would be a business glossary that defines the terms used in an organization. Back to our book example, business metadata there could be a summary or the genre, that provides us with context on what the book is about. Then we have operational metadata, which is like a diary of our data processing. It keeps a record of things like timestamps, ETL job status, and data quality metrics. It's like the daily health check-up for our data. Lastly, we have usage metadata. This type keeps track of data usage - who accessed it, when, and how it was used. It's like the security footage for your data, crucial for auditing and data security.

4. Where to store your metadata?
02:17 - 03:46
Finally, where do we keep all this metadata? Well, we've got some really good helpers for that - metadata management systems, like GCP's Data Catalog, AWS's Glue Catalog, or even Apache Atlas. GCP's Data Catalog is like a well-organized librarian, always ready to help you find your data. It integrates with services like BigQuery, Spanner, Cloud Storage, or Pub/Sub, automatically ingesting and storing metadata from these Google Cloud services. But what if your data is outside Google Cloud or simply not directly integrated, like in a local server or another cloud? You can use their API to register and index that external metadata, making it searchable within Data Catalog. Similarly, AWS Glue Catalog acts as a one-stop shop for your metadata. It integrates with services like S3, Redshift, and RDS, collecting, cataloging, and enriching your metadata. And for data outside AWS, Glue catalog offers crawlers that can connect to external data sources, such as databases hosted on-premises or in other clouds, and catalog that data. There are plenty of other solutions out there. The important thing here is that they allow us to easily integrate with the services and solutions we use to store our data, and also allow us to properly discover and understand it!



