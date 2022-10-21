# Newsboat

Newsboat is an RSS/Atom feedreader. RSS and Atom are a number of widely-used XML formats to transmit, publish and syndicate articles, for example news or blog articles. Newsboat is designed to be used on text terminals on Unix or Unix-like systems such as GNU/Linux, FreeBSD or macOS.

Website: https://newsboat.org/

FAQ: https://newsboat.org/releases/2.29/docs/faq.html

Documentation: https://newsboat.org/releases/2.29/docs/newsboat.html

## Contents

1. [Feed format](#feed-format)
1. [Example configuration](#example-configuration)
1. [Urls](#urls)
1. [Keys](#keys)
1. [See also](#see-also)

## Feed format

```
<url> [<tag1> <tag2> ...]
```

## Example configuration

```
#
# Default Newsboat config
#
####  always-display-description
#
# If set to `yes`, then the description will always be displayed even if e.g. a
# `<content:encoded>` tag has been found.
#
# Syntax: [yes/no]
#
# Default value: no
#
# always-display-description yes

####  always-download
#
# The parameters of this configuration command are one or more RSS URLs. These
# URLs will always get downloaded, regardless of their Last-Modified timestamp
# and ETag header.
#
# Syntax: <url> [<url>]
#
# Default value: n/a
#
# always-download "http://www.n-tv.de/23.rss"

####  article-sort-order
#
# The <sortfield> specifies which article property shall be used for sorting,
# currently available are: `date`, `title`, `flags`, `author`, `link`, `guid`
# and `random`. The optional <direction> specifies the sort direction. `asc`
# specifies ascending sorting, `desc` specifies descending sorting. Note that
# direction does not affect `random` sort order. For `date`, `desc` is default,
# for all others, `asc` is default.
#
# Syntax: <sortfield>[-<direction>]
#
# Default value: date
#
# article-sort-order author-desc

####  articlelist-format
#
# This variable defines the format of entries in the article list. See the
# respective section in the documentation for more information on format
# strings.
#
# Syntax: <format>
#
# Default value: "%4i %f %D %6L  %?T?|%-17T|  ?%t"
#
# articlelist-format "%4i %f %D   %?T?|%-17T|  ?%t"
articlelist-format "%f%?T?%-14T ? %t%> %D"

####  articlelist-title-format
#
# Format of the title in article list. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Articles in feed '%T' (%u unread, %t total) - %U"
#
# articlelist-title-format "Articles in feed '%T' (%u unread)"

####  auto-reload
#
# If set to `yes`, all feeds will be automatically reloaded at start up and
# then continuously after a certain time has passed (see `reload-time`).
#
# Syntax: [yes/no]
#
# Default value: no
#
auto-reload yes

####  bookmark-autopilot
#
# If set to `yes`, the configured bookmark command is executed without any
# further input asked from user, unless the url or the title cannot be
# found/guessed.
#
# Syntax: [yes/no]
#
# Default value: no
#
bookmark-autopilot yes

####  bookmark-cmd
#
# If set, then <command> will be used as bookmarking plugin. See the
# documentation on bookmarking for further information.
#
# Syntax: <command>
#
# Default value: ""
#
# bookmark-cmd "~/bin/delicious-bookmark.sh"
# bookmark-cmd "~/.config/newsboat/scripts/vimwiki"
bookmark-cmd ~/.config/newsboat/bookmark.sh

####  bookmark-interactive
#
# If set to `yes`, then the configured bookmark command is an interactive
# program.
#
# Syntax: [yes/no]
#
# Default value: no
#
# bookmark-interactive yes
bookmark-interactive no

####  browser
#
# Set the browser command to use when opening an article in the browser. If
# BROWSER environment variable is set, it will be used as the default browser,
# otherwise lynx will be used. Any occurrences of `%u` in <command> will be
# replaced by a URL in single quotes.
#
# Syntax: <command>
#
# Default value: %BROWSER, otherwise lynx
#
# browser "w3m %u"
browser "~/.config/newsboat/browser.sh"

####  cache-file
#
# This configuration option sets the cache file. This is especially useful if
# the filesystem of your home directory doesn't support proper locking (e.g.
# NFS).
#
# Syntax: <path>
#
# Default value: "~/.config/newsboat/cache.db"
#
# cache-file "/tmp/testcache.db"

####  cleanup-on-quit
#
# If set to `yes`, then the cache gets locked and superfluous feeds and items
# are removed, such as feeds that can't be found in the urls configuration file
# anymore.
#
# Syntax: [yes/no]
#
# Default value: yes
#
cleanup-on-quit yes

####  color
#
# Set the foreground color, background color and optional attributes for a
# certain element.
#
# Syntax: <element> <fgcolor> <bgcolor> [<attribute> ...]
#
# Default value: n/a
#
# color background white black

####  confirm-exit
#
# If set to `yes`, then newsboat will ask for confirmation whether the user
# really wants to quit newsboat.
#
# Syntax: [yes/no]
#
# Default value: no
#
# confirm-exit yes
confirm-exit no

####  cookie-cache
#
# Set a cookie cache. If set, cookies will be cached in (i.e. read from and
# written to) this file, using http://www.cookiecentral.com/faq/#3.5[Netscape
# format].
#
# Syntax: <path>
#
# Default value: ""
#
# cookie-cache "~/.config/newsboat/cookies.txt"

####  datetime-format
#
# This format specifies the date/time format in the article list. For a
# detailed documentation on the allowed formats, consult the manpage of
# strftime(3).
#
# Syntax: <date/time format>
#
# Default value: %b %d
#
# datetime-format "%D, %R"
datetime-format "%Y-%m-%d"

####  define-filter
#
# With this command, you can predefine filters, which you can later select from
# a list, and which are then applied after selection. This is especially useful
# for filters that you need often and you don't want to enter them every time
# you need them.
#
# Syntax: <name> <filterexpr>
#
# Default value: n/a
#
# define-filter "all feeds with 'fun' tag" "tags # \"fun\""

####  delete-read-articles-on-quit
#
# If set to `yes`, then all read articles will be deleted when you quit
# newsboat.
#
# Syntax: [yes/no]
#
# Default value: no
#
delete-read-articles-on-quit yes

####  dialogs-title-format
#
# Format of the title in dialog list. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Dialogs"
#
# dialogs-title-format "%N %V - Dialogs"

####  dirbrowser-title-format
#
# Format of the title in directory browser. See "Format Strings" section of
# Newsboat manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - %?O?Open Directory&Save File? - %f"
#
# dirbrowser-file-format "%?O?Open Directory&Save File? - %f"

####  display-article-progress
#
# If set to `yes`, then a read progress (in percent) is displayed in the
# article view. Otherwise, no read progress is displayed.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# display-article-progress no

####  download-full-page
#
# If set to `yes`, then for all feed items with no content but with a link, the
# link is downloaded and the result used as content instead. This may
# significantly increase the download times of "empty" feeds.
#
# Syntax: [yes/no]
#
# Default value: no
#
# download-full-page yes

####  download-retries
#
# How many times newsboat shall try to successfully download a feed before
# giving up. This is an option to improve the success of downloads on slow and
# shaky connections such as via a TOR proxy.
#
# Syntax: <number>
#
# Default value: 1
#
download-retries 4

####  download-timeout
#
# The number of seconds newsboat shall wait when downloading a feed before
# giving up. This is an option to improve the success of downloads on slow and
# shaky connections such as via a TOR proxy.
#
# Syntax: <number>
#
# Default value: 30
#
download-timeout 10

####  error-log
#
# If set, then user errors (e.g. errors regarding defunct RSS feeds) will be
# logged to this file.
#
# Syntax: <path>
#
# Default value: ""
#
# error-log "~/.config/newsboat/error.log"

####  external-url-viewer
#
# If set, then `show-urls` will pipe the current article to a specific external
# tool instead of using the internal URL viewer. This can be used to integrate
# tools such as urlview and urlscan.
#
# Syntax: <command>
#
# Default value: ""
#
# external-url-viewer "urlview"
external-url-viewer "urlscan"

####  feed-sort-order
#
# The <sortfield> specifies which feed property shall be used for sorting;
# currently available are: `firsttag`, `title`, `articlecount`,
# `unreadarticlecount`, `lastupdated` and `none`. The optional <direction>
# specifies the sort direction. `asc` specifies ascending sorting, `desc`
# specifies descending sorting. `desc` is the default.
#
# Syntax: <sortorder>[-<direction>]
#
# Default value: none
#
# feed-sort-order firsttag
feed-sort-order unreadarticlecount-asc

####  feedhq-flag-share
#
# If set and FeedHQ support is used, then all articles that are flagged with
# the specified flag are being "shared" in FeedHQ so that people that follow
# you can see it.
#
# Syntax: <flag>
#
# Default value: ""
#
# feedhq-flag-share "a"

####  feedhq-flag-star
#
# If set and FeedHQ support is used, then all articles that are flagged with
# the specified flag are being "starred" in FeedHQ and appear in the list of
# "Starred items".
#
# Syntax: <flag>
#
# Default value: ""
#
# feedhq-flag-star "b"

####  feedhq-login
#
# This variable sets your FeedHQ login for FeedHQ support.
#
# Syntax: <login>
#
# Default value: ""
#
# feedhq-login "your-login"

####  feedhq-min-items
#
# This variable sets the number of articles that are loaded from FeedHQ per
# feed.
#
# Syntax: <number>
#
# Default value: 20
#
# feedhq-min-items 100

####  feedhq-password
#
# This variable sets your FeedHQ password for FeedHQ support. Double quotes
# should be escaped, i.e. you should write `\"` instead of `"`.
#
# Syntax: <password>
#
# Default value: ""
#
# feedhq-password "here_goesAquote:\""

####  feedhq-passwordfile
#
# A more secure alternative to the above, by storing your password elsewhere in
# your system.
#
# Syntax: <path>
#
# Default value: ""
#
# feedhq-passwordfile "~/.config/newsboat/feedhq-pw.txt"

####  feedhq-passwordeval
#
# Another secure alternative, is providing your password from an external
# command that is evaluated during login. This can be used to read your
# password from a gpg encrypted file or your system keyring.
#
# Syntax: <command>
#
# Default value: ""
#
# feedhq-passwordeval "gpg --decrypt ~/.config/newsboat/feedhq-password.gpg"

####  feedhq-show-special-feeds
#
# If set and FeedHQ support is used, then "special feeds" like "People you
# follow" (articles shared by people you follow), "Starred items" (your starred
# articles) and "Shared items" (your shared articles) appear in your
# subscription list.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# feedhq-show-special-feeds "no"

####  feedhq-url
#
# Configures the URL where your FeedHQ instance resides.
#
# Syntax: <url>
#
# Default value: "https://feedhq.org/"
#
# feedhq-url "https://feedhq.example.com/"

####  feedlist-format
#
# This variable defines the format of entries in the feed list. See the
# respective section in the documentation for more information on format
# strings.
#
# Syntax: <format>
#
# Default value: "%4i %n %11u %t"
#
# feedlist-format " %n %4i - %11u -%> %t"

####  feedlist-title-format
#
# Format of the title in feed list. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "N %V - Your feeds (%u unread, %t total)%?T? - tag `%T'&?"
#
# feedlist-title-format "Feeds (%u unread, %t total)"

####  filebrowser-title-format
#
# Format of the title in file browser. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - %?O?Open File&Save File? - %f"
#
# filebrowser-title-format "%?O?Open File&Save File? - %f"

####  goto-first-unread
#
# If set to `yes`, then the first unread article will be selected whenever a
# feed is entered.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# goto-first-unread no

####  goto-next-feed
#
# If set to `yes`, then the next-unread, prev-unread and random-unread keys
# will search in other feeds for unread articles if all articles in the current
# feed are read. If set to `no`, then these keys will stop in the current feed.
#
# Syntax: [yes/no]
#
# Default value: yes
#
goto-next-feed no

####  help-title-format
#
# Format of the title in help window. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Help"
#
# help-title-format "%N %V - Help"

####  highlight
#
# With this command, you can highlight text parts in the feed list, the article
# list and the article view. For a detailed documentation, see the chapter on
# highlighting.
#
# Syntax: <target> <regex> <fgcolor> [<bgcolor> [<attribute> ...]]
#
# Default value: n/a
#
# highlight all "newsboat" red

####  highlight-article
#
# With this command, you can highlight articles in the article list if they
# match a filter expression. For a detailed documentation, see the chapter on
# highlighting.
#
# Syntax: <filterexpr> <fgcolor> <bgcolor> [<attribute> ...]
#
# Default value: n/a
#
# highlight-article "author =~ \"Andreas Krennmair\"" white red bold

####  history-limit
#
# Defines the maximum number of entries of commandline resp. search history to
# be saved. To disable history saving, set it to 0.
#
# Syntax: <number>
#
# Default value: 100
#
# history-limit 0

####  html-renderer
#
# If set to `internal`, then the internal HTML renderer will be used.
# Otherwise, the specified command will be executed, the HTML to be rendered
# will be written to the command's stdin, and the program's output will be
# displayed. This makes it possible to use other, external programs, such as
# w3m, links or lynx, to render HTML.
#
# Syntax: <command>
#
# Default value: internal
#
# html-renderer "w3m -dump -T text/html"

####  http-auth-method
#
# Set HTTP authentication method. Allowed values: `any`, `basic`, `digest`,
# `digest_ie` (only available with libcurl 7.19.3 and newer), `gssnegotiate`,
# `ntlm` and `anysafe`.
#
# Syntax: <method>
#
# Default value: any
#
# http-auth-method digest

####  ignore-article
#
# If a downloaded article from <feed> matches <filterexpr>, then it is ignored
# and not presented to the user. This command is further explained in the "kill
# file" section below.
#
# Syntax: <feed> <filterexpr>
#
# Default value: n/a
#
# ignore-article "*" "title =~ \"Windows\""

####  ignore-mode
#
# This configuration option defines in what way an article is ignored (see
# `ignore-article`). If set to `download`, then it is ignored in the
# download/parsing phase and thus never written to the cache, if it set to
# `display`, it is ignored when displaying articles but is kept in the cache.
#
# Syntax: [download/display]
#
# Default value: download
#
# ignore-mode "display"
ignore-mode "download"

####  include
#
# With this command, you can include other files to be interpreted as
# configuration files. This is especially useful to separate your configuration
# into several files, e.g. key configuration, color configuration, ...
#
# Syntax: <path>
#
# Default value: n/a
#
include ~/.config/newsboat/keys
# include "~/.config/newsboat/colors"
# include "~/.config/newsboat/colorschemes/commander
include "~/.config/newsboat/colorschemes/cyanism
# include "~/.config/newsboat/colorschemes/greenscreen
# include "~/.config/newsboat/colorschemes/gruvbox
# include "~/.config/newsboat/colorschemes/inkpot
# include "~/.config/newsboat/colorschemes/kinda-maia
# include "~/.config/newsboat/colorschemes/light
# include "~/.config/newsboat/colorschemes/nord
# include "~/.config/newsboat/colorschemes/plain
# include "~/.config/newsboat/colorschemes/psychedelic
# include "~/.config/newsboat/colorschemes/schleichfahrt
# include "~/.config/newsboat/colorschemes/simple
# include "~/.config/newsboat/colorschemes/solarized-dark
# include "~/.config/newsboat/colorschemes/solarized-light
# include "~/.config/newsboat/colorschemes/universal-color

####  itemview-title-format
#
# Format of the title in article view. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Article '%T' (%u unread, %t total)"
#
# itemview-title-format "Article '%T'"

####  inoreader-flag-share
#
# If set and Inoreader support is used, then all articles that are flagged with
# the specified flag are being "shared" in Inoreader so that people that follow
# you can see it.
#
# Syntax: <flag>
#
# Default value: ""
#
# inoreader-flag-share "a"

####  inoreader-flag-star
#
# If set and Inoreader support is used, then all articles that are flagged with
# the specified flag are being "starred" in Inoreader and appear in the list of
# "Starred items".
#
# Syntax: <flag>
#
# Default value: ""
#
# inoreader-flag-star "b"

####  inoreader-login
#
# This variable sets your Inoreader login for Inoreader support.
#
# Syntax: <login>
#
# Default value: ""
#
# inoreader-login "your-login"

####  inoreader-min-items
#
# This variable sets the number of articles that are loaded from Inoreader per
# feed.
#
# Syntax: <number>
#
# Default value: 20
#
# inoreader-min-items 100

####  inoreader-password
#
# This variable sets your Inoreader password for Inoreader support. Double
# quotes should be escaped, i.e. you should write `\"` instead of `"`.
#
# Syntax: <password>
#
# Default value: ""
#
# inoreader-password "here_goesAquote:\""

####  inoreader-passwordfile
#
# A more secure alternative to the above, by storing your password elsewhere in
# your system.
#
# Syntax: <path>
#
# Default value: ""
#
# inoreader-passwordfile "~/.config/newsboat/inoreader-pw.txt"

####  inoreader-passwordeval
#
# Another secure alternative, is providing your password from an external
# command that is evaluated during login. This can be used to read your
# password from a gpg encrypted file or your system keyring.
#
# Syntax: <command>
#
# Default value: ""
#
# inoreader-passwordeval "gpg --decrypt ~/.config/newsboat/inoreader-password.gpg"

####  inoreader-show-special-feeds
#
# If set and Inoreader support is used, then "special feeds" like "Starred
# items" (your starred articles) and "Shared items" (your shared articles)
# appear in your subscription list.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# inoreader-show-special-feeds "no"

####  keep-articles-days
#
# If set to a number greater than 0, only articles that are were published
# within the last <number> days are kept, and older articles are deleted. If
# set to 0, this option is not active. Note that changing this setting won't
# bring back the articles that were deleted earlier; currently, there's no
# non-hacky way to bring back deleted articles.
#
# Syntax: <number>
#
# Default value: 0
#
# keep-articles-days 30

####  macro
#
# With this command, you can define a macro key and specify a list of commands
# that shall be executed when the macro prefix and the macro key are pressed.
#
# Syntax: <macro key> <command list>
#
# Default value: n/a
#
# macro k open ; reload ; quit
macro i set pager "~/.config/newsboat/kitty-img-pager.sh"; open; set pager internal
macro f set browser firefox ; open-in-browser ; set browser "~/.config/newsboat/browser.sh"
macro w set browser w3m ; open-in-browser ; set browser "~/.config/newsboat/browser.sh"

####  mark-as-read-on-hover
#
# If set to `yes`, then all articles that get selected in the article list are
# marked as read.
#
# Syntax: [yes/no]
#
# Default value: no
#
# mark-as-read-on-hover yes

####  max-download-speed
#
# If set to a number great than 0, the download speed per download is set to
# that limit (in kB).
#
# Syntax: <number>
#
# Default value: 0
#
# max-download-speed 50

####  max-browser-tabs
#
# Set the maximum number of articles to open in a browser when using the
# `open-all-unread-in-browser` or `open-all-unread-in-browser-and-mark-read`
# commands.
#
# Syntax: <number>
#
# Default value: 10
#
# max-browser-tabs 4

####  max-items
#
# Set the number of articles to maximally keep per feed. If the number is set
# to 0, then all articles are kept.
#
# Syntax: <number>
#
# Default value: 0
#
# max-items 100

####  newsblur-login
#
# This variable sets your NewsBlur login for NewsBlur support.
#
# Syntax: <login>
#
# Default value: ""
#
# newsblur-login "your-login"

####  newsblur-min-items
#
# This variable sets the number of articles that are loaded from NewsBlur per
# feed.
#
# Syntax: <number>
#
# Default value: 20
#
# newsblur-min-items 100

####  newsblur-password
#
# This variable sets your NewsBlur password for NewsBlur support. Double quotes
# should be escaped, i.e. you should write `\"` instead of `"`.
#
# Syntax: <password>
#
# Default value: ""
#
# newsblur-password "here_goesAquote:\""

####  newsblur-passwordfile
#
# A more secure alternative to the above, by storing your password elsewhere in
# your system.
#
# Syntax: <path>
#
# Default value: ""
#
# newsblur-passwordfile "~/.config/newsboat/newsblur-pw.txt"

####  newsblur-passwordeval
#
# Another secure alternative, is providing your password from an external
# command that is evaluated during login. This can be used to read your
# password from a gpg encrypted file or your system keyring.
#
# Syntax: <command>
#
# Default value: ""
#
# newsblur-passwordeval "gpg --decrypt ~/.config/newsboat/newsblur-password.gpg"

####  newsblur-url
#
# Configures the URL where the NewsBlur instance resides.
#
# Syntax: <url>
#
# Default value: "https://newsblur.com"
#
# newsblur-url "https://localhost"

####  notify-always
#
# If set to `no`, notifications will only be made when there are new feeds or
# articles. If set to `yes`, notifications will be made regardless.
#
# Syntax: [yes/no]
#
# Default value: no
#
# notify-always yes

####  notify-beep
#
# If set to `yes`, then the speaker beep on new articles.
#
# Syntax: [yes/no]
#
# Default value: no
#
# notify-beep yes

####  notify-format
#
# Format string that is used for formatting notifications. See the chapter on
# format strings for more information.
#
# Syntax: <string>
#
# Default value: "newsboat: finished reload, %f unread feeds (%n unread articles total)"
#
# notify-format "%d new articles (%n unread articles, %f unread feeds)"

####  notify-program
#
# If set, then the configured program will be executed if new articles arrived
# (through a reload) or if `notify-always` is `yes`. The first parameter of the
# called program contains the notification message. In order to pass other
# hard-coded arguments to the program, write an appropriate wrapper shell
# script and use it as <command> instead.
#
# Syntax: <command>
#
# Default value: ""
#
# notify-program "~/bin/my-notifier"

####  notify-screen
#
# If set to `yes`, then a "privacy message" will be sent to the terminal,
# containing a notification message about new articles. This is especially
# useful if you use terminal emulations such as GNU screen which implement
# privacy messages.
#
# Syntax: [yes/no]
#
# Default value: no
#
# notify-screen yes

####  notify-xterm
#
# If set to `yes`, then the xterm window title will be set to a notification
# message about new articles.
#
# Syntax: [yes/no]
#
# Default value: no
#
# notify-xterm yes

####  ocnews-flag-star
#
# If set and ownCloud News support is used, then all articles that are flagged
# with the specified flag are being "starred" in ownCloud News.
#
# Syntax: <character>
#
# Default value: ""
#
# ocnews-flag-star "s"

####  ocnews-login
#
# Sets the username to use with the ownCloud instance.
#
# Syntax: <username>
#
# Default value: ""
#
# ocnews-login "user"

####  ocnews-password
#
# Configures the password to use with the ownCloud instance. Double quotes
# should be escaped, i.e. you should write `\"` instead of `"`.
#
# Syntax: <password>
#
# Default value: ""
#
# ocnews-password "here_goesAquote:\""

####  ocnews-passwordfile
#
# A more secure alternative to the above, by storing your password elsewhere in
# your system.
#
# Syntax: <path>
#
# Default value: ""
#
# ocnews-passwordfile "~/.config/newsboat/ocnews-pw.txt"

####  ocnews-passwordeval
#
# Another secure alternative, is providing your password from an external
# command that is evaluated during login. This can be used to read your
# password from a gpg encrypted file or your system keyring.
#
# Syntax: <command>
#
# Default value: ""
#
# ocnews-passwordeval "gpg --decrypt ~/.config/newsboat/ocnews-password.gpg"

####  ocnews-url
#
# Configures the URL where the ownCloud instance resides.
#
# Syntax: <url>
#
# Default value: ""
#
# ocnews-url "https://localhost/owncloud"

####  oldreader-flag-share
#
# If set and The Old Reader support is used, then all articles that are flagged
# with the specified flag are being "shared" in The Old Reader so that people
# that follow you can see it.
#
# Syntax: <flag>
#
# Default value: ""
#
# oldreader-flag-share "a"

####  oldreader-flag-star
#
# If set and The Old Reader support is used, then all articles that are flagged
# with the specified flag are being "starred" in The Old Reader and appear in
# the list of "Starred items".
#
# Syntax: <flag>
#
# Default value: ""
#
# oldreader-flag-star "b"

####  oldreader-login
#
# This variable sets your The Old Reader login for The Older Reader support.
#
# Syntax: <login>
#
# Default value: ""
#
# oldreader-login "your-login"

####  oldreader-min-items
#
# This variable sets the number of articles that are loaded from The Old Reader
# per feed.
#
# Syntax: <number>
#
# Default value: 20
#
# oldreader-min-items 100

####  oldreader-password
#
# This variable sets your The Old Reader password for The Old Reader support.
# Double quotes should be escaped, i.e. you should write `\"` instead of `"`.
#
# Syntax: <password>
#
# Default value: ""
#
# oldreader-password "here_goesAquote:\""

####  oldreader-passwordfile
#
# A more secure alternative to the above, by storing your password elsewhere in
# your system.
#
# Syntax: <path>
#
# Default value: ""
#
# oldreader-passwordfile "~/.config/newsboat/oldreader-pw.txt"

####  oldreader-passwordeval
#
# Another secure alternative, is providing your password from an external
# command that is evaluated during login. This can be used to read your
# password from a gpg encrypted file or your system keyring.
#
# Syntax: <command>
#
# Default value: ""
#
# oldreader-passwordeval "gpg --decrypt ~/.config/newsboat/oldreader-password.gpg"

####  oldreader-show-special-feeds
#
# If set and The Old reader support is used, then "special feeds" like "People
# you follow" (articles shared by people you follow), "Starred items" (your
# starred articles) and "Shared items" (your shared articles) appear in your
# subscription list.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# oldreader-show-special-feeds "no"

####  openbrowser-and-mark-jumps-to-next-unread
#
# If set to `yes`, jump to the next unread item when an item is opened in the
# browser and marked as read.
#
# Syntax: [yes/no]
#
# Default value: no
#
# openbrowser-and-mark-jumps-to-next-unread yes

####  opml-url
#
# If the OPML online subscription mode is enabled, then the list of feeds will
# be taken from the OPML file found on this location. Optionally, you can
# specify more than one URL. All the listed OPML URLs will then be taken into
# account when loading the feed list.
#
# Syntax: <url> ...
#
# Default value: ""
#
# opml-url "http://host.domain.tld/blogroll.opml" "http://example.com/anotheropmlfile.opml"

####  pager
#
# If set to `internal`, then the internal pager will be used. Otherwise, the
# article to be displayed will be rendered to be a temporary file and then
# displayed with the configured pager. If the command is set to an empty
# string, the content of the "PAGER" environment variable will be used. If the
# command contains a placeholder `%f`, it will be replaced with the temporary
# filename.
#
# Syntax: [<command>/internal]
#
# Default value: internal
#
# pager "less %f"

####  podcast-auto-enqueue
#
# If set to `yes`, then all podcast URLs that are found in articles are added
# to the podcast download queue. See the respective section in the
# documentation for more information on podcast support in newsboat.
#
# Syntax: [yes/no]
#
# Default value: no
#
# podcast-auto-enqueue yes

####  prepopulate-query-feeds
#
# If set to `yes`, then all query feeds are prepopulated with articles on
# startup.
#
# Syntax: [yes/no]
#
# Default value: no
#
prepopulate-query-feeds yes

####  ssl-verifyhost
#
# If set to `no`, skip verification of the certificate's name against host.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# ssl-verifyhost no

####  ssl-verifypeer
#
# If set to `no`, skip verification of the peer's SSL certificate.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# ssl-verifypeer no

####  proxy-auth-method
#
# Set proxy authentication method. Allowed values: `any`, `basic`, `digest`,
# `digest_ie` (only available with libcurl 7.19.3 and newer), `gssnegotiate`,
# `ntlm` and `anysafe`.
#
# Syntax: <method>
#
# Default value: any
#
# proxy-auth-method ntlm

####  proxy-auth
#
# Set the proxy authentication string.
#
# Syntax: <auth>
#
# Default value: n/a
#
# proxy-auth user:password

####  proxy-type
#
# Set proxy type. Allowed values: `http`, `socks4`, `socks4a`, `socks5` and
# `socks5h`.
#
# Syntax: <type>
#
# Default value: http
#
# proxy-type socks5

####  proxy
#
# Set the proxy to use for downloading RSS feeds. (Don't forget to actually
# enable the proxy with `use-proxy yes`.)
#
# Syntax: <server:port>
#
# Default value: n/a
#
# proxy localhost:3128

####  refresh-on-startup
#
# If set to `yes`, then all feeds will be reloaded when newsboat starts up.
# This is equivalent to the `-r` commandline option.
#
# Syntax: [yes/no]
#
# Default value: no
#
# refresh-on-startup yes

####  reload-only-visible-feeds
#
# If set to `yes`, then manually reloading all feeds will only reload the
# currently visible feeds, e.g. if a filter or a tag is set.
#
# Syntax: [yes/no]
#
# Default value: no
#
# reload-only-visible-feeds yes

####  reload-threads
#
# The number of parallel reload threads that shall be started when all feeds
# are reloaded.
#
# Syntax: <number>
#
# Default value: 1
#
reload-threads 4

####  reload-time
#
# The number of minutes between automatic reloads.
#
# Syntax: <number>
#
# Default value: 60
#
reload-time 90

####  reset-unread-on-update
#
# With this configuration command, you can provide a list of RSS feed URLs for
# whose articles the unread flag will be reset if an article has been updated,
# i.e. its content has been changed. This is especially useful for RSS feeds
# where single articles are updated after publication, and you want to be
# notified of the updates.
#
# Syntax: <url> ...
#
# Default value: n/a
#
# reset-unread-on-update "http://blog.fefe.de/rss.xml?html"

####  save-path
#
# The default path where articles shall be saved to. If an invalid path is
# specified, the current directory is used.
#
# Syntax: <path-to-directory>
#
# Default value: ~/
#
# save-path "~/Saved Articles"

####  search-highlight-colors
#
# This configuration command specifies the highlighting colors when searching
# for text from the article view.
#
# Syntax: <fgcolor> <bgcolor> [<attribute> ...]
#
# Default value: black yellow bold
#
# search-highlight-colors white black bold

####  searchresult-title-format
#
# Format of the title in search result. See "Format Strings" section of
# Newsboat manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Search result (%u unread, %t total)"
#
# searchresult-title-format "Search result"

####  selectfilter-title-format
#
# Format of the title in filter selection dialog. See "Format Strings" section
# of Newsboat manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Select Filter"
#
# selectfilter-title-format "Select Filter"

####  selecttag-format
#
# Format of the lines in "Select tag" dialog. See the respective section in the
# documentation for more information on format strings.
#
# Syntax: <format>
#
# Default value: "%4i  %T (%u)"
#
# selecttag-format "[%2i] %T (%n unread articles in %f feeds, %u feeds total)"

####  selecttag-title-format
#
# Format of the title in tag selection dialog. See "Format Strings" section of
# Newsboat manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - Select Tag"
#
# selecttag-title-format "Select Tag"

####  show-keymap-hint
#
# If set to `no`, then the keymap hints on the bottom of screen will not be
# displayed.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# show-keymap-hint no

####  show-title-bar
#
# If set to `no`, then the title bar on the top of the screen will not be
# displayed.
#
# Syntax: [yes/no]
#
# Default value: yes
#
# show-title-bar no

####  show-read-articles
#
# If set to `yes`, then all articles of a feed are listed in the article list.
# If set to `no`, then only unread articles are listed.
#
# Syntax: [yes/no]
#
# Default value: yes
#
show-read-articles no

####  show-read-feeds
#
# If set to `yes`, then all feeds, including those without unread articles, are
# listed. If set to `no`, then only feeds with one or more unread articles are
# list.
#
# Syntax: [yes/no]
#
# Default value: yes
#
show-read-feeds no

####  suppress-first-reload
#
# If set to `yes`, then the first automatic reload will be suppressed if
# `auto-reload` is set to `yes`.
#
# Syntax: [yes/no]
#
# Default value: no
#
# suppress-first-reload yes

####  swap-title-and-hints
#
# If set to `yes`, then the title at the top of screen and keymap hints at the
# bottom of screen will be swapped.
#
# Syntax: [yes/no]
#
# Default value: no
#
# swap-title-and-hints yes

####  text-width
#
# If set to a number greater than 0, all HTML will be rendered to this maximum
# line length or the terminal width (whichever is smaller). If set to 0, the
# terminal width will always be used. Does not apply when using external
# renderer or viewing the source. Also note that "Link" header and "Links"
# section won't be affected by it—they contain URLs which are better not
# wrapped.
#
# Syntax: <number>
#
# Default value: 0
#
text-width 80

####  toggleitemread-jumps-to-next-unread
#
# If set to `yes`, jump to the next unread item when an item's read status is
# toggled in the article list.
#
# Syntax: [yes/no]
#
# Default value: no
#
# toggleitemread-jumps-to-next-unread yes

####  ttrss-flag-publish
#
# If set and Tiny Tiny RSS support is used, then all articles that are flagged
# with the specified flag are being marked as "published" in Tiny Tiny RSS.
#
# Syntax: <character>
#
# Default value: ""
#
# ttrss-flag-publish "b"

####  ttrss-flag-star
#
# If set and Tiny Tiny RSS support is used, then all articles that are flagged
# with the specified flag are being "starred" in Tiny Tiny RSS.
#
# Syntax: <character>
#
# Default value: ""
#
# ttrss-flag-star "a"

####  ttrss-login
#
# Sets the username for use with Tiny Tiny RSS.
#
# Syntax: <username>
#
# Default value: ""
#
# ttrss-login "admin"

####  ttrss-mode
#
# Configures the mode in which Tiny Tiny RSS is used. In single-user mode,
# login and password are used for HTTP authentication, while in multi-user
# mode, they are used for authenticating with Tiny Tiny RSS.
#
# Syntax: [multi/single]
#
# Default value: multi
#
# ttrss-mode "single"

####  ttrss-password
#
# Configures the password for use with Tiny Tiny RSS. Double quotes should be
# escaped, i.e. you should write `\"` instead of `"`.
#
# Syntax: <password>
#
# Default value: ""
#
# ttrss-password "here_goesAquote:\""

####  ttrss-passwordfile
#
# A more secure alternative to the above, by storing your password elsewhere in
# your system.
#
# Syntax: <path>
#
# Default value: ""
#
# ttrss-passwordfile "~/.config/newsboat/ttrss-pw.txt"

####  ttrss-passwordeval
#
# Another secure alternative, is providing your password from an external
# command that is evaluated during login. This can be used to read your
# password from a gpg encrypted file or your system keyring.
#
# Syntax: <command>
#
# Default value: ""
#
# ttrss-passwordeval "gpg --decrypt ~/.config/newsboat/ttrss-password.gpg"

####  ttrss-url
#
# Configures the URL where the Tiny Tiny RSS installation you want to use
# resides.
#
# Syntax: <url>
#
# Default value: ""
#
# ttrss-url "http://example.com/ttrss/"

####  urls-source
#
# This configuration command sets the source where URLs shall be retrieved
# from. By default, this is ~/.config/newsboat/urls. Alternatively, you can set it
# to `opml`, which enables newsboat's OPML online subscription mode, to `ttrss`
# which enables newsboat's Tiny Tiny RSS support, to `oldreader`, which enables
# newsboat's The Old Reader support, to `newsblur`, which enables NewsBlur
# support, or `feedhq` for FeedHQ support, or `ocnews` for ownCloud News
# support, or `inoreader` for Inoreader support. Query feed specifications will
# be read from the local urls file regardless of this setting.
#
# Syntax: <source>
#
# Default value: "local"
#
# urls-source "oldreader"

####  urlview-title-format
#
# Format of the title in URL view. See "Format Strings" section of Newsboat
# manual for details on available formats.
#
# Syntax: <format>
#
# Default value: "%N %V - URLs"
#
# urlview-title-format "URLs"

####  use-proxy
#
# If set to `yes`, then the configured proxy will be used for downloading the
# RSS feeds.
#
# Syntax: [yes/no]
#
# Default value: no
#
# use-proxy yes

####  user-agent
#
# If set to a non-zero-length string, this value will be used as HTTP
# User-Agent header for all HTTP requests.
#
# Syntax: <string>
#
# Default value: ""
#
# user-agent "Lynx/2.8.5rel.1 libwww-FM/2.14"
user-agent "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:94.0) Gecko/20100101 Firefox/94.0"

####  miscellaneous
#
confirm-mark-feed-read no
download-path ~/Downloads/
max-downloads 2
scrolloff 50
```

## Urls

Example newsboat `urls` file:

```
# To add URLs that have restricted access via username/password,
# simply provide the username/password in the following way:
#
# http://username:password@hostname.domain.tld/feed.rss
#
# All unread articles in all feeds
#
"query:Unread Articles:unread = \"yes\""
#
#-------------------------
#-------NEWSFEEDS---------
#-------------------------
http://rss.cnn.com/rss/cnn_topstories.rss "~NEWS: CNN"
http://newsrss.bbc.co.uk/rss/newsonline_world_edition/front_page/rss.xml "~NEWS: BBC"
http://www.vox.com/rss/index.xml "~NEWS: VOX"
https://newsboat.org/news.atom "~NEWS: Newsboat"
#-------------------------
#-------YOUTUBE-----------
#-------------------------
https://www.youtube.com/feeds/videos.xml?channel_id=UC1aQCduPHWSXX5UgfHCyVCA "~YOUTUBE: Doctorfree"
#-------------------------
#-------REDDIT------------
#-------------------------
https://www.reddit.com/r/ascii.rss "~REDDIT: r/ascii"
https://www.reddit.com/r/asciiart.rss "~REDDIT: r/asciiart"
https://www.reddit.com/r/commandline.rss "~REDDIT: r/commandline"
https://www.reddit.com/r/linux.rss "~REDDIT: r/linux"
https://www.reddit.com/r/magicmirror.rss "~REDDIT: r/magicmirror"
https://www.reddit.com/r/opensource.rss "~REDDIT: r/opensource"
#-------------------------
#-------TWITTER-----------
#-------------------------
https://nitter.net/search/rss?f=tweets&q=ronrecord "~TWITTER: ronrecord"
#-------------------------
#-------GIT_REPOS---------
#-------------------------
https://github.com/doctorfree.atom "~GITHUB: Doctorfree"
#-------------------------
#-------BLOGS-------------
#-------------------------
https://blog.ronrecord.com/index.php/feed/ "~BLOG: Doctorwhen
https://github.blog/feed/ "~BLOG: Github"
https://github.blog/category/open-source/feed/ "~BLOG: Github Open Source"
#-------------------------
#-------FUN---------------
#-------------------------
http://xkcd.com/atom.xml "~FUN: xkcd"
http://www.dumbingofage.com/feed/ "~FUN: Dumbing of Age"
http://feeds.feedburner.com/oatmealfeed "~FUN: Oatmeal"
http://www.smbc-comics.com/rss.php "~FUN: Saturday Morning Breakfast Cereal"
```

## Keys

Example newsboat `keys` file:

```
####  bind-key
#
# Bind key <key> to <operation>. This means that whenever <key> is pressed,
# then <operation> is executed (if applicable in the current dialog). A list of
# available operations can be found below. Optionally, you can specify a
# dialog. If you specify one, the key binding will only be added to the
# specified dialog. Available dialogs are `all` (default if none is specified),
# `feedlist`, `filebrowser`, `help`, `articlelist`, `article`, `tagselection`,
# `filterselection`, `urlview`, `podbeuter`, and `dirbrowser`.
#
# Syntax: <key> <operation> [<dialog>]
#
# Default value: n/a
#
# bind-key ^R reload-all
bind-key j down feedlist
bind-key k up feedlist
bind-key j next articlelist
bind-key k prev articlelist
bind-key J next-feed articlelist
bind-key K prev-feed articlelist
bind-key j down article
bind-key k up article
bind-key l open
bind-key h quit
bind-key ^D pagedown
bind-key ^U pageup
bind-key b toggle-source-view
bind-key U toggle-show-read-feeds
bind-key u show-urls
bind-key g home
bind-key G end
bind-key b open-in-browser-and-mark-read
bind-key B open-in-browser
bind-key i sort
bind-key I rev-sort
bind-key SPACE toggle-article-read
bind-key a mark-all-above-as-read

####  unbind-key
#
# Unbind key <key>. This means that no operation is called when <key> is
# pressed. If you provide "-a" as <key>, all currently bound keys will become
# unbound. Optionally, you can specify a dialog (for a list of available
# dialogs, see `bind-key` above). If you specify one, the key binding will only
# be unbound for the specified dialog.
#
# Syntax: <key> [<dialog>]
#
# Default value: n/a
#
# unbind-key R
# unbind-key ENTER
unbind-key j
unbind-key k
unbind-key J
unbind-key K
unbind-key ^D
unbind-key ^U
unbind-key o
unbind-key g
unbind-key G
unbind-key C feedlist
```

## See also

- [Asciiville](../projects/Asciiville.md)
- [Tuir](tuir/tuir.md)
- [Irssi](irssi.md)
- [Neomutt](neomutt.md)
