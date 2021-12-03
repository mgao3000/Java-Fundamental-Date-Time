### Using Java Date and Time libraries, create a new class called CalendarHelper.

### The class skeleton is under package "com.devmountain.parse".

### This class should do the following:

1. Ask the user for their birthday and add it to this list 
2. Print the current date 
3. Display the days remaining until all holidays in the list 
   (ex: if the current day is December 10, there are 15 days remaining until Christmas)
   There are 3 holidays have been initialized in this class (_New Year, July 4th and Christmas_)
4. Alert the user which holiday is coming soonest

<span style="color:red">Note: Leap year will make the calculation be complicated. Thus, let's ignore Leap Year. In another word, do not use leap year when you give birthday date </span>
Here are some leap years: 
+ 1988
+ 1992
+ 1996
+ 2000
+ 2004
+ 2008
+ 2012
+ 2016
+ 2020
+ 2024

The following is a sample output when you execute CalendarHelperDriver class. 
```java
Please enter the month and day of you birthday in the format as M/d/yyyy, e.g. 09/03/1997 for September 3, 1997
12/1/1998
You entered: 12/1/1998
Do you want to continue? Yes or No?
y
The current date is: 12/2/2021

There are 214 days remaining before Holiday (7/4/2022)

There are 30 days remaining before Holiday (1/1/2022)

There are 23 days remaining before Holiday (12/25/2021)
the closest Holiday to the current date (12/2/2021) is: 12/25/2021
There are 364 days remaining before your 24th birthday (12/1/2022)

```