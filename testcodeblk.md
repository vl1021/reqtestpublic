
# Overview

## Android

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |


```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

```java
import java.util.Scanner;

public class HelloWorld {

    public static void main(String[] args) {

        // Creates a reader instance which takes
        // input from standard input - keyboard
        Scanner reader = new Scanner(System.in);
        System.out.print("Enter a number: ");

        // nextInt() reads the next integer from the keyboard
        int number = reader.nextInt();

        // println() prints the following line to the output screen
        System.out.println("You entered: " + number);
    }
}
```

```json
{
\"is_enabled\":false,
\"alert_profile_type\":1,
\"mobile_platform\":\"Apple\",
\"days_enabled\":96,
\"is_schedule_enabled\":true,
\"start_time_seconds\":84600,
\"end_time_seconds\":113400,
\"sdk_version\":\"2.1.0\",
\"profile_name\":\"Night Time\",
\"settings\":[
{\"sound_intensity\":1,\"is_enabled\":true,\"level\":56,\"alert_identifier\":\"AA-01\",\"snooze_length_seconds\":1800,\"sound\":\"polarisUrgentLowMedium\",\"sound_preference\":0,\"snooze_enabled\":true,\"lifetime_alert_acount\":0},
{\"sound_intensity\":1,\"rate\":0,\"is_enabled\":true,\"level\":56,\"alert_identifier\":\"AA-02\",\"snooze_length_seconds\":1800,\"sound\":\"polarisUrgentLowSoonMedium\",\"sound_preference\":0,\"snooze_enabled\":true,\"lifetime_alert_acount\":0},
{\"sound_intensity\":1,\"is_enabled\":true,\"level\":70,\"alert_identifier\":\"AA-03\",\"snooze_length_seconds\":3600,\"sound\":\"polarisLowMedium\",\"sound_preference\":0,\"snooze_enabled\":true,\"lifetime_alert_acount\":0},
{\"delay_enabled\":false,\"sound_intensity\":1,\"is_enabled\":true,\"delay_length_seconds\":3600,\"level\":252,\"alert_identifier\":\"AA-04\",\"snooze_length_seconds\":3600,\"sound\":\"polarisHighMedium\",\"sound_preference\":0,\"snooze_enabled\":false,\"lifetime_alert_acount\":0},
{\"sound_intensity\":1,\"rate\":2,\"is_enabled\":false,\"level\":148,\"alert_identifier\":\"AA-05\",\"sound\":\"polarisRiseRateMedium\",\"sound_preference\":0,\"lifetime_alert_acount\":0},
{\"sound_intensity\":1,\"rate\":2,\"is_enabled\":false,\"level\":247,\"alert_identifier\":\"AA-06\",\"sound\":\"polarisFallRateMedium\",\"sound_preference\":0,\"lifetime_alert_acount\":0},
{\"delay_enabled\":true,\"sound_intensity\":1,\"delay_length_seconds\":1200,\"is_enabled\":true,\"alert_identifier\":\"AA-07\",\"sound\":\"polarisSignalLossMedium\",\"sound_preference\":0,\"lifetime_alert_acount\":0},
{\"delay_enabled\":true,\"sound_intensity\":1,\"delay_length_seconds\":1200,\"is_enabled\":true,\"alert_identifier\":\"AA-08\",\"sound\":\"polarisBriefSensorIssueMedium\",\"sound_preference\":0,\"lifetime_alert_acount\":0},
{\"sound\":\"polarisTechnicalAlertMedium\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-11\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-12\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-15\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-17\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-19\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-27\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-28\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-29\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":2,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-30\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-31-A\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-31-B\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":2,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-34\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-35\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-36\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-39\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-40\",\"is_enabled\":true},
{\"sound\":\"polarisTechnicalAlertMedium\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-41\",\"is_enabled\":true},
{\"sound\":\"silence1sec\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-42\",\"is_enabled\":true},
{\"sound\":\"polarisTechnicalAlertMedium\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-43\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":2,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-44\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-51\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AA-52\",\"is_enabled\":true},
{\"sound\":\"polarisSystemAlert\",\"sound_intensity\":1,\"sound_preference\":0,\"lifetime_alert_acount\":0,\"alert_identifier\":\"AD-01\",\"is_enabled\":true}
]
}
```
