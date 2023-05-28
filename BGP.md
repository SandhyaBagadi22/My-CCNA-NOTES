# BGP States

![Link to public website (catchpoint)](https://www.catchpoint.com/bgp-monitoring/bgp-states)

- Idle.
- Connect.
- Active.
- OpenSent.
- OpenConfirm.
- Established.

# BGP Message Types

BGP uses different types of messages to form neighbor-ship and exchange routes, checking if the remote BGP neighbor is still there and/or notifying the remote side if any errors occur.

In-order to do this, BGP uses 4 types of messages:

Open message
Update message
Notification message
Keepalive message

## Common Header

<img width="231" alt="cm" src="https://github.com/SandhyaBagadi22/My-CCNA-NOTES/assets/110488017/bf65fd18-333d-496c-842f-c25b88018b96">

- Marker - All 1's (for sync and auth/security)
- Length - Length of entire BGP message
- Type field - indicates type of the message

## Open Message

![image](https://github.com/SandhyaBagadi22/My-CCNA-NOTES/assets/110488017/2bd123fc-b2f0-4530-8470-f725544de707)

- As - usefull for ibgp or ebgp diff
- Holdtime - atleast 3 secs, the value is chosen between the locally proposed and remote device, whichever is smaller.
- BGP identifier - BGP router ID

## Update Message

![image](https://github.com/SandhyaBagadi22/My-CCNA-NOTES/assets/110488017/220d0765-4c84-424e-8bd2-f7b5a1e7edbf)

Once two routers have become BGP neighbors, they can start exchanging routing information. This is done with the update message. In the update message you will find information about the prefixes that are advertised.In “BGP language” a prefix is referred to as NLRI (Network Layer Reachability Information). Here are some of the things you will find in an update message:

- Withdrawn Route Length: this field shows the length of the Withdrawn Routes field in bytes. When it is set to 0, there are no routes withdrawn and the Withdrawn Routes field will not show up.
- Withdrawn Routes: this field shows all the prefixes that should be removed from the BGP table.
- Total Path Attribute Length: here you will find the total length of the Path Attributes field.
- Path Attributes: the BGP attributes for the prefix are stored here, for example: origin, as_path, next_hop, med, local preference, etc. These path attributes are stored in TLV-format (Type, Length, Value).

Each of the BGP attributes also has an attribute flag that tells the BGP router how to treat the attribute. Here are the different bit flags:

- Optional: when the attribute is well-known this bit is set to 0, when its optional it is set to 1.
- Transitive: when an optional attribute is non-transitive this bit is set to 0, when it is transitive it is set to 1.
- Partial: when an optional attribute is complete this bit is set to 0, when it’s partial it is set to 1.
- Extended Length: when the attribute length is 1 octet it is set to 0, for 2 octets it is set to 1. This extended length flag may only be used if the length of the attribute value is greater than 255 octets.

## NOTIFICATION Message

<img width="340" alt="not" src="https://github.com/SandhyaBagadi22/My-CCNA-NOTES/assets/110488017/e9cdf980-9bef-4824-9267-fe0be6a73d33">

A Notification message is sent when an error is detected with the BGP session, such as a hold timer expiring, neighbor capabilities change, or a BGP session reset is requested. This causes the BGP connection to close.

## Keep Alive

BGP does not rely on the TCP connection state to ensure that the neighbors are still alive. Keepalive messages are exchanged every one-third of the Hold Timer agreed upon between the two BGP routers. Cisco devices have a default Hold Time of 180 seconds, so the default Keepalive interval is 60 seconds. If the Hold Time is set for zero, no Keepalive messages are sent between the BGP neighbors.
