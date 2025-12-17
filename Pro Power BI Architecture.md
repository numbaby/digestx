# Pro Power BI Architecture: Development, Deployment, Sharing, and Security for Microsoft Power BI Solutions, 2nd Edition
By: Reza Rad
Publisher: Apress © 2023

### Import Data or Scheduled Refresh
The Import Data connection type imports the entire dataset into memory. This is the memory of the machine that hosts the Power BI dataset. If you have a Power BI dataset opened on the Power BI Desktop, it will be the memory of the machine where Power BI Desktop is running. 
When you publish your Power BI file to the Power BI website, it will be the memory of that machine in the cloud.

Loading data into memory also means something more; data needs to be refreshed. You need to schedule data updates if you are using this method. Otherwise, the data will become obsolete. That is why this technique is called Import Data or Scheduled Refresh.

### How Power BI Stores Data in Memory
The first question that might come to your mind is how big the memory needs to be. What if you have hundreds of millions of records? Or many gigabytes of data? How does Power BI store data in memory? 
To answer these questions, you need to first learn a little bit about the in-memory engine called xVelocity.

Power BI, SQL Server Analysis Services Tabular, and Power Pivot are three technologies that use the same engine for storing data—the in-memory engine called **xVelocity**. xVelocity stores data in memory. However, it applies a few compression steps to the data before storing it. The data stored in memory will not be the same size as your data source in the majority of the cases. Data is compressed significantly. However, the compression is not always at the same rate. Depending on many factors, it might behave differently.

### How xVelocity Compresses Data
To really understand the concept of data compression in xVelocity, you would need to read an entire book. However, in this section, I’m going to briefly explain what happens when the xVelocity engine works on compressing the data.
Traditional database technologies stored data on disk because the dataset was too large. 

**xVelocity** uses column-store technology combined with other performance-tuned compression algorithms. In simple words, xVelocity stores data column by column. It first sorts every column by its values. Then it creates a mapping table (see Table 3-2) for it with indexes at the beginning and end of each section (this is also run-length encoding [RLE] compression).

Table 3-1: Traditional Way of Storing Data
Table 3-2: xVelocity Compression and Mapping Table

2025.12.17
