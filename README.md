# Working on Big-Data using PySpark:
 *Created by Anmol Kumar [May 11 2022]*

### Libraries required:
* Pandas, PySpark. To view instructions on installing them, visit [Pandas](https://pandas.pydata.org/) and [PySpark](https://spark.apache.org/docs/latest/api/python/index.html).
* In addition to this, Java is also required. Visit [Java](https://www.java.com/en/) for instructions.

### Process followed:
* Reading the csv file using SparkSession object. Since the file is ~1.38GB, Pandas cannot be used.

##### Task 1:
* To get the products which don't have a price, I have used ``pyspark.sql.Column.isNull`` to filter the rows with ``price_string`` as ``null``.

##### Task 2:
* To count of products without prices and with prices in each Product Type, Category, Level 1, I first removed the duplicates in each type of product.
* After getting a DataFrame of each unique type, I extracted all the unique values in a list.
* After that, I iterated over each item in the list to separately obtain two new DataFrames having prices and not having prices
* ``pyspark.sql.DataFrame.count`` is then used to get the required number.

##### Task 3:
* Using ``pyspark.sql.DataFrame.filter``, ``pyspark.sql.Column.isNotNull``, ``pyspark.sql.Column.startswith`` and ``pyspark.sql.Column.substr``, we can process in the following sequential way.
* I first look for the entries which have workable ``price_string``, i.e., non-``null`` values.
* After that I only look for the entries which begin with dollar sign to extract their values.
* I then extract the values and arrange them separately in ``values`` Column.

##### Task 4:
* Iterating over every category, we can use ``pyspark.sql.DataFrame.agg`` to get average prices in every category.

### How to run the notebook?
* Make sure the required libraries and Python are installed.
* Next, make sure the ``data_values.csv`` is present in the same directory as the notebook.
* Open a terminal in the directory and run the notebook. For notebook, visit [Jupyter Notebook](https://jupyter.org/) or any other notebook installation websites for further instructions.
* In case of Jupyter, open the notebook and click on 'Cell', then 'Run All'.
