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


- Marker - All 1's (for sync and auth/security)
- Length - Length of entire BGP message
- Type field - indicates type of the message

