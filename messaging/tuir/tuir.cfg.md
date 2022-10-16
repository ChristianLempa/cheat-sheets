# Terminal UI for Reddit Configuration File

```
; https://gitlab.com/ajak/tuir
;
; This file should be placed in $XDG_CONFIG/tuir/tuir.cfg
; If $XDG_CONFIG is not set, use ~/.config/tuir/tuir.cfg

[tuir]
##################
# General Settings
##################

; Turn on ascii-only mode to disable all unicode characters.
; This may be necessary for compatibility with some terminal browsers.
ascii = False

; Turn on monochrome mode to disable color.
monochrome = False

; Data being copied is piped into this command
clipboard_cmd = xclip -selection clipboard
;clipboard_cmd = xclip
;clipboard_cmd = xsel -b -i
;clipboard_cmd = wl-copy
;clipboard_cmd = pbcopy w

; Flash when an invalid action is executed.
flash = True

; Enable debugging by logging all HTTP requests and errors to the given file.
;log = /tmp/tuir.log

; Default subreddit that will be opened when the program launches.
subreddit = front
;subreddit = python
;subreddit = python+linux+programming
;subreddit = all

; Allow tuir to store reddit authentication credentials between sessions.
persistent = True

; Automatically log in on startup, if credentials are available.
autologin = True

; Clear any stored credentials when the program starts.
clear_auth = False

; Maximum number of opened links that will be saved in the history file.
history_size = 200

; Open external links using programs defined in the mailcap config.
enable_media = True

; Maximum number of columns for a comment
max_comment_cols = 120

; Maximum number of columns for pager
;max_pager_cols = 70

; Hide username if logged in, display "Logged in" instead
hide_username = False

; Set the look and feel. Default allows posts to be spread across 4 lines,
; while compact reduces it to 2 lines. Compact reduces the vertical space
; the cost of horizontal space - the title won't be wrapped to the next
; line.
; look_and_feel = default
; look_and_feel = compact

; The subreddit_format option defines the format of submissions in a
; SubredditPage. Some caveats:
;
; If specified, this option will override whatever was set in
; look_and_feel.
;
; Lines after the first line must be intented for Python's config parser to
; understand the option having multiple lines
;
; Attributes are assigned only to the text written from a format specifier.
; Certain characters ("<>/{}[]()|_-~") are assigned the separator attribute,
; but no extraneous text added by the user will have an attribute.
;
; This feature is experimental and bound to have bugs. If you find one, please
; file a bug report at https://gitlab.com/ajak/tuir/issues
;
; List of valid format specifiers and what they evaluate to:
; %i index
; %t title
; %s score
; %v vote status
; %c comment count
; %r relative creation time
; %R absolute creation time
; %e relative edit time
; %E absolute edit time
; %a author
; %S subreddit
; %u short url - 'self.reddit' or 'gfycat.com' for example
; %U full url
; %A saved
; %h hidden
; %T stickied
; %g gold
; %n nsfw
; %f post flair
; %F all flair - saved, hidden, stickied, gold, nsfw, post flair,
;                separated by spaces
;
; For example, the compact look_and_feel is a format of:
; subreddit_format = %t
;  <%i|%s%v|%cC> %r%e %a %S %F
;

; Color theme, use "tuir --list-themes" to view a list of valid options.
; This can be an absolute filepath, or the name of a theme file that has
; been installed into either the custom of default theme paths.
; Presets:
;     colorblind-dark     [requires 256 colors]
;     molokai             [requires 256 colors]
;     papercolor          [requires 256 colors]
;     solarized-dark      [requires 256 colors]
;     solarized-light     [requires 256 colors]

; Built-in:
;     default             [requires 8 colors]
;     monochrome          [requires 0 colors]
;theme = solarized-dark
theme = molokai

; Open a new browser window instead of a new tab in existing instance
force_new_browser_window = False

################
# OAuth Settings
################
; This sections defines the paramaters that will be used during the OAuth
; authentication process. tuir is registered as an "installed app",
; see https://github.com/reddit/reddit/wiki/OAuth2 for more information.

; These settings are defined at https://www.reddit.com/prefs/apps
; To login to Reddit using tuir you will need to create a new Reddit app
; and generate an OAuth client id and client secret then give that app
; authorization to access Reddit as your account. This process is described
; in greater detail in the Asciiville README at:
;    https://github.com/doctorfree/Asciiville#readme
;
; Change these two settings to enable Reddit login
oauth_client_id = zjyhNI7tK8ivzQ
oauth_client_secret = praw_gapfill
oauth_redirect_uri = http://127.0.0.1:65000/

; Port that the tuir webserver will listen on. This should match the redirect
; uri defined above.
oauth_redirect_port = 65000

; Access permissions that will be requested.
oauth_scope = edit,history,identity,mysubreddits,privatemessages,read,report,save,submit,subscribe,vote

; This is a separate token for the imgur api. It's used to extract images
; from imgur links and albums so they can be opened with mailcap.
; See https://imgur.com/account/settings/apps to generate your own key.
imgur_client_id = b33d69ac8931734

[bindings]
##############
# Key Bindings
##############
; If you would like to define custom bindings, copy this section into your
; config file with the [bindings] heading. All commands must be bound to at
; least one key for the config to be valid. 
;
; 1.) Plain keys can be represented by either uppercase/lowercase characters
;     or the hexadecimal numbers referring their ascii codes. For reference, see
;     https://en.wikipedia.org/wiki/ASCII#ASCII_printable_code_chart
;         e.g. Q, q, 1, ?
;         e.g. 0x20 (space), 0x3c (less-than sign)
;
; 2.) Special ascii control codes should be surrounded with <>. For reference,
;     see https://en.wikipedia.org/wiki/ASCII#ASCII_control_code_chart
;         e.g. <LF> (enter), <ESC> (escape)
;
; 3.) Other special keys are defined by curses, they should be surrounded by <>
;     and prefixed with KEY_. For reference, see
;     https://docs.python.org/2/library/curses.html#constants
;         e.g. <KEY_LEFT> (left arrow), <KEY_F5>, <KEY_NPAGE> (page down)
;
; Notes:
; - Curses <KEY_ENTER> is unreliable and should always be used in conjunction
;   with <LF>.
; - Use 0x20 for the space key.
; - A subset of Ctrl modifiers are available through the ascii control codes.
;   For example, Ctrl-D will trigger an <EOT> signal. See the table above for
;   a complete reference.

; Base page
EXIT = q 
FORCE_EXIT = Q
HELP = ?
SORT_1 = 1
SORT_2 = 2
SORT_3 = 3
SORT_4 = 4
SORT_5 = 5
SORT_6 = 6
SORT_7 = 7
MOVE_UP = k, <KEY_UP>
MOVE_DOWN = j, <KEY_DOWN>
PREVIOUS_THEME = <KEY_F2>
NEXT_THEME = <KEY_F3>
PAGE_UP = m, <KEY_PPAGE>, <NAK>
PAGE_DOWN = n, <KEY_NPAGE>, <EOT>
PAGE_TOP = gg
PAGE_BOTTOM = G
UPVOTE = a
DOWNVOTE = z
LOGIN = u
DELETE = d
EDIT = e
INBOX = i
REFRESH = r, <KEY_F5>
PROMPT = /
SAVE = w
COPY_PERMALINK = y
COPY_URL = Y
PRIVATE_MESSAGE = C
SUBSCRIPTIONS = s
MULTIREDDITS = S

; Submission page
SUBMISSION_TOGGLE_COMMENT = 0x20
SUBMISSION_OPEN_IN_BROWSER = o, <LF>, <KEY_ENTER>
SUBMISSION_POST = c
SUBMISSION_EXIT = h, <KEY_LEFT>
SUBMISSION_OPEN_IN_PAGER = l, <KEY_RIGHT>
SUBMISSION_OPEN_IN_URLVIEWER = b
SUBMISSION_GOTO_PARENT = K
SUBMISSION_GOTO_SIBLING = J

; Subreddit page
SUBREDDIT_SEARCH = f
SUBREDDIT_POST = c
SUBREDDIT_OPEN = l, <KEY_RIGHT>
SUBREDDIT_OPEN_IN_BROWSER = o, <LF>, <KEY_ENTER>
SUBREDDIT_FRONTPAGE = p
SUBREDDIT_HIDE = 0x20

; Subscription page
SUBSCRIPTION_SELECT = l, <LF>, <KEY_ENTER>, <KEY_RIGHT>
SUBSCRIPTION_EXIT = h, s, S, <ESC>, <KEY_LEFT>

; Inbox page
INBOX_VIEW_CONTEXT = l, <KEY_RIGHT>
INBOX_OPEN_SUBMISSION = o, <LF>, <KEY_ENTER>
INBOX_REPLY = c
INBOX_MARK_READ = w
INBOX_EXIT = h, <ESC>, <KEY_LEFT>
```
