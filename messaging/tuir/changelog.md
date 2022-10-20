# RTV/TUIR Changelog

## [1.29.0](https://gitlab.com/ajak/tuir/tree/v1.29.0) (2020-04-26)

Features

-   Links to twitch.tv can now be opened using the video/x-youtube
    mailcap entry
-   TUIR now supports using a mailcap in
    [\~/.config/tuir/mailcap]{.title-ref}, and this is the new default
    path for [tuir \--copy-mailcap]{.title-ref}
-   Experimental support for new config settings \"look_and_feel\" and
    \"subreddit_format\". These enable users to have greater control
    over the formatting of SubredditPages. More detailed information is
    available in the default config file.

## [1.28.3](https://gitlab.com/ajak/tuir/tree/v1.28.3) (2019-09-02)

Bugfixes

-   Add backwards compatibility for RTV config files by allowing parsing
    of [\[rtv\]]{.title-ref} sections rather than only
    [\[tuir\]]{.title-ref} sections. Resolves #13.

## [1.28.2](https://gitlab.com/ajak/tuir/tree/v1.28.2) (2019-06-12)

Miscellaneous

-   Change from old (RTV) Imgur API key to new key for TUIR. Please
    check the migration section of the README for the new key.

## [1.28.1](https://gitlab.com/ajak/tuir/tree/v1.28.1) (2019-06-09)

Bugfixes

-   Revert de1d06e3 - it breaks python2.7 compatibility

Miscellaneous

-   Add python2.7 gitlab-ci test

## [1.28.0](https://gitlab.com/ajak/tuir/tree/v1.28.0) (2019-06-09)

This is the first release of TUIR. Several changes come that don\'t fit
into a neat changelog category here:

-   Name change: \'Reddit Terminal Viewer\' to \'Terminal UI for
    Reddit\'
-   Fork is on Gitlab, so travis-ci configuration is partially converted
    to gitlab-ci

Features

-   Added a configuration option to allow the user to decide what
    program clipboard data is piped into. Default on Darwin stays the
    same and default on everything else is [xclip -selection
    clipboard]{.title-ref}

Bugfixes

-   Fix a crash when jumping to the bottom of a submission with no
    comments

## [1.27.0](http://github.com/michael-lazar/rtv/releases/tag/v1.27.0) (2019-06-02)

This is the final release of RTV. See here for more information:

<https://github.com/michael-lazar/rtv/issues/696>

Features

-   Added a configuration option to toggle whether to open web browser
    links in a new tab or a new window.

Documentation

-   Improved the mailcap example for the `feh` command.
-   Fixed the the descriptions for the `j` & `k` keys (they were
    swapped).

## [1.26.0](http://github.com/michael-lazar/rtv/releases/tag/v1.26.0) (2019-03-03)

Features

-   Added a brand new inbox page for viewing private messages and
    comment replies. The inbox is accessible with the `i` key. Supported
    actions include viewing message chains and replying to messages,
    marking messages as read/unread, and opening the context of a
    comment.
-   Added the ability to compose new private messages with the `C` key.
-   Updated the inline help `?` document to contain a more comprehensive
    list of commands.
-   Opening a link from the command line is now faster at startup
    because the default subreddit will not be loaded beforehand.
-   Added a new `--debug-info` command to display useful system
    information.

Bugfixes

-   Fixed opening comments with the prompt `/` from the subscription
    window.
-   The subscription and multireddit `s`/`S` keys now work from all
    pages.
-   Relative time strings are now correctly pluralized.
-   Fixed an unclosed file handler when opening the web browser.
-   Fixed the application not starting if the user has an empty front
    page.

Configuration Changes

-   Renamed the following keybindings to better represent their usage:
    -   `SORT_HOT` -\> `SORT_1`
    -   `SORT_TOP` -\> `SORT_2`
    -   `SORT_RISING` -\> `SORT_3`
    -   `SORT_NEW` -\> `SORT_4`
    -   `SORT_CONTROVERSIAL` -\> `SORT_5`
    -   `SORT_GILDED` -\> `SORT_6`
    -   `SUBREDDIT_OPEN_SUBSCRIPTIONS` -\> `SUBSCRIPTIONS`
    -   `SUBREDDIT_OPEN_MULTIREDDITS` -\> `MULTIREDDITS`
-   Added new keybindings to support the inbox page:
    -   `SORT_7`
    -   `PRIVATE_MESSAGE`
    -   `INBOX_VIEW_CONTEXT`
    -   `INBOX_OPEN_SUBMISSION`
    -   `INBOX_REPLY`
    -   `INBOX_MARK_READ`
    -   `INBOX_EXIT`
-   Added new theme elements to support the inbox page:
    -   \<New\>
    -   \<Distinguished\>
    -   \<MessageSubject\>
    -   \<MessageLink\>
    -   \<MessageAuthor\>
    -   \<MessageSubreddit\>
    -   \<MessageText\>

## [1.25.1](http://github.com/michael-lazar/rtv/releases/tag/v1.25.1) (2019-02-13)

Bugfixes

-   Fixed a bug that was causing newlines to be stripped when posting
    comments and submissions.

## [1.25.0](http://github.com/michael-lazar/rtv/releases/tag/v1.25.0) (2019-02-03)

Features

-   You can now open HTML links that are embedded inside of comments and
    submissions by pressing the `ENTER` key and selecting a link from
    the list. This also works when copying links to the clipboard using
    `Y`.
-   Added the `--no-autologin` command line argument to disable
    automatically logging in at startup.
-   Added the `max_pager_cols` configuration option to limit the text
    width when sending text to the system `PAGER`.
-   Additional filtering options have been added when viewing user
    pages.
-   The gilded flair now displays the number of times a submission has
    been gilded.
-   Submissions/comments now display the time that they were most
    recently edited.

Bugfixes

-   Fixed the MIME parser for gfycat, and gfycat videos are now
    downloaded as mp4.
-   Fixed formatting when composing posts with leading whitespace.
-   Fixed crash when attempting to display a long terminal title.

Documentation

-   RTV has been moved to the Arch Community Repository and installation
    instructions for Arch have been updated accordingly.

## [1.24.0](http://github.com/michael-lazar/rtv/releases/tag/v1.24.0) (2018-08-12)

Features

-   Python 3.7 is now officially supported.
-   Lines that start with the hash symbol (#) are no longer ignored when
    composing posts in your editor. This allows \# to be used with
    Reddit\'s markdown parser to denote headers.
-   Added a new *dark colorblind* theme.
-   Added support for the `$RTV_PAGER` environment variable, which can
    be used to set a unique PAGER for rtv.
-   Added the ability to sort submissions by **guilded**.

Bugfixes

-   Fixed a crash when setting the `$BROWSER` with python 3.7.
-   Improved the error message when attempting to vote on an archived
    post.
-   Cleaned up several outdated MIME parsers. Removed the vidme, twitch,
    oddshot, and imgtc parsers. Fixed the liveleak and reddit video
    parsers.

## [1.23.0](http://github.com/michael-lazar/rtv/releases/tag/v1.23.0) (2018-06-24)

Features

-   Submissions can now be marked as *\[hidden\]* using the `space` key.
    Hidden submissions will be removed from the feed when the page is
    reloaded.
-   New MIME parsers have been added for vimeo.com and streamja.com.
-   Added support for opening links with **qutebrowser**.

Bugfixes

-   Fixed unhandled OAuth server log messages being dumped to stdout.
-   Fixed the application crashing when performing rate-limited
    requests.
-   Fixed crash when displaying posts that contain null byte characters.

Documentation

-   Added README badge for *saythanks.io*.
-   Updated the mailcap template to support *v.redd.it* links.

## [1.22.1](http://github.com/michael-lazar/rtv/releases/tag/v1.22.1) (2018-03-11)

I forgot to check in a commit before publishing the 1.22.0 release
(whoops!)

Bugfixes

-   Updated the `__version__.py` file to report the current version.
-   Added the missing v1.22.0 entry to the CHANGELOG.

## [1.22.0](http://github.com/michael-lazar/rtv/releases/tag/v1.22.0) (2018-03-07)

Features

-   Added the `--no-flash` option to disable terminal flashing.

Bugfixes

-   Fixed automatically exiting on launch when trying to open an invalid
    subreddit with the `-s` flag.
-   Fixed error handling for HTTP request timeouts when checking for new
    messages in the inbox.
-   Fixed a typo in the sample theme config.

Documentation

-   Added the FreeBSD package to the README.

## [1.21.0](http://github.com/michael-lazar/rtv/releases/tag/v1.21.0) (2017-12-30)

Features

-   Full support for customizable themes has been added. For more
    information, see the new section on themes in the README, and the
    `THEMES.md` file.

Bugfixes

-   Fixed incorrect URL strings being sent to the **opera** web browser.
-   Fixed timeout messages for the **surf** and **vimb** web browsers.
-   Switched to using `XDG_DATA_HOME` to store the rtv browser history
    and credentials file.

## [1.20.0](http://github.com/michael-lazar/rtv/releases/tag/v1.20.0) (2017-12-05)

Features

-   Text piped to the `$PAGER` will now wrap on word / sentence breaks.
-   New MIME parsers have been added for liveleak.com and
    worldstarhiphop.com.

Bugfixes

-   Fixed a regression where text from the web browser\'s stdout/stderr
    was being sent to the terminal window.
-   Fixed crashing on startup when the terminal doesn\'t support colors.
-   Fixed broken text formatting when running inside of emacs `term`.

Codebase

-   Dropped support for python 3.3 because it\'s no longer supported
    upstream by **pytest**. The application will still install through
    pip but will no longer be tested.
-   Added a text logo to the README.

## [1.19.0](http://github.com/michael-lazar/rtv/releases/tag/v1.19.0) (2017-10-24)

Features

-   Greatly improved loading times by using smarter rate limiting and
    page caching.
-   The logout prompt is now visible as a popup notification.
-   New MIME parsers have been added for gifs.com, giphy.com, imgtc.com,
    imgflip.com, livememe.com, makeameme.org and flickr.com
-   Improved mailcap examples for parsing video links with mpv.

Bugfixes

-   Patched a backwards-incompatible Reddit API change with the comment
    permalink now being returned in the response JSON.
-   Fixed crashing when a comment contained exotic unicode characters
    like emojis.
-   Removed the option to select custom sorting ranges for controversial
    and top comments.
-   Fixed MIME parsing for single image Imgur galleries.

Codebase

-   Preliminary refactoring for the upcoming theme support.
-   Created some utility scripts for project maintenance.
-   Created a release checklist document.
-   Updated the README gif images and document layout.

## [1.18.0](http://github.com/michael-lazar/rtv/releases/tag/v1.18.0) (2017-09-06)

Features

-   The `rtv -l` flag has been deprecated and replaced with a positional
    argument, in order to match the syntax of other command line web
    browsers.
-   NSFW content is now filtered according to the user\'s reddit profile
    settings.
-   `$RTV_BROWSER` has been added as a way to set the preferred web
    browser.
-   Sorting options for **relevance** and **comments** are now displayed
    on the search results page.
-   An **\[S\]** badge is now displayed next to the submission author.
-   The gfycat MIME parser has been expanded to support more URLs.
-   New MIME parsers have been added for oddshot.tv, clips.twitch.tv,
    clippituser.tv, and Reddit\'s beta hosted videos.

Bugfixes

-   Users can now use the prompt to navigate to \"/comments/\...\" pages
    from inside of a submission.
-   Users can now navigate to multireddits using the \"/u/me/\" prefix.
-   Fixed the `$BROWSER` behavior on macOS to support the **chrome**,
    **firefox**, **safari**, and **default** keywords.

Codebase

-   Travis CI tests have been moved to the trusty environment.
-   Added more detailed logging of the environment and settings at
    startup.

## [1.17.1](http://github.com/michael-lazar/rtv/releases/tag/v1.17.1) (2017-08-06)

Bugfixes

-   `J`/`K` commands are now restricted to the submission page.

## [1.17.0](http://github.com/michael-lazar/rtv/releases/tag/v1.17.0) (2017-08-03)

Features

-   Added the `J` command to jump to the next sibling comment.
-   Added the `K` command to jump to the parent comment.
-   Search results can now be sorted, and the title bar has been updated
    to display the current search query.
-   Imgur URLs are now resolved via the Imgur API. This enables the
    loading of large albums with over 10 images. An `imgur_client_id`
    option has been added to the RTV configuration.
-   A MIME parser has been added for www.liveleak.com.
-   RTV now respects the `$VISUAL` environment variable.

Bugfixes

-   Fixed a screen refresh bug on urxvt terminals.
-   New key bindings will now attempt to fallback to their default key
    if not defined in the user\'s configuration file.

Documentation

-   Added additional mailcap examples for framebuffer videos and iTerm2.
-   Python version information is now captured in the log at startup.

## [1.16.0](http://github.com/michael-lazar/rtv/releases/tag/v1.16.0) (2017-06-08)

Features

-   Added the ability to copy links to the OS clipboad with `y` and `Y`.
-   Both submissions and comments can now be viewed on **/user/** pages.
-   A MIME parser has been added for www.streamable.com.
-   A MIME parser has been added for www.vidme.com.
-   Submission URLs can now be opened while viewing the comments page.

Bugfixes

-   More graceful handling for the invalid LOCALE error on MacOS.
-   A fatal error is now raised when trying to run on Windows without
    curses.
-   Fixed an error when trying to view saved comments.
-   Invalid refresh-tokens are now automatically deleted.
-   Users who are signed up for Reddit\'s beta profiles can now launch
    RTV.

## [1.15.1](http://github.com/michael-lazar/rtv/releases/tag/v1.15.1) (2017-04-09)

Codebase

-   Removed the mailcap-fix dependency for python versions \>= 3.6.0.
-   Enabled installing test dependencies with `pip install rtv[test]`.

## [1.15.0](http://github.com/michael-lazar/rtv/releases/tag/v1.15.0) (2017-03-30)

Features

-   Added the ability to open comment threads using the submission\'s
    permalink. E.g. **/comments/30rwj2**

Bugfixes

-   Updated `requests` requirement to fix a bug in version 2.3.0.
-   Fixed an edge case where comment trees were unfolding out of order.

Codebase

-   Removed dependency on the PyPI `praw` package. A version of PRAW 3
    is now bundled with rtv. This should make installation easier
    because users are no longer required to maintain a legacy version of
    praw in their python dependencies.
-   Removed `update-checker` dependency.

## [1.14.1](http://github.com/michael-lazar/rtv/releases/tag/v1.14.1) (2017-01-12)

Features

-   The order-by option menu now triggers after a single \'2\' or \'5\'
    keystroke instead of needing to double press.

Bugfixes

-   Mailcap now handles multi-part shell commands correctly, e.g.
    \"emacs -nw\"
-   OS X no longer relies on \$DISPLAY to check if there is a display
    available.
-   Added error handling for terminals that don\'t support hiding the
    cursor.
-   Fixed a bug on tmux that prevented scrolling when \$TERM was set to
    \"xterm-256color\" instead of screen.

Documentation

-   Added section to FAQ about garbled characters output by curses.

## [1.13.0](http://github.com/michael-lazar/rtv/releases/tag/v1.13.0) (2016-10-17)

Features

-   Pressing [2]{.title-ref} or [5]{.title-ref} twice now opens a menu
    to select the time frame.
-   Added the [hide_username]{.title-ref} config option.
-   Added the [max_comment_cols]{.title-ref} config option.

Bugfixes

-   Fixed the terminal title from displaying b\'\' in py3.
-   Flipped j and k in the documentation.
-   Fixed bug when selecting post order for the front page.
-   Added more descriptive error messages for invalid subreddits.

## [1.12.1](http://github.com/michael-lazar/rtv/releases/tag/v1.12.1) (2016-09-27)

Bugfixes

-   Fixed security vulnerability where malicious URLs could inject
    python code.
-   No longer hangs when using mpv on long videos.
-   Now falls back to ascii mode when the system locale is not utf-8.

## [1.12.0](http://github.com/michael-lazar/rtv/releases/tag/v1.12.0) (2016-08-25)

Features

-   Added a help banner with common key bindings.
-   Added [gg]{.title-ref} and [G]{.title-ref} bindings to jump to the
    top and bottom the the page.
-   Updated help screen now opens with the system PAGER.
-   The [/]{.title-ref} prompt now works from inside of submissions.
-   Added an Instagram parser to extract images and videos from urls.

Bugixes

-   Shortened reddit links (<https://redd.it/>) will now work with `-s`.

Codebase

-   Removed the Tornado dependency from the project.
-   Added a requirements.txt file.
-   Fixed a bunch of tests where cassettes were not being generated.
-   Added compatability for pytest-xdist.

## [1.11.0](http://github.com/michael-lazar/rtv/releases/tag/v1.11.0) (2016-08-02)

Features

-   Added the ability to open image and video urls with the user\'s
    mailcap file.
-   New `--enable-media` and `copy-mailcap` commands to support mailcap.
-   New command [w]{.title-ref} to save submissions and comments.
-   New command [p]{.title-ref} to toggle between the front page and the
    last visited subreddit.
-   New command [S]{.title-ref} to view subscribed multireddits.
-   Extended `/` prompt to work with users, multireddits, and domains.
-   New page `/u/saved` to view saved submissions.
-   You can now specify the sort period by appending **-(period)**, E.g.
    **/r/python/top-week**.

Bugfixes

-   Terminal title is now only set when \$DISPLAY is present.
-   Urlview now works on the submission as well as comments.
-   Fixed text encoding when using urlview.
-   Removed [futures]{.title-ref} dependency from the python 3 wheel.
-   Unhandled resource warnings on exit are now ignored.

Documentation

-   Various README updates.
-   Updated asciinema demo video.
-   Added script to update the AUTHORS.rst file.

## [1.10.0](http://github.com/michael-lazar/rtv/releases/tag/v1.10.0) (2016-07-11)

Features

-   New command, [b]{.title-ref} extracts urls from comments using
    urlviewer.
-   Comment files will no longer be destroyed if RTV encounters an error
    while posting.
-   The terminal title now displays the subreddit name/url.

Bugfixes

-   Fixed crash when entering empty or invalid subreddit name.
-   Fixed crash when opening x-posts linked to subreddits.
-   Fixed a bug where the terminal title wasn\'t getting set.
-   **/r/me** is now displayed as *My Submissions* in the header.

## [1.9.1](http://github.com/michael-lazar/rtv/releases/tag/v1.9.1) (2016-06-13)

Features

-   Better support for */r/random*.
-   Added a `monochrome` config setting to disable all color.
-   Improved cursor positioning when expanding/hiding comments.
-   Show `(not enough space)` when comments are too large.

Bugfixes

-   Fixed permissions when copying the config file.
-   Fixed bug where submission indicies were duplicated when paging.
-   Specify praw v3.4.0 to avoid installing praw 4.

Documentation

-   Added section to the readme on Arch Linux installation.
-   Updated a few argument descriptions.
-   Added a proper ascii logo.

## [1.9.0](http://github.com/michael-lazar/rtv/releases/tag/v1.9.0) (2016-04-05)

Features

-   You can now open long posts/comments with the \$PAGER by pressing
    [l]{.title-ref}.
-   Changed a couple of visual separators.

Documentation

-   Added testing instructions to the FAQ.

## [1.8.1](http://github.com/michael-lazar/rtv/releases/tag/v1.8.1) (2016-03-01)

Features

-   All keys are now rebindable through the config.
-   New bindings - ctrl-d and ctrl-u for page up / page down.
-   Added tag for stickied posts and comments.
-   Added bullet between timestamp and comment count.

Bugfixes

-   Links starting with np.reddit.com no longer return
    [Forbidden]{.title-ref}.

Documentation

-   Updated README.

## [1.8.0](http://github.com/michael-lazar/rtv/releases/tag/v1.8.0) (2015-12-20)

Features

-   A banner on the top of the page now displays the selected page sort
    order.
-   Hidden scores now show up as \"- pts\".
-   Oauth settings are now accesible through the config file.
-   New argument [\--config]{.title-ref} specifies the config file to
    use.
-   New argument [\--copy-config]{.title-ref} generates a default config
    file.

Documentation

-   Added a keyboard reference from keyboardlayouteditor.com
-   Added a link to an asciinema demo video

## [1.7.0](http://github.com/michael-lazar/rtv/releases/tag/v1.7.0) (2015-12-08)

**Note** This version comes with a large change in the internal
structure of the project, but does not break backwards compatibility.
This includes adding a new test suite that will hopefully improve the
stability of future releases.

Continuous Integration additions

-   Travis-CI <https://travis-ci.org/michael-lazar/rtv>
-   Coveralls <https://coveralls.io/github/michael-lazar/rtv>
-   Gitter (chat) <https://gitter.im/michael-lazar/rtv>
-   Added a tox config for local testing
-   Added a pylint config for static code and style analysis
-   The project now uses VCR.py to record HTTP interactions for testing.

Features

-   Added a wider utilization of the loading screen for functions that
    make reddit API calls.
-   In-progress loading screens can now be cancelled by pressing the
    [Esc]{.title-ref} key.

Bugfixes

-   OSX users should now be able to login using OAuth.
-   Comments now return the correct nested level when loading \"More
    Comments\".
-   Several unicode fixes, the project is now much more consistent in
    the way that unicode is handled.
-   Several undocumented bug fixes as a result of the code restructure.

## [1.6.1](http://github.com/michael-lazar/rtv/releases/tag/v1.6.1) (2015-10-19)

Bugfixes

-   Fixed authentication checking for */r/me*.
-   Added force quit option with the [Q]{.title-ref} key.
-   Removed option to sort subscriptions.
-   Fixed crash with pressing [i]{.title-ref} when not logged in.
-   Removed futures requirement from the python 3 distribution.

Documentation

-   Updated screenshot in README.
-   Added section to the FAQ on installation.

## [1.6](http://github.com/michael-lazar/rtv/releases/tag/v1.6) (2015-10-14)

Features

-   Switched all authentication to OAuth.
-   Can now list the version with [rtv \--version]{.title-ref}.
-   Added a man page.
-   Added confirmation prompt when quitting.
-   Submissions now display the index in front of their title.

Bugfixes

-   Streamlined error logging.

Documentation

-   Added missing docs for the [i]{.title-ref} key.
-   New documentation for OAuth.
-   New FAQ section.

## [1.5](http://github.com/michael-lazar/rtv/releases/tag/v1.5) (2015-08-26)

Features

-   New page to view and open subscribed subreddits with
    [s]{.title-ref}.
-   Sorting method can now be toggled with the [1]{.title-ref} -
    [5]{.title-ref} keys.
-   Links to x-posts are now opened inside of RTV.

Bugfixes

-   Added */r/* to subreddit names in the subreddit view.

## [1.4.2](http://github.com/michael-lazar/rtv/releases/tag/v1.4.2) (2015-08-01)

Features

-   Pressing the [o]{.title-ref} key now opens selfposts directly inside
    of rtv.

Bugfixes

-   Fixed invalid subreddits from throwing unexpected errors.

## [1.4.1](http://github.com/michael-lazar/rtv/releases/tag/v1.4.1) (2015-07-11)

Features

-   Added the ability to check for unread messages with the
    [i]{.title-ref} key.
-   Upped required PRAW version to 3.

Bugfixes

-   Fixed crash caused by downvoting.
-   Missing flairs now display properly.
-   Fixed ResourceWarning on Python 3.2+.

## [1.4](http://github.com/michael-lazar/rtv/releases/tag/v1.4) (2015-05-16)

Features

-   Unicode support has been vastly improved and is now turned on by
    default. Ascii only mode can be toggled with the
    [\--ascii]{.title-ref} command line flag.
-   Added pageup and pagedown with the [m]{.title-ref} and
    [n]{.title-ref} keys.
-   Support for terminal based webbrowsers such as links and w3m.
-   Browsing history is now persistent and stored in
    [\$XDG_CACHE_HOME]{.title-ref}.

Bugfixes

-   Several improvements for handling unicode.
-   Fixed crash caused by resizing the window and exiting a submission.

## [1.3](http://github.com/michael-lazar/rtv/releases/tag/v1.3) (2015-04-22)

Features

-   Added edit [e]{.title-ref} and delete [d]{.title-ref} for comments
    and submissions.
-   Added *nsfw* tags.

Bugfixes

-   Upvote/downvote icon now displays in the submission selfpost.
-   Loading large *MoreComment* blocks no longer hangs the program.
-   Improved logging and error handling with praw interactions.

## [1.2.2](http://github.com/michael-lazar/rtv/releases/tag/v1.2.2) (2015-04-07)

Bugfixes

-   Fixed default subreddit not being set.

Documentation

-   Added changelog and contributor links to the README.

## [1.2.1](http://github.com/michael-lazar/rtv/releases/tag/v1.2.1) (2015-04-06)

Bugfixes

-   Fixed crashing on invalid subreddit names

## [1.2](http://github.com/michael-lazar/rtv/releases/tag/v1.2) (2015-04-06)

Features

-   Added user login / logout with the [u]{.title-ref} key.
-   Added subreddit searching with the [f]{.title-ref} key.
-   Added submission posting with the [p]{.title-ref} key.
-   Added viewing of user submissions with [/r/me]{.title-ref}.
-   Program title now displays in the terminal window.
-   Gold symbols now display on guilded comments and posts.
-   Moved default config location to XDG_CONFIG_HOME.

Bugfixes

-   Improved error handling for submission / comment posts.
-   Fixed handling of unicode flairs.
-   Improved displaying of the help message and selfposts on small
    terminal windows.
-   The author\'s name now correctly highlights in submissions
-   Corrected user agent formatting.
-   Various minor bugfixes.

## 1.1.1 (2015-03-30)

-   Post comments using your text editor.
