# Overview
> https://moment.github.io/luxon/#/ <- It's the best library you can use it

## String to Date by pure JS
> YYYY-MM-DDTHH:mm:ss.sssZ
- T is a **literal character**, which indicates the beginning of the time part of the string. The T is required when specifying the time part.
- Z is the timezone offset, which can either be the literal character **Z** (indicating UTC), or **+** or **-** followed by **HH:mm**, the offset in hours and minutes from UTC.
### Examples
```
const eg1 = new Date('2013-09-29T18:46:19Z'); // UTC
const eg2 = new Date('2013-09-29T18:46:19+01:00'); // UTC+1
```


# Reference
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date#date_time_string_format
