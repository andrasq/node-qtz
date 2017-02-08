qdate
=====

Small, light and quick handy date conversion functions.

Unlike timezone packages that drag along their own timezone database, `qdate`
leverages the host system's native timezone support, making it much smaller.

This is a work in progress.


Summary
-------

    var qdate = require('qdate')
    qdate.adjust(new Date(), -30, 'minute');


Api
---

### abbrev( tzName ), getTimezoneAbbrev

return the three-character timezone abbreviation of the named timezone

### offset( tzName ), getTimezoneOffset

return the offset as minutes west of GMT of the named timezone.  This is what
`new Date().getTimezoneOffset()` does for the default timezone.

### list( ), getTimezoneList

return the list of known timezone names as an array of strings

### adjust( timestamp, delta, unit )

return the Date corresponding to the timestamp adjusted by +/- delta units.  Unit
may be one of 'year', 'month', 'week', 'day', 'hour', 'minute', 'second' or
'millisecond'.

### strtotime( timespec [,tzName] )

convert the time specification to a Date.  The time spec can be anything `date
--date` can parse, like "+2 hours" or "3 weeks ago" or "9pm last Friday".

##### ? format( timestamp [,tzName] )

format the timestamp in the named timezone locale.
Formatting by `phpdate`


##### ? convert( timestamp, tzFromName, tzToName, [format] )

convert the timestamp between timezones, and return a reformatted timestamp.
Formatting by `phpdate`

##### ? startOf( timestamp, unit ), current

return the Date corresponding to the timestamp at the start of the current unit.
Unit may be any of the time divisions listed under `adjust()`, eg 'year', 'month',
'week', 'day', etc.


Todo
----

- way to fetch the default timezone abbreviation (to use in formatting) `date +%Z`


Change Log
----------

- 0.0.3 - depend on phpdate-js
- 0.0.2 - rename to `qdate`, test (tbd) with qnit
- 0.0.1 - adjust(), strtotime(), tz abbrev, tz offset, list all known tz names

Related
-------

- `ctime(3)`
- `tzname(3)`
- `strftime(3)`
- [`phpdate-js`](https://github.com/andrasq/phpdate-js) - fast datetime formatting
- `/bin/date +%Z @0`
- `/etc/timezone`
- `/usr/share/zoneinfo`
- `tzselect(1)`
