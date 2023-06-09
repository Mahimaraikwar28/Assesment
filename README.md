# Assesment
## Back-end Internship at Volopay

### Steps to create a new project and install node in it.
1.npm init -i

2.now install express by 
node i express

3.Install the required dependencies by running the following command:
node i csv
node i fs

4.Import the card transaction dataset into your preferred database system or use it directly from the provided CSV file.

Start the server by running the following command:

* npm main.js

The server will start running on http://localhost:3000 by default.




## Api 1:

### End point : /api/total_items ,
### API Use Cases :

### Total item (total seats) sold in Marketting for last in q3 of the year?
### Expected O/P: returns integer
### Parameters: {start_date: DATE, end_date: DATE, department: string}

### Sol: 
Total Items Sold in Marketing
* Endpoint: /api/total_items
* Method: GET
* Parameters:

    start_date: Start date of the quarter (e.g., "2023-07-01").

    end_date: End date of the quarter (e.g., "2023-09-30").

    department: Department name.
* Response: Returns an integer representing the total items sold.

### Code Explaination:

1.we have initialize variable 'count' to 0 it will be used to keep track of total number of items.

2.Then we have for loop which iterates over the 'results' array, which contain object with a date property.

3.`const date = results[i].date.substring(0,11).split("-")[1];`: This line extracts the month portion from the `date` property of each object in the `results` array.It uses the `substring()` method to extract the first 11 characters, and then the `split()` method to split the resulting string by "-", returning an array. The `[1]` index retrieves the month portion.

4.Then we are checking a if condition in which we are extracting month which is betweren july(7) and september(9), if the condition is true then the code inside if is executed.

5.Then we are incrementing the value of 'count' by 1 for each object in the 'results'.

6.`res.json({"total_items": count});`: This line sends a JSON response back to the client with a single property `"total_items"` containing the value of the `count` variable.

Conclusion: The above code calculates the total number of items that have a date between july and september in the 'results' array.



## Api 2:

### End point : /api/nth_most_total_item ,

### API Use Cases:

### 1.What is the 2nd most sold item in terms of quantity sold in q4,

### 2.What is the fourth most sold item in terms of Total price in q2?

### Expected O/P: returns string name

### Parameters: { item_by: ("quantity" | | "price"), start_date: DATE, end_date:DATE, n:integer }

### Sol:
* Endpoint: /api/nth_most_total_item
* Method: GET
* Parameters:

    item_by: Type of ranking ("quantity" or "price").

    start_date: Start date of the quarter (e.g., "2023-10-01").

    end_date: End date of the quarter (e.g., "2023-12-31").

    n : Position of the item in the ranking.

* Response: Returns the name of the item.

### Code Explaination: 

1.Initialize an empty object 'frequencymap', it is used to store the frequency count of software names.

2.Iterate a loop over the 'results' array.Array name results contains a 'date' property and a 'software' property.

3.`const date = results[i].date.substring(0,11).split("-")[1];`: This line extracts the month portion from the `date` property of each object in the `results` array.It uses the `substring()` method to extract the first 11 characters, and then the `split()` method to split the resulting string by "-", returning an array. The `[1]` index retrieves the month portion.

4.Then we are providing the if condition which checks whether the extracted month is in between october(10) and december(12),if the condition is true the code inside the if statement is executed.

5.'frequencymap[results[i].software] = (frequencymap[results[i].software] || 0) + 1;`: This line increments the frequency count of the `software` name in the `frequencymap` object. If the `software` name does not exist in the `frequencymap`, it is initialized to 0 before incrementing.

6.Then we are converting the 'frequencymap' object into an array of key value pair using 'Object.entries()' method.

7.Then we are sorting 'name1' array in descending order on the frequency count (['1']) of each entry.

8. `name1 = name1[1][0];`: This line retrieves the software name from the second entry (`[1]`) in the `name1` array (since array indices start *at 0) and assigns it to the `name1` variable.

9.`res.json({"software1": name1, "software2": name2});`: This line sends a JSON response back to the client.The value of the property are software name with second highest frequency count and fourth highest frequency count.

Conclusion: The above explaination provides a way to determine the software names with specific frequency ranks based on the provided date ranges.


## Api 3:

### End point : /api/percentage_of_department_wise_sold_items

### API Use Cases:

### 1.What is the percentage of sold items (seats) department wise?

### Expected O/P: {dept_name: x%,....... }

### Parameters: {start_date: Date, end_date: Date}

### Sol: 
Percentage of Department-wise Sold Items
* Endpoint: /api/percentage_of_department_wise_sold_items
* Method: GET
* Parameters:
    start_date (string, required): Start date of the period.

    end_date (string, required): End date of the period.

* Response: Returns an object with department-wise sold item percentages.

### Code Explaination: 

1.Initializes an empty object called `frequencymap` and a variable `total_count` to keep track of the total count of sold items.

2.Then we have a variable total_count which is initialize to o and it will keep track of sold items.

3.Then we are running a loop over the 'results' array.'Results' array contains object with property name 'department' and 'seats'.

4.`frequencymap[results[i].department] = Number(frequencymap[results[i].department] || results[i].seats) + Number([results[i].seats])`: It will increment the frequency count of items in the 'frequencymap' object.If the `department` does not exist in the `frequencymap`, it initializes it with the value of `results[i].seats`. It then adds the value of `results[i].seats` to the existing count.

5.Then we are calculating the total_count of sold items by adding the values of `results[i].seats` to the `total_count` variable.

6.Then we are returning the 'total_count' value to the console.

7. `for (let key in frequencymap) { ... }`: This is a loop that iterates over the departments in the `frequencymap` object.

8.Then we are calculating the percentage of the sold items by diving the frequency count of the department by the 'total_count' and multiplying it by 100 then we are  rounding the result to 2 decimal points.

9.Then we are sending the JSON response to the client.

Conclusion: This will calculates the percentage of sold items per department and returns the result as a JSON response.