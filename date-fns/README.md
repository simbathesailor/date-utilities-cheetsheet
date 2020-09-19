# date-fns

## Work in progress

## UTC time

### UTC time when exact date, month, year, hours, minutes and second value is there

When you have access to individual date entities, getting UTC

```javascript
export function getUTCDate({
  year = new Date().getFullYear(),
  month = new Date().getMonth(),
  date = new Date().getDate(),
  hours = 0,
  minutes = 0,
  seconds = 0,
}) {
  // native one
  return Date.UTC(year, month, date, hours, minutes, seconds);
}
```

This will give the the UTC date with the passed date entities. No offset and all

## Zoned time

### When you have Utc string and timezone:

```javascript
/**
 * [utcToZonedTimeUtil description]
 *
 * @param   {[type]}  utcString  UTC string
 * @param   {[type]}  timeZone   timezone e.g "Asia/Calcutta"
 *
 * @return  {[type]}  Date instance
 *
 */

import { utcToZonedTime } from "date-fns-tz";

export function utcToZonedTimeUtil({ utcString, timeZone }) {
  if (!utcString) return null;
  return utcToZonedTime(utcString || new Date(), timeZone);
}
```
