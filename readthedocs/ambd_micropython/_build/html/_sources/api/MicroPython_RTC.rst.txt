RTC
===


**class RTC – Real Time Clock**

**Examples**

-  **RTC get time:**

Materials:

-  Ameba x 1

..

   Steps:

RTC module help microcontroller to keep track of time and is essential
to our time module. Here we an example to demonstrate how to get local
time and update the time.

Copy and paste the following code line by line into REPL to see its
effect.


>>> rtc = RTC()
>>> rtc.datetime() # get date and time 
>>> rtc.datetime((2020, 12, 31, 4, 23, 58, 59, 0)) # set a specific date and time (year, month, day, weekday(0 for Monday), hour, minute, second, total seconds)
>>> rtc.datetime() # check the updated date and time



**Constructors**

**RTC()**

Create a RTC object.

**Methods**

**RTC.datetime(**\ *array_8*\ [optional]\ **)**

This method works in 2 ways

-  Return the local date and time if NOT passing any argument into it.
   The returned format is as follows,

(year, month, date, hour, minute, second, weekday[0-6 for Mon to Sun],
yearday[1-366])

-  Update the local date and time if passing an eight-elements array
   into it, the array format is same as above
