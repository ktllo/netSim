# Preface
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).
# Simulation Control
## Time Control
If an object need to check with the time during the simulation, it MUST register with org.leolo.netsim.core.SimulationController and implemnets org.leolo.netsim.core.TimeEvent

The smallest unit of control is 1 nanosecond(tick), and ALL time related variable that SHOULD be 64-bit signed integer (long)

The controller MAY use multiple thread to process the TimeEvent across different element
## Passing data
Any data passing though different part of the OSI model should done though passing a bit stream. The bit stream should be put in a list and be processed at next tick. When the next layer cannot process more than 1 item at a time, the bit stream SHOULD be a queue,and MUST be thread safe.
## Simulation across machine
There are 2 mode of simulation, synchronized and asynchronize. 

Asynchronize mode will not synchronize the clock among different machine. Each link required their own port.

Synchronized mode are reuired to synchronized their clock every 10000 ticks. Slave are required to notify the master that they have finished that 10000ticks, and the slave has to wait the master told them to continue. This will requires an extra TCP port.

The simulation across machine are intended to designed as a unreliable link, if reliable link is required, it should be supported by the upper layer(Even simulation of OSI layer 1)

User are free to select the port number to be used for data. Synchronized data use a specific port, which is yet to be decided.
### MTU for Simulation across machine
MTU for simulation  across machine is 65507 bytes, including ALL headers. Although this number may be reduced due to the implemention of Java
### Datagram format(Payload)
We just load the uplayer data as the UDP payload. No additional header is included.


