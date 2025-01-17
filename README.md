https://www.gnu.org/software/emacs/tour/
# Table of Contents

1.  [An Emacs Course](#org62a8407)
    1.  [Introduction](#orgf6f8691)
    2.  [Setup](#orgad39e8a)
        1.  [Install the configuration and the course](#org4557c9e)
        2.  [Start Emacs and let it install the required Emacs packages](#orgbec30c7)
    3.  [Start the course](#org29a5bda)
        1.  [a short word on the notation of key commands](#org0091aad)
        2.  [Activate a theme for better readability](#org7b5396d)
        3.  [Starting the lessons](#org8c8fc8b)
        4.  [Starting can be hard](#orgb8e6bd4)
    4.  [Planning of learning stages](#org2acb90e)



<a id="org62a8407"></a>

# An Emacs Course

**NOTE: This is an early work in progress. Only some initial chapters
are done"** I am still at an early point where I try to go through
the course with some initial learners. So, it is not quite ready yet
for the general consumption and therefore I also have not yet
advertised it in any way. The current Emacs configuration for the
course will need to be adapted.  

A nice feature I can offer is auto-generated decks of [Anki](https://apps.ankiweb.net/) cards and
cheat sheets for the course directly from the course files. Look at
the `learning-helpers` forlder. The Anki decks are produced from
intermediate org flash-card files thanks to Louie Tan's [anki-editor](https://github.com/louietan/anki-editor) )


<a id="orgf6f8691"></a>

## Introduction

I had used Emacs for many years in its most simple way - just as a
programming editor, just using the minimal set of exotic
commands. But when I discovered around 2009 what Emacs really is -
one of the most flexible and well documented programming
environments that happens to be a very good editor as well, I was
blown away.

Org mode was a revelation - the dream of every scientist (my
original training had been in physical chemistry). A notebook where
you can write easy marked up text, math formulas, you can
calculate, and as a programmer you can use all your programming
languages inside of the documents and produce graphics inline - too
good to be true. And then it is one of the best task management
systems as well. I fell in love, learned lisp - relished its
different feel from the C and scripting languages I knew -
something that reminded me of the joy of playing with the HP
Scientific Calculators many years ago.

For a long time I entertained the hope of passing on the
know-how. I had some mixed success in my work environment where
several of my scientific computing group picked it up to some
degree. But I never was able to teach it in a very structured
way. It's not so easy, since the thing which makes Emacs so great
and efficient - its staggering flexibility - also makes it tough to
teach. Most long time users end up with configurations that fit
them like a glove. But other users will be very opinionated in
regards to the packages and optimizations that are used. There's a
good number of excellent meta-distributions around, like [Spacemacs](https://www.spacemacs.org/)
or [Doom](https://github.com/hlissner/doom-emacs). They are great and will fit many users. I myself always
stayed with my hand-written config that I constantly adapted to
more modern styles (which prevented me from ever having to declare
the dreaded [Dot Emacs Bankruptcy](https://www.emacswiki.org/emacs/DotEmacsBankruptcy)).

I now decided to make a first test run with a course that is based
on basic configuration of Emacs. I will start with an initial
configuration that already has a number of nice packages that will
serve to wet the appetite. But the idea is not that learners need
to adopt these exact configurations. They should first get a glimpse
of what Emacs can do and then progress to learning how the
configuration works and how they can adapt it. So, they by
themselves will be able to make an informed decision about whether
to adopt one of the meta distributions, change the
present one, or just develop their own.

My big thanks goes to the whole Emacs community. One of the most
welcoming and helpful communities I had the pleasure working
with. So many people have contributed to this environment and I
feel indebted to all of them.


<a id="orgad39e8a"></a>

## Setup


<a id="org4557c9e"></a>

### Install the configuration and the course

The Emacs configuration for the course you can find at
<https://github.com/dfeich/emacs-course-and-config>. 
It is best that you fork that repository and then clone your
forked copy to your (or a test user's) account's `~/emacs.d` directory on your
machine.

    git clone git@github.com:dfeich/emacs-course-and-config.git ~/.emacs.d
    
    # or if you made a fork
    
    git clone git@github.com:<YOUR-GITNAME>/emacs-course-and-config.git ~/.emacs.d

This repository contains the course in the form of Org mode task files.
It should be checked out into the `~/Documents/orgcourse` folder of your account.
The Emacs configuration for the course contains settings that expect to
find the files under that location.

    git clone git@github.com:dfeich/emacs-course.git ~/Documents/orgcourse

If you check out to another location, you need to adapt the
definition in the Emacs configuration.

When you start Emacs with the new configuration for the first time, it
will download all the missing packages from GNU, MELPA, and Org. This
may take some minutes.

I use Emacs version 26.3 and Org version 9.x for this course.


<a id="orgbec30c7"></a>

### Start Emacs and let it install the required Emacs packages

When you start Emacs with the new configuration, it will download
the packages that are defined in the config. It may also have to
compile some extensions and pull in some OS packages (e.g. for the
PDF integration).

Packages are pulled down from the [GNU ELPA](https://elpa.gnu.org/), [MELPA](https://melpa.org/#/), and [Org](https://orgmode.org/)
repositories. GNU ELPA has recently changed its gpg keys, so you
may need to run the following command in order to update your
gpg security configuration (q.v. [this nice article](https://metaredux.com/posts/2019/12/09/dealing-with-expired-elpa-gpg-keys.html))

    gpg --homedir ~/.emacs.d/elpa/gnupg --receive-keys 066DAFCB81E42C40

If Emacs stops with an error message, it does not necessarily
mean that there is a critical problem. Close Emacs either using your
mouse pointer or hit the `CTRL-x CTRL-c` key combination. Launch it
again and look whether it is able to progress further. Since some
downloaded packages are replacing older versions of existing
packages, it can sometimes happen that depending on your current
config, Emacs ends up in a state where the old package and the new
package conflict. Updating packages like we do it here, actually
means that we are **live-patching Emacs**. Usually Emacs deals
admirably well with this, since the largest part of its
functionality is written in LISP. But exchanging cogwheels while
the motor is running can sometimes lead to problems (we will learn
in some later lesson about package management how to avoid this).

If it fails repeatedly without progressing further then please
file an issue in this tracker, and I will try to help.


<a id="org29a5bda"></a>

## Start the course

Once you have everything installed, start the first stage by typing

    emacs ~/Documents/orgcourse/agenda/course01-basics.org


<a id="org0091aad"></a>

### a short word on the notation of key commands

Emacs is operated through control key combinations and all Emacs
documentation uses the following important notation convention for
the keystrokes:

-   **"C-f":** this means press the `CTRL` key together with the `f` key.
-   **"M-f":** M refers to the `META` key, which on Linux/MS-Windows is
    the `ALT` key (On Macs this can be the `Option` or `Command`
    key). So, `M-f` means press the `ALT` key together with the `f` key
-   **"S-g":** `S` is short for the `SHIFT` key, so this means press `SHIFT` and `g`
    together
-   **"M-S-;":** this means press the `META`, `SHIFT`, and `;` keys together.

Often commands consist of a key combination like

-   **"C-h e":** first press `CTRL` + `h`, then press `e`. When keys are connected
    with a dash, it means they should be pressed together. If a keycode is separated
    by a space, it should be pressed separately.
-   **"C-c C-c":** press `CTRL` + `c` twice (which you usually will do by
    keeping your finder on the `CTRL` key and pressing `c` twice)

**IMPORTANT:** When I use key combinations which are part of the standard
Emacs distribution, I will always state this by writing something like

> &#x2026; use the standard key-combo "C-x C-f" (find-file) to open a file

When I do not mention the term *standard key-combo*, then the
command refers to a key-combination that works in this present
course configuration. It usually will use extra packages (all
packages come from the Emacs community's official repositories like the
GNU ELPA, MELPA, and Org). You can naturally change these later on
and create your own mappings that may better fit your own workflows
and keyboard layouts. Actually I encourage you to do so.


<a id="org7b5396d"></a>

### Activate a theme for better readability

The file you are viewing is written in Org mode which is a
sophisticated markup mode. Here, and also in other parts of Emacs
it is immensely helpful to use a theme that also visually marks up
the different text elements. The Emacs configuration for this
course has installed [Fabrice Niessen's Leuven theme](https://github.com/fniessen/emacs-leuven-theme), which is my
own preferred light theme (you can naturally install others later).

**The theme still needs to be activated.** Use your mouse to select
within the `Options` menu on the top of your Emacs window:
`Customize Emacs -> Custom Themes`. On the displayed page with themes,
select the `leuven` theme (not `leuven-dark`) and use the `Save Theme Settings`
button to save the configuration. Then you press `q` to quit this buffer,
and you will be back in our course's first lessons file.


<a id="org8c8fc8b"></a>

### Starting the lessons

You should now see an Emacs session that looks like this

![img](README-att/course-start.png)

Navigate to the first headline (headlines are marked by one or multiple
leading stars) and unfold it by using the `<TAB>` key while you are on it.
You can press `<TAB>` multiple times, and it will cycle between the different
folding states.

When you open the **Course basics** you will see the following and you are
ready to go

![img](README-att/course-start2.png)


<a id="orgb8e6bd4"></a>

### Starting can be hard

The problem with such a complete system like Emacs can be that it
is a bit difficult to find the optimal path of minimal effort. And
often in order to do a certain thing it would be nice if you already
could use some other functionality that rather should be taught later
in another context. So, it's kind of a classical bootstrapping problem.
I try to minimize these situations, but I'll probably fail a few times
(e.g. how should you visit a link from inside of emacs in the first chapter
if the handling of links is only taught later). But I'll try to put some
additional description in those places. Just fill an issue in this github
if something seems really way beyond what you think can be understood.


<a id="org2acb90e"></a>

## Planning of learning stages

This is what I am planning to cover. Let's see whether I'll be able to
pull through&#x2026;

The sequence beyond step 1 is up to change&#x2026; I will teach a small
number of work colleagues in this first round. I'll adapt to the
feedback I will get. All of this will be hands-on with prepared
documents for the lessons. The configuration will grow with the
material covered in the lessons - and I may leave holes for this
first round, since the coworkers know some items already.

I will try to teach the most important standard Emacs commands, but
a lot of material will focus on **using the benefits of modern packages**.
The most basic standard commands are important if one ever finds oneself
having to use an unconfigured Emacs. But the real convenience and power
is attained through the add-ons that the community has created over
the years.

This is a **work in progress.** The parts which I have already covered, I mark
by filled checkboxes.

1.  Basic Emacs and Org mode
    -   this is a big first stage, but I think that Org mode must be introduced
        early, because it is one of the principal features that immediately
        offers big benefits to new users
    -   basic editor features
        -   [X] file loading, saving, save as
        -   [X] searching for strings and regexps
    -   file management
        -   [X] efficient file navigation with helm and ido
        -   [ ] dired file manager - basic commands
    -   [X] org mode as a basic task manager (org agenda, basic org file features)
    -   [X] executing Emacs commands
        -   [X] using smex or helm to more easily execute commands
    -   [ ] Emacs package management
    -   [X] how to use the info and help systems
    -   [ ] minimal Emacs lisp knowledge, just enough to understand the config
        in a rudimentary way and lose the fear of parentheses
2.  Emacs for higher productivity, programming and system management
    -   [ ] Emacs daemon
    -   [ ] Magit - is there a better Git interface than this project from Jonas Bernoulli?
    -   [ ] Tramp (a killer feature for users working on remote hosts. Loved by
        system administrators and developers)
    -   [ ] Emacs keyboard macros
    -   [ ] do inline calculations with Calc
    -   Org mode
        -   [ ] Org capture - create tasks and back-links from everywhere
        -   [ ] basic org mode tables
        -   [ ] simple first steps with Org Babel
    -   [ ] dired revisited (filename in-buffer editing, etc)
    -   [ ] shell command execution from Emacs
    -   [ ] gpg for encrypting files
3.  Emacs for programming
    -   [ ] a look at some of the programming modes
    -   [ ] lsp-mode (a modern IDE interface in Emacs)
    -   [ ] linting (Syntax checking with flycheck)
4.  Authoring Latex, HTML, and other documents with Org mode
    -   [ ] write scientific documents containing math, preview the math
    -   [ ] include graphics and screenshots
    -   [ ] Org Babel for executing code and creating graphics from data
5.  Org Babel for real
6.  Fast Presentations with Latex beamer through Org
7.  Integrating with your browser
    -   [ ] Use Emacs to edit forms in browsers like Firefox or Chrome
        (through the daemon)
    -   [ ] org-protocol: transfer information from the browser to Emacs,
        e.g. mark some text in the browser and get it into Emacs, or
        convert a web page to org mode and find it ready in your buffer!
8.  Emacs and email
    -   [ ] mu4e and mbsync to manage email
    -   [ ] integrate email with org mode task management, making
        efficient use of org capture and email links in workflows.
9.  Emacs for science
    -   [ ] helm-bibtex
    -   [ ] org-ref
    -   [ ] org-babel
    -   [ ] org-noter and PDF management
    -   [ ] jupyter (maybe)

