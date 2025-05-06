# comp2017-assignment-1-localised-chat-server-solved
**TO GET THIS SOLUTION VISIT:** [COMP2017 Assignment 1-Localised Chat server Solved](https://www.ankitcodinghub.com/product/comp2017-assignment-1-localised-chat-server-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;97339&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;0&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;0&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;0\/5 - (0 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;COMP2017 Assignment 1-Localised Chat server Solved&quot;,&quot;width&quot;:&quot;0&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 0px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            <span class="kksr-muted">Rate this product</span>
    </div>
    </div>
You are to develop a localised chat server that will support a number of clients through named pipes (FIFOs). The server and client applications will communicate through a fixed sized binary protocol. The server will manage a global named pipe for establishing connections, after a connection has been established it will construct a separate read and write named pipes for the client to utilise. The client will communicate to the server over the named pipes. The server must be able to read from all clients asynchronously.

Global Process

The global server is involved in facilitating the initial connection from clients. The initial message from the client will be an identifier prefix for the named pipes to be constructed. The client will read and write to the respective pipes that are post fixed with _RD and _WR.

This process will be responsible for creating the separate client handler daemons responding to each client as a separate process. These processes will need to listen to all messages sent from the client and write to back to the client and any other client’s named pipe to relay messages from client to others.

The global event pipe goes by the name gevent, this pipe should only be read by the global process but can be written to by any other process.

Client-Handler

A client-handler is spawned when a client is connected, a client-handler will be relegated to a specific domain. A domain is simply a folder relative to the current working directory.

The Protocol

The system uses a binary message protocol to facilitate communication between the server, client-handler and client. The server and client interaction is simply for acknowledgement and setting up the named pipes. The main protocol will be used between the client-handler and the client. The client-handler is spawned by the global server process to handle a client and will communicate with the client.

The binary message is broken up two parts, the first part being the type of message and the second being contents related to the type. The type will determine how to interpret the contents in the second part. Each message is 2048 bytes.

Under each message type in the following sections, the binary representation will be presented. The type is at the start of the message and is 2 bytes in size.

Anatomy of a message:

+————-+———————+

|type: 2 bytes| contents: 2046 bytes|

+————-+———————+

GlobalProcess-Client Protocol

CONNECT &lt;identifier&gt; &lt;domain&gt;

Type Decimal: 0

Type Binary: 00000000 00000000

The client will connect to the server, the server will construct two named pipes the identifier. The client is expected to connect to the named pipes after sending a well formed connect message to the server.

The identifier part of the message is maximum 256 characters ASCII encoded. The domain component will map to a folder relative to the current working directory.

ClientHandler-Client Protocol

SAY &lt;message&gt;

Type Decimal: 1

Type Binary: 00000000 00000001

Packet Layout:

Type: 2bytes

Message: 1790bytes, ASCII characters

The client will send the SAY command to the client-handler, the client-handler will need to relay this to all other clients that are connected to same domain using the RECEIVE message. The contents maximum is 1790 characters.

SAYCONT &lt;message&gt; &lt;termination&gt;

Type Decimal: 2

Type Binary: 00000000 00000010

Packet Layout:

Type: 2bytes

Message: 1789bytes, ASCII characters

Termination: 1byte, 255 indicates termination

The client will send the SAYCONT command to the client-handler, this is a variation on SAY in which the server will relay the message as a RECVCONT. SAY command typically sends one message within 2046 bytes of its message contents. SAYCONT reserves the 2046th byte as a termination byte for the message’s contents, when the termination byte represents the value 255, the message is considered complete. The maximum message is 1789 characters.

The buffering of the SAYCONT messages will occur on client side. Note this detail when testing your code.

RECEIVE &lt;identifier&gt; &lt;message&gt;

Type Decimal: 3

Type Binary: 00000000 00000011

Packet Layout:

Type: 2bytes

Identifier: 256bytes

Message: 1790bytes

This message is sent from the client-handler to all other clients (excludes sender). When a client has sent a SAY message to the client-handler, the client-handler relays the message along with the identifier to all other clients in the domain. The contents (2046 bytes) where the first 256 bytes are reserved for the identifier and the 1790 bytes afterwards is the message.

RECVCONT &lt;identifier&gt; &lt;message&gt; &lt;termination&gt;

Type Decimal: 4

Type Binary: 00000000 00000100

Packet Layout:

Type: 2bytes

Identifier: 256bytes

Message: 1789bytes Termination: 1byte

Similar to SAYCONT, the client handler will be sending the message in chunks to the client. The message will contain an identifier (who sent it) and send termination byte.

The buffering of the RECVCONT messages will occur on client side. Note this detail when testing.

DISCONNECT

Type Decimal: 7

Type Binary: 00000000 00000111

Packet Layout:

Type: 2bytes

This message is sent from the client to the client-handler. This will tell the client-handler that the FIFOs can be removed and the handler can be terminated.

Extension

PING

Type Decimal: 5

Type Binary: 00000000 00000101

Packet Layout:

Type: 2bytes

The PING message is sent from the client-handler to the client. This is to check that the client is still alive in the event the process crashed. This extension requires some form of asynchronous IO to be implemented. The PING message is sent every 15 seconds from the server.

PONG

Type Decimal: 6

Type Binary: 00000000 00000110

Packet Layout:

Type: 2bytes

The PONG message is sent from the client to the client-handler. This is the response to the PING message being sent from the server to check if it is still alive.

Daemon Alive

Each client-handler will send a signal to the global process under SIGUSR1 to indicate that it is shutting down. The global process can use this information, to clean up the process before the child becomes a zombie process.

As an extension, you are required to implement PING and PONG messages that will check that the client is still alive. Every 15 seconds, the client-handler will send a PING message to a client, requiring the client to respond to the message. with PONG.
