# History
There is a flood of interest in learning how to processing data in large-scale systems in terms of extract, transform, load in real time, partly because there are situations in which the time-value of data makes real-time analytic so attractive and important. 

But gathering in-the-moment insights with complex data processing in the fly is extremely difficult. Although, there are available big data framework or applications available to such use case, there are either too complex to use or incapable for particular type of jobs. In addition, most time we need to combine both history data and real-time data together because history data accumulate values and asset for prediction and tuning the data in the fly. All of these requirements make existing big data framework alone, such as [Hadoop](http://hadoop.apache.org/), [Hive](http://hive.apache.org/), [Pig](http://pig.apache.org/), [Spark](http://spark.apache.org/), [Flink](https://flink.apache.org/), [Storm](https://storm.apache.org/), etc, not applicable well. Most companies start building in-house solutions to solve this technical issues. And, this is why it comes to the creation of DataFibers to provide a way ease of generic big data processing. 

## Architecture
The big data processing architecture adapts to the speed and demanding for exploring values behind of the big data. The architectures of big data processing have three milestones during this evolution. 

### Batch Processing Architecture
In the earlier period of big data processing, aka Hadoop 1.0 era, most big data processing was based on Hive/Pig and MapReduce batch jobs. At that time, big data batch job gained attention over traditional data warehouse applications in terms of cost, stability, and performance. At nowadays, batching processing is still playing an important role in most enterprises as transaction from legacy data processing framework. 

<p style="text-align: center;">
<img src="https://hadoopabcd.files.wordpress.com/2015/03/hadoop1.png" alt="Hadoop MapReduce Based Batch Processing"><br>
Figure 1.1 Hadoop MapReduce Based Batch Processing
</p>

### Hybrid Processing Architecture
When [IoT](https://en.wikipedia.org/wiki/Internet_of_things) becomes popular, there are quite a lot demanding on the speed of acquiring data. Apache Storm, Apache Spark, Flink, Kafka attracts more attention on their steaming data processing. In addition, more use cases using ad-hoc analytic queries on Hadoop data make batch processing, the single solution, awkward and frustrated. Lots demo or POC are started as sperate streaming based big data processing system parallel running with batch processing system. What's more, [Lambda Architecture](https://en.wikipedia.org/wiki/Lambda_architecture) comes to the picture of big data processing for the very first time.

<p style="text-align: center;">
<img src="http://lambda-architecture.net/img/la-overview_small.png" alt="Lambda Architecture for Hybrid Data Processing"><br>
Figure 1.2 Lambda Architecture for Hybrid Data Processing
</p>

The Lambda Architecture is designed to satisfy the needs for combined analysis on both history data, which is typically coming from batch processing (batch layer), and on-time data, which is ingested by data streaming (speed layer). This combined feature,which is served from serving layer, has wider use cases when data-driven business looking at the on-flying data for statistics and history data for decision making. 

### Unified Processing Architecture
When there are lots of start-up coming into big data processing technology, they usually do not have burden like legacy system or history of data. Most of them jump directly into streaming processing especially for mobile related business or projects. Experienced gained when more people got used to streaming architecture and tentative to use the same processing architecture for batch data as well. In another saying, this comes to the unified big data processing architecture for various of type of big data processing, batch or stream. In addition, this is a pure streaming data processing architecture and reuse for batch processing as well. [Kappa Architecture](http://milinda.pathirage.org/kappa-architecture.com/) is one of very interesting and promising design by removing complex layers from Lambda Architecture - a Kappa Architecture is a simplification of Lambda Architecture. And, this is where DataFibers start from too.

<p style="text-align: center;">
<img src="https://www.ericsson.com/research-blog/wp-content/uploads/2015/11/LambdaKappa1_2.png" alt="Kappa Architecture for Unified Processing"><br>
Figure 1.3 Kappa Architecture for Unified Processing
</p>

### To Conclude
Many companies have started or been staring evolving from pure batch to pure stream big data processing architecture. There are reasons arranged from legacy warehouse maintenance to technology maturity. Some company are still in the Batch or Lambda architectures. However, Lambda Architecture is [NOT recommended](https://www.oreilly.com/ideas/questioning-the-lambda-architecture)  because of complexity and overhead, unless the company has very closed dependency on legacy data pipe and their big data architecture was already matured in the last three years. Kappa is where leading data company approaching.


## Service

### Data Oriented and Centric

<p style="text-align: center;">
<img src="data_oriented.jpg" alt="Data Oriented and Centric"><br>
Figure 1.4 Data Oriented and Centric
</p>
### Data Application vs. Framework


