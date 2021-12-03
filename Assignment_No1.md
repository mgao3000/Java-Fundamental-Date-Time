### You need to implement two classes named as WorldClock and WorldClockDriver
### The class skeleton is under package "com.devmountain.currentdate". 
### For class WorldClock, please implement the following methods: 
```java
public LocalDate getNowForDate();
public LocalDateTime getNowForDateAndTime();
public DayOfWeek getDayOfWeekForNow();
public int getDayOfMonthForNow();
public int getDayOfYearForNow();
public ZonedDateTime getNowDateTimeForNewYork();
public ZonedDateTime getNowDateTimeForLA();
public ZonedDateTime getNowDateTimeForLondon();
public ZonedDateTime getNowDateTimeForMoscow();
public ZonedDateTime getNowDateTimeForTokyo(); 
```
### In WorldClockDriver, you need instantiate WorldClock and then print out the results of each API provided by the class WorldClock. 
<span style="color:red">Note: When print out the results of WorldClock APIs, please use DateTimeFormatter to format the Date value to make them more user-friendly</span>

The two empty classes WorldClock and WorldClockDriver are already created under the package com.devmountain.currentdate. What you need to do is implement them using java Date, Time and DateTimeFormatter. 


### Sample output: 
```java
nowLocalDate=2021/12/01
nowLocalDateTime=2021/12/01 18:52:35

owLocalDate.getDayOfWeek()=WEDNESDAY
owLocalDate.getDayOfMonth()=1
owLocalDate.getDayOfYear()=335

nowZonedDateTimeForNewYork=2021/12/01 18:52:35
nowZonedDateTimeForNewYork.getZone()=America/New_York

nowZonedDateTimeForLA=2021/12/01 15:52:35
nowZonedDateTimeForLA.getZone()=America/Los_Angeles

nowZonedDateTimeForLondon=2021/12/01 23:52:35
nowZonedDateTimeForLondon.getZone()=Europe/London

nowZonedDateTimeForMoscow=2021/12/02 02:52:35
nowZonedDateTimeForMoscow.getZone()=Europe/Moscow

nowZonedDateTimeForTokyo=2021/12/02 08:52:35
nowZonedDateTimeForTokyo.getZone()=Asia/Tokyo

```