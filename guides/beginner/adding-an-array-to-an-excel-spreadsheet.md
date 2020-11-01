# Adding an array to an Excel spreadsheet

The OpenAF's XLS plugin offers one of the most handy features: the ability to write a simple javascript array of maps to an Excel spreadsheet. But first a warning: it can't be a complex sub maps/arrays, just plain strings/numbers array which usually is enough (although there is an alternative way that will mention on the end of the post).

The functionality is captured on the setTable function of the XLS plugin. Giving an example, let's say we get an array with all the files and corresponding info from a folder using io.listFiles: 

````javascript
var path = ".";
var outputFile = "test.xlsx";

var listOfFiles = io.listFiles(path).files; 
// files is an array returned by io.listFiles with filesystem details of files & folders on the provided path

plugin("XLS");
var xls = new XLS(); 

// Determines in which sheet the array will be added
var sheet = xls.getSheet("my sheet"); 

// Writes all the array elements and corresponding properties to the provided sheet starting on excel position B2.
xls.setTable(sheet, "B", "2", listOfFiles); 

// Writes the prepared excel to a xls/xlsx file.
xls.writeFile(outputFile);
xls.close(); 
// Don't forget to close the object to free up used files and resources before using the generated excel file.
````

On the first lines of the code we defined the output file as "test.xlsx". After running this script: 

````bash
openaf -f test.js
````

if there wasn't any errors you will find a test.xlsx on the same folder that will look similar to this:

![xls-files-sample-1](xls-files-sample-1.png)

The first instinct is: "can I format it?" The answer is yes. You can add an auto-filter easily:

````javascript
ow.loadFormat();
ow.format.xls.autoFilter(sheet, "B2:K2")
````

"Can I change color, font, etc&#46;&#46;&#46;?": Yes, check out ow.format.xls.getStyle.

"Can I just use a previous excel template and just fill it in?": Yes. The probably the easiest to do. Just change the new XLS line to this:

````javascript
var xls = new XLS("myTemplate.xlsx");
````