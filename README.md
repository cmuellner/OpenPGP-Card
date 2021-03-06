OpenPGP-Card
============

Open source implementation of the OpenPGP smart card version 2.0 on a java card.

Card Requirements
-----------------
* Java card version 2.2.2 (2.2.1 might work but it is untested)
* 2048 bit RSA key support
* Global platform 2.1.1 or above to use the loading scripts.

The applet was developed and tested on a JCOP 2.4.1 card (NXP J2A080).

Brief instructions
------------------
* Make sure that the card reader is working.
* The easiest way is to use [GlobalPlatformPro](https://github.com/martinpaljak/GlobalPlatformPro) to install the CAP file 

* The harder way is to use the GlobalPlatform tools 
  * Install the GlobalPlatform and gppcscconnectionplugin libraries from http://sourceforge.net/projects/globalplatform/files/GlobalPlatform%20Library/GlobalPlatform%20Library%206.0.0/
  * Install GPShell from http://sourceforge.net/p/globalplatform/wiki/GPShell/
  * Load the applet on the card
 
The actual parameters used to load the applet on the card depend on the card manufacturer, version and state.
If using a JCOP 2.4.1 cards with test keys, the 'installJCOP41GPG.gpshell' script can be used:

    gpshell installJCOP41GPG.gpshell

*Warning!* Too many failed authentications when trying to load the applet can lock the card and make it unusable.

* Once the applet is initialized gpg / gpg2 can be used to initialize the card.
* GnuPG 2.0.22 or above is recommended (older versions do not support importing RSA keys in the CRT format).

```
gpg2 --card-edit
```
The user PIN is '123456' and the admin PIN is '12345678' and it changing them is recommended.

For more details check this page: http://wiki.fsfe.org/Card_howtos (but note that the 'with backup' methods will need GnuPG 2.0.22 or above).
