## Command
`nmap -f <target>`

## Related commands
```
nmap --script path-mtu <target>
nmap -mtu <size #> <target>
```

**What is fragmentation?**
Fragmentation is a process of dividing a packet into smaller packets (fragments) because a network won’t accept packets that come in larger size than its Maximum Transmission Unit (MTU). 
For example, if the MTU size for a network’s ethernet is 1500 bytes, and a packet is 4000 bytes, the packet will be divided into smaller packets before being sent over the ethernet. 
Inside an IP address structure, there are 3 things that deal with fragmentation.
- Identifier – All fragments carry the same ID.
- Flags – All fragments have ‘1’ as their flags, except the last fragment will be set to ‘0’.
- Fragment offset – This information is used to reassemble the data from all the fragments (whether they arrive in order or not).

The packets will travel through router(s), and when they arrive to their destination host, they will be then reassembled back to the original packet.

When we are performing nmap scans, we are not worried about MTU because the size of fragments via nmap are small enough to fit in a normal MTU. What concerns us is the firewall/IDS on our target machine. They have packet filtering rules that would block us from sending scan packets. 
