# Equal-Cost Multi-Path Routing

In this exercise we will implement a layer 3 forwarding switch that is able to load balance traffic
towards a destination across equal cost paths. To load balance traffic across multiple ports we will implement ECMP (Equal-Cost
Multi-Path) routing. When a packet with multiple candidate paths arrives, our switch should assign the next-hop by hashing some fields from the
header and compute this hash value modulo the number of possible equal paths. For example in the topology below, when `s1` has to send
a packet to `h2`, the switch should determine the output port by computing: `hash(some-header-fields) mod 4`. To prevent out of order packets, ECMP hashing is done on a per-flow basis,
which means that all packets with the same source and destination IP addresses and the same source and destination
ports always hash to the same next hop.

<p align="center">
  <img src="https://github.com/nsg-ethz/p4-learning/blob/master/exercises/05-ECMP/images/multi_hop_topo.png" title="Multi Hop Topology"/>
<p/>

To read more about ECMP see the following [page](https://www.juniper.net/documentation/us/en/software/junos/flow-packet-processing/topics/topic-map/security-ecmp-flow-based-forwarding.html).
