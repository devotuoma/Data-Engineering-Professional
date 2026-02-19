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
