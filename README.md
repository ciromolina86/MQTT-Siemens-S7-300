# MQTT-Siemens-S7-300
Work in Progress!

MQTT functionality written in SCL for S7-300 with CP343-1

### Current State:
At this time, this is working for CPU313C-2DP with CP343-1 Lean Ethernet module.
I am locally connecting to a HiveMQ broker and controlling PLC outputs using published messages.
I can also publish a hard coded message from the PLC.

# Requirements
It should work with most S7-300 CPU's.
You must have a CP343-1 module with v2.1 or higher.
This code is written in Step7 SCL v5.3 SP1. It probably needs modification for it to compile in TIA.

# How to Use
The following needs to be setup in you project in Simatic Manager:

1. The tcp connection to the broker must be set up in NetPro (IP Address + Port: 1883)
2. You must call the MQTT function block in your OB1 program loop.
2. Your project's symbol list needs appropriate block numbers assigned to them, mine is:

- MQTT   		: FB1
- PacketReader	: FB2
- Globals  		: DB100
- Data			: DB101
- connect 		: FC50
- sendTCP		: FC51
- write 		: FC52
- writeString	: FC53
- available		: FC54
- readByte 		: FC55
- readByteToBuf	: FC56
- publish     	: FC57
- subscribe		: FC58
- connected		: FC59


# Example
Included is an example application function block (FB66) that is typically called from OB1.
Inputs for this block can trigger a MQTT broker connect, publish a message or subscribe to a MQTT channel.