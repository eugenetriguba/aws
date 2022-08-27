i.e. X as a Service (https://en.wikipedia.org/wiki/As_a_service)

Infrastructure Stack

* Stack of things an application needs in order to run.
  * Facilities -> Infrastructure -> Servers -> Virtualization -> O/S -> Container -> Runtime -> Data -> Application
  * Parts that *you* manage
  * Parts managed by the *vendor*
  * Unit of consumption.
    * What makes each service model different. If you're using Netflix, you're unit of consumption is the service itself end to end. If you're getting a provisioned VM, your unit of consumption is the O/S.
  * With on-premise, you own everything in the stack.
    * While it is expensive and has risk, it is very flexible since systems can be tailor made for your system.
  * With data center hosting, the vendor then controls the facilities our hardware is running in, but we supply the hardware. and everything else up.

IAAS

* Infrastructure as a Service
* AWS -> EC2 (Elastic Compute)
* Vendor managed: Facilities -> Infrastructure -> Servers -> Virtualization
* Consumed: O/S
* User managed: Container -> Runtime -> Data -> Application

PAAS

* Platform as a Service
* Vendor managed: Facilities -> Infrastructure -> Servers -> Virtualization -> O/S -> Container
* Consumed: Runtime
* User managed:  Data -> Application

SaaS

* Software as a Service
* i.e. Netflix, etc.
* Vendor managed: Facilities -> Infrastructure -> Servers -> Virtualization -> O/S -> Container -> Runtime -> Data
* Consumed: Application
