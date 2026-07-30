# Lessons Learned
## 1. Different subnets do not automatically provide complete network isolation

Creating a separate subnet (192.168.200.0/24) successfully separated the addressing space from the main home network (192.168.100.0/24). However, this alone did not guarantee complete isolation between both environments.

## 2. NAT is not a firewall

Although the AirPort performed Network Address Translation (NAT), it did not enforce security policies between the home network and the laboratory network. NAT changes how traffic is routed but should not be considered a replacement for a firewall.

## 3. Communication direction matters

Traffic behavior was asymmetric. Devices inside the laboratory network could initiate outbound connections, while devices in the main home network could not directly initiate communication toward the laboratory subnet without additional routing.

Understanding the direction of communication is essential when designing secure networks.

## 4. Ping is not always a reliable security test

Initial ICMP tests suggested that devices were isolated. Later testing revealed that Windows Firewall was blocking ICMP Echo Requests, demonstrating that host firewalls can influence connectivity tests.

Network validation should include multiple testing methods rather than relying solely on ping.

## 5. Double NAT can be useful in a laboratory

Although Double NAT is often discouraged in production environments, it provided a practical opportunity to understand how multiple routers interact and how NAT affects routing behavior.

## 6. Documentation is part of the learning process

Documenting the network topology, configuration steps, and test results made it easier to understand the environment and identify incorrect assumptions during troubleshooting.

## 7. Older hardware can still provide educational value

An older Apple AirPort Extreme A1521 proved sufficient for learning core networking concepts such as DHCP, NAT, routing, wireless security, and network design without requiring additional hardware.

# Future Improvements
- Replace the AirPort routing functionality with pfSense.
- Configure the AirPort as a wireless Access Point.
- Implement firewall rules to control traffic between networks.
- Create separate VLANs for different laboratory scenarios.
- Deploy IDS/IPS solutions such as Suricata or Snort.
- Centralize logging and network monitoring.
- Document security policies and network diagrams.
