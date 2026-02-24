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

