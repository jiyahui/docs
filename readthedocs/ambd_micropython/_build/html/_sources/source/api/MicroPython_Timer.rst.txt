Timer
======



**class Timer – General Timers**

**Examples**

-  **Periodical timer:**

Materials:

-  Ameba x 1

..

   Steps:

There are 3 sets of general timers available to user, each at 32KHz,
they are timer 1/2/3.

Here we use timer 1 as example to demonstrate how a periodical timer
works.

Copy and paste the first 3 lines of code into REPL to see its effect.


>>> from machine import Timer
>>> t = Timer(1)  # Use Timer 1/2/3 only
>>> t.start(2000000, t.PERIODICAL)  # Set GTimer fired periodically at duration of 2 seconds, printing text on the terminal
# To stop the periodical timer, type 
>>> t.stop()


A text of “--timer triggered. to stop: type t.stop()--” will be printed
on the terminal every 2 seconds

To stop the timer, simply type t.stop()

**Constructors**

**Timer(**\ *unit*\ [optional]\ **)**

Create a timer object with given unit ID.

-  **unit**: can be 1 / 2 / 3 for timer 1 / 2 / 3

**Methods**

**Timer.start(**\ *microseconds*\ [required], *type*\ [required]\ **)**

This method will start a given type of timer, either one-shot or
periodical, at duration of given microseconds.

-  **microseconds**: number of microseconds interval, must be an integer

-  **type**: either Timer. PERIODICAL or Timer.ONESHOT

**Timer.deinit()**

This method will de-initialize the Timer object created and stop the
timer.

**Timer.stop()**

This method will stop the timer and its timer interrupt handler.

**Timer.us ()**

This method will return the current timer tick in microsecond.

**Timer.tick ()**

This method will return the current timer tick in Gtimer clock(0~32768).

**Timer.reload (**\ *duration_us*\ [required]\ **)**

This method will reload the timer with given duration in microsecond.

-  **duration_us**: duration in microsecond
