# Challenge 11: UFOs

## Overiew of UFOs
The purpose of this project is to build a web page for UFO Sightings which allows users to dynamically filter the presented data based on their input. The table filters available are: date, city, state, country and shape. This application will be using JavaScript and HTML. 

The data for the web page is in [data.js](https://github.com/Hala-INTJ/UFOs/blob/main/static/js/data.js), the web application logic is in [app.js](https://github.com/Hala-INTJ/UFOs/blob/main/static/js/app.js) and the structure of the webpage is in [index.html](https://github.com/Hala-INTJ/UFOs/blob/main/static/js/index.html).
## UFOs Results

The UFO webpage displays filter criteria fields on the left and a table of UFO Sightings on the right. To filter the list of UFO Sightings, enter values in any of the filter fields, then press "enter" or "tab", and the table will be updated automatically.

The solution is divided into these three parts:
### Building the Table
Upon loading the webpage, the UFO Sightings data in [data.js](https://github.com/Hala-INTJ/UFOs/blob/main/static/js/data.js) is loaded and presented in a table. The code in [app.js](https://github.com/Hala-INTJ/UFOs/blob/main/static/js/app.js) registers event handlers on the text input fields, which then invokes a callback function to update the table content.

![](https://github.com/Hala-INTJ/UFOs/blob/main/static/images/webpage.png)
### Update Filters
When the user alters the text in any of the text input fields, the sets of filters is updated. Filters can be removed by clearing the values in the fields. The filters are only updated after pressing "enter" or "moving focus". 
### Filtering the Table
Whenever filters are updated, the data displayed in the table is updated accordingly and the user interface is refreshed. Only rows which match all filter values will be displayed, and only exact matches.

![](https://github.com/Hala-INTJ/UFOs/blob/main/static/images/filtered_table.png)
## Summary
### Drawback of The Webpage
All of the data is loaded into the webpage upfront, therefore, this may become a scalability issue -- if the number of rows exceed hundreds of thousands. 
### Recommendations For Further Development
#### Improve Filtering 
The current solution requires the user to enter exact match filter criteria. To enhance the user experience, the filter values could be interpreted as patterns, rather than exact matches. 

| Before | Modification | Comments| 
| --- | --- | --- |
| ```d3.selectAll("input").on("change", updateFilters);``` | ```d3.selectAll("input").on("input", updateFilters);``` | Apply filters as the user types rather than waiting for "enter" or "tab" |
| ```Object.entries(filters).forEach(([key, val]) => { filteredData = filteredData.filter(row => row[key] === val);})``` | ``` Object.entries(filters).forEach(([key, val]) => { filteredData = filteredData.filter(row => row[key].startsWith(val));})```| Filter matches on the first part of the text rather than the entire text |
| ```Object.entries(filters).forEach(([key, val]) => { filteredData = filteredData.filter(row => row[key] === val);})``` | ``` Object.entries(filters).forEach(([key, val]) => { filteredData = filteredData.filter(row => row[key].includes(val));})``` | Filter matches anywhere found in the text |
#### Replace Text Filters With Selections
For some fields such as state and shape, it would be better to present the user with a drop-down list of values to select from. These values could be discovered from the data. Here's an example for the shape filter field:

![](https://github.com/Hala-INTJ/UFOs/blob/main/static/images/dropdown_allshapes.png) ![](https://github.com/Hala-INTJ/UFOs/blob/main/static/images/dropdown_oval.png)






