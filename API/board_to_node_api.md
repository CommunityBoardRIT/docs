# Board to Node API
## Changelog


## Objective

Defines the inteface for the bidirectional communication between the CommunityBoard application and peripheral nodes.

## Overview

The (tentative) protocol is SCTP, which is the happy middle ground between TCP (providing reliable, in order messages), and UDP (uses datagrams rather than streams).

Each message is sent in wrappers. After unpacking from the SCTP wrapper, the data will be contained in a Message Header (defined below). This contains generic information such as the purpose of the message, checksum, payload length, and the payload itself.

The payload will differ in conjuction with the purpose as specified in the Message Header.

<br>

# Data Descriptions

## Message Wrapper

|Byte Index|Name|Type|Count|Description|
|---|---|---|---|---|
|0|ID|UINT32|1|The unique ID of the message; Prevents message duplication|
|4|Address|UINT16|1| Address of the endpoint |
|6|Command Value|UINT16|1|A number corresponding to the command to be executed|
|8|Length|UINT16|1| Number of bytes in payload |
|10|Payload|UINT8[]|_Length_|Contents of payload|
|10 + _Length_|CRC|UINT16|1|Checksum; Calculated by CRC over the entire Message (excluding the CRC itself)|

## Payloads

### Handshake
#### Command Value: 0x0000

Returns the name, version number, and other TBD values (such as potentially GPS location, network statistics, sub-api (explained in "Subcommand")).

### Update Encryption
#### Command Value: 0x0002
If encryption is enabled (Outside scope of MVP), this command can include updating AES256 keys.

### Subcommand
#### Command Value: 0x0004
Defined by the end node, and it's associated sub-api. The payload will consist of a wrapper and sub-payload, in a manner very similar to the Message wrapper.

#### Subcommand Wrapper:
|Byte Index|Name|Type|Count|Description|
|---|---|---|---|---|
|0|Subcommand Value|UINT16|1|A number corresponding to the command to be executed|
|2|Sublength|UINT16|1| Number of bytes in payload |
|4|Payload|UINT8[]|_Sublength_|Contents of payload|

### Configure Polling
#### Command Value: 0x0006
Many nodes have to send data at reguluar intervals of time. This command allows this feature to be enabled, and configured.