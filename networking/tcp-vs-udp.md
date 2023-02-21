# TCP vs UDP

## Comparison of UDP and TCP

TCP is a connection-oriented protocol and requires handshaking to set up end-to-end communications. Once a connection is set up, user data may be sent bi-directionally over the connection.

- Reliable - TCP manages message acknowledgment, retransmission and timeouts. Multiple attempts to deliver the message are made. If data gets lost along the way, data will be re-sent. In TCP, there's either no missing data, or, in case of multiple timeouts, the connection is dropped.
- Ordered - If two messages are sent over a connection in sequence, the first message will reach the receiving application first. When data segments arrive in the wrong order, TCP buffers the out-of-order data until all data can be properly re-ordered and delivered to the application.
- Heavyweight - TCP requires three packets to set up a socket connection before any user data can be sent. TCP handles reliability and congestion control.
- Streaming - Data is read as a byte stream, no distinguishing indications are transmitted to signal message (segment) boundaries.

UDP is a simpler message-based connectionless protocol. Connectionless protocols do not set up a dedicated end-to-end connection. Communication is achieved by transmitting information in one direction from source to destination without verifying the readiness or state of the receiver.

- Unreliable - When a UDP message is sent, it cannot be known if it will reach its destination; it could get lost along the way. There is no concept of acknowledgment, retransmission, or timeout.
- Not ordered - If two messages are sent to the same recipient, the order in which they arrive cannot be guaranteed.
- Lightweight - There is no ordering of messages, no tracking connections, etc. It is a very simple transport layer designed on top of IP.
- Datagrams - Packets are sent individually and are checked for integrity on arrival. Packets have definite boundaries which are honored upon receipt; a read operation at the receiver socket will yield an entire message as it was originally sent.
- No congestion control - UDP itself does not avoid congestion. Congestion control measures must be implemented at the application level or in the network.
- Broadcasts - being connectionless, UDP can broadcast - sent packets can be addressed to be receivable by all devices on the subnet.
- Multicast - a multicast mode of operation is supported whereby a single datagram packet can be automatically routed without duplication to a group of subscribers.

## Notes

Each frame goes through several buffers as you send it: The application buffer, The Protocol Buffer, The Software interface buffer and the Hardware interface buffer. As you start stressing the stack by sending high speed data you will fill up these buffers and either block or lose data. You also have strategies for timeliness and polling that can impact your performance. For example, by using a larger buffer and poll less often you can get much better performance while sacrificing latency.

TCP is optimized for high speed bulk transfers while UDP is optimized for low latency in the Linux kernel. This has an impact on buffer sizes and how data is polled and handed over. In addition to this, you frequently have offloading to hardware for TCP. I would expect considerably better performance for TCP compared to UDP.

Note that sending high speed data over UDP is usually a bad idea, unless you implement your own congestion control. TCP protects your network from congestion collapses. Use UDP when you have small amounts of data or high timeliness requirements.

## See also

- [TCP](tcp.md)
- [UDP](udp.md)
- [List of TCP and UDP port numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers).
