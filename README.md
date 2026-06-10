# Network-Traffic-Lab
Network-Traffic-Lab
A simple, interactive C# Windows Forms application built to demonstrate network protocols and packet analysis. The app sets up a local web server that sends and receives unencrypted HTTP traffic, providing a safe sandbox environment to learn how to capture and read data packets using Wireshark.

Features
Dynamic Local Web Server: Runs an HttpListener on a randomly generated port (between 8000 and 8100) every time you start it. This lets you see how changing port numbers changes the socket configuration in your network traffic.

Multi-Threaded: Uses asynchronous background tasks (Task.Run) to handle incoming network connections without freezing the desktop application window.

Interactive Responsive Dashboard: Hosts a beautifully styled, card-based HTML grid dashboard that automatically stays synchronized with whatever random port the server is currently running on.

Live Traffic Capturing & Logging: Safe multi-threaded UI bridging (InvokeRequired) to print network request statuses, query strings, and custom form inputs directly inside the desktop application window in real-time.

Setup & Walkthrough
1. Fire up the Server
Open the project in Visual Studio, hit F5 to compile, and click the Start Server button. Look at the application log box to see which random port your server chose (for example: http://127.0.0.1:8042/).

2. Configure Wireshark
Open Wireshark and choose your local loopback interface (usually listed as Adapter for loopback traffic capture or Npcap Loopback Adapter). In the display filter bar at the top, type http and press Enter to filter out background system noise.

3. Generate and Analyze Traffic
Open your browser and navigate to the random link shown in your app's log box.

Testing GET Requests (Card 1): Click the green Go to Random Link button. The server will scramble a brand new path extension (like /secret_page or /flag_captured). In Wireshark, watch how the GET request updates dynamically on your active port.

Testing POST Requests (Card 2): Type a custom message into the text box and click Send Message. Find the corresponding POST packet in Wireshark, look at the middle pane, and expand "HTML Form URL Encoded" to see your exact text traveling over the wire.

Testing Credential Exposure (Card 3): Type a dummy username and password into the simulator card and click login. Because this lab uses plain HTTP, you can instantly find your raw credentials completely unencrypted inside the Wireshark packet payload!

Testing Status Codes (Card 4): Click any of the error response buttons (403, 404, or 500). Look at Wireshark’s Status column to observe how web servers communicate back different state conditions to a browser.

Use Case
This project is a practical tool for learning Layer 7 (Application Layer) networking. By intentionally leaving the traffic unencrypted and randomizing the ports, it shows the exact mechanics behind browser headers, GET vs POST methods, dynamic sockets, and server response codes. It also perfectly illustrates a core cybersecurity lesson: why modern web security relies so heavily on HTTPS to protect data from being read in plain text.
