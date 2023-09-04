# Capturing-Packets-with-Wireshark
In this guided project, I used Wireshark to capture packets on a specific interface and use filters to observe website traffic.
Here is the link to the post I made on LinkedIn: https://www.linkedin.com/posts/allon-ingram-0a0803226_completion-certificate-for-wireshark-for-activity-7095944502657351681-XkPi?utm_source=share&utm_medium=member_desktop
  Wireshark is a network protocol analyzer or in other words an application that captures packets from a network connection such as from your PC to the internet. A packet is basically a small piece of a bigger message and data sent over the internet are divided into packets. They are also the basic units of communication over a TCP/IP network.
    Wireshark is a powerful and widely used network protocol analyzer that allows Security(SOC) Analysts to capture and inspect nework packets in real time. Wireshark provides a detailed view of network traffic, allowing professionals to analyze, troubleshoot, and detect potential security threats. 
    
    Here are the steps I took for this guided project :
    
 Step 1 : Install and set up Wireshark on Ubuntu 
     To get the latest version of Wireshark on Ubuntu Linux, I used the add-apt-repository comand : sudo add-apt-repository ppa:wireshark-dev/stable.
     For security reasons you should not run Wireshark as superuser. 
     I then added a user to the Wireshark group to add packet captre capabilities: sudo usermod -aG wireshark $USER
     
 Step 2 : Start a packet capture on an ethernet port and save it to file
     The wired interface includes the ethernet packet capture,which begis with "en" in Wireshark. The Wireshark app also includes controls to start packet capture, stop capture, save the packets to a file, and load the capture files. A important feature to remember about Wireshark is that a capture can only be saved once the capture has stopped.
     
 Step 3 : Use a display filter to detect HTTPS packets:
       In Wireshark to view specific packets in an existing packet capture, use a display filter. 
        To display ONLY HTTPS TRAFFIC, use a filter on TCP port 443: tcp.port == 443
        
 Step 4 : Visi a web page and detect its IP Address using a display filter:
        A TLS Handshake display filter may be used to detect a website visit in a packet list: tls.handshake.type ==1. 
        For context, during a TLS Handshake two communicating sides exchange messages to acknowledge each other, verify each other, establish he crypotographic alogorithms tey will use and agree on session keys. It basicaly starts this secure communication session that uses the TLS encryption technique.
        Next, The IP address is used in a filter to obtain packet information for a particular website: ip.addr == 142.251.163.105
        
Step 5: Locate all HTPS packets from a capture not containing a certian IP Address: 
        A conditional statement may be used to include and eliminate packets from a wireshark capture" !(ip.adr == 8.43.85.97) and tcp.port == 443
        Lastly, A compound conditional shoudl include parentheses to avoid order of execution erors: !(ip.addr == 8.43.85.97) and (tcp.port == 80 or tcp.port == 443) 
      
