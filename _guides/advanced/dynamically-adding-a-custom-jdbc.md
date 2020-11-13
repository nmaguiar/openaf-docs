# Dynamically adding a custom JDBC driver

The latest OpenAF versions enable the dynamic loading of custom JDBC drivers. 

Let's take, for example, the [CSV JDBC](http://csvjdbc.sourceforge.net/) driver. After downloading the jar file to an empty folder let's also create a sample CSV file (test.csv):

````CSV
"key";"value"
1; "Item 1"
2; "Item 2"
3; "Item 3"
````

Then, on an OpenAF script or console execute:

````javascript
> loadExternalJars(".")
> var db = new DB("org.relique.jdbc.csv.CsvDriver", "jdbc:relique:csv:.?separator=;&fileExtension=.csv", "sa", "sa");
> sql db select * from test
key|  value
---+---------
1  | "Item 1"
2  | "Item 2"
3  | "Item 3"
[#3 rows]
````

So, what happened:

* The _loadExternalJars_ function tries to dynamically load all .jar files on the path provider (using the OpenAF's custom class loader).
* When creating the _DB_ object instance, OpenAf will try to find the provided JDBC class driver and will load it through an internal "proxy", if needed.
* The returned _DB_ object instance will work as the H2, PostgreSQL, etc&#46;&#46;&#46; drivers (within the limits of the JDBC driver).