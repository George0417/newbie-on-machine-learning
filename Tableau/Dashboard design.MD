### Advantage
1.only when we start the chart do we understand the difference between different data sets.this is the power of visual analytics.

### Five design principle
1. relevant metrics
...if it doesn't get measured,it doesn't get improved.

2. make it visual
...human being eye is much better at reading graphs,using chart aid in the analysis of data. 
...make it 3-5 kind of dashboard retio

3. make it interactive
...let user explore the data and adjust it to meet their needs.

4. make it easy to use
...through Tableau Server or Tableau Public

5. keep improving
...requirement Gathering(who is the ueser,usability feedback)----Design---Feedback(interview,surveys,specific data use case,demoing)---redesign---test---redesigh---launch

### data sourse
databank.worldbank.org/data/home.aspx


### Picking charts
1.Bar graphs for categorical
2.Line for time series
3.Pie for %comparisons
4.Scatter plots for relationships
...www.tableau.com/sites/default/files/media/which_chart_v6_final_0.pdf

### operation on Tableau
1.open excel and find the file
2.grab the datarevised and drag it over to the sheet
3.go over to the work sheet 
4.drap some measures data to darp field and if you want to see the relationship betwwen it , you could drap the other measures data to the Columns to wind up with the the base of scatter plot.last drag the Dimensions data into the color.
5.click the analystics and drap the trend line to our relationship and we can got the P-Value
⇒the scatter plot can't tell us the fact but can tell us the relationship between two datas
6.To calculate the ratio
  we need right click to creat calculated field -ratio(sum (money)/sum(people))
  then drap the new ratio to the drop field
  convert the year data to discrete and darp to the drop field
 
 ### calculated field
 Create new calculated field as v-area
 input the code 
 ELSEIF[country]="Turkey" THEN "Middle EAST"
 END
 
 ### plot
 1.drap the internet ratio to the dimensions
 2.put the country into the drop field
 3.click the chart on show me bar
 4.get out of the bar and go up and down
 5.drop the v-area to the color then you can see the bar plot with different region
 
 ### creat sets , do the filter and merge them
 1.add new sheet
 2.click the country and click create set
 3.condition setting to do the filter then you will get one set1
 3.Top setting can use to select top 10 ones with population then you will get one set2
 4.click one set and click create combined set and can get the set satisfy both option.
 
 ### Reference lines
 1.change the graph from automatic to circle at the marks bar
 2.right click on the Y-Axis and click on Add Reference Line
 3.you can change the label to custom and set it to AVg:,click the > select value
 ⇒the reference line can tell us one ,the overall view of the trend and to be able to see which one are above and below the trend.
 
 ### Dashboard Hierarchy
 Left to right ,Top to bottom
 1.Foundation lawer
 ...base of the report,background
 
 2.Control
 ...Parameters
 
 3.Content
 ...Text,tables,graphs
 
 ------------------------------------------------
 To create a report
 1. click the dashboard
 2. drag the text set the word to be 36 input the title 
 3. drop the vertical in uderneath the title
 4. garb the sheet and drag it down put it underneath the context 

### story
1.new story feature
⇒example how to make the story
1 public.tableau.com/s/gallery


### dashboard object----set the boundary layer
1.drop the horizontial or vertical to the underneath of the context
2. then drop the sheet and adjust the size of it
3.double click one of the graph then click the Format Container on the right corner and select the border. 

### Quick filter
1.back to the work sheet
2.drag the Dimension data such like country,region,year to the filters area
3.right click the country,apply to worksheets---all using this data source
4.go to the dashboard,drop the horizontal to the top of the contatx
5.go to anysheet and right click and choose quick filters and select region then drag to the top
6.repeat it to choose the filter you need and add to the right side of the top
7.right click the region filter then choose multiple values(dropdown)
8.right click the region filter then choose only relevant values
9.click the arrow in the top of right on region filter,then choose format quick filters,clikc the shading.

>>change the color of the table 
dashboard ----format----subtitle and shading

### Design interactivity with parameters---add filters to change the parameters
1.jump to sheet 1,under the dimension section,right click and do create parameter
2.change data type to string,allow value to be list and write the data name on the list,such like country,region
3.go to the dashboard ,click the arrow on the top right of graph,select parameters to which you create.
4.create calculated field and input """IF [Dimension Selector]="country"then [country] ELSEIF [Dimension Selector]="region"then[region]END"""
5.replace this caluculated rule into the columns

### change chart types with two graph
1.duplate the sheet with bar and map
2.create parameter,change data type into string
3.change the list of values,like add bar and map in the list
4.then you can see the new chart type in the parameters in the lift of bar
5.clikc the map in the show me bar which can let you jump into de map graph
6.format the values,right click and choose format,select AVG(Internet usage Ratio)color item from fields
7.change the number(custom)to 1
8.edit the color for area brown and click the stepped color
9.create calculated field and input """IF [chart type]="bar"then "bar" ELSEIF [chart type]="Map"then"Map"END"""
10.drop the chart type into the filters and select the custom values and add map
11.right click the graph and add quick filter ,choose country.
12.right click the label and choose the multiple values(Dropdown)

### add Page into the mian dashboard
1.right click the Y-axis and add reference line
2.choose label to custom,Avg:<Values>
3.drop off the show recalculated line for highlighted and choose the fill below
4.drop the new dashbood page into the main sheet

### highlight
1.clikc the dashboard on the top and click the actions
2.add action select highlight
3.then select fields at the target highlighting and click the parameters
