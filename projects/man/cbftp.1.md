---
title: CBFTP
section: 1
header: User Manual
footer: cbftp 1.0.0
date: March 27, 2022
---
## NAME
cbftp - Ncurses FTP and FXP Client

## SYNOPSIS
**cbftp** [-h] [-d] [-a AUDIO] [-c CYCLE]

## DESCRIPTION
The *cbftp* command is an advanced multi-purpose FTP/FXP client that focuses
on efficient large-scale data spreading, while also supporting most regular
FTP/FXP use cases in a modern way. It runs in a terminal and provides a
semi-graphical user interface through ncurses.

## MAJOR FEATURES

- Spread jobs for efficient many-to-many FTP server data spreading through FXP
- Transfer jobs for regular file transfer needs: FXP, Upload, Download
- Efficient slot handling: slots are used and reused for any purpose at any
  time. A large job does not "lock" slots, and neither does the UI
- Concurrency: Multiple jobs can run at the same time.
- Encrypted data file with AES-256
- TLS support (AUTH TLS) and TLS FXP support
- IPv6 support and IPv6 FXP support
- Remote commands for performing various tasks through REST API and UDP calls
- Ncurses UI, runs in a terminal which makes cbftp highly flexible
- Advanced skiplisting
- Internal file viewer with support for multiple encodings
- File viewing through external applications when running in a local terminal
- SOCKS5 proxy support

## CONFIGURATION

FTP site details and other settings are stored in the cbftp data file, which
will be created the first time cbftp is started. It is located at
`~/.cbftp/data`. By default it is stored as plain text, but encryption can
be enabled through the global settings, and your data file will then be
encrypted with aes-256-cbc.

## GETTING STARTED

After starting cbftp (and possibly entering your passphrase), you will end up
on the main ui screen of the client. This is where your FTP sites will be
listed, along with the latest few spread jobs and transfer jobs if there are
any. In the bottom of the screen, there will be various key binding information
scrolling by. This area is known as "the legend bar" and is used to list
available key bindings at any given time.
The first thing you will want to do here is probably to add a site, so
press A.

## USER INTERFACE

The cbftp user interface is based on several views - main screen,
edit site screen, browse screen, etc. The available views can be considered
as a stack - after you've entered a new view, leaving it will normally take
you back to where you came from.

## KEY MAPPING

```
C-c             Quit/Exit program
Left/Right      Refresh After Changes

=== CBFTP MAIN
A               Add site
G               Global settings
l               Event log
t               transfers
r               All races (aka All Spread Jobs)
j               All transferjobs
U               toggle Udp
c               Browse local
i               General info
s               sections
S               Snake
Esc             back to browsing
Tab             split browse
Right/b         browse site (BROWSING aka connect to ftp server)
w               raw command
E               Edit site
C               Copy site
D               Delete site
q               quick jump
L               Login all slots
0-9             Browse to section
Down            Next option
Up              Previous option

=== SITE OPTIONS (A/E)
Enter           Modify
Down            Next option
Up              Previous option
d               done, save changes
c               cancel, undo changes
s               sections
S               Skiplist

=== BROWSING (Right/b)
Tab             switch side
Esc             Cancel
c               close
Up/Down         Navigate
Enter/Right     open dir
Backspace/Left  return
r               spread
v               view file
D               Download
b               bind to section
s               sort
w               raw command
W               Wipe
Delete          Delete
n               nuke
m               make directory
P               Toggle seParators
q               quick jump
f               Toggle filter
F               Regex Filter
l               view cwd log
Space           Hard select
^Up/^Down       Soft select
A               Select All
0-9             Browse to section

=== GLOBAL SETTINGS (G)
Enter           Modify
Down            Next option
Up              Previous option
d               done
c               cancel
S               Skiplist

=== EVENT LOG (l)
PgUp            Scroll Up
Pgdn            Scroll Down
ESC/Enter       Return
f               Toggle filtering

=== TRANSFERS (t)
Esc/c           Return
Up/Down         Navigate
Enter           Details
f               toggle filtering
B               ABort transfer

=== ALL SPREAD JOBS (r)
Esc/c                       Return
Enter                       Details
Up/Down/PgUp/Pgdn/Home/End  Navigate
r                           reset job
R                           Hard Reset job
B                           ABort job
t                           transfer for job
z                           Abort job and delete own files on incomplete sites

=== ALL TRANSFER JOBS (j)
Esc/c           Return
Enter           Details
Up/Down         Navigate
B               ABort job
t               transfers for job

=== LOCAL BROWSING (c)
Tab             switch side
Up/Down         Navigate
Enter/Right     open dir
s               sort
Backspace/Left  return
Esc             Cancel
c               close
q               quick jump
f               Toggle filter
F               Regex Filter
Space           Hard select
^Up/^Down       Soft select
A               Select All

=== SECTIONS (s)
A               Add section
Enter/E         Details
Esc/c/d         Return
Up/Down         Navigate
Delete          Delete section

=== SNAKE Game (S)
Arrows          steer
r               reset
Esc/c           Close
```

## BROWSING

After adding a site, you can browse it by selecting it and pressing b
from the main screen. This will take you to a different view where the
contents of the root (or base path) of the site will be shown. You can browse
around through directories by using the arrow keys.
Various features are available here, see the legend bar at the bottom.
The browse screen is also considered a "main window" in cbftp; you can toggle
back and forth between the browse screen and the main screen by pressing esc.

## STARTING A TRANSFER JOB

If you would like to transfer something, there are some ways to start a
transfer job. The simplest way is to select an item that you wish to download
and then press D. A transfer job for downloading that item will be started
in the background, and will also be visible in the bottom legend bar while the
browse screen is open. By default, download jobs will be downloaded to the
download path specified in the global options screen, press G from the main
screen to get there.

For other types of transfer jobs, you'll need to open the split view.
Press TAB to open the split view. In the newly opened view, you'll be
presented with the option to either browse your download directory, or any of
your added sites.

After opening the split view, you can press TAB at any time to switch side.
If you wish to start an upload job, browse your download directory, select
an item that you wish to upload, and then press t. A transfer job will be
started in the background that uploads your specified item to the directory
on the site that was opened on the other side of the split view. It will also
be visible in the bottom legend bar while the browse screen is open.
The same thing goes for FXP transfer jobs, but you will obviously need to open
a site instead of the local view. Choose item and press t to start a job
in the background. It will also be visible in the bottom legend bar while the
browse screen is open.

Your newly created transfer job will be visible in the main screen of cbftp.
Transfer jobs use a single slot on each site by default; this can be modified
in the detailed view of each transfer job.

## STARTING A SPREAD JOB

A spread job is a larger form of transfer job that spreads an item among
a selection of multiple sites through FXP. It is an action that does not
exist natively in other clients (at the time of writing), and it is the
original purpose of cbftp. Spread jobs do not use 'chains' like other
clients do - see the "the transfer engine" section further down for more
information.

Spread jobs rely on sections being properly defined on all sites that should
be involved - a site can only be added to a spread job if it has a matching
section defined with a suitable path.

To start a spread job, browse a site and select the item that you wish to
spread, and then press 'r'. If the current working directory is bound to a
section, the "new spread job" screen will be opened where you can specify
which sites to include in the job, and possibly which section to use if there
are several bound to the same directory. Sites that have the same section
defined as the one where the selected item was located will be available for
selection.

After selecting sites, press 's' to start the spread job.

## SLOT HANDLING

In many traditional FTP clients, a login slot is "locked" to the UI window
that it occurs in. To use multiple slots or multiple sites, separate tabs
or windows must be opened. This is possibly where cbftp differs the most from
other clients - cbftp handles slots and pairs in a very different way.

First and foremost, the UI in cbftp s merely a complement to the backend.
Cbftp can actually be compiled and run just fine completely without UI.
Secondly, cbftp considers each site as an entity, rather than each login
slot - a specific slot can be used and reused for any purpose at any time.
Slots are locked only for the duration of a single file transfer. When the
single transfer finishes, the slot is free to be used for any other task -
most likely the next file in the same job, but it can also be a task from
another job, a raw command, a file list request, a local download for
viewing - whatever cb considers most important at the time.

There is simply no "queue" built up around a single slot, instead cbftp
has a global queue of things to do and jobs to work on, and evaluates what
is most important to do next whenever a slot becomes available.

This also results in that a slot is never bound to be used specifically for
uploading or downloading - a slot can be used for downloading a file,
and then right after it might be used for uploading another file.
The user has partial control over this by specifying how many slots that can
be used for download and upload on each site.

The UI is not built around transfer tabs, since everything happens in the
backend.

## THE TRANSFER ENGINE

The transfer engine is the heart of cbftp, and it decides where, when and
how to perform file transfers. It summarizes information about the state of
all current spread jobs and transfer jobs from all sites, and then calculates
which transfers that are most favorable to perform by assigning scores to
potential transfers based on various criteria - site speed vs other sites
where the file is not yet available, file size, spread job progress on the site
versus other sites, percentage of files uploaded by you, target site priority,
etc. The potential transfers are summarized in a scoreboard where the ones
with the highest scores will be performed first, until there are no more
transfer slots free on the sites. Whenever a file list is refreshed on some
site or a slot becomes available when a transfer finishes, the procedure runs
again.

This action pattern results in that cbftp can and will pair connections
against varying sites frequently. Between every single file transfer,
all conditions are reevaluated and if it becomes more favorable to pair
sites differently, that will happen. This is the main reason why large-scale
data spreading in cbftp is so simple to deal with - there are no chains, no
tab setup, no preparation necessary at all before starting each spread job.
Just specify what to transfer onto which sites, and cbftp will handle the
rest.

The user has partial control over the transfer patterns by limiting which
sites that can transfer to where by using the allow/block lists available for
each site, and also by specifying site priorities.

## SKIPLISTING

Cbftp supports advanced skiplisting of what to deny or allow, both on job
and file basis. Skiplisting can be specified globally, per section, and/or per
site.

The global skiplist can be accessed by pressing G from the main screen and
then selecting "configure skiplist". The section-specific skiplist is available
when editing sections globally. The site-specific skiplist is available when
editing a site.

The skiplist works by matching items against the list from the top to the
bottom. If a rule that matches the item is found, the action of that rule
is applied to the item, and the remainder of the skiplist is ignored.

Possible actions are Allow, Deny, Unique and Similar.

Unique means that only the first
file found in a directory that matches the rule will be allowed - others
will be skipped/denied.

Similar means that the file will only be allowed if its name is similar enough
to other files in the directory matching any similar-rule.
The criteria is that only the file extension OR a the last numbering sequence
in the file names may differ, not both and not anything else.
Similar-rules only affect files in spread jobs.

An item is normally a file name or a directory name. There are buttons
available on each entry in the skiplist if it should match files and/or
directories.

The scope setting specifies where the skiplist should apply.
"In spread job" entries will only be used for matching inside a spread job
directory. It will not be able to match on the name of the spread job
directory itself, and the path in the entry should start inside the
spread job directory.

"Allround" entries will match on entire paths, and can be used to skip
entire jobs on a specific site, or even globally. Allround rules also apply
on regular transfer jobs, which 'in spread job' rules do not.

To test your skiplist rules, you can use the TEST PATTERN function at the
top.

The site-specific skiplist is applied first for matching on a specific site.
If no match is found it falls through to the section skiplist (for spread
jobs), which in turn falls through to the global skiplist.

The wildcard characters * (match any number of any character) and ? (match any
single character) are the currently supported, or regex mode can be used.
The skiplists are not case sensitive.

The regex flavor is ECMAScript, which is default in C++'s std::regex,
with the addition of case insensitivity support via (?i).

Some skiplisting examples:

Skip all files ending with .jpg in the main dir of spread jobs:

`[ ] *.jpg  [X]  [ ]  Deny  In spread job`

Skip all files ending with .jpg in all subdirs of spread jobs:

`[ ] */*.jpg  [X]  [ ]  Deny  In spread job`

Allow only "Sample" and "Proof" as subdirs in spread jobs:

`[ ] sample  [ ]  [X]  Allow  In spread job`

`[ ] proof   [ ]  [X]  Allow  In spread job`

`[ ] *       [ ]  [X]  Deny   In spread job`

Skip all spread jobs with .INTERNAL. in the name:

`[ ] *.INTERNAL.*  [ ]  [X]  Deny  Allround`

Only allow one nfo and sfv file within each directory:

`[ ] *.sfv  [X]  [ ]  Unique  In spread job`

`[ ] *.nfo  [X]  [ ]  Unique  In spread job`

Skip files with spaces in the name everywhere:

`[ ] * *  [X]  [X]  Deny  Allround`

Skip files that don't belong in the directory through Similar-rules:

`[ ] *.r??       [X]  [ ]  Similar  In spread job`

`[ ] *.s??       [X]  [ ]  Similar  In spread job`

`[ ] *.t??       [X]  [ ]  Similar  In spread job`

`[ ] *.u??       [X]  [ ]  Similar  In spread job`

And again, note that the first match applies. If the skiplist does not
behave as you expect it to do, then you will need to think through if there
might be other rules that are matching your item too early. Use the pattern
test feature.

## REMOTE COMMANDS

Cbftp supports executing various commands remotely via two interfaces - a
simple one-way UDP API, and an advanced HTTPS/JSON REST API.
The listeners can be configured in the global options screen (press G from the
main screen).

You will need to set a suitable password that a client must provide
for cbftp to accept the commands.

In the UDP API, the password is part of the message.
In the HTTPS/JSON REST API, the password is sent through HTTP Basic auth.

Specifications for the API's are available in the API file.

## CONNECTION DETAILS

To see details about what cbftp is doing on each connection to a site,
select the site from the main screen and press enter. Here you can cycle
between the connections (if there are multiple) by using the left/right
arrow keys. You can also force connect/disconnect specific connections
from this view.

## RAW COMMANDS

To send raw commands to a site, select a site on the main screen and press w.
You will be presented with a new window where raw commands and their results
are shown. Just type and press enter for the command to be sent to the site.
By default, raw commands will be executed from the base path of the site.
You can also go to the raw command view when browsing a site by pressing w.
Raw commands will then be issued in the directory that you were browsing.
The currently selected file name can be pasted by pressing Insert.
If you want to send raw commands on a specific connection, go to the specific
connection (see "connection details" above) and press w there.

## ADD A SITE / EDIT A SITE

When selecting to add or edit a site, you will be presented with several
fields where you can enter settings and parameters for your site.
When you are done editing your site, press 'd' to save your changes.

Field summary:

- Name - The name that cbftp knows this site by.
- Address: the hostname or IP address and port of your site. This field
  supports multiple values if a site has multiple entry addresses available,
  and they can be entered on the same line by separating them with spaces.
- TLS mode: Whether the site should be connected to securely with TLS. Note
  that not all FTP servers support this - it depends on the server whether it
  works or not.
- Username: The username that you use to login onto the site. For sites where
  you do not have a username, 'anonymous' should be entered.
- Password: The password for your user on the site. If you do not have a user,
  'anonymous' should be entered.
- Login slots: The number of simultaneous slots that the site allows you to
  log in with.
- Upload slots: The number of simultaneous uploads that the site allows you
  to perform. Enter 0 for unlimited, or same as the number of logins.
- Download slots: The number of simultaneous downloads that the site allows
  you to perform. Enter 0 for unlimited, or same as the number of logins.
- Advanced slot configuration contains the following additional options:
  - Leave one slot free: Useful if you want to be able to list dirs or issue
    commands on the site with immediate response even while jobs are running.
  - Download slots on pre: On jobs that match the affil list, apply this
    amount of download slots instead.
  - Download slots on complete spread job: For a spread job that has completed
    on this site, apply this amount of download slots instead.
  - Download slots on transfer jobs: The number of download slots available
    for transfer jobs, and also the default number of slots to use when
    starting them.
- TLS Transfers: The security behavior for transfers to/from this site.
- Transfer protocol: Preferred/supported protocol IPv4/IPv6
- Stay logged in: Don't log out from sites automatically. Enable
  anti-anti-idle with the configured max idle time as period.
- List command: Which command the site should use to list directories.
  STAT -l is normally faster and better if it is available, but not all FTP
  servers support it.
- Base path: The default path that should be listed first when browsing the
  site, or changed into by default when performing raw commands.
- CEPR supported: Custom Extended Passive Reply is an extension of the EPSV
  command to make its response include the address to connect to. This setting
  is required for IPv6 transfers to/from another address than the main site
  address, for example when the site uses an FTP bouncer or when the transfer
  protocol is different from the control connection protocol.
- SSCN supported: SSCN is a special command used for TLS FXP transfers.
  Not all servers support this, but it should be enabled if it is supported.
- CPSV supported: CPSV is a special command used for TLS FXP transfers.
  Not all servers support this, but it should be enabled if it is supported.
- Force binary mode: Force the site to use binary mode for transfers. This
  is normally the default, but on some FTP servers it is not, in which case
  this option should be enabled.
- Broken PASV: Enable this option if the site reports a bad passive IP or
  does not allow connections on the host/ports it provides.
- Max idle time: The number of seconds that the site will stay connected
  before logging out if there's nothing to do.
- Use XDUPE: This is a special command that reduces control overhead during
  multi-file transfers, but few servers support it.
- Needs PRET: PRET is a special command needed for transfers on distributed
  FTP servers such as DrFTPD. Should be enabled on such sites, and disabled
  on all others.
- Proxy: select which proxy (if any) to use for control connections to this
  site.
- Data proxy: select which proxy (if any) to use for data connections to this
  site.
- Configure skiplist: Set up a skiplist specific to this site. In most cases,
  using the global skiplist is preferred instead.
- Disabled: Disables a site from participating in spread jobs.
- Allow upload: Whether to allow uploading to the site during spread jobs.
- Allow download: Whether to allow downloading from the site during spread
  jobs. Can also be set to "Affils only" to only allow downloading of affil
  releases.
- Priority: How important the site is considered to be during spread jobs.
  The priority is factored into the transfer scoring - you can read more about
  this in the "the transfer engine" section.
- List frequency: The rate of file list refreshes during active spread jobs.
  Dynamic mode is normally optimal and based on current cpu load (low load = 
  higher refresh rate). Having too many sites at a fixed high refresh rate may
  overload the cpu and cause unwanted latency.
- Transfer source policy: Sets whether to have a block list or an allow list
  of sites to transfer with. Setting the policy to "allow" means the
  list below will be a block list, and vice versa.
- Transfer target policy: Same as above but when the site is acting as a
  destination for a transfer rather than a source.
- Block transfers from: The list mentioned above.
- Block transfers to: The list mentioned above.
- Affils: Which groups that pre on the site. Set this list properly to avoid
  uploading into affil releases.
- Configure sections: Set sections/bookmarks for the site. Spread jobs use
  sections to match dirs together between sites, i.e. creating a section with
  the same name on different sites and then using that section in a spread job
  will result in the job operating in the specified section directory for
  each site.

## GLOBAL OPTIONS

Most global cbftp settings can be accessed by pressing G from the main screen.
When you are done editing, press 'd' to save changes.

Field summary:

- Default network interface - The network interface that cbftp will bind to
  by default. Useful if you have multiple usable network interfaces, otherwise
  you can ignore this setting.
- Local transfer protocol - Preferred/supported protocol IPv4/IPv6 for local
  downloads/uploads and file lists (with LIST).
- Active mode port range - The ports that cbftp will use for active mode
  connections. If you are behind a NAT gateway, you will need to forward
  those ports to your local machine in the gateway. Note that cbftp does not
  use active mode by default - only when a site has 'Broken PASV' enabled.
- Use active mode address - see below
- Active mode address IPv4 - The address to report for active mode connections.
  If you are behind a NAT gateway, you will need to set this to your external
  IP address (check whatismyip.com). Note that cbftp does not use active mode
  by default - only when a site has 'Broken PASV' enabled.
- Active mode address IPv6 - same as above but for IPv6 transfers.
- Enable HTTPS/JSON API - Whether or not to listen on TCP for remote commands.
- HTTPS/JSON API Port: the TCP port to listen for remote commands on.
- Enable UDP API - Whether or not to listen on UDP for remote commands.
- UDP API port - the UDP port to listen for remote commands on.
- API password - the password that should be provided in remote commands for
  cbftp to accept them.
- Remote command bell - Trigger the terminal bell when remote commands that
  require user action arrive.
- Prepared spread job expiration time - The time that a prepared spread job
  will remain available on the main screen before it disappears.
- Next prepared spread job starter timeout - The duration that the next
  prepared spread job starter (N) will stay active if no spread job appears.
- Spread job history: The maximum number of spread jobs to keep in history.
- Transfer job history: The maximum number of transfer jobs to keep in history.
- Transfer history: The maximum number of transfers to keep in history.
- Log buffer history: The maximum number of log lines to keep in log buffers.
- Legend bar - the mode of operation for the legend bar.
- Default site - default values when creating a new site.
- Download path - the default download path that cbftp should use for
  download jobs.
- Configure skiplist - enters a new screen that lets you configure the global
  skiplist.
- Configure proxy settings - add or remove proxies that can be used by sites.
- Configure file viewing - specify which file types that should be opened
  with what applications. Only applicable when running in a local terminal.
- Configure global keybinds - specify hotkeys that are globally available
  throughout the ui.
- Enable/Disable data file encryption - Change the encryption state of the
  data file.
- Change encryption key - Set a new encryption key for the data file.

## TRANSFERS

The transfers screen is available by pressing 't' from the main screen.
this screen presents a summary of the transfers that cbftp is performing,
and has performed previously. Select a transfer and press enter for detailed
information about that specific transfer.

## GLOBAL KEY BINDINGS

There are a few hotkeys that work from (almost) anywhere in the cbftp UI:

`\` - Toggle fullscreen mode (i.e. hide info bar + legend bar).

`p` - Start the latest prepared spread job.

`N` - Toggle the next prepared spread job auto starter. While this function is
    enabled, the next 'prepare' remote command that arrives will be started
    immediately. The toggle times out after 10 minutes.

`-` - Highlight the entire table line. Usable in lists, tables etc where it
    might be hard to tell which items that are on the same line

They can be configured through the global options screen.

## METRICS

In the metrics screen, there are a few metrics shown as graphs:

- CPU load total: the total CPU usage of the cbftp process, for all CPU cores.
  (100% load on all cores => 100% in this metric)
- CPU load worker: The load of the worker thread in cbftp.
- Performance level: an internal level used for deciding file list frequency
  during spread jobs on sites where dynamic list frequency is specified.
  High CPU load causes the level to drop, and it will rise back up again
  once the CPU load shrinks. The idea is to avoid full load on the CPU since
  it results in latency when work is queued up, and slightly lower list
  frequency is often preferable over latency.

## SPREAD JOB STATUS

The spread job status screen has a table of files that might seem rather
unintelligible at a glance.

The table shows all files in the job and their status on all sites.
Each row represents a site and each column represents a file. The three
characters above each table column vertically represents a unique pattern as a
way to identify the file. For example, a directory containing rar archives
with the same name except for the file name extension will show the file name
extension there - rar, r01, r02 etc, since that is the only unique pattern to be
found. For other kinds content, the unique tag may be found elsewhere in the
file names.

Example:

```
         rrrrr        
         a0000  <-- unique file name pattern: *.rar, *.r00, *.r01, *.r02, *.r03
         r0123
 SITE1 / .UooU
 SITE2 / ....u <--- file markers
 SITE3 / .Do.d
```

The single character marking each file describes the state of the file:

`_` - file does not exist

`.` - file exists

`o` - you own this file

`u` - someone is uploading this file

`U` - you are uploading this file

`d` - you are downloading this file

`D` - you are downloading this file and you also own it

`s` - you are downloading this file that someone else is uploading

`S` - you are uploading and downloading this file

`p` - file exists and the site is download-only in this job

## EXTERNAL SCRIPTS

Cbftp can be configured to execute external scripts based on certain triggers.
There is an intended default directory for scripts at ~/.cbftp/scripts, but
they may be placed anywhere. The scripts may be written in any language, the
only requirement is that they are saved as executable files - a hashbang
specifier at the first line of the file along with execute permission will be
required for scripting languages.

Information regarding the reason for execution is provided in args to the
script.
Scripts are meant to communicate with cbftp using the API. The script will be
provided with a temporary API auth token that only works for the duration of
the script, to avoid having to store the API password in the script itself.
The args to the scripts are: <api-token> <trigger> [various trigger args]

Currently, external scripts are available in the browse screen. Press x
while browsing to configure scripts, and then go to the keybinds screen to bind
a key for executing the script.
An example script execution from there might have the following args:

`<api-token> browse-site <site> <path> <selected-items>`

Example scripts are available in the examples directory.

## OTHER UI WINDOWS

There are various other views in the cbftp UI that are not mentioned here in
this readme, but most are quite self-explanatory with the help of the key
binding information found in the legend bar. You can probably figure it out.

## FAQ

Q: Why aren't my IPv6 transfers working?

A: The site(s) or your local system may not be configured with working IPv6
   connectivity, or the site(s) might not include an address in its EPSV
   response. Make sure that CEPR is enabled and that the site responds with an
   address in the EPSV command response, and that the address returned is
   connectable.

Q: What key should I press to do xyz?

A: A full keybind summary and configuration for the current screen is available
   by pressing '?'. You can also see keybinds in the legend bar at the bottom.

Q: My modifications are not saved when I edit a setting/site/whatever!

A: You usually need to press 'd' (as in Done) to save settings when editing.
   Pressing c or escape normally means cancel without saving changes.

Q: Can I change key bindings?

A: Yes, press '?' to see and edit keybindings for the current screen.

Q: Some fields do not seem to be visible in the UI, or are disappearing
   sometimes. What's going on?

A: Cbftp adjusts the view dynamically depending on how much space is needed
   to show the fields, and how much space is available. The fields shown
   are chosen based on an internal priority specification. Make your terminal
   larger!

Q: What is the difference between fixed and dynamic list frequency? And what
   does auto mean in this context?

A: Dynamic list frequency means that the number of times per second that cbftp
   will refresh file lists on that site will drop voluntarily if the CPU load
   gets too high, but also that it refreshes a little faster than its fixed
   counterpart otherwise. This is in theory a good thing since lower rate is
   usually preferred over added latency. Fixed list frequency is the opposite:
   it will always attempt to refresh a fixed number of times per second. Very
   high means about 20 times per second for both fixed and dynamic. Very low
   means once per second, and the rest of the options are somewhere in between.
   Auto means a dynamic rate matching the priority of the site, but not higher
   than "normal". The auto mode is meant to be a balanced setting that works
   very well in most scenarios.

Q: Cbftp looks weird. It shows things like ljljljljljljljljlj in various
   places. And/or I can't see the snake when trying to play snake. Why?

A: Cbftp is meant to be displayed with unicode. Somewhere between cbftp and
   your terminal emulator, there is a component that strips unicode characters
   away. It could be that your system locale is not set to UTF-8, that your
   screen or tmux doesn't have UTF-8 enabled, that the ncurses build on your
   system doesn't support wide characters, that your ssh client gui application
   doesn't use UTF-8... Go through every step of the way and make sure that
   unicode/UTF-8 support is enabled everywhere.

Q: Cbftp gets SSL/TLS error when connecting to some of my sites, what should I
   do?

A: Your system is probably using an old version of OpenSSL. Either upgrade
   to a newer system version, or grab a copy of the latest OpenSSL version
   from openssl.org, compile it (./config && make) and then let cbftp know
   that it should use that by modifying the top line of Makefile.inc in the
   cbftp root dir, and then rebuild cbftp.

Q: Is there some raw connection data output available anywhere?

A: Yes, see the "connection details" section above.

Q: How can I see which chains cbftp is using?

A: Cbftp doesn't really use chains in the traditional sense. See the "the
   transfer engine" section further up in this file.
   You can see current transfers and their source/destination by pressing t
   from the main screen.

Q: What's the difference between 'race' and 'distribute' when starting a
   spread job?

A: The profile affects the algorithm that assigns scores to potential
   transfers. The 'race' profile focuses on uploading more files than other
   users everywhere, while the 'distribute' profile focuses on finishing the
   job on all sites as quickly as possible.

Q: What is the block of seemingly random characters above the spread job status
   table supposed to be?

A: Read each column from top to bottom. Cbftp attempts to describe each file
   in the job by finding a sequence of 3 characters in the file name that are
   unique to that file. In many cases it will be the file suffix, or maybe
   some kind of numbering. See the "spread job status" section above.

Q: Can I use multiple addresses (bouncers) to a site? How do I sort them?

A: Yes, just add them all on the address line with spaces between. Cbftp does
   actually have a built-in sorting feature, but it's hard to spot. By default
   cbftp will attempt to connect on the first address in the list. If it does
   not manage to connect within 1 second, cbftp will attempt to connect on any
   other addresses as well. Whichever address manages to connect first will
   be stored first in the list for next time.

Q: I have so many spread jobs running! Why won't they finish?

A: Cbftp tries its best to make sure that all files are uploaded on all
   involved sites. As long as any site does not have all files, cbftp will
   keep trying to upload (until a reasonable amount of attempts have been
   made). If a lot of jobs are started simultaneously and one or more sites
   can't keep up, there will be lots of running jobs.

Q: I have a spread job that says 100% done but is still running, why?

A: Cbftp needs to list the directories for a few seconds after all files
   in a spread job have been uploaded to make sure that the directory is
   completed. If all slots for any involved site are busy doing other things,
   like transferring files in other jobs, then the job will stay running
   until that site has time to list the directory.

Q: My spread jobs end in timeout instead of "done", what's wrong?

A: Usually this happens because one or more sites cannot finish the job
   due to being down, out of space, not having any transfer sources, or some
   other reason for not being able to receive files. Another common reason
   is that some unwanted files were uploaded on one or several sites during the
   job, and cb will then expect those files to be uploaded to all other sites
   as well before considering the job done, which may not always be possible.
   Make sure to skiplist anything unwanted!

Q: One or several sites is executing STAT/LIST commands over and over, why?

A: During a spread job, cbftp uses connections that are currently not busy
   performing file transfers for continuously listing the spread job
   directories. This information is then used for calculating the transfer
   speeds of ongoing transfers, figuring out which files to transfer next,
   and so on. It is completely normal.

Q: How do I disconnect from a site?

A: Disconnecting is an old habit that comes from traditional clients that
   "lock" slots to the user interface. Cbftp does not do this, and there's
   really no gain in disconnecting manually. Cbftp will disconnect by itself
   after a while. If you really want to disconnect manually you can press K
   from the main screen. To disconnect single conections, press enter
   on the site from the main screen, use the arrow keys to navigate to the
   right connection, and then press d.

Q: How do I exit cbftp? Do I need to save the data file somehow?

A: press ctrl-c. The data file is written automatically once in a while
   when cbftp is running, and upon exit.

Q: Can I edit the data file manually?

A: Yes, there are tools provided for that: bin/datafilecat and
   bin/datafilewrite. You can also read the file directly through OpenSSL
   commands:
   openssl enc -d -aes-256-cbc -pbkdf2 -md sha256 -in ~/.cbftp/data

Q: Can I run cbftp on Windows?

A: Yes, it should work through cygwin, but it hasn't been tested lately and
   the polling mechanism available there is not as efficient.

Q: Can I share this software with others?

A: Sure, go ahead.

Q: Will feature X be added soon?

A: I'm open to all kinds of suggestions, but I have very little spare time
   and development is therefore rather slow.

Q: How do I upgrade to a newer version?

A: Just compile and run the new version. The data file will be adjusted to
   the new format if necessary. But CAREFUL! Do not start an older version
   again after this, as this might result in some information being lost
   from the data file. Make a backup of the data file (~/.cbftp/data) if you
   are uncertain or want to try things out.

Q: Can I make modifications to cbftp?

A: That's why the source code is provided! If you are adding things that
   would be useful for others, make sure to pass your changes back upstream,
   and they might end up in the upstream source tree eventually.

Q: Where can I donate to show my support for this awesome software?

A: No need, I mostly do this for my own amusement.

## LICENSING
CBFTP is distributed under an Open Source license.
See the file LICENSE in the CBFTP source distribution
for information on terms &amp; conditions for accessing and
otherwise using CBFTP and for a DISCLAIMER OF ALL WARRANTIES.

## BUGS
Submit bug reports online at:

https://github.com/doctorfree/Asciiville/issues

## SEE ALSO
**asciiart**(1), **asciimpplus**(1), **asciiplasma**(1), **asciisplash**(1), **asciisplash-tmux**(1), **asciiville**(1)

Full documentation and sources at:

https://github.com/doctorfree/Asciiville
