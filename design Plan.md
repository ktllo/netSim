# Preface
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.
# Simulation Control
## Time Control
If an object need to check with the time during the simulation, it MUST register with org.leolo.netsim.core.SimulationController and implemnets org.leolo.netsim.core.TimeEvent

The smallest unit of control is 10picosecond(tick), and ALL time related variable that SHOULD be 64-bit signed integer (long)

The controller MAY use multiple thread to process the TimeEvent across different element
## Passing data
Any data passing though different part of the OSI model should done though passing a bit stream. The bit stream should be put in a list and be processed at next tick. When the next layer cannot process more than 1 item at a time, the bit stream SHOULD be a queue,and MUST be thread safe.
## Simulation across machine
Simulation across different machine will use a longer tick, which will be 10ms. The extract method is yet to decide but there SHOULD be master and slave machine, and they should be run in a synchronized way.
