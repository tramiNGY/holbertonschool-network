
# What happens when...

Explaining what happens when you type https://www.google.com in your browser and press Enter.

## DNS request
**Step 1: Typing https://www.google.com in browser**

When typing in web browser https://www.google.com, you need to convert this human-readable domain into a machine-readable value. This is what DNS (Domain Name System) does.

**Step 2: DNS getting IP address**

If not in DNS cache, the computer will ask DNS resolver, searching first TLD (Top-Level Domain) here, .com, and finally get DNS server IP for google.com and return IP: 142.250.64.78

The computer now knows where to send the request.

## TCP/IP
**Step 3: Transmission protocole TCP/IP**

TCP/IP stands for Transmission Control Protocol/INternet Protocol, it is a set of communication protocols to define how data is transmitted over the internet.
- Upon receiving the HTTPS request, it is passed to TCP which breaks it down into packets, each having a sequence number and hands them to IP.
- IP adds source and destination IP address and routes them accross networks.
- The Link Layer uses Ethernet/Wi-FI to send the packets physically to arrive at Google's server.


## Firewall
**Step 4: Firewall filter**

A Firewall manages traffic passing beween two networks based on preconfigured rules analysing data packets that request entry to the network.

The browser tries to establish a TCP connection to Google's IP address on port 443 (for HTTPS).

When passing through the firewall, packets are inspected for malicious behavior or unauthorzied ports. If the firewall rules allow the traffic, it passes through. Here port 443 is allowed so the request is sent to Google's servers.


## HTTPS/SSL
**Step 5: HTTPS/SSL Encrypted Session**

HTTPS stnds for Hypertext Transfer Protocole Secure. It is the secure version of HTTP which means all data exchanged is encrypted. HTTPS uses SSL (Secure Sockets Layer) to protect data in transit.
After TCP connection:

- Browser sends a ClientHello to Google (ex: SSL version list)
- Google's server responds with a ServerHello (chosen TLS version, SSL certificate)
- Browser verifies Google's certificate using Certificate Authorities (CAs), if it is valid, unexpired and correctly issued for www.google.com
- Browser generates session's key encrypted using Google's public key and sends it to Google to compute the same session key
- Both send a finished message encrypted with the session key. The encrypted and secure HTTPS session begins.

Now that the HTTPS session is established, the brows actually sends the HTTPS request over SSL.

## Load-balancer
**Step 6: Traffic distribution**

A load balancer distributes traffic (incoming internet requests) efficiently so no single server is overloaded. It is in front of a group of servers and decides which server should handle each request. 

It can use algorithms like Round Robin (send each new request to the next server in line).

## Web server
**Step 7: Static Content**

A Web Server is a program (or device) that handles HTTP(S) reuqests and is responsible for serving static content (HTML/CSS, images) which can be found in its local or network storage and can be sent back directy to browser.

Here the Google logo, layout and styling are static assets.

If the request is not only static and more complex it will forward the request to the Application Server.

## Application server
**Step 8: Dynamic content**

An Application server handles Business Logic and interacts with the database. It generates dynamic content. 

If the user is signed into Google, the search page might show a profile picture, pre-load search suggestions or recent activities. This requires application server and database access.

The application server will for instance calculate research suggestions base on history, interests etc..., check user's authentification and rights.

## Database
**Step 9: Database**

A Database is a system to store, orgnaize and manage data. Those data can be user's information, preferences, research results, history etc..

When the application server needs to access or modify information, it connects to the database and send query (ex SQL). 

## Way back to browser
**Step 10: Request's response**
- The database then proceeds the request and returns it to the app server.
- The app server receives data and use it to personnalize the page,
- Once the data is treated, the result is sent back to the web server,
- the web server will send information to the browser for displaying the page.
