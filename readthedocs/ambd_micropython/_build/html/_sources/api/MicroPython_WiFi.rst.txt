WiFi
====


**class WLAN – Wireless Local Area Network**

**Examples**

-  **WiFi Scan:**

Materials:

-  Ameba x 1

..

   Steps:

   WiFi Scan function can help us quickly discover what WiFi networks
   are available in our surrounding. This example does not require any
   additional hardware, thus simply copy, and paste the following code
   into REPL to see its effect.


>>> from wireless import WLAN
>>> wifi = WLAN(mode = WLAN.STA)
>>> wifi.scan()


-  **WiFi Connect:**

Materials:

-  Ameba x 1

..

   Steps:

   Ameba can connect to WiFi access point with open security or WPA2
   security type, which is the most common security type used in
   household wireless routers. Here we are going to connect to a WiFi
   access point using code below, copy and paste the following code line
   by line into REPL to see their effects.

>>> from wireless import WLAN
>>> wifi = WLAN(mode = WLAN.STA)
>>> wifi.connect(ssid = "YourWiFiName", pswd = "YourWiFiPassword")


**Constructors**

**WLAN(**\ *mode*\ [required]\ **)**

Create a WLAN object and configure it to the given mode. This then
allows you to control WiFi and check its status.

-  **mode**: use WLAN.STA for station mode

**Methods**

**WLAN.scan()**

This method scan and list out all available WiFi network in the
surroundings.

**WLAN.connect(**\ *ssid*\ [required], *pswd*\ [optional],
*security*\ [optional]\ **)**

This method attempts to establish a connection to a WiFi access point.

-  **ssid**: The name of your WiFi network

-  **pswd:** The password of your WiFi network

-  **security:** The security type of your WiFi network

Leaving optional parameters blank will assume taking default values
which are

========= =============
Parameter Default value
========= =============
pswd      NULL
security  WPA2_AES_PSK
========= =============

Note: Connecting to an **OPEN** network is also supported, just omit
'pswd' parameter and type in "security = WLAN.OPEN" followed by ssid.

**WLAN.get_ip()**

This method returns the IP address of the current WLAN interface. Only
works after successful connection to an AP.

**WLAN.disconnect()**

This method disconnect ameba from current WiFi AP, but still keep WiFi
module on.

**WLAN.on()**

This method turns on the WiFi device.

**WLAN.off()**

This method shut down WiFi device and suspend all connections.

**WLAN.wifi_is_running()**

This method returns the WiFi status. True when WiFi is on, and False
when off.

**WLAN.is_connect_to_ap()**

This method returns the connection status. True if ameba is connected to
an AP, False if ameba is not connected to anything.
