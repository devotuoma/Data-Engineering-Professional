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


