# Configuring PySpark on Windows 7

## Default Spark home on Windows

`SPARK_HOME=C:\spark-1.6.1-bin-hadoop2.6`

## Windows %PATH% Update

Add `C:\spark-1.6.1-bin-hadoop2.6\bin` to the Windows `%PATH%`

## Configuring Hadoop Stub

Create `C:\HADOOP_HOME` directory
Add `HADOOP_HOME=C:\HADOOP_HOME` to the User Environment
Copy **winutils.exe** into `C:\HADOOP_HOME\bin` directory

## To Start PySpark

`pyspark --driver-memory 512M --executor-memory 2G --executor-cores 2`

## To Start Spark-Shell

`spark-shell --driver-memory 512M --executor-memory 2G --executor-cores 2`

## To Start Spark UI

Spark UI: [http://localhost:4040/](http://localhost:4040/)

## PySpark Example

Spark example in interactive Python (didn't work: exec(open("./pi.py").read())):

```python
import sys
from random import random
from operator import add
partitions = 2
n = 1000000 * partitions
def f(_):
    x = random() * 2 - 1
    y = random() * 2 - 1
    return 1 if x ** 2 + y ** 2 < 1 else 0

count = sc.parallelize(range(1, n + 1), partitions).map(f).reduce(add)
print("Pi is roughly %f" % (4.0 * count / n))
```

## References

[How to set up Spark on Windows?](http://stackoverflow.com/questions/25481325/how-to-set-up-spark-on-windows)

[How to run Apache Spark on Windows7 in standalone mode](http://nishutayaltech.blogspot.ca/2015/04/how-to-run-apache-spark-on-windows7-in.html)
