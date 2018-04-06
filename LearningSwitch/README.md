# Layer 2 Learning Switch 


 The learning switch "brain" associated with a single OpenFlow switch.

 When we see a packet, we'd like to output it on a port which will
 eventually lead to the destination.  To accomplish this, we build a
 table that maps addresses to ports.

 We populate the table by observing traffic.  When we see a packet
 from some source coming from some port, we know that source is out
 that port.

 When we want to forward traffic, we look up the desintation in our
 table.  If we don't know the port, we simply send the message out
 all ports except the one it came in on.  (In the presence of loops,
 this is bad!).

 In short, our algorithm looks like this:

 For each packet from the switch:
 1) Use source address and switch port to update address/port table
 2) Is transparent = False and either Ethertype is LLDP or the packet's
    destination address is a Bridge Filtered address?
    Yes:
       2a) Drop packet -- don't forward link-local traffic (LLDP, 802.1x)
           DONE
 3) Is destination multicast?
    Yes:
       3a) Flood the packet
           DONE
 4) Port for destination address in our address/port table?
    No:
       4a) Flood the packet
           DONE
 5) Is output port the same as input port?
    Yes:
       5a) Drop packet and similar ones for a while
 6) Install flow table entry in the switch so that this
    flow goes out the appopriate port
    6a) Send the packet out appropriate port

 
 The working of the Python script is mentioned in comments of the script.

