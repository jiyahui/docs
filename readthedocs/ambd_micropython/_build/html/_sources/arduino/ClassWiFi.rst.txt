WiFiClass Class
================



Description
------------

Defines a class of WiFi and network implementation for Ameba

**Syntax**

class WiFiClass

**Members**

**Public Constructors**

+-----------------------+---------------------------------------------+
| WiFiClass:: WiFiClass | Constructs a WiFiClass object and           |
|                       | initializes the WiFi libraries and network  |
|                       | settings.                                   |
+-----------------------+---------------------------------------------+

**Public Methods**

+------------------------------+--------------------------------------+
| WiFiClass:: firmwareVersion  | Get firmware version                 |
|                              |                                      |
| WiFiClass:: begin            | Start Wifi connection for OPEN       |
|                              | networks                             |
+==============================+======================================+
| WiFiClass:: config           | Configure network IP settings        |
+------------------------------+--------------------------------------+
| WiFiClass:: setDNS           | Set the DNS server IP address to use |
+------------------------------+--------------------------------------+
| WiFiClass:: disconnect       | Disconnect from the network          |
+------------------------------+--------------------------------------+
| WiFiClass:: macAddress       | Get the interface MAC address        |
+------------------------------+--------------------------------------+
| WiFiClass:: localIP          | Get the interface IP address         |
+------------------------------+--------------------------------------+
| WiFiClass:: subnetMask       | Get the interface subnet mask        |
|                              | address                              |
+------------------------------+--------------------------------------+
| WiFiClass:: gatewayIP        | Get the gateway IP address           |
+------------------------------+--------------------------------------+
| WiFiClass:: SSID             | Return the current SSID associated   |
|                              | with the network                     |
+------------------------------+--------------------------------------+
| WiFiClass:: BSSID            | Return the current BSSID associated  |
|                              | with the network.                    |
+------------------------------+--------------------------------------+
| WiFiClass:: RSSI             | Return the current RSSI (Received    |
|                              | Signal Strength in dBm) associated   |
|                              | with the network                     |
+------------------------------+--------------------------------------+
| WiFiClass:: encryptionType   | Return the Encryption Type           |
|                              | associated with the network          |
| WiFiClass:: scanNetworks     |                                      |
|                              | Start scan WiFi networks available   |
| WiFiClass:: SSID             |                                      |
|                              | Return the SSID discovered during    |
| WiFiClass:: encryptionType   | the network scan                     |
|                              |                                      |
| WiFiClass:: encryptionTypeEx | Return the encryption type of the    |
|                              | networks discovered during the       |
| WiFiClass:: RSSI             | scanNetworks                         |
|                              |                                      |
| WiFiClass:: status           | Return the security type and         |
|                              | encryption type of the networks      |
| WiFiClass:: hostByName       | discovered during the scanNetworks   |
|                              |                                      |
| WiFiClass:: apbegin          | Return the RSSI of the networks      |
|                              | discovered during the scanNetworks   |
| WiFiClass:: disablePowerSave |                                      |
|                              | Return Connection status             |
|                              |                                      |
|                              | Resolve the given hostname to an IP  |
|                              | address                              |
|                              |                                      |
|                              | Start AP mode                        |
|                              |                                      |
|                              | Disable power-saving mode            |
+------------------------------+--------------------------------------+

**
**

**WiFiClass:: WiFiClass**

**Description**

Constructs a WiFiClass object and initializes the WiFi libraries and
network settings.

**Syntax**

WiFiClass::WiFiClass()

**Parameters**

The function requires no input parameter.

**Returns**

The function returns nothing.

**Example Code**

NA

**Notes and Warnings**

An instance of WiFiClass is created as WiFi inside WiFi.h and is extern
for direct use.

**
**

**WiFiClass:: firmwareVersion**

**Description**

Get firmware version

**Syntax**

char\* WiFiClass::firmwareVersion()

**Parameters**

The function requires no input parameter.

**Returns**

WiFi firmware version

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFI network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details.

1.   #include <WiFi.h>  

2.     

3.   // char ssid[] = "yourNetwork";     //  your network SSID (name)  

4.   // char pass[] = "secretPassword";  // your network password  

5.   **char** ssid[] = "SINGTEL-D45F";                     // your network SSID (name)  

6.   **char** pass[] = "mooxuteeth;                         // your network key  

7.   **int** status = WL_IDLE_STATUS;     // the Wifi radio's status  

8.     

9.   **void** setup() {  

10.    //Initialize serial and wait for port to open:  

11.    Serial.begin(9600);  

12.    **while** (!Serial) {  

13.      ; // wait for serial port to connect. Needed for native USB port only  

14.    }  

15.    

16.    // check for the presence of the shield:  

17.    **if** (WiFi.status() == WL_NO_SHIELD) {  

18.      Serial.println("WiFi shield not present");  

19.      // don't continue:  

20.      **while** (**true**);  

21.    }  

22.    

23.    String fv = WiFi.firmwareVersion();  

24.    **if** (fv != "1.1.0") {  

25.      Serial.println("Please upgrade the firmware");  

26.    }  

27.    

28.    // attempt to connect to Wifi network:  

29.    **while** (status != WL_CONNECTED) {  

30.      Serial.print("Attempting to connect to WPA SSID: ");  

31.      Serial.println(ssid);  

32.      // Connect to WPA/WPA2 network:  

33.      status = WiFi.begin(ssid, pass);  

34.    

35.      // wait 10 seconds for connection:  

36.      delay(10000);  

37.    }  

38.    

39.    // you're connected now, so print out the data:  

40.    Serial.print("You're connected to the network");  

41.    printCurrentNet();  

42.    printWifiData();  

43.    

44.  }  

45.    

46.  **void** loop() {  

47.    // check the network connection once every 10 seconds:  

48.    delay(10000);  

49.    printCurrentNet();  

50.  }  

51.    

52.  **void** printWifiData() {  

53.    // print your WiFi shield's IP address:  

54.    IPAddress ip = WiFi.localIP();  

55.    Serial.print("IP Address: ");  

56.    Serial.println(ip);  

57.    Serial.println(ip);  

58.    

59.    // print your MAC address:  

60.    byte mac[6];  

61.    WiFi.macAddress(mac);  

62.    Serial.print("MAC address: ");  

63.    Serial.print(mac[0], HEX);  

64.    Serial.print(":");  

65.    Serial.print(mac[1], HEX);  

66.    Serial.print(":");  

67.    Serial.print(mac[2], HEX);  

68.    Serial.print(":");  

69.    Serial.print(mac[3], HEX);  

70.    Serial.print(":");  

71.    Serial.print(mac[4], HEX);  

72.    Serial.print(":");  

73.    Serial.println(mac[5], HEX);  

74.  }  

75.    

76.  **void** printCurrentNet() {  

77.    // print the SSID of the network you're attached to:  

78.    Serial.print("SSID: ");  

79.    Serial.println(WiFi.SSID());  

80.    

81.    // print the MAC address of the router you're attached to:  

82.    byte bssid[6];  

83.    WiFi.BSSID(bssid);  

84.    Serial.print("BSSID: ");  

85.    Serial.print(bssid[5], HEX);  

86.    Serial.print(":");  

87.    Serial.print(bssid[4], HEX);  

88.    Serial.print(":");  

89.    Serial.print(bssid[3], HEX);  

90.    Serial.print(":");  

91.    Serial.print(bssid[2], HEX);  

92.    Serial.print(":");  

93.    Serial.print(bssid[1], HEX);  

94.    Serial.print(":");  

95.    Serial.println(bssid[0], HEX);  

96.    

97.    // print the received signal strength:  

98.    **long** rssi = WiFi.RSSI();  

99.    Serial.print("signal strength (RSSI):");  

100.   Serial.println(rssi);  

101.   

102.   // print the encryption type:  

103.   byte encryption = WiFi.encryptionType();  

104.   Serial.print("Encryption Type:");  

105.   Serial.println(encryption, HEX);  

106.   Serial.println();  

107. }  

**Notes and Warnings**

NA

**
**

**WiFiClass:: begin**

**Description**

Start Wifi connection for OPEN networks

**Syntax**

-  int WiFiClass::begin(char\* ssid)

-  int WiFiClass::begin(char\* ssid, uint8_t key_idx, const char \*key)

-  int WiFiClass::begin(char\* ssid, const char \*passphrase)

**Parameters**

ssid: Pointer to the SSID string

key_idx: The key index to set. Valid values are 0-3.

key: Key input buffer.

passphrase: Passphrase. Valid characters in a passphrase must be between
ASCII 32-126 (decimal).

**Returns**

WiFi status

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
WiFiClass:: config**

**Description**

Configure network settings for the WiFi network

**Syntax**

void WiFiClass::config(IPAddress local_ip)

void WiFiClass::config(IPAddress local_ip, IPAddress dns_server)

void WiFiClass::config(IPAddress local_ip, IPAddress dns_server,
IPAddress gateway)

void WiFiClass::config(IPAddress local_ip, IPAddress dns_server,
IPAddress gateway, IPAddress subnet)

**Parameters**

local_ip: Local device IP address to use on the network

dns_server: IP address of the DNS server to use

gateway: IP address of the gateway device on the network

subnet: Subnet mask for the network, expressed as a IP address

**Returns**

The function returns nothing.

**Example Code**

NA

**Notes and Warnings**

This will disable the DHCP client when connecting to a network, and will
require the network accepts a static IP. The configured IP addresses
will also apply to AP mode, but the DHCP server will not be disabled in
AP mode.

**
**

**WiFiClass:: setDNS**

**Description**

Configure the IP address of the DNS server to use

**Syntax**

void WiFiClass::setDNS(IPAddress dns_server1)

void WiFiClass::setDNS(IPAddress dns_server1, IPAddress dns_server2)

**Parameters**

dns_server1: IP address of DNS server to use

dns_server2: IP address of DNS server to use

**Returns**

The function returns nothing.

**Example Code**

NA

**Notes and Warnings**

NA

**
**

**WiFiClass:: disconnect**

**Description**

Disconnect from the network

**Syntax**

int WiFiClass::disconnect()

**Parameters**

The function requires no input parameter.

**Returns**

The function returns one value of wl_status_t enum as an integer.

**Example Code**

NA

**Notes and Warnings**

NA

**
**

**WiFiClass:: macAddress**

**Description**

Get the interface MAC address

**Syntax**

uint8_t\* WiFiClass::macAddress(uint8_t\* mac)

**Parameters**

mac: an array to store MAC address

**Returns**

The function returns a pointer to uint8_t array with length
WL_MAC_ADDR_LENGTH.

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: localIP**

**Description**

Get the interface IP address

**Syntax**

IPAddress WiFiClass::localIP()

**Parameters**

The function requires no input parameter.

**Returns**

Ip address value

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: subnetMask**

**Description**

Get the interface subnet mask address

**Syntax**

IPAddress WiFiClass::subnetMask()

**Parameters**

The function requires no input parameter.

**Returns**

subnet mask address value

**Example Code**

Example: ConnectNoEncryption

This example demonstrates how to connect to an unencrypted WiFi network
and prints the MAC address of the WiFi shield, the IP address obtained,
and other network details.

1.   #include <WiFi.h>  

2.     

3.   **char** ssid[] = "SINGTEL-D45F_5G";     // the name of your network  

4.   **int** status = WL_IDLE_STATUS;     // the Wifi radio's status  

5.     

6.   **void** setup() {  

7.     //Initialize serial and wait for port to open:  

8.     Serial.begin(9600);  

9.     **while** (!Serial) {  

10.      ; // wait for serial port to connect. Needed for native USB port only  

11.    }  

12.    

13.    // check for the presence of the shield:  

14.    **if** (WiFi.status() == WL_NO_SHIELD) {  

15.      Serial.println("WiFi shield not present");  

16.      // don't continue:  

17.      **while** (**true**);  

18.    }  

19.    

20.    String fv = WiFi.firmwareVersion();  

21.    **if** (fv != "1.1.0") {  

22.      Serial.println("Please upgrade the firmware");  

23.    }  

24.    

25.    // attempt to connect to Wifi network:  

26.    **while** (status != WL_CONNECTED) {  

27.      Serial.print("Attempting to connect to open SSID: ");  

28.      Serial.println(ssid);  

29.      status = WiFi.begin(ssid);  

30.    

31.      // wait 10 seconds for connection:  

32.      delay(10000);  

33.    }  

34.    

35.    // you're connected now, so print out the data:  

36.    Serial.print("You're connected to the network");  

37.    printCurrentNet();  

38.    printWifiData();  

39.  }  

40.    

41.  **void** loop() {  

42.    // check the network connection once every 10 seconds:  

43.    delay(10000);  

44.    printCurrentNet();  

45.  }  

46.    

47.  **void** printWifiData() {  

48.    // print your WiFi shield's IP address:  

49.    IPAddress ip = WiFi.localIP();  

50.    Serial.print("IP Address: ");  

51.    Serial.println(ip);  

52.    Serial.println(ip);  

53.    

54.    // print your MAC address:  

55.    byte mac[6];  

56.    WiFi.macAddress(mac);  

57.    Serial.print("MAC address: ");  

58.    Serial.print(mac[0], HEX);  

59.    Serial.print(":");  

60.    Serial.print(mac[1], HEX);  

61.    Serial.print(":");  

62.    Serial.print(mac[2], HEX);  

63.    Serial.print(":");  

64.    Serial.print(mac[3], HEX);  

65.    Serial.print(":");  

66.    Serial.print(mac[4], HEX);  

67.    Serial.print(":");  

68.    Serial.println(mac[5], HEX);  

69.    

70.    // print your subnet mask:  

71.    IPAddress subnet = WiFi.subnetMask();  

72.    Serial.print("NetMask: ");  

73.    Serial.println(subnet);  

74.    

75.    // print your gateway address:  

76.    IPAddress gateway = WiFi.gatewayIP();  

77.    Serial.print("Gateway: ");  

78.    Serial.println(gateway);  

79.  }  

80.    

81.  **void** printCurrentNet() {  

82.    // print the SSID of the network you're attached to:  

83.    Serial.print("SSID: ");  

84.    Serial.println(WiFi.SSID());  

85.    

86.    // print the MAC address of the router you're attached to:  

87.    byte bssid[6];  

88.    WiFi.BSSID(bssid);  

89.    Serial.print("BSSID: ");  

90.    Serial.print(bssid[5], HEX);  

91.    Serial.print(":");  

92.    Serial.print(bssid[4], HEX);  

93.    Serial.print(":");  

94.    Serial.print(bssid[3], HEX);  

95.    Serial.print(":");  

96.    Serial.print(bssid[2], HEX);  

97.    Serial.print(":");  

98.    Serial.print(bssid[1], HEX);  

99.    Serial.print(":");  

100.   Serial.println(bssid[0], HEX);  

101.   

102.   // print the received signal strength:  

103.   **long** rssi = WiFi.RSSI();  

104.   Serial.print("signal strength (RSSI):");  

105.   Serial.println(rssi);  

106.   

107.   // print the encryption type:  

108.   byte encryption = WiFi.encryptionType();  

109.   Serial.print("Encryption Type:");  

110.   Serial.println(encryption, HEX);  

111. }  

**Notes and Warnings**

NA

**
**

**WiFiClass:: gatewayIP**

**Description**

Get the gateway IP address

**Syntax**

IPAddress WiFiClass::gatewayIP()

**Parameters**

The function requires no input parameter.

**Returns**

The function returns the value of the gateway IP address.

**Example Code**

Example: ConnectNoEncryption

This example demonstrates how to connect to an unencrypted WiFi network
and prints the MAC address of the WiFi shield, the IP address obtained,
and other network details. Details of the code can be found in the
section of WiFiClass:: subnetMask.

**Notes and Warnings**

NA

**
**

**WiFiClass:: SSID**

**Description**

Return the current SSID associated with the network

**Syntax**

char\* WiFiClass::SSID()

**Parameters**

The function requires no input parameter.

**Returns**

The function returns current SSID associate with the network.

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: BSSID**

**Description**

Return the current BSSID associated with the network.

**Syntax**

uint8_t\* WiFiClass::BSSID(uint8_t\* bssid)

**Parameters**

bssid: an array to store bssid

**Returns**

pointer to uint8_t array with length WL_MAC_ADDR_LENGTH

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: RSSI**

**Description**

Return the current RSSI (Received Signal Strength in dBm) associated
with the network

**Syntax**

int32_t WiFiClass::RSSI(void)

**Parameters**

The function requires no input parameter.

**Returns**

The function returns a signed-value signal strength.

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: encryptionType**

**Description**

Return the Encryption Type associated with the network

**Syntax**

uint8_t WiFiClass::encryptionType()

**Parameters**

The function requires no input parameter.

**Returns**

The function returns one unsigned integer value of wl_enc_type enum

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: scanNetworks**

**Description**

Start scan WiFi networks available

**Syntax**

int8_t WiFiClass::scanNetworks(void)

**Parameters**

The function requires no input parameter.

**Returns**

The function returns the number of discovered networks as an integer.

**Example Code**

Example: ScanNetworks

This example prints the Wifi shield's MAC address, and scans for
available Wifi networks using the Wifi shield. Every ten seconds, it
scans again. It doesn't connect to any network, so no encryption scheme
is specified.

1.   #include <WiFi.h>  

2.     

3.   **void** setup() {  

4.     //Initialize serial and wait for port to open:  

5.     Serial.begin(9600);  

6.     **while** (!Serial) {  

7.       ; // wait for serial port to connect. Needed for native USB port only  

8.     }  

9.     

10.    // check for the presence of the shield:  

11.    **if** (WiFi.status() == WL_NO_SHIELD) {  

12.      Serial.println("WiFi shield not present");  

13.      // don't continue:  

14.      **while** (**true**);  

15.    }  

16.    

17.    String fv = WiFi.firmwareVersion();  

18.    **if** (fv != "1.1.0") {  

19.      Serial.println("Please upgrade the firmware");  

20.    }  

21.    

22.    // Print WiFi MAC address:  

23.    printMacAddress();  

24.  }  

25.    

26.  **void** loop() {  

27.    // scan for existing networks:  

28.    Serial.println("Scanning available networks...");  

29.    listNetworks();  

30.    delay(10000);  

31.  }  

32.    

33.  **void** printMacAddress() {  

34.    // the MAC address of your Wifi shield  

35.    byte mac[6];  

36.    

37.    // print your MAC address:  

38.    WiFi.macAddress(mac);  

39.    Serial.print("MAC: ");  

40.    Serial.print(mac[0], HEX);  

41.    Serial.print(":");  

42.    Serial.print(mac[1], HEX);  

43.    Serial.print(":");  

44.    Serial.print(mac[2], HEX);  

45.    Serial.print(":");  

46.    Serial.print(mac[3], HEX);  

47.    Serial.print(":");  

48.    Serial.print(mac[4], HEX);  

49.    Serial.print(":");  

50.    Serial.println(mac[5], HEX);  

51.  }  

52.    

53.  **void** listNetworks() {  

54.    // scan for nearby networks:  

55.    Serial.println("** Scan Networks **");  

56.    **int** numSsid = WiFi.scanNetworks();  

57.    **if** (numSsid == -1) {  

58.      Serial.println("Couldn't get a wifi connection");  

59.      **while** (**true**);  

60.    }  

61.    

62.    // print the list of networks seen:  

63.    Serial.print("number of available networks:");  

64.    Serial.println(numSsid);  

65.    

66.    // print the network number and name for each network found:  

67.    **for** (**int** thisNet = 0; thisNet < numSsid; thisNet++) {  

68.      Serial.print(thisNet);  

69.      Serial.print(") ");  

70.      Serial.print(WiFi.SSID(thisNet));  

71.      Serial.print("\tSignal: ");  

72.      Serial.print(WiFi.RSSI(thisNet));  

73.      Serial.print(" dBm");  

74.      Serial.print("\tEncryptionRaw: ");  

75.      printEncryptionTypeEx(WiFi.encryptionTypeEx(thisNet));  

76.      Serial.print("\tEncryption: ");  

77.      printEncryptionType(WiFi.encryptionType(thisNet));  

78.    }  

79.  }  

80.    

81.  **void** printEncryptionTypeEx(uint32_t thisType) {  

82.    /*  Arduino wifi api use encryption type to mapping to security type. 

83.     *  This function demonstrate how to get more richful information of security type. 

84.     */  

85.    **switch** (thisType) {  

86.      **case** SECURITY_OPEN:  

87.        Serial.print("Open");  

88.        **break**;  

89.      **case** SECURITY_WEP_PSK:  

90.        Serial.print("WEP");  

91.        **break**;  

92.      **case** SECURITY_WPA_TKIP_PSK:  

93.        Serial.print("WPA TKIP");  

94.        **break**;  

95.      **case** SECURITY_WPA_AES_PSK:  

96.        Serial.print("WPA AES");  

97.        **break**;  

98.      **case** SECURITY_WPA2_AES_PSK:  

99.        Serial.print("WPA2 AES");  

100.       **break**;  

101.     **case** SECURITY_WPA2_TKIP_PSK:  

102.       Serial.print("WPA2 TKIP");  

103.       **break**;  

104.     **case** SECURITY_WPA2_MIXED_PSK:  

105.       Serial.print("WPA2 Mixed");  

106.       **break**;  

107.     **case** SECURITY_WPA_WPA2_MIXED:  

108.       Serial.print("WPA/WPA2 AES");  

109.       **break**;  

110.   }  

111. }  

112.   

113. **void** printEncryptionType(**int** thisType) {  

114.   // read the encryption type and print out the name:  

115.   **switch** (thisType) {  

116.     **case** ENC_TYPE_WEP:  

117.       Serial.println("WEP");  

118.       **break**;  

119.     **case** ENC_TYPE_TKIP:  

120.       Serial.println("WPA");  

121.       **break**;  

122.     **case** ENC_TYPE_CCMP:  

123.       Serial.println("WPA2");  

124.       **break**;  

125.     **case** ENC_TYPE_NONE:  

126.       Serial.println("None");  

127.       **break**;  

128.     **case** ENC_TYPE_AUTO:  

129.       Serial.println("Auto");  

130.       **break**;  

131.   }  

132. }  

**Notes and Warnings**

NA

**
**

**WiFiClass:: SSID**

**Description**

Return the SSID discovered during the network scan

**Syntax**

char\* WiFiClass::SSID(uint8_t networkItem)

**Parameters**

networkItem: specify from which network item want to get the information

**Returns**

The function returns ssid string of the specified item on the networks
scanned a list.

**Example Code**

Example: ScanNetworks

This example prints the Wifi shield's MAC address, and scans for
available Wifi networks using the Wifi shield. Every ten seconds, it
scans again. It doesn't connect to any network, so no encryption scheme
is specified. The details of the code can be found in the previous
section of WiFiClass:: scanNetworks.

**Notes and Warnings**

NA

**
**

**WiFiClass:: encryptionType**

**Description**

Return the encryption type of the networks discovered during the
scanNetworks

**Syntax**

uint8_t WiFiClass::encryptionType(uint8_t networkItem)

**Parameters**

networkItem: specify from which network item want to get the information

**Returns**

encryption type (enum wl_enc_type) of the specified item on the networks
scanned a list

**Example Code**

Example: ScanNetworks

This example prints the Wifi shield's MAC address, and scans for
available Wifi networks using the Wifi shield. Every ten seconds, it
scans again. It doesn't connect to any network, so no encryption scheme
is specified. The details of the code can be found in the previous
section of WiFiClass:: scanNetworks.

**Notes and Warnings**

NA

**
**

**WiFiClass:: encryptionTypeEx**

**Description**

Return the security type and encryption type of the networks discovered
during the scanNetworks

**Syntax**

uint32_t WiFiClass::encryptionTypeEx(uint8_t networkItem)

**Parameters**

networkItem: specify from which network item want to get the information

**Returns**

security and encryption type of the specified item on the networks
scanned a list

**Example Code**

Example: ScanNetworks

This example prints the Wifi shield's MAC address, and scans for
available Wifi networks using the Wifi shield. Every ten seconds, it
scans again. It doesn't connect to any network, so no encryption scheme
is specified. The details of the code can be found in the previous
section of WiFiClass:: scanNetworks.

**Notes and Warnings**

NA

**
**

**WiFiClass:: RSSI**

**Description**

Return the RSSI of the networks discovered during the scanNetworks

**Syntax**

int32_t WiFiClass::RSSI(uint8_t networkItem)

**Parameters**

networkItem: specify from which network item want to get the information

**Returns**

signed value of RSSI of the specified item on the networks scanned a
list

**Example Code**

Example: ScanNetworks

This example prints the Wifi shield's MAC address, and scans for
available Wifi networks using the Wifi shield. Every ten seconds, it
scans again. It doesn't connect to any network, so no encryption scheme
is specified. The details of the code can be found in the previous
section of WiFiClass:: scanNetworks.

**Notes and Warnings**

NA

**
**

**WiFiClass:: status**

**Description**

Return Connection status

**Syntax**

uint8_t WiFiClass::status()

**Parameters**

The function requires no input parameter.

**Returns**

The function returns one of the values defined in wl_status_t as an
unsigned integer.

**Example Code**

Example: ConnectWithWPA

This example demos how to connect to an unencrypted WiFi network, and
prints the MAC address of the Wifi shield, the IP address obtained, and
other network details. The details of the code can be found in the
previous section of WiFiClass:: firmwareVersion.

**Notes and Warnings**

NA

**
**

**WiFiClass:: hostByName**

**Description**

Resolve the given hostname to an IP address

**Syntax**

int WiFiClass::hostByName(const char\* aHostname, IPAddress& aResult)

**Parameters**

aHostname: Name to be resolved

aResult: IPAddress structure to store the returned IP address

**Returns**

The function returns “1” if aIPAddrString was successfully converted to
an IP address, otherwise, it will return as an error code.

**Example Code**

NA

**Notes and Warnings**

NA

**
**

**WiFiClass:: apbegin**

**Description**

Start AP mode

**Syntax**

-  int WiFiClass::apbegin(char\* ssid, char\* channel)

-  int WiFiClass::apbegin(char\* ssid, char\* password, char\* channel)

**Parameters**

ssid: SSID of the AP network

channel: AP’s channel, default 1

password: AP’s password

**Returns**

The function will return the WiFi status.

**Example Code**

Example: WiFiAPMode

1.  #include <WiFi.h>  

2.  **char** ssid[] = "yourNetwork";  //Set the AP's SSID  

3.  **char** pass[] = "Password";     //Set the AP's password  

4.  **char** channel[] = "1";         //Set the AP's channel  

5.  **int** status = WL_IDLE_STATUS;     // the Wifi radio's status  

6.    

7.  **void** setup() {  

8.    //Initialize serial and wait for port to open:  

9.    Serial.begin(9600);  

10.   **while** (!Serial) {  

11.     ; // wait for serial port to connect. Needed for native USB port only  

12.   }  

13.   // check for the presence of the shield:  

14.   **if** (WiFi.status() == WL_NO_SHIELD) {  

15.     Serial.println("WiFi shield not present");  

16.     **while** (**true**);  

17.   }  

18.   String fv = WiFi.firmwareVersion();  

19.   **if** (fv != "1.1.0") {  

20.     Serial.println("Please upgrade the firmware");  

21.   }  

22.   

23.   // attempt to start AP:  

24.   **while** (status != WL_CONNECTED) {  

25.     Serial.print("Attempting to start AP with SSID: ");  

26.     Serial.println(ssid);  

27.     status = WiFi.apbegin(ssid, pass, channel);  

28.     delay(10000);  

29.   }  

30.   

31.   //AP MODE already started:  

32.   Serial.println("AP mode already started");  

33.   Serial.println();  

34.   printWifiData();  

35.   printCurrentNet();  

36. }  

37.   

38. **void** loop() {  

39.   // check the network connection once every 10 seconds:  

40.   delay(10000);  

41.   printCurrentNet();  

42. }  

43.   

44. **void** printWifiData() {  

45.   // print your WiFi shield's IP address:  

46.   IPAddress ip = WiFi.localIP();  

47.   Serial.print("IP Address: ");  

48.   Serial.println(ip);  

49.   

50.   // print your subnet mask:  

51.   IPAddress subnet = WiFi.subnetMask();  

52.   Serial.print("NetMask: ");  

53.   Serial.println(subnet);  

54.   

55.   // print your gateway address:  

56.   IPAddress gateway = WiFi.gatewayIP();  

57.   Serial.print("Gateway: ");  

58.   Serial.println(gateway);  

59.   Serial.println();  

60. }  

61.   

62. **void** printCurrentNet() {  

63.   // print the SSID of the AP:  

64.   Serial.print("SSID: ");  

65.   Serial.println(WiFi.SSID());  

66.   

67.   // print the MAC address of AP:  

68.   byte bssid[6];  

69.   WiFi.BSSID(bssid);  

70.   Serial.print("BSSID: ");  

71.   Serial.print(bssid[0], HEX);  

72.   Serial.print(":");  

73.   Serial.print(bssid[1], HEX);  

74.   Serial.print(":");  

75.   Serial.print(bssid[2], HEX);  

76.   Serial.print(":");  

77.   Serial.print(bssid[3], HEX);  

78.   Serial.print(":");  

79.   Serial.print(bssid[4], HEX);  

80.   Serial.print(":");  

81.   Serial.println(bssid[5], HEX);  

82.   // print the encryption type:  

83.   byte encryption = WiFi.encryptionType();  

84.   Serial.print("Encryption Type:");  

85.   Serial.println(encryption, HEX);  

86.   Serial.println();  

87. }  

**Notes and Warnings**

NA

**WiFiClass:: disablePowerSave**

**Description**

Disable power-saving mode

**Syntax**

int WiFiClass::disablePowerSave()

**Parameters**

The function requires no input parameter.

**Returns**

1 if disable success, 0 if failed

**Example Code**

NA

**Notes and Warnings**

NA
