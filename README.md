# TCP_IP_traffic_analysis: Analyzing Local Network Traffic with Wireshark and Scapy

**1. Installing Wireshark:**

Before you start capturing network traffic, you need to install Wireshark on your system. You can download Wireshark from the official website: [Wireshark Download Page](https://www.wireshark.org/download.html). Follow the installation instructions provided for your operating system.

**2. Capturing Local Network Traffic:**

Once Wireshark is installed, you can use it to capture local network traffic. Open Wireshark and select the network interface corresponding to your local network connection (e.g., Wi-Fi). Click on the interface to start capturing packets.

**3. Saving the Capture File:**

After capturing the desired network traffic, you can save the capture file for further analysis. Go to `File` > `Save As` and choose a location to save the capture file. It's recommended to save the capture file in the `.pcap` format, which is a standard format for packet capture files.

**4. Analyzing the Capture File with Python and Scapy:**

Once you have saved the capture file, you can analyze it using Python and Scapy. Scapy is a powerful packet manipulation tool that allows you to work with captured packets programmatically.

**5. Loading the Capture File in Python:**

In your Python environment, you can use Scapy to load the capture file and analyze the captured packets. Here's a basic example of how to load the capture file and perform analysis:

```python
from scapy.all import *

# Load the capture file
packets = rdpcap('capture.pcap')

# Analyze the captured packets
# Example: Print summary information of the first 10 packets
print("Summary of the first 10 packets:")
print(packets.summary())

# Further analysis and visualization can be performed as needed
```

**6. Additional Analysis and Visualization:**

You can perform various types of analysis on the captured packets, such as extracting source/destination IP addresses, analyzing packet sizes, identifying communication patterns, etc. You can also visualize the data using libraries like NetworkX and Matplotlib.

**7. Plotting Network Graph:**

Here's an example of how to plot a network graph using NetworkX:

```python
import networkx as nx
import matplotlib.pyplot as plt

# Create an empty directed graph
G = nx.DiGraph()

# Extract source and destination IP addresses from packets
edges = [(pkt[IP].src, pkt[IP].dst) for pkt in packets if IP in pkt]

# Add edges to the graph
G.add_edges_from(edges)

# Plot the network graph
plt.figure(figsize=(10, 8))
nx.draw(G, with_labels=True, node_size=500, node_color='skyblue', font_size=10, edge_color='gray')
plt.title('Network Communication Graph')
plt.show()
```

This will create a network graph representing the communication between devices in the captured network traffic.

**8. Dependencies:**

Make sure you have the necessary dependencies installed in your Python environment, including Scapy, NetworkX, and Matplotlib. You can install them using `pip` if they are not already installed:

```
pip install scapy networkx matplotlib
```

**9. License:**

This project is licensed under the [MIT License](LICENSE). Feel free to use and modify it according to your needs.

**10. Acknowledgments:**

Special thanks to the developers of Wireshark, Scapy, NetworkX, and Matplotlib for providing the tools necessary for network traffic analysis and visualization.
