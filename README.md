# remote-cat
An TFTP based client to read and display the contents of a remote file on the local system's STDOUT.

## Introduction
TFTP is a simple file transfer protocol that uses UDP as its underlying protocol and enables a client to fetch a file from a remote server (host where TFTP is installed). It is designed to be small and easy to implement. Therefore, it lacks most of the features of a regular FTP. The only thing it can do is read and write files (or mail) from/to a remote server. Hence, we are going to use this property to our advantage and transfer files from servers and render the data on local STDOUT.

+ A client initiates a transfer by issuing a read request to read a file from a remote server. 
+ The server on accepting the request sends the file in fixed block lengths usually within a single IP packet. 
+ The client on receiving the packet must send an ACK before it can receive another block. 
+ The server sends numbered packets to the client and the client replies with the ACKs. 
+ The final data packet should contain less than full sized block to indicate that it is the final block.

## Architecture

    remcat Client --------------->  TFTP Server (file.txt)
                    RRQ                                           


    remcat Client <---------------  TFTP Server (file.txt)
     [STDOUT]         DAT (TFTP)                                
                       

    


## Usage
    user@system:~ remcat hostname file.txt                  
    
## References
RFC1350 details: https://www.ietf.org/rfc/rfc1350.txt
