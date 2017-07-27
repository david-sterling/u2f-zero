

U2F Zero
========

U2F Zero is an open source U2F token for 2 factor authentication.  It is implemented securely.  It works with Google accounts, Github, Duo, and anything else supporting U2F.  The latest version uses key derivation and has no limit on registrations.

![](http://i.imgur.com/dQpo9wC.jpg "The door keys are not used")

You can easily [build your own](https://github.com/conorpp/u2f-zero/wiki/Building-a-U2F-Token).  You just need to order the
[8 SMT parts](https://github.com/conorpp/u2f-zero/wiki/Parts-List#smt-parts), [$1.13-$3.5 per PCB](https://github.com/conorpp/u2f-zero/wiki/Parts-List#pcbs), and [programmer](http://www.digikey.com/product-detail/en/silicon-labs/DEBUGADPTR1-USB/336-1182-ND/807653).
It ends up being $35 for programmer and ~$5/board.  The token should be durable enough to survive on a key chain for years, even after going through the wash.

Check out [the wiki](https://github.com/conorpp/u2f-zero/wiki) for more on how to [build your own](https://github.com/conorpp/u2f-zero/wiki/Building-a-U2F-Token).



Security Overview
-----------------

The security level is about the same as a modern car key.  Any secret information cannot be read or duplicated.  A true random number generator is used to create unpredictable keys.  

However, side channel leakage is an unsolved problem in industry and academia.  So for well equipped adversaries that can make targetted attacks and get physical access, secret information leakage is possible.  Any other hardware token that claims it's "impenetrable" or otherwise totally secure is *still* vulnerable to physical side channels and it's important to acknowledge.  However, most people don't worry about targeted attacks from well equipped adversaries.

For more information about U2F Zero's secure implementation and the problem of side channels, check out [the wiki](https://github.com/conorpp/u2f-zero/wiki/Security-Overview).


License
-------

Everything is open source and licensed under the [Simplified BSD License](https://github.com/conorpp/u2f-zero/blob/master/LICENSE.txt).

Panelizing for cost savings
---------------------------

If you work with the marvelous and fancy but expensive Altium (maybe you work with the expensive and horrible Orcad) is very easy to panelize. However the rest of PCB CAD still do not include such an easy tool.

Good news is that there is a EPIC open source tool that works reasonably well and you can pull from here
[Gerber_Tools](https://github.com/ThisIsNotRocketScience/GerberTools). The magic is generating the tabs.

I have tried and run a small batch and everything was fine, however with kicad generated gerbers you have to modify one layer name since they think better to reinvent gerber de facto standard than just using the standard.

From this [Hackaday post](http://hackaday.com/2017/06/21/panelizing-boards-the-easy-way/) "Gerber Panelizer is not without significant issues, although some of the blame can be directed at KiCad. The KiCad philosophy makes a distinction between milled, plated layers and the final cutout of the board. In KiCad, this means there’s a difference between .GKO and .GML Gerber files. KiCad, in its infinite wisdom, decided the cutout layer of the board should use the file extension .GM1 as an output Gerber." So change GM1 for GKO.

I recommend to arrange the boards so the usb part always have a clean cut without tabs.
