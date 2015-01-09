# Preface
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119.
# Simulation Control
If an object need to check with the time during the simulation, it MUST register with org.leolo.netsim.core.SimulationController and implemnets org.leolo.netsim.core.TimeEvent

The smallest unit of control is 10picosecond, and ALL time related variable that SHOULD be 64-bit signed integer (long)
# Passing data
Any data passing though different part of the OSI model should done though passing a bit stream. The extract method for the implemention is yet to decide.
