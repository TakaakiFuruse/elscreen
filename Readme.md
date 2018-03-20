ElScreen private fork
==========


This is a fork of [ElScreen](http://www.morishima.net/~naoto/elscreen-en/?lang=en)


(This is just a private fork.  
I have added all the pull requests available on Elscreen's original repository.  
Looks Elscrenn is not maintained anymore but I wanted to use it.  
Elscreen does not work on Emacs 25 and Spacemacs 0.200,  
if you loved or loving elscreen but annoyed by self-pathing job, this fork is for you.)  


Installation
------------


The preferred way to install ElScreen is through
[MELPA](https://melpa.org/) and `package.el`.  If you have Emacs 24,
you should already have `package.el`.  To enable MELPA, add something
like the following in your `.emacs.d` file:

    (add-to-list 'package-archives
         '("melpa" . "https://melpa.org/packages/") t)

Once you have installed ElScreen, you can activate it like so:

    (elscreen-start)


Usage
-----
You may use following sequences on ElScreen:

`C-z c`<br />
`C-z C-c`<br />
Create a new screen and switch to it.

`C-z C`<br />
Create a new screen with the window-configuration of
the current screen.
           
`C-z k`<br />
`C-z C-k`<br />
Kill current screen.

`C-z M-k`<br />
Kill current screen and buffers.

`C-z K`<br />
Kill other screens.

`C-z n`<br />
`C-z C-n`<br />
Switch to the "next" screen in a cyclic order.

`C-z p`<br />
`C-z C-p`<br />
Switch to the "previous" screen in a cyclic order.

`C-z a`<br />
`C-z C-a`<br />
Toggle to the screen selected previously.

`C-z '`<br />
Prompt for a screen number to switch to.

`C-z "`<br />
Present a list of all screens for selection.

`C-z 0..9`<br />
Jump to the screen number 0-9.

`C-z C-s`<br />
Swap current screen with previous one.
  
`C-z w`<br />
`C-z C-w`<br />
Show a list of screen.
  
`C-z A`<br />
Allow the user to enter a name for the current screen.

`C-z m`<br />
`C-z C-m`<br />
Repeat the last message displayed in the mini-buffer.
  
`C-z t`<br />
`C-z C-t`<br />
    
`C-z b`<br />
Switch to the screen in which specified buffer is
splayed.
  
`C-z C-f`<br />
Create new screen and open file.
  
`C-z C-r`<br />
Create new screen and open file but don't allow changes.
  
`C-z d`<br />
Create new screen and run dired.

`C-z M-x`<br />
Read function name, then call it with new screen.

`C-z i`<br />
Show/hide the screen number in the mode line.

`C-z T`<br />
Show/hide the tab on the top of each frame.

`C-z v`<br />
Display ElScreen version.

`C-z ?`<br />
Show key bindings of ElScreen and Add-On softwares.
  


Setup
-----
You can set the following variables to configure ElScreen.  These
can be set in `.emacs` file directly or "Options" in your menu bar.

    elscreen-prefix-key

ElScreen prefix-key.  The default value is `\C-z`.

    elscreen-buffer-to-nickname-alist

The pairs of buffer-name and corresponding screen nickname or function
that returns nickname, which are listed by
`elscreen-display-screen-name-list` only when major-mode cannot
determine its screen nickname.  The default value is:

        '(("^dired-mode$" .
           (lambda ()
             (format "Dired(%s)" dired-directory)))
          ("^Info-mode$" .
           (lambda ()
             (format "Info(%s)" (file-name-nondirectory Info-current-file))))
          ("^mew-draft-mode$" .
           (lambda ()
             (format "Mew(%s)" (buffer-name (current-buffer)))))
          ("^mew-" . "Mew")
          ("^irchat-" . "IRChat")
          ("^liece-" . "Liece")
          ("^lookup-" . "Lookup"))

    elscreen-mode-to-nickname-alist

The pairs of major-mode and corresponding screen nickname or function
that returns nickname, which are listed by
`elscreen-display-screen-name-list`.  The default value is:

        '(("[Ss]hell" . "shell")
          ("compilation" . "compile")
          ("-telnet" . "telnet")
          ("dict" . "OnlineDict")
          ("*WL:Message*" . "Wanderlust"))

    elscreen-startup-command-line-processing

If non `nil`, ElScreen processes command line arguments of Emacsen when
starting up, and opens files with new screens if needed.  The default
value is `t`.

    elscreen-display-screen-number

If non `nil`, show the number of the current screen in mode line.  The
default value is `t`.

    elscreen-display-tab

Specify how the tabs at the top of frame should be displayed.  `t` means
to display tabs whose width should be calculated automatically.  A
value of integer means to display tabs with fixed width of this value.
`nil` means don't display tabs.  The default value is `t`.

    elscreen-tab-display-control

If non `nil`, display the tab (labeled with `[<->]`) to switch to
next/previous screen or create new screen at the most left side of the
tab line.  The default value is `t`.

    elscreen-tab-display-kill-screen

Location of the icon (`[X]`) to kill corresponding screen on each tab.
Possible values are `'left`, `'right` and `nil` (to hide icons).  The
default value is `'left`.


Bugs
----
Under multiple-frame environment, screen numbers displayed on mode
line of each frame is changed at the same time.  On GNU Emacs 21, tabs
also has this restriction.


Acknowledgment
--------------
Many people contributed to ElScreen by reporting problems or suggesting
various improvements.  Here is a list of these people.

  * Tohru Sugayama
  * Yoshinobu Takenaga
  * Masatoshi Takamura
  * Jin Kashimura
  * Takahiko Sakai
  * Norio Suzuki
  * Yoshitatsu Takeshita
  * Yoichi Nakayama
  * sen_ml@eccosys.com
  * Dan Debertin
  * Yoshinori Koseki
  * Hideyuki Shirai
  * Masahiro Ishiyama
  * Alexy Khrabrov
