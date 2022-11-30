<h1>Basic LabView program to send and receive data for one sensor over TCP</h1>

<h2>This program involves two VIs, the Send.vi and Read.vi</h2>
<h3>Send.vi</h3>
<ul>
    <l1>This program involves a TCP open connection node, two TCP write nodes, and a TCP close connection node</l1>
    <l1>All timeout values are set to -1 so it doesn't timeout</l1>
    <l1>The TCP open connection node is initialized with a PORT value</l1>
    <li>The error and the connection are passed into the while loop, which iterates once per second</li>
    <li> Inside the loop, the program first attempts to receive a packet that is 1 byte in size (4 bits, 0-15)</li>
    <li>First, the thermometer data is converted to a string</li>
    <li>the length of the string is then converted to a string and is sent out preliminarily</li>
    <li>The thermometer string data is then sent out on the port</li>
    <li>This continues until the stop is called, at which time the connection is closed and any error is passed</li>
</ul>

<h3>Read.vi</h3>
<ul>
    <l1>This program involves a TCP Listener node, two TCP read nodes, and a TCP close connection node</l1>
    <l1>All timeout values are set to -1 so it doesn't timeout</l1>
    <l1>The TCP listener node is initialized with a PORT value and with a blank string converted to an ip, which returns the local machine ip.</l1>
    <li>The error and the connection are passed into the while loop, which iterates once per second</li>
    <li> Inside the loop, the program first attempts to receive a packet that is 1 byte in size (4 bits, 0-15)</li>
    <li>After the length data is received, the length is converted to an int and passed to the next receive node where the actual data is received</li>
    <li>The String is converted to a number and the thermometer is set to the value</li>
    <li>This continues until the stop is called, at which time the connection is closed and any error is passed</li>
</ul>