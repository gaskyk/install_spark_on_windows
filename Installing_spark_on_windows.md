# Installing Spark on a Windows 10 local machine

1. Install Java. In my case this was already installed.
2. Add the Java path to your environment variables. To do this in Windows 10, search for "env";, which brings up the &#39;System Properties&#39; window and &#39;Advanced&#39; tab. Click on &#39;Environment variables&#39; at the bottom, then in the &#39;System variables&#39; section, edit the &#39;Path&#39; to add in a link to where java is installed on your machine
3. Check Java is correctly installed by typing `java –version` into the CMD command prompt in Windows. It should return a version number (eg. 1.8)
4. Download scala. The latest version is at the bottom of [this page](https://www.scala-lang.org/download/), for example &#39;scala-2.13.0.zip&#39;. Unzip the files then save them to &#39;C:\Program Files&#39;
5. Add the scala path to your environment variables. The path will look similar to &#39;C:\Program Files\scala-2.13.0\bin&#39;
6. Check that scala is correctly installed by typing `scala –version` into the CMD command prompt in Windows. Again, it should return a version number (eg. 2.13)
7. Download Spark. To do this, go to this page, click on the .tgz file (eg. Spark-2.4.3-bin-hadoop2.7.tgz) then download from one of the mirrors shown
8. Windows struggles with .tgz files, so when I unzipped the .tgz file, Windows thought I had a .7 file (representing the end of the Spark-2.4.3-bin-hadoop2.7 string). I needed to rename this file to .tgz or .zip to be able to unzip it further
9. Save the unzipped spark files into somewhere like C:\ProgramFiles. You may need to create this folder, but spark won&#39;t recognise it if it has a space in the file extension (eg. C:\Program Files).
10. Add the spark\bin path to your environment variables.
11. If you have Anaconda3 for Python installed, you will also need to add a link to this to the environment variables
12. Check that spark is correctly installed by typing `spark-shell` into the CMD command prompt in Windows. It should return &#39;Welcome to spark&#39; with the spark version number

## To use pyspark from Python

1. Install the pyspark package. It is not part of Anaconda so you will need to install it specifically (via something like `conda install pyspark`)

```
# Load packages
From pyspark.sql import SparkSession
From pyspark import SparkContext

# Connect to the local spark instance using as many threads as on your machine
spark = SparkSession.builder.master("local[\*]";).appName("test").getOrCreate()

# Example to read in a CSV
my_data = spark.read.csv("/path/to/csv/my\_data.csv", header=true)

```