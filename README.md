# smbdoor

![ExtraPulsar](extrapulsar.png)

The proof-of-concept smbdoor.sys driver is a silent remote backdoor that does not bind new sockets or perform function modification hooking. Instead it abuses undocumented APIs in srvnet.sys to register itself as a valid SMB handler. It then listens on the already-bound ports 139/445 for special packets in which to execute secondary shellcode. In several ways, it has similarities with DoublePulsar and DarkPulsar, as well as ToxicSerpent.

Of course, it comes with practical limitations that make it mostly an academic exploration, but I thought it might be interesting to share, and is possibly something EDR products should monitor.

### Detection: 
- https://twitter.com/zerosum0x0/status/1117701672237535233
- https://twitter.com/msuiche/status/1117716796658864128

---------


//Now, many people maybe just got this to compile & run flawlessly the first time, but I'm doing this for the people that (obviously) had a bit of compiler errors/and other issue(s).


## Original repo is: https://github.com/zerosum0x0/smbdoor


#### I forked this with the goal of improving & contributing, especially to help the "issues" (open) at the original repo.

#### Which (currently) is the following: (https://github.com/zerosum0x0/smbdoor/issues)

### ISSUES

---------------------------------

- "About SMBDOOR_SRVNET_REGISTRATION #3 opened on Nov 5, 2019 by fengxianzhiling"
- "Could U Provide Downloadable smbdoor.sys for US - #2 opened on Sep 13, 2019 by fxicx"
- "Interaction With SMBDoor - #1 opened on Apr 25, 2019 by katesaikishore"

---------------------------------

In my case I (too) had a bunch of compiler errors; (mentioned in Issue #2) 
I (in my case) had the following errors:

---------------------
    (...) - "Device driver does not install on any devices, use primitive driver if this is intended."
    Here, I exactly do not know what fixed this but, in my case (**NOTE, read carefully or you may accidentaly delete the inf file**) I deleted (In visual studio) the smbdoor.inf file, but I kept the "file" itself. And - somehow, it worked.

----------------------
    (...) - [Version] section should specify PnpLockdown=1.
    fix: Just add "PnpLockdown=1" below [Version]

----------------------

Please, if any of those fixes (and any of the following which I will continue adding) 
worked for someone, please tell me that (so I know that it worked)

-----------------------

Contact details for 
Questions or Discussion or anything else:



Mail: William-martens@protonmail.ch

Discord: Ken-Kaneki#3978
