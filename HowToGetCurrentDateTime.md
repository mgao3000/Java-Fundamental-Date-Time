## This tutorial shows you how to get the current date time from the new Java 8 java.time.* like _**Localdate**_, _LocalTime_, _LocalDateTime_, _ZonedDateTime_

## and also the legacy date time APIs like _java.util.Date_ and _java.util.Calendar_

### 1. Get current date time in Java

### The below are some code snippets to display the current date-time in Java.

#### For java.time.LocalDate, uses LocalDate.now()
```Java
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("uuuu/MM/dd");
LocalDate localDate = LocalDate.now();
System.out.println(dtf.format(localDate));   
//The printout will be something like 2021/12/02 which depends on the current date
```
#### For java.time.localTime, uses LocalTime.now()
```Java
  DateTimeFormatter dtf = DateTimeFormatter.ofPattern("HH:mm:ss");
  LocalTime localTime = LocalTime.now();
  System.out.println(dtf.format(localTime));            // 16:37:15
```
#### For java.time.ZonedDateTime, uses ZonedDateTime.now()
```Java
  // get current date-time, with system default time zone
  DateTimeFormatter dtf = DateTimeFormatter.ofPattern("uuuu/MM/dd HH:mm:ss");
  ZonedDateTime now = ZonedDateTime.now();
  System.out.println(dtf.format(now));                  // 2021/03/22 16:37:15
  System.out.println(now.getOffset());                  // +08:00

  // get current date-time, with a specified time zone
  ZonedDateTime japanDateTime = now.withZoneSameInstant(ZoneId.of("Asia/Tokyo"));
  System.out.println(dtf.format(japanDateTime));        // 2021/03/22 17:37:15
  System.out.println(japanDateTime.getOffset());        // +09:00
```
<span style="color:red">Note: In the above java.time.* API, java.time.format.DateTimeFormatter is used to format the current date</span>

#### Check DayOfWeek (e.g. Friday), DayOfMonth (e.g. 10th day of the month) and DayOfYear (e.g. 300th day of the year)
```java
        System.out.println("owLocalDate.DayOfWeek()=" + nowLocalDate.getDayOfWeek());  //e.g. Friday
        System.out.println("owLocalDate.DayOfMonth()=" + nowLocalDate.getDayOfMonth()); //e.g. 10
        System.out.println("owLocalDate.DayOfYear()=" + nowLocalDate.getDayOfYear());   //e.g. 300

```
#### For java.util.Date, uses new Date()
```java
  DateFormat dateFormat = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");
  Date date = new Date(); 
  //Another way to get the current date time is: Date date = new Date(System.currentTimeMillis()); 
  System.out.println(dateFormat.format(date));           // 2021/03/22 16:37:15
```
#### For java.util.Calendar, uses Calendar.getInstance()
```java
  DateFormat dateFormat = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");
  Calendar cal = Calendar.getInstance();
  System.out.println(dateFormat.format(cal.getTime()));  // 2021/03/22 16:37:15
```
<span style="color:red">Note: In the above legacy java.util.Date and java.util.Calendar, java.text.SimpleDateFormat is used to format the current date</span>



