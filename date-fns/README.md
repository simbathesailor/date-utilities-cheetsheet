# date-fns

## Work in progress

## UTC time

### UTC time when exact date, month, year, hours, minutes and second value is there

WHen you have access to individual date entities, getting UTC

```javascript
export function getUTCDate({
  year = new Date().getFullYear(),
  month = new Date().getMonth(),
  date = new Date().getDate(),
  hours = 0,
  minutes = 0,
  seconds = 0,
}) {
  return Date.UTC(year, month, date, hours, minutes, seconds);
}
```

This will give the the UTC date with the passed date entities. No offset and all

## Zoned time

### When you have Utc string and timezone:

```javascript
/**
 * [utcToSpecificZonedTime description]
 *
 * @param   {[type]}  utcString  UTC string
 * @param   {[type]}  timeZone   timezone e.g "America/Los_Angeles"
 *
 * @return  {[type]}  Date instance
 */
export function utcToSpecificZonedTime({ utcString, timeZone }) {
  if (!utcString) return null;
  return utcToZonedTime(utcString || new Date(), timeZone);
}
```

```javascript
/**
 * You have hours and minutes which are in UTC  with you, and you want
 * the time in UTC.
 *
 * @param   {[type]}  timeZone  timezone e.g "America/Los_Angeles"
 * @param   {[type]}  hours     number 0 - 23
 * @param   {[type]}  minutes   number 0 - 59
 *
 * @return  {[type]}            e.g 1:00 PM , 2:30 AM
 */
export function utcHoursMinutesToZonedTime({
  timeZone,
  hours,
  minutes,
  format = "hh:mm a",
}) {
  const ZonedTime = utcToZonedTime(
    getUTCDateFormatWhenIndividualDateEntityPresent({
      hours,
      minutes,
    }),
    timeZone
  );
  return formatTimeZone(ZonedTime, format);
}
```
