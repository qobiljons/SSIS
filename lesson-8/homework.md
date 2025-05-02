You have folder and files. File names are like this: data1.txt data2.txt….. till  data10.txt.
You need to process flat files from a folder (data1.txt, data2.txt, etc.), but only those with a numeric suffix less than 5 (i.e., data1.txt, data2.txt, data3.txt, data4.txt). The task will:
1.	Dynamically construct file names based on a numeric index using a For Loop.
2.	Use a Script Task to log each file name being processed.
3.	Load data from these files into a SQL table (dbo.Customers), adding a LoadDate column (current date/time).
