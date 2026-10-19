*This project has been created as part of the 42 curriculum by agomez-a.*

# NetPractice

## Description

NetPractice is a hands-on introduction to the basics of computer networking. The goal is to make small, simulated networks work by correctly configuring their parameters: IP addresses, subnet masks, routing tables and default gateways of hosts, routers and switches.

The project is delivered as a training web interface that runs locally. It contains **10 levels**. Each level shows a non-working network diagram and a list of goals (for example, "host A needs to communicate with host B"). Only the unshaded fields can be edited. The aim is to modify them until every goal is reported as `OK`.

The networks are simulated and fictitious; the addresses used are not connected to any real-world configuration.

Main skills practiced:

- Reading and writing IPv4 addresses and subnet masks, in dotted-decimal and CIDR (`/n`) notation.
- Working out the network address, broadcast address and usable host range of a subnet.
- Choosing the right IP for each interface so that devices on the same link share the same subnet.
- Writing routing tables, including the default route (`0.0.0.0/0`), so that packets can reach their destination **and** come back.
- Understanding the role of the default gateway, routers and switches.

## Instructions

### Running the training interface

1. Download the archive attached to the project page and extract it in any folder.
2. From that folder, run:

   ```bash
   ./run.sh
   ```

   This launches a local web server and opens your default browser on the training page.

3. If `run.sh` does not work, start the server manually and open the page yourself:

   ```bash
   python3 -m http.server 49242
   ```

   Then go to `http://localhost:49242` (the port number can be changed).

4. In the **Training** tab, enter your intranet login (this is required, because the evaluation uses it to know your configuration) and press **Start!**. The **Evaluation** tab generates a random configuration, suitable for practice before the defense.

### Solving a level

- Read the goals at the top of the page.
- Edit the unshaded fields (IP addresses, masks, routes).
- Press **Check again** to verify the configuration.
- Read the logs at the bottom of the page if a goal fails: they show where the packet was dropped (for example, "destination does not match any route").
- When all goals are `OK`, a **Next level** button appears.

### Exporting configurations

Before moving to the next level, press **Get my config** to download the configuration of the current level. Do this for each of the 10 levels.

### Submission requirements

- The repository must contain the **10 exported configuration files (one per level)** at its root.
- The login must have been entered in the interface before exporting.
- Only the content of the Git repository is evaluated during the defense.
- During the defense, three random levels must be completed in a limited amount of time, without external tools (a simple calculator such as `bc` is tolerated).

## Resources

### Networking concepts studied

- **TCP/IP addressing**: structure of IPv4 addresses, network part and host part, private address ranges.
- **Subnet masks**: dotted-decimal notation and CIDR prefix (for example, `255.255.255.128` = `/25`), network and broadcast addresses, number of usable hosts.
- **Default gateways**: the router interface a host sends packets to when the destination is outside its own subnet.
- **Routers and switches**: routers forward packets between different networks using routing tables; switches connect devices inside the same network.
- **Routing tables**: destination network, next hop, and the default route `0.0.0.0/0`.
- **OSI layers**: the layered model of networking, with focus on layer 2 (switching) and layer 3 (IP addressing and routing).

### References

- RFC 791 — Internet Protocol: https://www.rfc-editor.org/rfc/rfc791
- RFC 950 — Internet Standard Subnetting Procedure: https://www.rfc-editor.org/rfc/rfc950
- RFC 1918 — Address Allocation for Private Internets: https://www.rfc-editor.org/rfc/rfc1918
- RFC 4632 — Classless Inter-domain Routing (CIDR): https://www.rfc-editor.org/rfc/rfc4632

### Use of AI

AI  was used as a learning aid, not to replace understanding of the exercises:

- **Concept explanations**: understanding how to choose the destination of a route (including why `0.0.0.0/0` is used when a device must reach several different networks) and how to convert a subnet mask into CIDR notation by counting bits.
- **Documentation**: drafting the structure of this README from the project subject.
