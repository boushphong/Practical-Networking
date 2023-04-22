# Layer 1 - Physical - Transporting Bits
- Computer data exists in the form of Bits (1's and 0's)
- Something has to transport those bits between `Hosts`
- L1 Technologies: Cables, Wifi, Repeaters, Hubs

# Layer 2 - Data Link - Hop to Hop
- Interacts with the Wire (i.e., Physical layer)
  - NIC - Network INterface Cards / Wi-Fi Access Cards
- Addressing Scheme - MAC addresses
  - 48 bits, represented as 12 hex digits
  - Every `NIC` has a unique MAC address, These MAC addresses allow data to go from one `NIC` to another (one Hop to the next)
L2 Technogies: NICs, Switches
- Often communication between hosts require multiple hops

![image](https://user-images.githubusercontent.com/59940078/233783494-340e75bb-091a-4468-8cfe-bc5ee9e4593e.png)

# Layer 3 - Network - End to End
- Addressing Scheme - IP addresses
  - 32 bits, represented as 4 octets, each 0-255
L3 Technologies: Routers, Hosts, (anything with an IP)

![image](https://user-images.githubusercontent.com/59940078/233783621-5db620b2-6ccc-49a9-946e-90a822f76508.png)

We need both IP and MAC because IP is for End to End delivery. But during the hop, the client needs to know which Router it has to send data to from each hop.
1. Client initiates end to end delivery, add extra header information containing the `Source IP` and `Destination IP` to the package.
2. It then needs to know which router it has to send data to first. Then it adds another extra header information contaning its `MAC` and the router's `MAC`
3. Once the package reaches the first router, it deletes the header info of the last hop, and add a new one containing the router `MAC` and the next router's `MAC` for the hop
4. The hop will resolves until the last router's hop with the header of it's `MAC` and the destination PC's `MAC`.
5. Once the package reaches the destination, all the Layer's header can be removed. (`Layer 2` will be removed first then `Layer 3`)

**NOTE:** The `Source IP` and `Destination IP` retain during all the hops.
