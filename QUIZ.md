### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?
The DevBoard handles received serial messages through callbacks. This allows the DevBoard to receive serial messages whenever it needs to rather than running in a constant loop, which is the naive approach. By utilizing this kind of procedure, the devboard only receives an input when it needs to, leading to better efficiency compared to constantly checking for an input.

### What does `detached_callback` do? What would happen if it wasn't used?
detached_callback creates a new detached thread everytime a function is called from a button being pressed. The benefit of this kind of decorator is that it allows every function called within it to be executed independently from the rest of the program. If it wasn't used, the UI would get stuck on any serial code that gets stuck or has a long runtime, hindering the performance of the UI.

### What does `LockedSerial` do? Why is it _necessary_?
LockedSerial prevents multiple threads from accessing the serial port at once. This is necessary because it prevents the serial port from receiving too much information. If the serial port were to have every thread trying to interact with it, the sequence of the program could go out of order. Therefore, LockedSerial is important for preserving the synchronization between the multiple threads and the serial port.
