
# Repartition and PartitionBy


### Rebalancing skewed datasets

The idea is to have a random number inside natural partitions 
that will control a the rows that will come inside each partition's file. 

The way to creates this numbers should have an equal distribution to help
all files terminate with an aproximate size. 


```python
from pyspark.sql.functions import rand

partitions = ['field1', 'field2', 'fieldn']
number_of_rows_per_file = 1_000_000
partition_count = df.groupBy(*partitions).count()

df_balanced = ( 
                df
                .join(partition_count, on=partitions)
                .withColumn('partition_seed', rand() * col('count') / number_of_rows_per_file)
                .repartition(*partitions, 'partition_seed')
              )
```

Related and useful links:
- [Partitioning a large skewed dataset in S3 with Spark's partitionBy method](https://stackoverflow.com/questions/53037124/partitioning-a-large-skewed-dataset-in-s3-with-sparks-partitionby-method/65433689#65433689)