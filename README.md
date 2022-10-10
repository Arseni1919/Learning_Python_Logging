# Learning Python Logging

By default, there are 5 standard levels indicating the severity of events. 
Each has a corresponding method that can be used to log events at that level of severity. 
The defined levels, in order of increasing severity, are the following:

- DEBUG
- INFO
- WARNING
- ERROR
- CRITICAL

## Imports

```python
import logging

logging.basicConfig(format='%(asctime)s - %(message)s', datefmt='%d-%b-%y %H:%M:%S', level=logging.INFO)

# or

logging.basicConfig(format='%(asctime)s - %(message)s', datefmt='%d-%b-%y %H:%M:%S', level=logging.DEBUG)
```

## MyUsage

```python

```

## Usage

```python
logging.debug('This is a debug message')
logging.info('This is an info message')
logging.warning('This is a warning message')
logging.error('This is an error message')
logging.critical('This is a critical message')
```
 
The output will be: 

```
WARNING:root:This is a warning message
ERROR:root:This is an error message
CRITICAL:root:This is a critical message
```

## Basic Configurations

Some commonly used parameters for basicConfig() are the following:

* `level`: The root logger will be set to the specified severity level.
* `filename`: This specifies the file.
* `filemode`: If filename is given, the file is opened in this mode. The default is `a`, which means append. Can be also `w`, for example.
* `format`: This is the format of the log message.

Link to all attributes of `basicConfig()`: [https://docs.python.org/3/library/logging.html#logging.basicConfig](https://docs.python.org/3/library/logging.html#logging.basicConfig)

List of attributes to log: [https://docs.python.org/3/library/logging.html#logrecord-attributes](https://docs.python.org/3/library/logging.html#logrecord-attributes)

**Basically, this function can only be called once.**

```python
import logging
logging.basicConfig(level=logging.DEBUG)
logging.debug('This will get logged')
```

```python
logging.basicConfig(level=logging.DEBUG, filename='app.log', filemode='w', format='%(name)s - %(levelname)s - %(message)s')
```

```python
import logging
logging.basicConfig(format='%(asctime)s - %(message)s', level=logging.INFO)
logging.info('Admin logged in')
```

`%(asctime)s` adds the time of creation of the LogRecord. The format can be changed using the `datefmt` attribute, which uses the same formatting language as the formatting functions in the `datetime` module, such as `time.strftime()`:

```python
import logging
logging.basicConfig(format='%(asctime)s - %(message)s', datefmt='%d-%b-%y %H:%M:%S')
logging.warning('Admin logged out')
```

For more settings of datetime modes: [https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior)

### `exc_info` parameter

```python
import logging
a = 5
b = 0
try:
  c = a / b
except Exception as e:
  logging.error("Exception occurred", exc_info=True)
```

But better:

```python
import logging

a = 5
b = 0
try:
  c = a / b
except Exception as e:
  logging.exception("Exception occurred")
```


## Credits

- [blog | Logging in Python](https://realpython.com/python-logging/)
- [`.basicConfig()` attributes](https://docs.python.org/3/library/logging.html#logging.basicConfig)
- [`log` attributes](https://docs.python.org/3/library/logging.html#logrecord-attributes)
- [`strptime` attributes](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior)

