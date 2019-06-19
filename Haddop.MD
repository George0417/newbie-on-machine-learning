1.why move awaay from relational databases
・Scalability---the storage of data will be extend to GB or TB
・Speed---some customer will be favorite at real time
・others---application of sophisticated processing(machine learning)
   ・Hadoop uses an alternative file system--HDFS which is similary to GFS
   ・HBase is a NoSQL database(wide columnstore-the width of columns varies depending on the amount of information that is inserted)
   
 **CAP Theory**
 ・Consistency---adding the money into a checking account and the data will changed successfully or neither.
 ・Availability---you can copy the data even one copy goes down for location,the data is still available
 ・Partitioning---split data set across multiple processing locations
 
 **understanding big data**
 ・LOB(LINE of business)not great fit for hadoop
 ・Behavioral data---process as a group,rather than individually queried(great candidate for hadoop)
 
 2.what is Hadoop
 **Two components plus projects**
    ・open-source data storage:HDFS
    ・Processing API:MapReduce
    ・other project/libraries:HBase,Hive,Pig
 **distribute**
    ・open source---Apache Hadoop
    ・commerical---MapR
    ・Cloud---AWS,Azure
 **why use Hadoop**
    ・cheaper
    ・faster
    ・better
