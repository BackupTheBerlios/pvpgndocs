Comments and miscellaneous.
---------------------------

This document now contains stuff that needs a home.
Any correspondence or updates should be in the changelog  

#================================================
DW: Captured Conversation from IRC 15Nov2004
DW: --> recommend inserting into diablo doc??

Arelius: PVPGN with Diablo II closed, what is a decent system to run it on? and the diff bewteen 1.6.6 and 1.7.3?

d1zzy: there is a NEWS file into 1.7.x describing the major diffs between 1.6.x and 1.7.x  you will need win32 for d2gs
d1zzy: so the d2gs machine needs to have about 5-6 mbytes of memory for each game you want to host
d1zzy: d2gs is a binary win32 only package made by some other people

Arelius: can it not be run in linux?
d1zzy: I know people run it with wine but it shows instabilities (as you might expect) especially if you host more than 5 games at a time or so

Arelius: and d2gs does what exactally?
d1zzy: and with wine also the hw requirements are increased d2gs is the game server
d1zzy: d2 closed games different from all other blizzard games does hosts games serverside
d1zzy: and it is d2gs that does all the game computation and the world

Arelius: can it be run on a differnet computer?
d1zzy: yes it can d2cs/d2dbs too can run on another one
d1zzy: you can even have more than one d2gs for a single realm and d2cs will spread the games evenly between available d2gs


d1zzy:
ok... you want to know how d2 works
pvpgn package consists of several programs in which there are also 3 daemons: bnetd, d2cs and d2dbs.
bnetd takes care of most of the battle.net functionality, user management, chatting, game publishing and matching, stats and reports with d2. However things are a little different for d2. bnetd only takes care of account management and chatting it also has a list of "realms" which is sent to the client after successful auth. 
For each realm you need a d2cs/d2dbs pair of daemons these two manage a realm and have specific functions. d2cs manages characters and games and talks to d2gs for creating games. d2dbs on the other hand manages ladders. We think d2cs connects to bnetd and registers himself so bnetd knows to list that realm to the user because it knows the realm it works. d2gs which manages the games connects to both d2cs and to d2dbs

#================================================    

Captured 15 September 2004 by dgwilson65 - needs a home within the documentation


http://forums.pvpgn.org/index.php?showtopic=2781
<http://forums.pvpgn.org/index.php?showtopic=2781>


have some problems with my Warcraft 3 Server.

The webpage for my War 3 Server... We cannot get the Thing to Work! Can anyone help me with this?

Changing maps on the War 3 server.. We want to change the ladder maps on the War 3 server, how do I do this?

Is it possible to get the Tournement thing in the top right to work like it does on battle.net.

Also how do we change the icons for each win..(Like undead 25 win icon changed to fiend) for example.. Thanks





a) pvpgn only hands a link to the game clients (check anongame_infos.conf) , you have to setup web-pages for ladder yourself.

b) modify bnmaps.conf for this task. but be aware that clients will only accept blizzard signed maps.

c) pvpgn currently only support preliminary rounds for tournaments. check tournament.conf for more details.

d) you can't change the icons, just the number of wins needed to achieve them (again check anongame_infos.conf)


SO there is absolutely NO way to use custom maps on a PVPGN server for ladder?

that has nothing to do with PvPGN. the maps (ladder maps) are digitally signed with blizzard's private key and the public key in the client (war3) checks the signature, so unless you find out blizzard's private key (in about a hundred centuries with all the computers in the world) or hack the client to disable the check there is nothing you can do.


#================================================    

dizzy  	
post Apr 6 2004, 06:37 PM

BTW, all the games except diablo2 exchange traffic directly through themselves, 
the latency in game has nothing to do with pvpgn (or pvpgn's connection).

#================================================ 
ZSoft  	
post Feb 1 2004, 05:26 PM

I thought by setting up our own PvPGN server, we wouldn't have to deal with some abnoxious friends of ours from constantly joining our games - either over the LAN or regular Battle.net, however, it looks like I'll still need the ability to use /ipban.

It looks like it only is setup to accept IP addresses, such as "/ipban add 1.2.3.4". However, how do you find the IP address of the abusing user?


dizzy  	
post Feb 1 2004, 10:11 PM

 /netinfo <user>

PS: read conf/bnhelp
PPS: check /serverban for that, accepts users too


#================================================ 
Roland  	
post Apr 21 2003, 05:40 PM

Quick D2 Gateway Alterations, Mac OS 9.x

What you need:

ResEdit. I used version 2.1.3.

What you do:

Make a copy of your Diablo II Preferences file. If this doesn't work,
delete the modified file and rename your copy to restore the original file.

Open the System Folder:Preferences:Diablo II Preferences in ResEdit. You
should see a binary resource group, HKEY. Open that.

Look for the line
"HKEY_CURRENT_USER\Software\Battle.net\Configuration\Diablo II Battle.net
gateways". Open it.

Note: There is a similar line that refers to "Battle.net gateways" without
the "Diablo II". Leave it alone.

The opened HKEY should look like bunch of hex numbers on the left and a
list of gateways on the right.

Select a null (a down-caret -> ù)
copy it to the Clipboard. It will come in handy.

Place your insertion point by clicking immediately after the down-caret
after the word "Europe". Then type <IP Address><null><zone><null><gateway
name><null>.

You can get the nulls by pasting the null character you copied earlier. To
enter the information, you would type:

123.45.67.89(paste a null)6(paste a null)Server Name(paste a null)

You should wind up with the text column looking like:

ùùùù1002ù01ùuswest ... Europeù123.45.67.89ù6ùServerùù

Save the file ("Save" under the FIle menu). Quit ResEdit. You're done.

How I got there:

I noticed that the supplied gateway editor was for StarCraft and only
modified the StarCraft preference file. I reasoned that if I made the same
changes to the D2 preferences file, I'd get a reasonable result, so I
copied the changes from the StarCraft preferences file to the D2
preferences file, and it worked. In retrospect, it would have been easier
just to type in the changes, as described above.

Now if only I could get StarCraft to work.

"Dammit" Jim Gould   

#================================================ 

Wanna play Starcraft? Here's how..
 Forum:   SecurePoint.COM - Netfilter mailing list archive
 Date:      2001, Feb 28
 From:      Rick Kramer <nobody at nowhere.com>

Using the following setup, I was able to play a 3v3 game of Starcraft on
BNET. 3 of us where inside the firewall playing against 3 external clients.
The internet connection was a 256k up / 512k down cable modem connection.
The firewall is a 486/166 with 32 megs and 1.2 gigs of disk running the beta
release of RedHat Fisher (7.0.99 - 2.4.0). I have not upgraded my iptables
installation.

Since I'm not using this machine as my default firewall yet (just putting it
up during games), I haven't shored it up. In my script, all the default
policies were set to ACCEPT. In addition to the following translation lines,
a secure system probably also needs some ACCEPT rules in the FORWARD chain
to get this to work.

#----------------------------------------------------------------------
echo Enabling BNET

for i in 10 11 12 13 14 15
do
  # handle the forward to the machine
  iptables -t nat -A PREROUTING -p udp -d $extip --dport 630$i \
  -j DNAT --to-destination 10.69.1.$i:6112

  # handle the translation of packets from the machine
  iptables -t nat -A POSTROUTING -p udp -s 10.69.1.$i --sport 6112 \
 -j SNAT --to-source $extip:630$i
done

What this table does is reserve external UDP ports 63010 - 63015 as the
external ports corresponding to 6112 for internal clients 10.69.1.10 -
10.69.1.15. Clearly, you can pick any port range you want and any internal
client range you want.

The first rule does destination translation, making sure that any packets
sent to the external ip address inside the reserved port range are rewritten
and sent to the appropriate internal client.

The second rule does source translation, making sure that any packets sent
from the internal machines (6112) is translated to the external address
(630xx).

Observed Behavior:

1. Translation appears to work as expected for communication with external
clients. The DNAT translation works on all in coming packets and the SNAT
translation works on all outgoing packets.

2. Communication between internal clients is very strange. In my earlier
work with linux 2.0.x, I saw the first packet from an internal client go to
the external address of the client. However, using this setup, the first
packet appears to go directly from one internal client to the other. I'm
kinda hoping this is because tcpdump is seeing the packets after PREROUTING
DNAT, but I'm not sure. In any case, the POSTROUTING SNAT works fine and the
packet is retransmitted to the internal net with a source of $extip:630xx.

3. You cannot substitute -j MASQUERADE for the SNAT rule. MASQUERADE means
do SNAT using the address of the interface that the packet is being sent out
on. This works great for packets going out to external clients. However,
when two internal clients are trying to communicate, the packets appear to
come from the internal interface of the firewall, which is useless. The
internal clients will ignore the packets unless they appear to come from the
external interface. This is the reason why you have to use -j SNAT and
specify the external address.

4. It appeared to take a few seconds to setup the initial translations. This
could be because the box is slow and has very little memory. In any case,
the first time each client tried to connect to bnet, the connection failed.
On the second try, we typically got 1 bar green lag. I should note here that
it is difficult to test things like this because bnet itself is so
unreliable.

5. We played many 3v3 games without any problems. That is not to say that we
didn't encounter standard bnet stuff: the odd laggy external client slowing
the game down and bnet server we were connected to crashing during the
evening.

6. A little advice to anyone that wants to play with your friends in a tvb
3v3 game: You should all try to login to the same bnet server. For whatever
reason, it takes time for the game to propagate to other servers on
creation. So, if you and your friends are not on the same server, the game
will not appear for them to join for a few seconds. Of course, in that few
seconds, 5 people will join your game and you won't have the nice tvb setup
you were hoping for.

7. While playing I saw console messages saying that packets were being
suppressed. I suspect that this is due to the flow control stuff built into
iptables, but it didn't affect the games so I didn't spend much time on it.

Limitations:

1. The rules require you to know your external address. This can be
problematic for dhcp setups. In my situation, my external ip does not change
very often. I use pump -s to get the information for my external interface
and pull the address out, so my script doesn't have the address hard-coded.
If you're one of those people who's cable provider has 1 hour lease times
and experiences addresses change regularly, I guess this isn't for you.

2. The rules require you to reserve internal addresses and external ports.
Given the address space available for internal networks (10.x.x.x), I don't
really think this is a big issue. If you run dhcp on your internal net
hosted from the firewall box like I do, you can just setup some
reservations. I have reservations in my configuration for the ethernet cards
of all my friends' laptops so that they can just plug in and go. iptables
starts handing out ports at 1025 I believe, so port collisions are unlikely
if you reserve a fairly high port range. There's also no reason why you
can't reserve more machines.. I just trimmed it down to 5 in my example for
readability.

There you have it folks.. No module required.. I'd like to thank Doron Oz
for getting me started with an initial rule set.

 -rick
