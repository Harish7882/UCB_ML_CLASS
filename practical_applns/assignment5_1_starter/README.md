# EXPLORATORY DATA ANALYSIS ASSIGNMENT

### GOAL:
Using the provided Amazon Mechanical Turk Survey data on different driving scenarios, time of the day, weather, passenger information etc, we need to determine the answer 
for the primary question below.

##### Primary Question : "Will a customer accept a Coupon?"

There are 3 possible answers:
* “Right away”
* “Later, before the coupon expires”
* “No, I do not want the coupon”

We need do a exploratory analysis on this data to determine which **features play a significant role** in determines whether a customer will accept the coupon or not. 

### BUSINESS USECASE:
Amazon wants to use this information to promote local businesses by presenting the `right coupon` at the `right time` to the `right customer` to maximize acceptance rate
and consequentially drive business for the coupon provider. So We need do a exploratory analysis on this data to determine which features play a significant role
in determines whether a customer will accept the coupon or not. 

### AVAILABLE DATA:
##### User Attributes: 
| Attribute                     | Possible Values                                                     |
| ----------------------------- | ------------------------------------------------------------------- |
| **Gender**                    | male, female                                                        |
| **Age**                       | below 21, 21–25, 26–30, etc.                                        |
| **Marital Status**            | single, married partner, unmarried partner, widowed                 |
| **Number of Children**        | 0, 1, more than 1                                                   |
| **Education**                 | high school, bachelor’s degree, associate’s degree, graduate degree |
| **Occupation**                | architecture & engineering, business & financial, etc.              |
| **Annual Income**             | less than $12,500; $12,500–$24,999; $25,000–$37,499; etc.           |
| **Bar Visits**                | 0, less than 1, 1–3, 4–8, greater than 8                            |
| **Takeaway Purchases**        | 0, less than 1, 1–3, 4–8, greater than 8                            |
| **Coffee House Visits**       | 0, less than 1, 1–3, 4–8, greater than 8                            |
| **Restaurant (< $20) Visits** | 0, less than 1, 1–3, 4–8, greater than 8                            |

##### Contextual Attributes: 
| Attribute                | Possible Values                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------- |
| **Driving Destination**  | home, work, no urgent destination                                                  |
| **Location Information** | Map showing user, coupon, and destination with travel time and direction alignment |
| **Weather**              | sunny, rainy, snowy                                                                |
| **Temperature**          | 30°F, 55°F, 80°F                                                                   |
| **Time**                 | 10AM, 2PM, 6PM                                                                     |
| **Passenger**            | alone, partner, kid(s), friend(s)                                                  |

##### Coupon Attributes: 
| Attribute              | Possible Values |
| ---------------------- | --------------- |
| **Time Before Expiry** | 2 hours, 1 day  |

<img width="567" height="560" alt="download" src="https://github.com/user-attachments/assets/b2c413c1-588d-4450-a389-84bc2908d3d6" />

### ANALYSIS RESULTS: 
Acceptance Rates 

