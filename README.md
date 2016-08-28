# jelastic-spark-cluster
Jelastic CloudScript to create an Apache Spark Standalone cluster

## How to import the cluster
Firstly, clone this project in any folder you like.

In Jelastic control panel, click in the down arrow button at the side of
'New environment', and then click in 'import'. After that, in 'Local file' tab,
click in 'Browse', select the jelastic-spark-cluster.json file, and click in 'Import'
button.

In the next dialog, set the name of the environment, the region, and click in
'Install' button.

## How to run the job
Access the container in Jelastic using SSH:

```{bash}
ssh -p 3022 <Your user number>@gate.<the domain of you Jelastic host>
```

For example:

```{bash}
ssh -p 3022 9999@gate.demo.jelastic.com
```

After that, access the container named **master**. Inside the **master**
 container, access the **job** folder and run the following command:

```{bash}
/opt/spark-2.0.0-bin-hadoop2.7/bin/spark-submit --class WordCount --master spark://$HOSTNAME:7077 spark-wordcount-assembly-1.0.jar /inputs /outputs
```
