# Hadoop

The Apache Hadoop software library is a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It is designed to scale up from single servers to thousands of machines, each offering local computation and storage. Rather than rely on hardware to deliver high-availability, the library itself is designed to detect and handle failures at the application layer, so delivering a highly-available service on top of a cluster of computers, each of which may be prone to failures.

Hadoop consists of four main modules:

Hadoop Distributed File System (HDFS) – A distributed file system that runs on standard or low-end hardware. HDFS provides better data throughput than traditional file systems, in addition to high fault tolerance and native support of large datasets.
Yet Another Resource Negotiator (YARN) – Manages and monitors cluster nodes and resource usage. It schedules jobs and tasks.
MapReduce – A framework that helps programs do the parallel computation on data. The map task takes input data and converts it into a dataset that can be computed in key value pairs. The output of the map task is consumed by reduce tasks to aggregate output and provide the desired result.
Hadoop Common – Provides common Java libraries that can be used across all modules.

![Logo](https://editor.analyticsvidhya.com/uploads/526181_kPKoXmHBDmGthbah-0549A.png)

Download Hadoop from here: https://hadoop.apache.org/releases.html

Download Java JDK from here: https://docs.oracle.com/en/java/javase/11/install/installation-jdk-linux-platforms.html#GUID-737A84E4-2EFF-4D38-8E60-3E29D1B884B8

extract and install
```bash
tar -zxvf hadoop-2.9.1.tar.gz (Extract the tar file)
 tar -zxvf jdk-8u45-linux-x64.tar (Extract the tar file)

sudo apt-get install vim (Install USER Friendly Editer)
```

 open bachrc file to source the hadoop and java files 
```bash
vi .bashrc (Set the java Path in your Home Path)

export JAVA_HOME=/home/username/jdk1.8.0_45
export PATH=HOME/bin:JAVA_HOME/bin:PATH

 source .bashrc 
 echo JAVA_HOME 
```

2. Modify Hadoop Configuration Files
```bash
NAMENODE ----> core-site.xml
RESOURCE MANGER ----> mapperd-site.xml
SECONDARYNAMENODE ---->
DATANODE ----> slaves
NODEMANGER ----> slaves & yarn-site.xml
```

vi etc/hadoop/core-site.xml
```bash
<property>
<name>fs.default.name</name>
<value>hdfs://localhost:50000</value>
</property>
```
 vi etc/hadoop/yarn-site.xml
```bash
<property>
<name>yarn.nodemanager.aux-services</name> <value>mapreduce_shuffle</value>
</property>
<property>
<name>yarn.nodemanager.aux-services.mapreduce.shuffle.class</name> <value>org.apache.hadoop.mapred.ShuffleHandler</value>
</property>
<property>
<description>The hostname of the RM.</description>
<name>yarn.resourcemanager.hostname</name>
<value>localhost</value>
</property>
<property>
<description>The address of the applications manager interface in the RM.</description>
<name>yarn.resourcemanager.address</name>
<value>{yarn.resourcemanager.hostname}:8032</value>
</property>
```

 vi etc/hadoop/hdfs-site.xml
```bash
<property>
<name>dfs.namenode.name.dir</name>
<value>/home/username/hadoop2-dir/namenode-dir</value>
</property>
<property>
<name>dfs.datanode.data.dir</name>
<value>/home/username/hadoop2-dir/datanode-dir</value>
</property>
```

 vi etc/hadoop/mapred-site.xml
```bash
<property>
<name>mapreduce.framework.name</name>
<value>yarn</value>
</property>
```

```bash
 vi etc/hadoop/hadoop-env.sh
export JAVA_HOME=/home/username/jdk1.8.0_45

 vi etc/hadoop/mapred-env.sh
export JAVA_HOME=/home/username/jdk1.8.0_ 45

 vi etc/hadoop/yarn-env.sh
export JAVA_HOME=/home/username/jdk1.8.0_45

 vi etc/hadoop/slaves
localhost
```

install the ssh key for passwordless communication

```bash
(Generates, Manages and Converts Authentication keys)
 sudo apt-get install openssh-server
 ssh-keygen -t rsa
(Setup passwordless ssh to localhost and to slaves )
 cd .ssh
 ls
 cat id_rsa.pub >> authorized_keys (copy the .pub)
(Copy the id_rsa.pub from NameNode to authorized_keys in all machines)
 ssh localhost
(Asking No Password )

```

Some basic hadoop commands

```bash
bin/hadoop fs -ls/  (to list files in hdfs)
bin/hadoop -mkdir /data (to upload a file named data to hdfs)
bin/hadoop fs -put/home/username/words /w1.txt (to upload a local folder to hdfs)

```

To start and stop hadoop

```bash
sbin/start-all.sh
sbin/stop-all.sh

```

## Documentations

[hadoop](https://hadoop.apache.org/) 

[Java jdk](https://docs.oracle.com/javase/8/docs/)



## Authors

- [@Anshumaan - <anshuphukan031@gmail.com>](https://github.com/Anshumaan031)
