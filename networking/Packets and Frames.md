Packets and frames are small pieces of data that when formed together make up a larger piece of information.
In the OSI model they are two different things:

* A packet is piece of data from layer 3 (the network layer) that contains information such as an IP header and payload.
* A frame is used at layer 2 (the data link layer) and encapsulates the packet and adds additional information on top of it such as MAC addresses.

Types of headers on a packet include:

| **Header**          | **Description**                                                                                                                                                         |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Time to Live        | This field sets an expiry timer for the packet to not clog up our network if it never manages to reach a host or escape.                                                |
| Checksum            | This field provides integrity checking for protocols such as TCP/IP. If any data is changed, this value will be different from what was expected and therefore corrupt. |
| Source Address      | The IP address of the device that the packet is being sent **from** so that data knows where to **return to**.                                                          |
| Destination Address | The device's IP address the packet is being sent to so that data knows where to travel next.                                                                            |
TCP/IP model, which is similar to the OSI model consists of only 4 layers instead of 7:
1. Network Interface layer
2. Internet Layer
3. Transport Layer
4. Application Layer

When a packet traverses these layers the process is called either encapsulation (as it goes up the layers) and decapsulation (as it goes down the layers).

TCP is connection-based which means that TCP must establish a connection between a client and a device acting as a server before the data is sent.
This is how TCP guarantees that any data will be received on the other end, this process is called the Three-way handshake.

| **Advantages of TCP**                                                                                       | **Disadvantages of TCP**                                                                                                                                              |
| ----------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Guarantees the integrity of data.                                                                           | Requires a reliable connection between the two devices. If one small chunk of data is not received, then the entire chunk of data cannot be used and must be re-sent. |
| Capable of synchronising two devices to prevent each other from being flooded with data in the wrong order. | A slow connection can bottleneck another device as the connection will be reserved on the other device the whole time.                                                |
| Performs a lot more processes for reliability                                                               | TCP is significantly slower than UDP because more work (computing) has to be done by the devices using this protocol.                                                 |
TCP packets contain various sections of information, also known as headers, that are then added via the process of encapsulation.

| Header                 | Description                                                                                                                                                                                                                                         |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Source Port            | This value is the port opened by the sender to send the TCP packet from. This value is chosen randomly (out of the ports from 0-65535 that aren't already in use at the time).                                                                      |
| Destination Port       | This value is the port number that an application or service is running on the remote host (the one receiving data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random.                       |
| Source IP              | This is the IP address of the device that is sending the packet.                                                                                                                                                                                    |
| Destination IP         | This is the IP address of the device that the packet is destined for.                                                                                                                                                                               |
| Sequence Number        | When a connection occurs, the first piece of data transmitted is given a random number.                                                                                                                                                             |
| Acknowledgement Number | After a piece of data has been given a sequence number, the number for the next piece of data will have the sequence number + 1.                                                                                                                    |
| Checksum               | This value is what gives TCP integrity. A mathematical calculation is made where the output is remembered. When the receiving device performs the mathematical calculation, the data must be corrupt if the output is different from what was sent. |
| Data                   | This header is where the data, i.e. bytes of a file that is being transmitted, is stored.                                                                                                                                                           |
| Flag                   | This header determines how the packet should be handled by either device during the handshake process. Specific flags will determine specific behaviours.                                                                                           |
The three-way handshake process starts when a connection between two devices are established, and it communicates using the following messages:

1. `SYN` - a `SYN` message is the initial packet that gets sent by the client during the handshake process, which is used to initiate a connection and synchronize both devices together.
2. `SYN/ACK` - this packet is sent by the receiving device to acknowledge the synchronization attempt from the client.
3. `ACK` - the acknowledgement packet that can be used by either the client or server to acknowledge that a series of messages / packets have been successfully received.
4. `DATA` - once a connection has been established the data is sent via the `DATA` message.
5. `FIN` - this packet is used to properly close the connection after it's been complete.
6. `RST` - this packet abruptly ends all communication, this is the last resort and indicates there was some problem during the process, such as low system resources.

During the process the agreed upon order is during three steps:
1. `SYN` - the client gives the Initial Sequence Number (ISN) to synchronize with (0).
2. `SYN/ACK` - the server gives his ISN to synchronize with (5,000) and acknowledges the client's ISN (0).
3. `ACK` - the client acknowledges the ISN of the server (5,000) and gives data that is his ISN + 1 (0 + 1).

| Device          | **Initial Number Sequence (ISN)  <br>** | **Final Number Sequence  <br>** |
| --------------- | --------------------------------------- | ------------------------------- |
| Client (Sender) | 0                                       | 0 + 1 = 1                       |
| Client (Sender) | 1                                       | 1 + 1 = 2                       |
| Client (Sender) | 2                                       | 2 + 1 = 3                       |
A TCP closing connection sequence would look like the folllwing:

1. `FIN` - client sends a `FIN` packet.
2. `ACK/FIN` - server acknowledges the `FIN` packet and sends his own `FIN` packet to the client.
3. `ACK` - client acknowledges server's `FIN` packet.

UDP is a stateless protocol that doesn't require a constant connection between the two devices for the data to be sent.
Which is why it's used in situations where applications can tolerate data being lost (like video streaming or voice chat) or in scenarios where an unstable connection is the end-all.

| **Advantages of UDP**                                                                                           | **Disadvantages of UDP**                                                           |
| --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| UDP is much faster than TCP.                                                                                    | UDP doesn't care if the data is received or not.                                   |
| UDP leaves the application (user software) to decide if there is any control over how quickly packets are sent. | It is quite flexible to software developers in this sense.                         |
| UDP does not reserve a continuous connection on a device as TCP does.                                           | This means that unstable connections result in a terrible experience for the user. |
UDP packets are much simpler than TCP ones and have less headers, however, both protocols share some standard headers:

| **Header**          | **Description**                                                                                                                                                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Time to Live (TTL)  | This field sets an expiry timer for the packet, so it doesn't clog up our network if it never manages to reach a host or escape.                                                                                                  |
| Source Address      | The IP address of the device that the packet is being sent from, so that data knows where to return to.                                                                                                                           |
| Destination Address | The device's IP address the packet is being sent to so that data knows where to travel next.                                                                                                                                      |
| Source Port         | This value is the port that is opened by the sender to send the UDP packet from. This value is randomly chosen (out of the ports from 0-65535 that aren't already in use at the time).                                            |
| Destination Port    | This value is the port number that an application or service is running on the remote host (the one receiving the data); for example, a webserver running on port 80. Unlike the source port, this value is not chosen at random. |
| Data                | This header is where data, i.e. bytes of a file that is being transmitted, is stored.                                                                                                                                             |
These packets can be sent across different ports on the source and destination addresses, there are anywhere between 0-65535 ports, and while there are common ports (0-1024) some applications / services are associated with different ports:

|                                                                    |                 |                                                                                                                                                            |
| ------------------------------------------------------------------ | --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Protocol**                                                       | **Port Number** | **Description**                                                                                                                                            |
| **F**ile **T**ransfer **P**rotocol (**FTP**)                       | 21              | This protocol is used by a file-sharing application built on a client-server model, meaning you can download files from a central location.                |
| **S**ecure **Sh**ell (**SSH**)                                     | 22              | This protocol is used to securely login to systems via a text-based interface for management.                                                              |
| **H**yper**T**ext Transfer Protocol (**HTTP**)                     | 80              | This protocol powers the World Wide Web (WWW), our browser uses this to download text, images and videos of web pages.                                     |
| **H**yper**T**ext **T**ransfer **P**rotocol **S**ecure (**HTTPS**) | 443             | This protocol does the exact same as above; however, securely using encryption.                                                                            |
| **S**erver **M**essage **B**lock (**SMB**)                         | 445             | This protocol is similar to the File Transfer Protocol (FTP); however, as well as files, SMB allows you to share devices like printers.                    |
| **R**emote **D**esktop **P**rotocol (**RDP**)                      | 3389            | This protocol is a secure means of logging in to a system using a visual desktop interface (as opposed to the text-based limitations of the SSH protocol). |