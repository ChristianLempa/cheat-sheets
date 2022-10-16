# Controls

## Basic Commands

- <kbd>j</kbd> or <kbd>▼</kbd> - Move the cursor down
- <kbd>k</kbd> or <kbd>▲</kbd> - Move the cursor up
- <kbd>l</kbd> or <kbd>►</kbd> - View the currently selected item
- <kbd>h</kbd> or <kbd>◄</kbd> - Return to the previous view
- <kbd>m</kbd> or <kbd>PgUp</kbd> - Move the cursor up one page
- <kbd>n</kbd> or <kbd>PgDn</kbd> - Move the cursor down one page
- <kbd>gg</kbd> - Jump to the top of the page
- <kbd>G</kbd> - Jump to the bottom of the page
- <kbd>1</kbd> to <kbd>7</kbd> - Sort submissions by category
- <kbd>r</kbd> or <kbd>F5</kbd> - Refresh the content on the current page
- <kbd>u</kbd> - Login to your reddit account
- <kbd>q</kbd> - Quit
- <kbd>Q</kbd> - Force quit
- <kbd>y</kbd> - Copy submission permalink to clipboard
- <kbd>Y</kbd> - Copy submission link to clipboard
- <kbd>F2</kbd> - Cycle to the previous color theme
- <kbd>F3</kbd> - Cycle to the next color theme
- <kbd>?</kbd> - Show the help screen
- <kbd>/</kbd> - Open a prompt to select a subreddit

The <kbd>/</kbd> key opens a text prompt at the bottom of the screen. You can use
this to type in the name of the subreddit that you want to open. The following text
formats are recognized:

- ``/python`` - Open a subreddit, shorthand
- ``/r/python`` - Open a subreddit
- ``/r/python/new`` - Open a subreddit, sorted by category
- ``/r/python/controversial-year`` - Open a subreddit, sorted by category and time
- ``/r/python+linux+commandline`` - Open multiple subreddits merged together
- ``/comments/30rwj2`` - Open a submission, shorthand
- ``/r/python/comments/30rwj2`` - Open a submission
- ``/r/front`` - Open your front page
- ``/u/me`` - View your submissions
- ``/u/me/saved`` - View your saved content
- ``/u/me/hidden`` - View your hidden content
- ``/u/me/upvoted`` - View your upvoted content
- ``/u/me/downvoted`` - View your downvoted content
- ``/u/spez`` - View a user's submissions and comments
- ``/u/spez/submitted`` - View a user's submissions
- ``/u/spez/comments`` - View a user's comments
- ``/u/multi-mod/m/android`` - Open a user's curated multireddit
- ``/domain/python.org`` - Search for links for the given domain

## Authenticated Commands

Some actions require that you be logged in to your reddit account. You can login
by pressing the <kbd>u</kbd> key. Once you are logged in, your username will
appear in the top-right corner of the screen.

- <kbd>a</kbd> - Upvote
- <kbd>z</kbd> - Downvote
- <kbd>c</kbd> - Compose a new submission or comment
- <kbd>C</kbd> - Compose a new private message
- <kbd>e</kbd> - Edit the selected submission or comment
- <kbd>d</kbd> - Delete the selected submission or comment
- <kbd>i</kbd> - View your inbox (see [inbox mode](#inbox-mode))
- <kbd>s</kbd> - View your subscribed subreddits (see [subscription mode](#subscription-mode))
- <kbd>S</kbd> - View your subscribed multireddits (see [subscription mode](#subscription-mode))
- <kbd>u</kbd> - Logout of your reddit account
- <kbd>w</kbd> - Save the selected submission or comment

## Subreddit Mode

The following actions can be performed when viewing a subreddit:

- <kbd>l</kbd> or <kbd>►</kbd> - View the comments for the selected submission (see [submission mode](#submission-mode))
- <kbd>o</kbd> or <kbd>ENTER</kbd> - Open the selected submission link using your web browser or ``.mailcap`` config
- <kbd>SPACE</kbd> - Mark the selected submission as *hidden*
- <kbd>p</kbd> - Toggle between the currently viewed subreddit and ``/r/front``
- <kbd>f</kbd> - Open a prompt to search the current subreddit for a text string

## Submission Mode

The following actions can be performed when viewing a submission:

- <kbd>h</kbd> or <kbd>◄</kbd> - Close the submission and return to the previous page
- <kbd>l</kbd> or <kbd>►</kbd> - View the selected comment using the system's pager
- <kbd>o</kbd> or <kbd>ENTER</kbd> - Open a link in the comment using your web browser or ``.mailcap`` config
- <kbd>SPACE</kbd> - Fold or expand the selected comment and its children
- <kbd>b</kbd> - Send the comment text to the system's urlviewer application
- <kbd>J</kbd> - Move the cursor down the the next comment at the same indentation
- <kbd>K</kbd> - Move the cursor up to the parent comment

## Subscription Mode

The following actions can be performed when viewing your subscriptions or multireddits:

- <kbd>h</kbd> or <kbd>◄</kbd> - Close your subscriptions and return to the previous page
- <kbd>l</kbd> or <kbd>►</kbd> - Open the selected subreddit or multireddit

## Inbox Mode

The following actions can be performed when viewing your inbox:

- <kbd>h</kbd> or <kbd>◄</kbd> - Close your inbox and return to the previous page
- <kbd>l</kbd> or <kbd>►</kbd> - View the context of the selected comment
- <kbd>o</kbd> or <kbd>Enter</kbd> - Open the submission of the selected comment
- <kbd>c</kbd> - Reply to the selected comment or message
- <kbd>w</kbd> - Mark the selected comment or message as seen
