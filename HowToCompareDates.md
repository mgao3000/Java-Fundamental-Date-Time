### Compare two date and time using _java.time.*_ API
For the new Java 8 _java.time.*_ classes, all contains similar
<span style="color:red">compareTo</span>, 
<span style="color:red">isBefore()</span>,
<span style="color:red">isAfter()</span> and
<span style="color:red">isEqual()</span> 
to compare two dates, and it works the same way.
* <span style="color:red">java.time.LocalDate</span> – date without time, no time-zone.
* <span style="color:red">java.time.LocalTime</span> – time without date, no time-zone. 
* <span style="color:red">java.time.LocalDateTime</span>java.time.LocalDateTime – date and time, no time-zone. 
* <span style="color:red">java.time.ZonedDateTime</span> – date and time, with time-zone. 
1. Compare two LocalDate
```java
        DateTimeFormatter dtf = DateTimeFormatter.ofPattern("uuuu-MM-dd");

        LocalDate date1 = LocalDate.parse("2020-02-01", dtf);
        LocalDate date2 = LocalDate.parse("2020-01-31", dtf);

        System.out.println("date1 : " + date1);  //output as "date1 : 2020-02-01"
        System.out.println("date2 : " + date2);  //output as "date2 : 2020-01-31"

        if (date1.isEqual(date2)) {
            System.out.println("Date1 is equal Date2"); 
        }

        if (date1.isBefore(date2)) {
            System.out.println("Date1 is before Date2"); 
        }

        if (date1.isAfter(date2)) {
            System.out.println("Date1 is after Date2"); 
        }

        // test compareTo
        if (date1.compareTo(date2) > 0) {
            System.out.println("Date1 is after Date2");
        } else if (date1.compareTo(date2) < 0) {
            System.out.println("Date1 is before Date2");
        } else if (date1.compareTo(date2) == 0) {
            System.out.println("Date1 is equal to Date2");
        } else {
            System.out.println("How to get here?");
        }
```
2. Compare two LocalDateTime
```java
      DateTimeFormatter dtf = DateTimeFormatter.ofPattern("uuuu-MM-dd HH:mm:ss");

      LocalDateTime date1 = LocalDateTime.parse("2020-01-31 11:44:43", dtf);
      LocalDateTime date2 = LocalDateTime.parse("2020-01-31 11:44:44", dtf);

      System.out.println("date1 : " + date1);  //Print out as "date1 : 2020-01-31T11:44:43"
      System.out.println("date2 : " + date2);  //Print out as "date2 : 2020-01-31T11:44:44"

      if (date1.isEqual(date2)) {
          System.out.println("Date1 is equal Date2");
      }

      if (date1.isBefore(date2)) {
          System.out.println("Date1 is before Date2");
      }

      if (date1.isAfter(date2)) {
          System.out.println("Date1 is after Date2");
      }
```
3. Check if a date is within a certain range
```java
  public boolean isWithinRange(LocalDate startDate,
        LocalDate endDate, 
        LocalDate testDate) {

      // exclusive startDate and endDate
      //return testDate.isBefore(endDate) && testDate.isAfter(startDate);

      // inclusive startDate and endDate
      return (testDate.isEqual(startDate) || testDate.isEqual(endDate))
              || (testDate.isBefore(endDate) && testDate.isAfter(startDate));
  }
```
4. Check if the date is older than 6 months
```java
      DateTimeFormatter dtf = DateTimeFormatter.ofPattern("uuuu-MM-dd");

      LocalDate now = LocalDate.parse("2021-12-05", dtf);
      LocalDate futureDate = LocalDate.parse("2022-05-05", dtf);

      System.out.println("now: " + now); //Print out as "now: 2021-12-05"
      System.out.println("futureDate: " + futureDate); //Print out as "futureDate 2022-05-05"

      // add 6 months
      LocalDate nowPlus6Months = now.plusMonths(6);
      System.out.println("nowPlus6Months: " + nowPlus6Months);

      System.out.println("If date1 older than 6 months?");

      // if want to exclude the 2020-07-01, remove the isEqual
      if (date1.isAfter(nowPlus6Months) || date1.isEqual(nowPlus6Months)) {
          System.out.println("Yes");
      } else {
          System.out.println("No");
      }
```
### Compare two date and time using legacy java.util.Date, we can use 
* <span style="color:red">compareTo</span>
* <span style="color:red">before()</span> 
* <span style="color:red">after()</span>after() and 
* <span style="color:red">equals()</span> 
### to compare two dates.
1. Below example uses Date.compareTo to compare two java.util.Date in Java.
* Return value of 0 if the argument date is equal to the Date. 
* Return value is greater than 0 or positive if the Date is after the argument date. 
* Return value is less than 0 or negative if the Date is before the argument date.
```java
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
        Date date1 = sdf.parse("2020-01-30");
        Date date2 = sdf.parse("2020-01-31");

        System.out.println("date1 : " + sdf.format(date1));
        System.out.println("date2 : " + sdf.format(date2));

        int result = date1.compareTo(date2);
        System.out.println("result: " + result);

        if (result == 0) {
            System.out.println("Date1 is equal to Date2");
        } else if (result > 0) {
            System.out.println("Date1 is after Date2");
        } else if (result < 0) {
            System.out.println("Date1 is before Date2");
        } else {
            System.out.println("How to get here?");
        }
```
2. Date.before(), Date.after() and Date.equals()
```java
      SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
      //Date date1 = sdf.parse("2009-12-31");
      Date date1 = sdf.parse("2020-02-01");
      Date date2 = sdf.parse("2020-01-31");

      System.out.println("date1 : " + sdf.format(date1));
      System.out.println("date2 : " + sdf.format(date2));

      if (date1.equals(date2)) {
          System.out.println("Date1 is equal Date2");
      }

      if (date1.after(date2)) {
          System.out.println("Date1 is after Date2");
      }

      if (date1.before(date2)) {
          System.out.println("Date1 is before Date2");
      }
```
3. Check if a date is within a certain range
#### Version 1: 
```java
    public boolean isWithinRange(Date startDate,
        Date endDate,
        Date testDate){
        boolean result = false;
        if ((testDate.equals(startDate) || testDate.equals(endDate)) ||
                (testDate.after(startDate) && testDate.before(endDate))) {
            result = true;
        }
        return result;
    }
```
#### Version 2:
```java
    public boolean isWithinRange(Date startDate,
        Date endDate,
        Date testDate){
        boolean result = false;

        // compare date and time, inclusive of startDate and endDate
        // getTime() returns number of milliseconds since January 1, 1970, 00:00:00 GMT
        if ((testDate.getTime() >= startDate.getTime()) &&
            (testDate.getTime() <= endDate.getTime())) {
            result = true;
        }
        return result;
    }
```
### Compare two legacy java.util.Calendar
#### The java.util.Calendar works the same way as java.util.Date. And The Calendar contains the similar 
* <span style="color:red">compareTo</span>
* <span style="color:red">before() </span>
* <span style="color:red">after()</span> and 
* <span style="color:red">equals()</span> 
#### to compare two calender.
```java
      SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
      Date date1 = sdf.parse("2020-02-01");
      Date date2 = sdf.parse("2020-01-31");

      Calendar cal1 = Calendar.getInstance();
      Calendar cal2 = Calendar.getInstance();
      cal1.setTime(date1);
      cal2.setTime(date2);

      System.out.println("date1 : " + sdf.format(date1));
      System.out.println("date2 : " + sdf.format(date2));

      if (cal1.after(cal2)) {
          System.out.println("Date1 is after Date2");
      }

      if (cal1.before(cal2)) {
          System.out.println("Date1 is before Date2");
      }

      if (cal1.equals(cal2)) {
          System.out.println("Date1 is equal Date2");
      }
```




