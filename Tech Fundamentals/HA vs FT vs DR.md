High-Availability (HA)

* Aims to **ensure** an agreed level of operation **performance**, usually **uptime**, for a **higher than normal period**.
* HA is not aiming to stop failure, and it definitely doesn't mean that customers won't experience outages.
* It is a system that is designed for when it fails, it's components can be fixed or replaced as quickly as possible, often using automation.
* It is about maximizing a system's online time.
* System availability is normally expressed as a percentage of uptime.
  * 99.9% = 8.77 hours per/year of downtime.
  * 99.999% = 5.26 minutes per/year of downtime.
* For instance, if we had a two server setup with one on standby, it may mean that when one goes down, all traffics gets routed to the new one. However, that also means the customers may have to re-login or something like that but that is okay with HA since it is purely focused on uptime.
* About fast or automatic recovery of issues, not necessarily about preventing user disruption.
* Has costs and automation required to implement, sometimes redundant servers and infrastructure.

Fault-Tolerance (FT)

* Similar to HA but much more.
* Property that enables a system to **continue operating properly** in the event of the **failure of some** (one or more faults within) of its **components**.
* If a system has one or more faults, the system should continue to operate properly. They are designed to work through failure without disruption.

Disaster Recovery (DR)

* A set of policies, tools, and procedures to **enable the recovery** or **continuation** of **vital** technology infrastructure and systems **following a natural or human-induced disaster**.
* i.e. what happens when your HA or FT does not work? What if the building is flooded or catches on fire?
* Given a disaster, it is about what happens before, the pre-planning, and about what happens after, the DR process.
* Examples: taking regular backups (in multiple places, off-site), having extra servers elsewhere, having a place to go in the event of disaster, all logins being available at the standby site, running periodic DR testing (think of pilot or passenger evacuation systems). DR, with cloud and automation, can now largely be automated.

HA = maximize uptime (have spare components)
FT = operate through failure (can be much more expensive to implement and design, levels of redundancy and system components that can route traffic between all components)
DR = what happens when these all go wrong?
