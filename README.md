# BigDataAnalytics
## USE CASE OF TRAFFIC MANAGEMENT
### Structured abstract
Background:
The development of big data also goes hand in hand with the development of its infrastructure. As enormous amounts of data are being created at high speeds, storing it is also an issue.

Objective:
The objective is to describe the infrastructure and techniques of the traffic management example, and an example workflow is also proposed. It also presents the limitations of the research and the issues of additional research proposals and ethical perspectives.

Conclusion:
Extract meaningful information using IoT technology. Further research will be needed.

Keywords:
Traffic management, Lambda architecture, Hadoop, Spark

### Part 1. Introduction
The meaning of current data is not just numbers and letters. With the development of technology, various types of data, such as video and picture, continue to be developed and produced (Frankel & Reid, 2008). This variety of new kinds of data are being produced at a tremendous rate, so it naturally focused on the infrastructure where the enormous amount of data will be stored. The development and introduction of new infrastructure have become more critical (Marr, 2016).

Since the evolution of data storage capacity on hard drives does not keep up with the rate of big data production, the introduction of a scale out network that can store data across a cluster of servers could solve this problem (White, 2015). For example, Hadoop is an open source framework for processing extensive data analytics. This is the implementation of Google File System (GFS) and MapReduce, which were announced in 2003 and 2004, similar to Google's in a number of areas of design and ideas (Ghemawat et al., 2003). Hadoop 1.x version consists of Hadoop Distributed File System (HDFS), which distributes, stores, and manages massive amounts of data, and MapReduce, which performs analysis of large amounts of data.

HDFS is installed and operated on a number of Linux servers, and its scalability provides more than one petabyte (1,024 terabyte) of data storage space. In addition, multiple servers simultaneously handle data distributed to ensure high speed for large scale data processing of data. In particular, the cost of building a system is lower than that of a Relational Database Management System (RDBMS), which uses expensive equipment. Spark is also a framework for analysis that can be operated on Hadoop or as a stand-alone cluster with easy algorithm implementation. The benefit of Spark is that it could produce quick results without slowing down. Spark does not include its own file management system, but it can be used in conjunction with any cloud-based data platform other than HDFS. However, since the spark itself was originally designed for Hadoop, it is appropriate to use the spark and Hadoop together (Wakde et al., 2018).

The distributed system described earlier focuses on the storage of data. However, a new streaming data-driven architecture that requires continuous monitoring and rapid processing has also emerged, and a number of companies and institutions are now using it for their businesses or operations. For example, game companies monitor customers' cheating in real time to prevent their damage and crimes (Gandomi & Haider, 2015).

This study examines a batch and streaming analysis of traffic management cases and presents the related infrastructure and effects. The justification for this study is to identify the opportunities and challenges in handling big data, including situations suitable for big data analysis in traffic management. Furthermore, this study could help emphasize the importance of big data in traffic management by explaining and proposing how to determine the most appropriate big data infrastructure solution for the area.

### Part 2. Traffic management cases
#### 1.	Data Infrastructure solution
Most of the things that people see and use will be connected to the Internet and exchanged information. The Internet of Things (IoT) refers to a technology or environment that attaches sensors to objects and sends and receives data through the Internet in real-time. In traffic management, various knowledge and insights will be obtained through large volume and fast big data analysis engine with IoT-based network system. In other words, the establishment of the IoT system is to utilize data for real-time analysis of traffic (Al-Shammari, Al-Aboody & Al-Raweshidy, 2017). However, there are a number of things that need to be done to realize and commercialize this in traffic management. IoT systems could collide with each other in the process of sending and receiving data. In addition, different types of data storage and collection, such as video, photography, and text, suggest that it is not easy to realize (Yamada et al., 2018). Figure 1 below illustrates the big data infrastructure of traffic management and toll collection.

![Figure1](https://raw.githubusercontent.com/myaqueenas/BigDataAnalytics-/2215dc74b26e16fb25f4533737c888b494253525/Figure/Figure%201-1.PNG)

Figure 1. The infrastructure of Big data

The distributed file system described earlier in the introduction is the infrastructure needed for traffic management to store data. In particular, HDFS for Hadoop is optimized for throughput per hour, strong against large datasets, and low cost because it involves moving computational tasks rather than moving data. Also, it works well, even if different hardware and software platforms are bundled together. They are mainly used for batch processing through MapReduce.

Apache HBase is an open, nonrelational distributed database for Hadoop platforms ("Apache HBase – Apache HBase™ Home", 2020). With the ability to store and access large amounts of data safely and quickly, it can be useful for storing ad click data, user behaviour data collection, log collection, IOT's sensor data, and time series data in finance. In addition, On-Line Analytical Processing (OLAP), a data analysis technique that uses multi-dimensional data structures to process complex, multi-dimensional queries at high speed, means continuous aggregation for specific columns, so the column store database is appropriate (Chang et al., 2008)

Flume is a service that has the reliability to effectively collect large amounts of log data in a distributed environment, combine them and transmit them elsewhere. Flume is based on flexible and straightforward streaming data flow architecture. Also, Kafka is an open-source stream-processing software platform, and it provides a platform with high-throughput, unified, low-latency that can handle real-time data feeds (Garg, 2013).

Spark has emerged as the most robust framework, overtaking the existing MapReduce paradigm, which led to Hadoop's popularity in big data processing with two significant advantages. The first advantage is speed. Spark can perform tasks 100 times faster than MapReduce under certain circumstances through in-memory data engines. The second advantage is developer-friendly. This is no less important than the speed of the spark, and some developers say that the familiarity of the Spark API (Application Programming Interface) is more important than the speed. (Wakde et al., 2018; Armbrust et al., 2015).

In the previous Apache Hadoop environment, batch and stream processing were separate. MapReduce codes are used when batch processing is needed, and Apache Storms are used when real-time streaming is necessary. This required synchronization of the two codebases, each with different resources and different operational considerations for the application domain, even though they were based on a completely different framework. Spark streaming expanded the concept of Apache Spark's batch processing to a streaming by splitting streams into continuous micro-batch (Maarala et al., 2015).

#### 2.	Data workflow and example queries
The workflow of traffic management adopted the lambda architecture, which is a data processing architecture designed to handle large volumes of data using both batch and stream processing methods (Hausenblas & Bijnens, 2017). The architecture uses batch processing to balance latency, throughput and fault tolerance. At the same time, it uses real-time stream processing to provide online data view. Two view outputs can be combined (Schuster, 2014). The principles of lambda architecture include minimizing transfer delay, the consistency as a result of the analysis, and accuracy through performance and expansion balance. Besides, the architecture consists of a batch, speed, and serving layers. In the batch layer, all incoming data is stored in the master data set, and views are created and delivered to the serving layer. The master data set is an immutable data structure that can only be stored and viewed in chronological order. In addition, specific data values can be accurately extracted. The batch layer cannot process new incoming data during the processing of extensive data stored in the master data set. Therefore, the speed layer processes new data flowing in during the batch layer performance. It also minimizes processing latency. Finally, the serving layer provides results by merging batch views, real-time views, upon request for analysis from the user (Hausenblas & Bijnens, 2017; Schuster, 2014). The workflow is as follows:

![Figure2](https://raw.githubusercontent.com/myaqueenas/BigDataAnalytics-/2215dc74b26e16fb25f4533737c888b494253525/Figure/Figure%202-1.PNG)

Figure 2. Lambda architecture

![Figure3](https://raw.githubusercontent.com/myaqueenas/BigDataAnalytics-/2215dc74b26e16fb25f4533737c888b494253525/Figure/Figure%202.PNG)

Figure 3. Data workflow

This is an example query about traffic volume and speed by road section using spark SQL. Spark SQL, a data processing framework that enables rapid processing of very large datasets, while distributing data processing to multiple computers, either on its own or in coordination with other distributed computing tools. Spark SQL focuses on structured data processing using data frame approaches in R and Python (Pandas). The centre of Apache Spark is the concept of Resilient Distributed Dataset (RDD). RDD is a programming abstraction that represents a collection of immutable objects that can be divided across computing clusters. In addition, work in RDD is split across the cluster and can be handled in a parallel batch process, so parallel processing is faster and more scalable (Zaharia et al., 2010). The hypothetical dataset consists of attributes such as vehicle registration number, vehicle type, vehicle speed, license number, road number, point of departure and destination.

![Figure4](https://raw.githubusercontent.com/myaqueenas/BigDataAnalytics-/2215dc74b26e16fb25f4533737c888b494253525/Figure/Figure%203.PNG)

Figure 4. Example query

### Part 3. Discussion and conclusions
This study described and selected the best fit for big data analysis on traffic management and the most appropriate big data infrastructure solution. In addition, this part consists of understanding the conclusions above and identifying the challenges, and opportunities when dealing with big data and it is the use of IoT devices.

This architecture in the study is based on YARN and HDFS. Also, Hive is a data warehouse system for Hadoop that can perform data summaries, queries, and analyses using Hive Query Language (HiveQL), using query language similar to SQL. Hive can be used to create batch processing where data can be reviewed or reused in two directions. Hive is designed for batch processing (Venner, 2009). Besides, lambda architecture was adopted in this study when the system handled batch processing and streaming analysis. PySpark, a Python API is written in Python, was used to support Apache Spark (Drabas, & Lee, 2017).

As a limitation of this study, more photo or video data could be extracted from the camera. Graph processing modules will need to be included to obtain additional graphic information. In addition, the kappa architecture may be adopted in place of the lambda architecture. Kappa architecture is proposed to eliminate the functional redundancy and complexity of the batch layer and speed layer of the lambda architecture. The kappa architecture proposed by LinkedIn's Jay Kreps is designed to eliminate batch layers, stream all data from the speed layer to the serving layer. Because the kappa architecture streams through the speed layer if the version is changed, the rework is processed by version and stored in a separate table, and the rework is completed when the previous version of the stream is finished. Unlike the Lambda architecture, the batch layer is removed and operates under a single framework with only management points for one layer, which gives you the advantage of operational/maintenance and debugging and testing in the event of anomaly or failure. However, we believe that we should also consider the real-time service provision in the event of an abnormality in the speed layer or failure, as well as supplementation of data loss (Lin, 2017).

![Figure5](https://raw.githubusercontent.com/myaqueenas/BigDataAnalytics-/2215dc74b26e16fb25f4533737c888b494253525/Figure/Figure%204.PNG)

Figure 5. Kappa architecture

The Internet of Things has never existed before. In some cases, collecting data on the Internet of Things could emerge as a sensitive issue. Planning on how to dispose of data collected in the cloud after a certain amount of time should be established, and how to utilize the data collected should be clarified. For example, data on when the washing machine turns on and when the refrigerator door opens can be used as a reference in court, which can cause privacy problems. No other information shall be extracted or resold for the data collected. Companies that collect consumer data are walking a tightrope between privacy infringement and service provision (Lin & Bergmann, 2016).

### References
Al-Shammari, B. K., Al-Aboody, N., & Al-Raweshidy, H. S. (2017). IoT traffic management and integration in the QoS supported network. IEEE Internet of Things Journal, 5(1), 352-370.

Apache HBase – Apache HBase™ Home. Hbase.apache.org. (2020). Retrieved 12 August 2020, from https://hbase.apache.org/.

Armbrust, M., Xin, R. S., Lian, C., Huai, Y., Liu, D., Bradley, J. K., ... & Zaharia, M. (2015). Spark sql: Relational data processing in spark. In Proceedings of the 2015 ACM SIGMOD international conference on management of data (pp. 1383-1394).

Chang, F., Dean, J., Ghemawat, S., Hsieh, W. C., Wallach, D. A., Burrows, M., ... & Gruber, R. E. (2008). Bigtable: A distributed storage system for structured data. ACM Transactions on Computer Systems (TOCS), 26(2), 1-26.

Drabas, T., & Lee, D. (2017). Learning PySpark. Packt Publishing Ltd.

Frankel, F., & Reid, R. (2008). Big data: Distilling meaning from data. Nature, 455(7209), 30-30.

Gandomi, A., & Haider, M. (2015). Beyond the hype: Big data concepts, methods, and analytics. International Journal of Information Management, 35(2), 137-144.

Garg, N. (2013). Apache Kafka. Birmingham: Packt Publishing.

Ghemawat, Sanjay, Gobioff, Howard, & Leung, Shun-Tak. (2003). The Google file system. Operating Systems Review, 37(5), 29-43.

Hausenblas, M., & Bijnens, N. (2017). Lambda Architecture. Lambda-architecture.net. Retrieved 12 August 2020, from http://lambda-architecture.net/.

Lin, H., & Bergmann, N. W. (2016). IoT privacy and security challenges for smart home environments. Information, 7(3), 44.

Lin, J. (2017). The lambda and the kappa. IEEE Internet Computing, 21(5), 60-66.

Maarala, A. I., Rautiainen, M., Salmi, M., Pirttikangas, S., & Riekki, J. (2015, October). Low latency analytics for streaming traffic data with Apache Spark. In 2015 IEEE International Conference on Big Data (Big Data) (pp. 2855-2858). IEEE.

Marr, B. (2016). Big Data in Practice. New York: John Wiley & Sons, Incorporated.

Schuster, W. (2014). Nathan Marz on Storm, Immutability in the Lambda Architecture, Clojure. InfoQ. Retrieved 13 August 2020, from https://www.infoq.com/interviews/marz-lambda-architecture/.

Venner, J. (2009). Pro hadoop. Apress.

Wakde, A., Shende, P., Waydande, S., Uttarwar, S., & Deshmukh, G. (2018). Comparative analysis of Hadoop tools and spark technology. In 2018 Fourth International Conference on Computing Communication Control and Automation (ICCUBEA) (pp. 1-4). IEEE.

White, T. (2015). Hadoop : The definitive guide (Fourth edition, revised & updated. ed.). Sebastopol, California: O'Reilly.

Yamada, Y., Shinkuma, R., Iwai, T., Onishi, T., Nobukiyo, T., & Satoda, K. (2018). Temporal traffic smoothing for IoT traffic in mobile networks. Computer Networks, 146, 115-124. 

Zaharia, M., Chowdhury, M., Franklin, M. J., Shenker, S., & Stoica, I. (2010). Spark: Cluster computing with working sets. HotCloud, 10(10-10), 95.
