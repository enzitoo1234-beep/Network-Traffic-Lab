# Network-Traffic-Lab
Local HTTP Network Traffic Lab
A simple, interactive C# Windows Forms application built to demonstrate network protocols and packet analysis. The app sets up a local web server that sends and receives unencrypted HTTP traffic, providing a safe sandbox environment to learn how to capture and read data packets using Wireshark.

Features
Local Web Server: Runs an HttpListener directly on http://127.0.0.1:8080/ without needing external hosting or an internet connection.

Multi-Threaded: Uses asynchronous background tasks (Task.Run) to handle incoming network connections without freezing the desktop window.

Interactive UI & Web Dashboard: Hosts a styled HTML page with a functional message submission form and a live logging text box on the desktop app.

Dynamic Route Testing: Includes a random link generator that spits out unique URL paths (like /secret_page or /flag_captured) so you can watch how browsers request different resources.

Plain-Text Traffic: Uses standard HTTP instead of HTTPS so you can inspect raw network payloads, headers, and form inputs.

Setup & Walkthrough
1. Fire up the Server
Open the project in Visual Studio, hit F5 to compile, and click the Start Server button.

2. Configure Wireshark
Open Wireshark and choose your local loopback interface (usually listed as Adapter for loopback traffic capture or Npcap Loopback Adapter). In the display filter bar at the top, type http and press Enter to filter out background system noise.

3. Generate Traffic
Open your browser and navigate to http://127.0.0.1:8080/.

Testing GET Requests: Click the green Go to Random Link button. You'll see the browser jump to a new URL, and the specific path (e.g., GET /lab_test) will show up in Wireshark's Info column.

Testing POST Requests: Type a message into the text box and click submit. Find the POST packet in Wireshark, look at the middle pane, and expand "HTML Form URL Encoded" to see your exact message sitting in plain text.

Use Case
This project is a practical tool for learning Layer 7 (Application Layer) networking. By intentionally leaving the traffic unencrypted, it shows the exact mechanics behind browser headers, GET vs POST methods, and the loopback address. It also perfectly illustrates why modern web security relies so heavily on HTTPS to protect data from being read over the wire.
