# Tutorial

For my story, I looked at the crimes that have been committed in the West Midlands between 1 January 2020 and 31 August 2020. I wanted to know how many of them have already been solved and what the outcomes were. 

I downloaded the data at [data.police.uk](https://data.police.uk/data/) (I selected the mentioned date range and ticked "West Midlands" as force as well as the data sets "crime data" and "outcomes data"). 

For every month and selected data set you'll get a seperate .csv file. At first you have to put them all in two Excel-sheets: one for the crimes and one for the crime outcomes (the files have a column in which the date is stored, so you still know in which month the crime was committed/ the outcome was published). I named them "crimes-2020-west-midlands" and "outcomes-2020-west-midlands". 

When you look at your data, you will see that (almost) every crime has a Crime-ID. I used **VLOOKUP** to match each crime with its outcome. Before I did that, I copied the "crimes-2020-west-midlands" sheet and renamed the copy to "crimes-and-outcomes-2020". In the new sheet, I added a column with the name "Outcome types" - this is where I want to see the outcome for each crime. 

  =VLOOKUP(A2,'outcomes-2020-west-midlands'!A:J,10,FALSE)

- A2 = the cell in which the Crime-ID is stored - this is the value I want to look up
- 'outcomes-2020-west-midlands'!A:J = the sheet in which the crime outcomes are stored, the range is between the Crime-ID (first column) and the outcome type (in this case last column)
- 10 = the column in which the outcome type is stored. This is the information I want to bring back 
- FALSE = to get an exact match

After you run the function, you can see the outcome type for each crime - but in some cases it says **"#N/A"** instead. You can sort your data, so that they come to the top. 
You will see that for every crime of "Anti-social behaviour" there is no Crime-ID. Therefore, there is also no information on the outcomes of these crimes. If there is no ID, VLOOOKUP cannot match the crime with the outcome. You can rename those to something like "Anti-social behaviour: no outcome data". 

Then, take a look at the remaining "#N/A"s again. The column "Last outcome category" gives information about the investigation status. There are two types left: "Status update unavailable" and "Under investigation". Rename the "#N/A"s accordingly. 

You can work out which outcome type occours most often by using a **pivot table** and placing the field "outcome type" in both rows and value box. You could also use the **COUNTIF** function. 

You can read the story [here](https://medium.com/@vanessa.fillis/only-4-percent-of-suspects-charged-in-2020-b725b3d7ba6f?sk=c560b22e9654f92f9575cf43a0860d32). 
