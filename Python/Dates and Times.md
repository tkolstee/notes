### Overview
`from datetime import date, time, datetime, timedelta`

#### Date and Time Types
- date: date on Gregorian calendar extended infinitely
- time: time within an ideal date (no leap seconds)
- datetime: composite of date and time

#### Timezone Awareness
Date and time types can operate in naive or aware mode.
- tzinfo: abstract timezone class
- timezone: carries timezone info for timezone-aware objects

## Date  Type
Represents dates on the Gregorian calendar extended infinitely.

### Constructing
```python
from datetime import date

date(year, month, day)         # positional or named, named is clearer
date.today()                   # today's date
date.fromtimestamp(epochtime)  # Seconds since 01-01-1970
date.fromordinal(ord_date)     # Days since 0001-01-01
```

### Class Attributes and Methods
| Attribute       | Description        |
| --------------- | ------------------ |
| date.min        | =date(1, 1, 1)     |
| date.max        | =date(9999,12,31)  |
| date.resolution | =timedelta(days=1) |

### Instance Attributes and Methods
| Attribute       | Description           |
| --------------- | --------------------- |
| d.year          | Year portion of date  |
| d.month         | Month portion of date |
| d.day           | Day portion of date   |
| d.weekday()     | 0=Mon - 6=Sun         |
| d.isoweekday()  | 1=Mon - 7=Sun         |
| d.isoformat     | 'YYYY-MM-DD'          |
| d.strftime(fmt) | Format from string    |

### Using str.format()
```python
"The date is {:%A %d %B %Y}".format(d)  # The date is Sunday 07 December 1941
```

## Time Type

### Constructing
```python
from datetime import time

time(hour, minute, second, microsecond)
```

### Class Attributes and Methods
| Attribute       | Description               |
| --------------- | ------------------------- |
| time.min        | time(0, 0)                |
| time.max        | time(23, 59, 59, 999999)  |
| time.resolution | timedelta(microseconds=1) |


### Instance Attributes and Methods
| Attribute       | Description                 |
| --------------- | --------------------------- |
| t.hour          | Hour portion of time        |
| t.minute        | Minute portion of time      |
| t.second        | Second portion of time      |
| t.microsecond   | $\mu$second portion of time |
| t.isoformat()   | '10:31:47.675623'           |
| t.strftime(fmt) | Format from string                            |

### Using str.format()
```python
"The time is {t.hour}:{t.minute}:{t.second}".format(t=t)
```

## Datetime Type

### Constructing

When importing into the main namespace, use an alias for `datetime` to avoid type/module naming conflict.
```python
from datetime import datetime as dt

# Positional or named arguments
dt(year, month, day, hour, minute, second, microsecond)

# Now, in local timezone
dt.today()
dt.now()

# Now in UTC
dt.utcnow()

# Date (no time) in days since 01-01-01
dt.fromordinal(734_000)

# Epoch timestam (seconds since 01-01-1970), local timezone
dt.fromtimestamp(1658279730)

# Epoch timestamp in UTC
dt.utcfromtimestamp(1658279730)

# Date from today (at midnight)
dt.date.today()

# Combine date and time into datetime type
dt.combine(date, time)

# Read time from format string
dt.strptime("Monday 6 January 2014, 12:13:31", "%A %d %B %Y, %H:%M:%S")`
```

### Instance Attributes and Methods
| Attribute     | Description                  |
| ------------- | ---------------------------- |
| dt.date()      | date portion as date type    |
| dt.time()      | time portion as time type    |
| dt.year        | year portion                 |
| dt.month       | month portion                |
| dt.day         | day portion                  |
| dt.hour        | hour portion                 |
| dt.minute      | minute portion               |
| dt.second      | second portion               |
| dt.microsecond | $\mu$second portion          |
| dt.isoformat() | '2022-08-19T21:19:59.394223' |

### Class Attributes and Methods
| Attribute     | Description                                |
| ------------- | ------------------------------------------ |
| dt.min        | datetime(1, 1, 1, 0, 0)                    |
| dt.max        | datetime(9999, 12, 31, 23, 59, 59, 999999) |
| dt.resolution | timedelta(microseconds=1)                  |

## Timedelta Type
Represents an interval between two times/dates
Allows for adding and subtracting to/from dates/times, and can be multiplied.

### Constructing
```python
from datetime import timedelta

datetime.timedelta(weeks=1, milliseconds=1, microseconds=1000)
```
Possible arguments - all default to 0 - are:
days, seconds, microseconds, milliseconds, minutes, hours, weeks
Keyword arguments strongly recommended for clarity.

### Instance Attributes and Methods
| Attribute          | Description                                          |
| ------------------ | ---------------------------------------------------- |
| td.days            | days portion                                         |
| td.milliseconds    | msec portion                                         |
| td.microseconds    | $\mu$sec portion                                     |
| td.total_seconds() | total seconds (incl. fractional part) for all values |
|
| Attribute     | Description                                                    |
| ------------- | -------------------------------------------------------------- |
| td.max        | timedelta(days=999999999, seconds=86399, microseconds=999999)) |
| td.min        | timedelta(days=-999999999)                                     |
| td.resolution | timedelta(microseconds=1)                                      |
|               |                                                                |

## Time Zones
Use `tzinfo` for "aware" objects.
Other third-party modules like `pytz` or `dateutil` have more accurate and up to date timezone info.

`tzinfo` is abstract, but `timezone` is concrete and is a fixed offset from UTC.

```python
edt = datetime.timezone(datetime.timedelta(hours=-4), "EDT")
pdt = datetime.timezone(datetime.timedelta(hours=-7), "PDT")

# Flight leaves east coast at 14:00
departure = datetime.datetime(2020, 7, 19, 14, 0, tzinfo=edt)

# Arrives west coast at 17:15
arrival = datetime.datetime(2020, 7, 19, 17, 15, tzinfo=pdt)

# find duration of flight
print (arrival - departure)   # 6:15:00
```

For proper DST support, etc. you can either subclass tzinfo (Instructions in [these docs](http://docs.python.org/3/library/datetime.html#tzinfo-objects)) or use `pytz` or `dateutil` module.
