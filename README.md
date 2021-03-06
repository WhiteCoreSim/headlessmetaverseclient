﻿# Headless client for the Second Life protocol.
Or more precisely, it has no GUI, but speaks a small subset of IRC as its user interface.

Currently, it listens on localhost:6668 and is hardwired for the main Second Life grid.

SL usernames are translated to IRC nicknames as Firstname.Lastname, so you'll see a lot of people
called things like "Bob.Resident".

Log in using your SL name thusly as your nick, and your SL password as the server password. Note
that error handling is sub-par so errors might not be sent to your client (this includes the one
where you tried to log in too soon after logging out or crashing).

If your client doesn't display the numerics used for presence sensibly (such as irssi), pass
`--presence-notices` on the command line and they'll be sent as `NOTICE` instead.

## Supported:

 * Logging in
 * Talking and listening in local chat
 * Group chat
   * People with moderator permissions are listed as chanops.
   * You can't leave or detach a groupchat.
 * See who's in the same region as you.
   * People in regular chat range are voiced.
 * IMs
 * Friend presence, using [`MONITOR`](http://ircv3.net/specs/core/monitor-3.2.html) to report/
   display it.
   * You can't add or remove people, only see their presence.
   * Your client needs to be okay with the server prepopulating the MONITOR list.
   * The command-line option `--presence-notices` sends you a `NOTICE` every time a friend's presence
     changes, instead of `MONITOR` numerics.
   * Send `MONITOR NON` to get notices listing who's currently online.
 * RLV `@sit` and `@sendchat`. `@redirchat` may work.
 * You can see `llDialog()`s but not respond to them.

## Things that definitely don't work
 * Getting a correct list of who's in a groupchat with you (regular clients can't do this either)
 * Closing groupchats (you'll be forcibly rejoined)
 * Adding or removing friends
 * Joining or leaving groups
 * Teleport requests (you'll send an autoreply to whoever asked you to teleport).
 * Pretty much everything else.

## Building
You will need to run `libopenmetaverse/runprebuild2013.bat` before the project will load.
