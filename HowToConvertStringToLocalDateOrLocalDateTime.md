### Convert String to LocalDate
The following is an example of converting a String to the java.time.LocalDate
```java
  DateTimeFormatter formatter = DateTimeFormatter.ofPattern("d/MM/yyyy");
  String date = "16/08/2016";

  //convert String to LocalDate
  LocalDate localDate = LocalDate.parse(date, formatter);
```
The key is to understand the java.time.format.DateTimeFormatter [patterns](https://docs.oracle.com/javase/8/docs/api/java/time/format/DateTimeFormatter.html)

1. If the String is in ISO_LOCAL_DATE format, we can parse the String directly, no need conversion.
```java
        String date = "2016-08-16";

        //default, ISO_LOCAL_DATE
        LocalDate localDate = LocalDate.parse(date);

        System.out.println(localDate);
        //Output:  2016-08-16 
```
2. The below program is running fine only if the default locale understands English. For example, _Locale.US_ or _Locale.English_
```java
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("d-MMM-yyyy");

        String date = "16-Aug-2016";

        LocalDate localDate = LocalDate.parse(date, formatter);

        System.out.println(localDate);  //default, print ISO_LOCAL_DATE as "2016-08-16"

        System.out.println(formatter.format(localDate)); // print formatter date as "16-Aug-2016"
```
2.1 Now, change the locale to <span style="color:red">Locale.FRANCE</span>, the <span style="color:red">DateTimeFormatter</span> will fail to parse the <span style="color:red">Aug</span> and throws <span style="color:red">DateTimeParseException</span> exception:
```java
        // not all default locale is Locale.US
        // simulate a France locale.
        Locale.setDefault(Locale.FRANCE);

        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("d-MMM-yyyy");

        String date = "16-Aug-2016";

        LocalDate localDate = LocalDate.parse(date, formatter);

        System.out.println(localDate);

        System.out.println(formatter.format(localDate));
```
The exception will be thrown as below: 
```java
Exception in thread "main" java.time.format.DateTimeParseException: Text '16-Aug-2016' could not be parsed at index 3
	at java.base/java.time.format.DateTimeFormatter.parseResolved0(DateTimeFormatter.java:2046)
	at java.base/java.time.format.DateTimeFormatter.parse(DateTimeFormatter.java:1948)
	at java.base/java.time.LocalDate.parse(LocalDate.java:428)
```
2.2 The safest way is always specified a <span style="color:red">Locale.US</span> for <span style="color:red">DateTimeFormatter</span>.
```java
        Locale.setDefault(Locale.FRANCE);

        // no problem now, DateTimeFormatter always uses Locale.US
        //Even the default locale is set as Locale.FRANCE above
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("d-MMM-yyyy", Locale.US);

        String date = "16-Aug-2016";

        LocalDate localDate = LocalDate.parse(date, formatter);

        System.out.println(localDate);  //default, print ISO_LOCAL_DATE as "2016-08-16"

        System.out.println(formatter.format(localDate)); // print formatted date as "16-Aug-2016"
```
3. Parsing String "16/08/2016"
```java
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("d/MM/yyyy");

        String date = "16/08/2016";

        LocalDate localDate = LocalDate.parse(date, formatter);

        System.out.println(localDate); //Print out as "2016-08-16"

        System.out.println(formatter.format(localDate)); //print out as "16/08/2016"

```
4. Parsing String "Tue, Aug 16 2016"
```java
        // define a locale which understand English words
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("E, MMM d yyyy", Locale.US);

        String date = "Tue, Aug 16 2016";

        LocalDate localDate = LocalDate.parse(date, formatter);

        System.out.println(localDate);  //Print out as "2016-08-16"  

        System.out.println(formatter.format(localDate)); //Print out as "Tue, Aug 16 2016"

```
### Convert String to LocalDateTime
5. Parsing String "Tuesday, Aug 16, 2016 12:10:56 PM"
```java
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("EEEE, MMM d, yyyy hh:mm:ss a", Locale.US);

        String date = "Tuesday, Aug 16, 2016 12:10:56 PM";

        LocalDateTime localDateTime = LocalDateTime.parse(date, formatter);

        System.out.println(localDateTime); //print out as "2016-08-16T12:10:56"

        System.out.println(formatter.format(localDateTime));  //Print out as "Tuesday, Aug 16, 2016 12:10:56 PM"
```
6. Parsing String "2016-08-16T10:15:30+08:00"
```java
        String date = "2016-08-16T10:15:30+08:00";

        ZonedDateTime result = ZonedDateTime.parse(date, DateTimeFormatter.ISO_DATE_TIME);

        System.out.println("ZonedDateTime : " + result); //print out as "ZonedDateTime : 2016-08-16T10:15:30+08:00"

        System.out.println("TimeZone : " + result.getZone());  //Print out as "TimeZone : +08:00"

        LocalDate localDate = result.toLocalDate();

        System.out.println("LocalDate : " + localDate);  //Print out as "LocalDate : 2016-08-16"
```
7. If the date is unable to parse, it will throw <span style="color:red">DateTimeParseException</span>
```java
public class JavaDateExample8 {
    private static final DateTimeFormatter dtf = DateTimeFormatter.ofPattern("d-MMM-yyyy", Locale.US);

    public static void main(String[] args) {
        try {
            LocalDate localDate = LocalDate.parse("16-ABC-2016", dtf);
            System.out.println(dtf.format(localDate));
        } catch (DateTimeParseException e) {
            System.err.println("Unable to parse the date!");
            //e.printStackTrace();
        }
    }
}
```
Output: 
```java
Unable to parse the date!
```
### Common Date and Time Patterns
The followings are some common date and time patterns:
* y – Year (1996; 96)
* M – Month in year (July; Jul; 07)
* d – Day in month (1-31)
* E – Day name in week (Friday, Sunday)
* a – AM/PM marker (AM, PM)
* H – Hour in day (0-23)
* h – Hour in AM/PM (1-12)
* m – Minute in hour (0-60)
* s – Second in minute (0-60)
### For a full list of symbols that we can use to specify a pattern for parsing click [here](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/time/format/DateTimeFormatter.html#patterns).
 





