[Back to Portfolio](./)

Project 3 Air Drop
===============

-   **Class:** CSCI 332
-   **Grade:** 97 (A)
-   **Language(s):** C ++
-   **Source Code Repository:** [features/mastering-markdown](https://guides.github.com/features/mastering-markdown/)  
    (Please [email me](mailto:bjcooper2@csustudent.net?subject=GitHub%20Access) to request access.)

## Project description

This group project, “Air Drop”, implements a simple reliable file transfer application over UDP sockets using C++ on Linux/Ubuntu. The goal is to practice C++ syntax, network programming with UDP, and basic reliability mechanisms on top of an unreliable protocol.

The system is split into two programs:

Client (Timmy’s Client) – reads a file from disk, breaks it into chunks, wraps each chunk in a small custom protocol (“Data” / “Done”), and sends the packets to the server using UDP. 

Server (Brandon’s Server) – listens on a UDP port, receives the packets, reconstructs the original file, and writes it out with the extension

Protocol Overview

Each application-level packet uses the following simple format: 

First 4 bytes: Type

"Data" – indicates that the packet contains file data.

"Done" – indicates the end of the transmission.

Remaining bytes (for Data packets): Raw file data.

The client:

1. Sends the filename first.

2. Reads the file in 1000-byte chunks into a buffer.

3. Builds a packet by copying "Data" into the first 4 bytes, followed by the 1000 bytes (or fewer for the last chunk) of file data. 

4. Sends the packet to the server and waits for a small acknowledgment (the first 4 bytes echoed back).


After the entire file has been sent, the client sends a final "Done" packet and waits for the final acknowledgment, then closes the connection. 



The server:

1. Receives the initial filename and opens a new output file named <filename>.received in binary append mode. 

2. For each packet:

     If the first 4 bytes are "Data", it writes the remaining bytes to the file, and sends an acknowledgment by echoing the first 4 bytes back to the client.

     If the first 4 bytes are "Done", it sends back "Done" as acknowledgment and terminates the loop. 


This forms a simple stop-and-wait protocol on top of UDP: the client sends one packet and waits for an acknowledgment before sending the next, which adds reliability to UDP’s best-effort delivery.

## How to compile and run the program

Protocol Overview

Each application-level packet uses the following simple format: 

Final Project Air Drop(1)

First 4 bytes: Type

"Data" – indicates that the packet contains file data.

"Done" – indicates the end of the transmission.

Remaining bytes (for Data packets): Raw file data.

The client:

Sends the filename first.

Reads the file in 1000-byte chunks into a buffer.

Builds a packet by copying "Data" into the first 4 bytes, followed by the 1000 bytes (or fewer for the last chunk) of file data. 

Timmyclient

Sends the packet to the server and waits for a small acknowledgment (the first 4 bytes echoed back).

After the entire file has been sent, the client sends a final "Done" packet and waits for the final acknowledgment, then closes the connection. 

Timmyclient

The server:

Receives the initial filename and opens a new output file named <filename>.received in binary append mode. 

Brandon_Server_2

For each packet:

If the first 4 bytes are "Data", it writes the remaining bytes to the file, and sends an acknowledgment by echoing the first 4 bytes back to the client.

If the first 4 bytes are "Done", it sends back "Done" as acknowledgment and terminates the loop. 



This forms a simple stop-and-wait protocol on top of UDP: the client sends one packet and waits for an acknowledgment before sending the next, which adds reliability to UDP’s best-effort delivery.

## How to Run the Program

Prerequisites

Ubuntu / Linux  VM environment. Ensure that you are on the same network

g++ (C++ compiler) installed.

The files: Timmyclient.cpp(client), Brandon_Server_2.cpp(server), Honey_Applecrisp.jpg (transfer file)

Step 1 – Compile

Open a terminal in the directory containing the .cpp files and run:

```
g++ -o server Brandon_Server_2.cpp
g++ -o client Timmyclient.cpp
```

This produces two executables: server and client .out files

Step 2 – Start the Server

In Terminal 1:
Navigate to the directory of your compiled "server" file

```
./Brandon_Server_2.out
```
You will see the prompt to enter the listening port

```
Please enter the listening port:
```

Enter the UDP port you want the server to listen on and press Enter. The server will then display the following message:

```
Listening on UDP port 12345 — waiting for first packet…
```
Step 3 – Start the Client

In Terminal 2:
Navigate to the directory of your compiled "client" file

```
./Timmyclient.out
```

The client will prompt you for:

 1. Server Address
  ```
  Timmy;s Client - Please enter the server Address:
  ```
 
 Enter the server’s IP address.
 
 2. Server Port
  ```
  Timmy's Client - Please enter the server port:
  ```
 Enter the same port you entered on the server    
 
 3. File Name
 ```
 Timmy's Client - Please enter the file name:
 ```
 Type the name of an existing file in the current directory (Honey_applecrisp.jpg)

The client will:

Open the file in binary mode.

Send the filename to the server.

Begin sending "Data" packets and waiting for acknowledgments.

Finally send a "Done" packet and print:

```
Timmy's Client - File transfer complete.
```
Step 4 – Check the Result on the Server

The server saves the incoming data as a new file named:

```
<Honey_Applecrisp>.received
```
On the server terminal, you’ll see log output:

```
Brandon's Project Received Filename: test.jpg
Brandon's Project Filename to be saved: test.jpg.received
Brandon's Project Received 1000 bytes
Brandon's Project Received 1000 bytes
...
Brandon's Project Transfer complete.

```


## UI Design

This project uses a text-based console UI. There is no graphical interface; instead, user interaction happens entirely through terminal input and status messages.

Client UI (Timmy’s Client)

Main behaviors: 

Timmyclient

Input Prompts

Prompts user for the server IP address:

"Timmy's Client - Please enter the server Address:"

Prompts user for the server port:

"Timmy's Client - Please enter the server port:"

Prompts user for the file name to send:

"Timmy's Client - Please enter the file name:"

File Transfer Feedback

If the file cannot be opened, the client prints an error using perror (e.g., "Timmy's Client - Error opening file!") and exits.

For each successful data packet, the client prints:

"Timmy's Client - Sent Data"

After the final "Done" acknowledgment, it prints:

"Timmy's Client - File transfer complete."

Behind the Scenes

Reads 1000-byte chunks from the file into a buffer.

Constructs packets with "Data" or "Done" headers.

Sends a packet and waits for a 4-byte acknowledgment before sending the next, providing simple reliability over UDP.

Server UI (Brandon’s Server)

Main behaviors: 

Brandon_Server_2

Startup Prompt

Asks:

"Please enter the listening port:"

After binding the socket, shows that it is listening:

"Listening on UDP port <port> — waiting for first packet…"

Filename Handling

When the first packet (filename) is received, the server prints:

"Brandon's Project Received Filename: <name>"

"Brandon's Project Filename to be saved: <name>.received"

Data Reception Feedback

For each data packet:

Writes the payload to the output file.

Prints a message like:

"Brandon's Project Received <N> bytes"

Sends a 4-byte acknowledgment ("Data") back to the client.

When it receives a "Done" packet:

Prints:

"Brandon's Project Transfer complete."

Sends back "Done" and then exits the loop.

Output File Design

The .received suffix clearly distinguishes the received copy from the original file name.

The server uses binary append mode ("ab") so any binary content (images, PDFs, etc.) is preserved correctly.


<div class="video-wrapper">
  <iframe
    width="560"
    height="315"
    src="https://www.youtube.com/embed/ztwCs3WP70g"
    title="Air Drop over UDP team project"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
    allowfullscreen>
  </iframe>
</div>


[Back to Portfolio](./)
