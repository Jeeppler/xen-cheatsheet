~~~
title: Xen Cheatsheet
~~~

# xl

`xl info` - returns the information about the hypervisor and dom0 including version, free memory etc. 

\---

`xl list` - returns a list of vm's (including dom0) and displays the id, memory, vcpus (virtual cpus), vm state and the total run time.

An example format for the list is as follows:

    Name                                        ID   Mem VCPUs      State   Time(s)
    Domain-0                                     0   750     4     r-----   11794.3
    win                                          1  1019     1     r-----       0.3
    linux                                        2  2048     2     r-----    5624.2

Name is the name of the domain. ID the numeric domain id. Mem is the desired amount of memory to allocate to the domain (although it may not be the currently allocated amount). VCPUs is the number of virtual CPUs allocated to the domain. State is the run state (see below). Time is the total run time of the domain as accounted for by Xen. ([xl manpage][xl-man])

\---

`xl dmesg` - reads the Xen message buffer.  The buffer contains informational, warning, and error messages created during Xen's boot process. ([xl manpage][xl-man])

\---

`xl destroy`

`xl create`

`xl top`

# xenstore

`xenstore-ls` - dumps the contents of the xenstore

`xenstore-ls -f` - dumps the contents of the xenstore (flatten)

# Xen Services

`xencommons` - Xen Project relies on an init script called xencommons to initialize all the services. It should be executed by default at boot time. ([Xencommons][xencommons]

`xenstore` - Xen uses a xenstore daemon to allow dom0 and guests get access to information about configuration space for itself and the system. XenStore is an information storage space shared between domains maintained by the Xenstored. ([Xenstore][xenstore])

[xenstore]: https://wiki.xen.org/wiki/XenStore "XenStore"

[xencommons]: https://wiki.xenproject.org/wiki/Distros#init_scripts:_xencommons "init scripts: xencommons"

[xl-man]: http://xenbits.xen.org/docs/unstable/man/xl.1.html
