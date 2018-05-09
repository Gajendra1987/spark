# spark
Welcome to the spark wiki!

1. READ THE JSON FILE
scala> var jonDF=sqlContext.read.json("/sparktraining1/employee.json")
jonDF: org.apache.spark.sql.DataFrame = [designation: string, empId: bigint, name: string]

scala> var jsonDF=sqlContext.read.json("/sparktraining1/employee.json")
jsonDF: org.apache.spark.sql.DataFrame = [designation: string, empId: bigint, name: string]

scala> jsonDF.registerTempTable("emp");

scala> sqlContext.sql("select * from emp");
res2: org.apache.spark.sql.DataFrame = [designation: string, empId: bigint, name: string]

scala> sqlContext.sql("select * from emp").show();
+-----------+-----+--------+
|designation|empId|    name|
+-----------+-----+--------+
|       Lead| 1001|   Arjun|
|   Engineer| 1002|   David|
| Accountent| 1003|Gajendra|
|  Developer| 1004|   Phani|
|  Architect| 1005|    John|
+-----------+-----+--------+


scala> import org.apache.spark.sql.types._
import org.apache.spark.sql.types._

scala> var empSchema=StructType(List())
empSchema: org.apache.spark.sql.types.StructType = StructType()

scala> var empSchema=StructType(List(
     | StructField("empId",IntegerType,false),
     | StructField("name",StringType,false),
     | StructField("designation",StringType,false))
     | )
empSchema: org.apache.spark.sql.types.StructType = StructType(StructField(empId,IntegerType,false), StructField(name,StringType,false), StructField(designation,StringType,false))

scala> var jsonDF=sqlContext.read.schema(empSchema).json("/sparktraining1/employee.json")
jsonDF: org.apache.spark.sql.DataFrame = [empId: int, name: string, designation: string]

scala> jsonDF.registerTempTable("emp_tbl");

scala> sqlContext.sql("select * from emp_tbl").show
+-----+--------+-----------+
|empId|    name|designation|
+-----+--------+-----------+
| 1001|   Arjun|       Lead|
| 1002|   David|   Engineer|
| 1003|Gajendra| Accountent|
| 1004|   Phani|  Developer|
| 1005|    John|  Architect|
+-----+--------+-----------+


scala> 

