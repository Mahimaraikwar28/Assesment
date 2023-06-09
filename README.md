# Assesment
## Back-end Internship at Volopay

### Steps to create a new project and install node in it.
npm init -i
now install express by 
node i express
Install the required dependencies by running the following command:
node i csv
node i fs
Import the card transaction dataset into your preferred database system or use it directly from the provided CSV file.

Start the server by running the following command:

npm main.js
The server will start running on http://localhost:3000 by default.




### Api 1:

End point : /api/total_items ,
API Use Cases :
1. Total item (total seats) sold in Marketting for last in q3 of the year?
Expected O/P: returns integer
Parameters: {start_date: DATE, end_date: DATE, department: string}

sol: 
1. Total Items Sold in Marketing
Endpoint: /api/total_items
Method: GET
Parameters:
start_date: Start date of the quarter (e.g., "2023-07-01").
end_date: End date of the quarter (e.g., "2023-09-30").
department: Department name.
Response: Returns an integer representing the total items sold.

Code Explaination:

1.we have initialize variable 'count' to 0 it will be used to keep track of total number of items.

2.Then we have for loop which iterates over the 'results' array, which contain object with a date property.

3.`const date = results[i].date.substring(0,11).split("-")[1];`: This line extracts the month portion from the `date` property of each object in the `results` array.It uses the `substring()` method to extract the first 11 characters, and then the `split()` method to split the resulting string by "-", returning an array. The `[1]` index retrieves the month portion.

4.Then we are checking a if condition in which we are extracting month which is betweren july(7) and september(9), if the condition is true then the code inside if is executed.

5.Then we are incrementing the value of 'count' by 1 for each object in the 'results'.

6.`res.json({"total_items": count});`: This line sends a JSON response back to the client with a single property `"total_items"` containing the value of the `count` variable.

Conclusion: The above code calculates the total number of items that have a date between july and september in the 'results' array.