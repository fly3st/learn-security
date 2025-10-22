The OSI (Open Systems Interconnection) Model is a model that provides a framework that dictates how all network devices send and receive data.

The model is made up of 7 layers:
1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

The physical layer references the physical components of the hardware used in networking and is the lowest layer.
Devices on this layer use electrical signals to transfer data between each other in binary (1's and 0's).

The data link layer focuses on the physical addressing of the transmission.
When a packet is received from the network layer it adds in the physical MAC address.

The network layer is where assembly and re-routing takes place, using the protocols OSPF (Open Shortest Path First) and RIP (Routing Information Protocol).
In this layer everything is dealt using IP addresses.

The transport protocol follows one of the two different protocols that are decided upon based on several factors:
* TCP
* UDP

Transmission Control Protocol (TCP) is a protocol that is designed with reliability and guarantee in mind since it reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received.
Also, TCP incorporates error checking so that it can guarantee that data is sent from small chunks in the session layer and has been received and re-assembled in the same order.

User Datagram Protocol (UDP) is a protocol that's less advanced than TCP.
UDP just sends the data off, doesn't matter whether the recipient got the data or not and thus making it much faster than TCP, albeit less reliable.

The session layer creates and maintains connections to other computer for which the data is destined.
When a connection is established, a session is created and whilst the connection is active, so is the session.
This layer is also responsible for closing the connection if it hasn't been used for a while or lost.
Additionally, a session can contain "checkpoints" where if the data is lost, only the newest pieces of data are required to be sent which saves bandwidth.

The presentation layer translates the data to and from the application layer, the receiving end will also understand data sent to a computer in one format destined for in another format.
Security features such as data encryption (like HTTPS for example) occur on this layer.

The application layer is the layer most people are familiar with, because this layer is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received.
Other protocols include DNS (Domain Name System).