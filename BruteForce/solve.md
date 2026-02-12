# Question 1) How many Audit Failure events are there? 

To solve this, count the number of occurrences of "Audit Failure" in the text file.

![alt text](image.png)

# Question 2) What is the username of the local account that is being targeted?

![alt text](image-1.png)

# Question 3) What is the failure reason related to the Audit Failure logs?

![alt text](image-2.png)

# Question 4) What is the Windows Event ID associated with these logon failures?

![alt text](image-3.png)

# Question 5) What is the source IP conducting this attack?

![alt text](image-4.png)

# Question 6) What country is this IP address associated with?

Look up the discovered IP address using GeoIP lookup services.

![alt text](image-5.png)

# Question 7) What is the range of source ports that were used by the attacker to make these login requests?

For this question, write a simple Python script to parse the CSV file content. Extract all source port values into a set or list, then output the minimum and maximum port numbers to determine the range.

![alt text](image-6.png)