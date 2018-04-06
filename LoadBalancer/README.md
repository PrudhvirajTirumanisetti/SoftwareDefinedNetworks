# SDN LOAD BALANCER

The Load Balancer is implemented in python using the Dijkstra Shortest Path Algorithm, Floodlight Controller is used for this project. The LoadBalancing increased the bandwith and the efficiency of the network by 300%. 

Getting Started with the Experiment:

1) First Run the mininet topology from the file Topology.py, this is run in the terminal window by using the following commans "$ Sudo mn --customn ~DIR/Topology.py --topo mytopo" / "$ sudo mn --controller=remote,ip=127.0.0.1,port=6633" for more examples using mininet please refer to the following link "http://mininet.org/walkthrough/".

2) Run the Load Balancer.py in the mininet window, check the terminal window for the stastics and use wirshark monitor on the loopback address.
