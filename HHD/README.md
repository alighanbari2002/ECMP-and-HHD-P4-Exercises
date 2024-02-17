# Heavy Hitter Detection

<p align="center">
  <img src="https://github.com/nsg-ethz/p4-learning/blob/master/exercises/06-Heavy_Hitter_Detector/images/heavy_hitter_topo.png" title="Small Topology"/>
<p/>

In this exercise we will play with probabilistic data structures. First we will implement very simple heavy hitter detector
using a counting bloom filter.
Heavy hitters can simply be defined as the traffic sources who send unusually large traffic.
This can be categorized solely by source IP address or can be classified to each application,
or application session that sends the traffic. To implement a bloom filter
we need registers and hash functions (to get indexes to the register). The counting bloom filter will allow us to perform heavy hitter
detection on `tcp` flows without using any controller.

The main idea behind a counting bloom filter is to compute multiple hashes of some header values (flow's 5-tuple) and increment the corresponding
indexes in the register structure. We can then check if a flow is in a bloom filter by checking if all the values are above a threshold. This method can suffer from hash collisions when there are too many heavy hitters for the filter to track. In this exercise we
will not create too many connections, so it should not be a problem.
