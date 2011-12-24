#Learn HTTP the Hard Way

I've been talking to a lot of new programmers about how HTTP works and why we build apps with HTTP.

I wanted to take a lot of those lessons and codify them into something that can be worked with
asynchronously.

The goal of this project is to teach HTTP in order to use the protocol to understand and make web applications. I'm going to use curl, wget, sinatra, chrome and jquery to introduce the HTTP concepts important in designing and delivering web applications in any environment.

Definitely included will be:

 * URLs
 * Response Codes
 * Verbs
 * Headers
 * Response/Request Body
 * Resource Orientation

Note: this project is mirrored at both [github](https://github.com/kylefritz/learn-http-the-hard-way) and [gitorious](https://gitorious.org/~kylefritz/learn-x-the-hard-way/learn-http-the-hard-way).

---

This is a starter project for people looking to make a "Learn X The Hard Way"
book.  If you want to have a book for your favorite language, and you like the
style of "Learn Python The Hard Way" and "Learn Ruby The Hard Way", then this
kit will get you started quickest for the best results.

I've developed this kit after using various publishing and authoring systems
over the years, and I've found this to be the best for producing high quality
self-published text.  It does require you to learn LaTeX, but I'll be including
a crash course in LaTeX that uses the features of this book kit.

Getting Started
===============

First thing is, you should install both tex-live and dexy.

To install tex-live, follow the quick instructions [here](http://www.tug.org/texlive/quickinstall.html).

As for dexy, make sure you have python installed, and then simply

    $ easy_install dexy

You may or may not need sudo. If this doesn't work for you, check the instructions on [Dexy's site](http://dexy.it).

Once you have those, try this:

  $ dexy --setup
  $ make

This will produce all the gear for dexy, and then build the sample starter book
into output/book-final.pdf.  Go look at that book and see what is produced.


Setting Up Your Book
====================

You should now probably setup whatever revision control tool you need to use.
If you want to keep using git, then I suggest doing:

  $ rm -rf .git
  $ make clean
  $ git init .
  $ git add .
  $ git commit -am "first commit"

That will make sure you get a clean git setup that is just for your book.  Feel
free to change the above to fit whatever system and workflow you need.

Once you have this setup, you then want to edit the kit to fit your book.
Here's what you need to change:

1. book.tex -- Set your own author and title settings at the top.
2. preamble.tex -- Do the same for author and title in the PDF specifics here.
3. Makefile -- Change the target host for rsyncing it to your server if you use one.

Make the book again and check the resulting book-final.pdf to see your title.

Structure And Initial Content
=============================

Now you can lay down your structure and introduction.  Here's what I suggest.

1. Write a quick introduction in the introduction.tex to get your feeling down.
2. Write your preface.tex to give some personal stuff about you, why you're writing.
3. Edit ex0.tex such that it teaches a total nobody how to install the needed gear.
4. Edit ex1.tex such that it teaches a total nobody how to print out a bunch of stuff.
5. Edit next.tex to explain where the student should go after finishing your book. 

Once you have this you should have a basic feel for the book, and enough
content to show it to some people.  Show it to a few folks and watch them try
your exercises.  This will tell you if you've got it simple enough.


Recommended Contents
====================

I recommend for your ex0.tex install instructions you focus on the following:

1. Use just a simple editor like gedit, notepad+, or Textwrangler.  NO vim! NO emacs!
2. Do *not* have them use git or other RCS tools. They're here to learn code, not git.
3. Make it work for Windows, OSX, and Linux if you can.
4. The install of your language should not involve tons of steps.

For your introduction, and for the whole rest of the book, remember these
points:

1. Your book should *educate* people, not *indoctrinate* them.  If you find
yourself talking constantly about how awesome your language is and how it will
change their life, then you're not educating, you're just making another cult
follower.  Leave the decision of whether the language is good to the reader.
2. Read through my Introduction and give advice for learning, especially persistence and
how the book is *supposed* to be hard and tedious at first.
3. Be honest about flaws and problems in your language so the reader is not discouraged
when they encounter them.
4. Lightly make fun of programmers and inoculate your student against religious wars
over syntax, idioms, editors, tools, and anything else that gets in the way of them 
learning.  Remember, you are writing this book for *them*, not your fellow coder 
friends.
5. Make it clear that programmers are not scary geniuses.  This goes a long way to
encourage your readers to try to learn as it will reduce their "code anxiety".


Working With Dexy
=================

Dexy is fairly new, but a very good tool for this kind of work.  What it does
is take code for your exercises and then injects it into your .tex files in a
nice pretty printed format that's publication ready.  You use it like this:

1. Edit the .dexy file and put your language extension in there like I've got.
The syntax is FILENAME_PATTERN|FILTER1|FILTER2, etc.  For mine, I'm mostly using
the pyg(pygmentize) filter.  For python, it looks like this: "*.py|pyg|l": {}.  *.py
is the pattern of files to convert, pyg is the pygmentize filter for highlting code
and "l" is the filter for converting to LaTex.  
2. Put your code for each exercise in code/ named after each exercise.
3. Look at the ex0.tex that I've written which shows you how to include this code.
4. Finally, if you want to show the output of your programs, there are two ways to
do this.  If you want to use dexy, you can create another entry in .dexy like this:
"*.py|py|pyg|l".  This means, run the code through python (py), then pass the result
to pyg (if you are generating HTML or xml or whatever it will be highlighted), and
finally, pass to the LaTeX filter.  The other low tech way is simply to put the output for each program into code as ex#.txt and 
include that as well. ex0.tex has both.

Refer to http://dexy.it for more information on how to use it.


Working With Tex
================

TeX (or actually LaTeX) may seem daunting compared to markdown or textile, but
it's actually fairly easy.  Get yourself one of the many LaTeX cheat-sheets out
there and sit down with it to write.  The things to remember are:

1. TeX assumes anything not marked up is just a paragraph of text. Write like normal.
2. Block style things, like lists and code blocks, are bounded by \begin{thing} and \end{thing}.
3. Look in commands.tex for a list of available blocks and helpers I've already written.
4. Write your own helpers for things you seem to write over and over again.

The power of TeX, apart from its awesome typesetting and structure, is that you
can extend it to include your own macros and time saving tricks.  Steal
anything you can find about it.


Last Steps
==========

Once you've got your voice and initial setup, I recommend that you go through
and setup all the titles and the big structure of your book.  Look at LPTHW to
get a general idea of a good structure.  Here it is in a short form:

1. Two sections split at 26 exercises.
2. First half is repetitive interactions with the computer that are immediate, with heavy
focus on functions and no objects, complex data structures, algorithms, or math.
3. Second half is a sudden ramp-up in difficulty that teaches logic, OOP, data structures,
and the more complex things your language features.
4. Focus on simple text adventure games as the main kind of program they make.  These are
fun, easy to create, immediate, and don't require any special geometry skills or graphics
systems.

The way to think of the book's structure is the first half gets them strong,
the second half gets them skills.  In the first half they're just doing
push-ups and sit-ups and getting used to your language's basic syntax and
symbols.  In the second half they use this strength and grounding in the basics
to start learning more advanced techniques and concepts, then apply them to
real problems.

I recommend that you create a single text file and make a basic outline of all
your chapter titles to get an idea of your structure.  Once you've got that
kind of thought out, go through and fill in each of the ex#.tex files with the
titles and a short note on what you plan to teach there.  This will turn the
book into an easy to follow TODO list of what to write.

Then, just go through and write each one in order and change later ones as you
go in new directions.  Don't be a slave to your structure, but having one helps
keep you motivated and organized.


Publishing Your Book
====================

If you want help publishing or promoting your book, then contact me at
zedshaw-AT-zedshaw.com.



