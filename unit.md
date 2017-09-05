# Units #
A Unit is our most generic model. The idea is to let our customers decide; what do I need to model this time / in this case?

The most common usage is when a Unit are used to model a SMS- or Email-receiver. The reasons this is so common dates back to the legacy system that MobileResponse is replacing and most processes were centered around sending and receiving messages with humans. Nowadays more and more processes use units as representation for some more abstract models. Some examples of how units are used without acting as a recipient of messages:

 - A First come, first served (1) – workflow, can use units to represent the state and results for each round.
 - When IOT (Internet Of Things) – devices communicates with workflow, a unit might represent the current state of the device, current battery-status, current temperature in the room.

Units have phone, email and IOT (which is actually MQTT) endpoints. In most cases one or more of the communication channels are used, but in some cases (like first example given in listing above) we won’t need any communication channels configured for the unit. We will not be sending messages to that unit.

>   1) Typical workflow that solves a case where the employer need more workers for next shift, send a question/message to off-duty personal and the first to answer will be offered extra work for the next shift.


