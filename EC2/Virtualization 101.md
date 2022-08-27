* https://www.brendangregg.com/blog/2017-11-29/aws-ec2-virtualization-2017.html

Emulated Virtualization

* Host OS still runs on hardware
* Virtual Machines run on a Hypervisor
* Software ran in privilieged mode so full access to hardware on host server
* Guest OS believe they are running on real hardware.
* Hypervisor performs binary translation of calls the Guest OSs make in software.
* Slow, big performance penalty to do so in software.

Paravirtualization

* Like emulated virtualization except needs a modified OS that makes "Hypercalls" (calls to the particular hypervisor) instead of the regular system calls.
* OS become almost virtualization aware but it was still a set of software processes.

Major improvements came when physical hardware become virtualization aware.

Hardware Assisted Virtualization

* CPU itself is aware it is performing virtualization
* When guest OSs try to make system calls, they are trapped by the CPU and redirected to the hypervisor by the hardware to handle how they are executed.
* This means there is very little performance degredation.
* Limitation of network/disk IO still since we still only have one network card/drive/etc.

SR-IOV

* Single root, IO virtualization
* Allows one network card or any other card to present themselves not as one card but as many and is supported in hardware.
* Elimates translation having to be done by the hypervisor. Each Guest OS can simply use its card. Physical card that supports SR-IOV handles this
* EC2 => Enhanced Networking
  * Faster speeds
  * Lower latency
  * Consistent lower latency even at high loads
  * Lower CPU usage
  * AWS has a stack called Nitro but it implements these standards.
