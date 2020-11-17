---
title: 'Making my writing setup my own'
date: '01-11-2020 18:28'
aura:
    pagetype: website
metadata:
    'og:url': 'http://site.neurario.com/blog/2020-writing-setup'
    'og:type': website
    'og:title': 'Making my writing setup my own | Neurario Dot Com'
    'og:author': 'Neurario Dot Com'
    'twitter:card': summary_large_image
    'twitter:title': 'Making my writing setup my own | Neurario Dot Com'
    'twitter:site': '@splatsune'
    'twitter:creator': '@splatsune'
    'article:published_time': '2020-11-01T18:28:00+00:00'
    'article:modified_time': '2020-11-17T07:28:17+00:00'
    'article:author': 'Neurario Dot Com'
---

In the process of making [the latest chapter of Begin Again](/writing/begin-again/part-3/02-neu-wave-music), I more-or-less finalised the system that I use for writing and putting new chapters together. 

===

You can see a bit of that in this screenshot:

![image|690x374, 100%](upload://c3NwOOuUcO2gTghpy75WVaD4RXa.png) 

What I have at the moment is a means to split my writing in a way that lets me split my chapters into scene-by-scene files that are based on the Markdown formatting language - essentially, text files. This structure also allows me to write a scene that comes to mind, no matter how far ahead in the story it might be.

Then, when I want to see what that writing looks like rendered out, I put together a script that works using Microsoft Powershell to sort all of the files in the correct order (harder than it sounds), and pipe the content into a program called Pandoc that converts that Markdown/plain text into a nicely formatted HTML or ePub file. Then I can just grab the rich text from that file and copy it directly into AO3 or Fanfiction.net (by the way, [I maintain a mirror of Begin Again there](https://www.fanfiction.net/s/13397436/1/Begin-Again-Chronicles-of-an-Ex-Human-In-Inkopolis), as one story - I wonder if I should have done that here on AO3... but it's a bit late now).

This got me thinking a bit about how I progressed through different writing solutions, and the question of:

**What do I use to write?**

The answer for me, right now, is: "Whatever text editor I feel like."

---

# Editing Begin Again, through the ages

When I first began writing Begin Again, I was basically trying to write down a thread of daydreams I was having so that I wouldn't forget them, and so I just used Google Docs to write everything. Google Docs because it has an interface both on computers /and/ on mobile, because I was doing a lot of writing through my phone while on breaks at work.

![image|690x381, 75%](upload://abrf2cAUfTyhVriMzJcGNqHmo59.png) 

In fact once I started writing it as an actual story I used one document for everything - all of Part 1 and the first third of Part 2 (in its initial form) was written in the same document. Unfortunately, once it had gotten to this point it was approximately 100 pages and the document was slow to load for editing, or for sharing with other people.

I began looking for an alternative, and was pointed toward a program called Scrivener - a tool made specifically for writers, with an organisation system I still love and wanted to emulate in my own system. Unfortunately a few things made this too annoying to use regularly, especially on a mobile OS (where it is only available on iOS, and I flip-flopped a lot). Otherwise a very good tool and I would still recommend it if you're serious.

![image|690x414, 75%](upload://2AzPFahlFsYHUdv0AGyW18rvTCT.png) 

I actually settled on a site/webapp called Notion for quite a while, and used it to write the rest of Part 2 and 2.5 due to its easy access to desktop *and* mobile apps - while I'm not sure straight writing was part of its use cases, the ability to nest pages in pages and format the pages in different ways made it handy as a dashboard too, and I ended up using this as my home for my series' world building, character pages, etc.

![image|634x500, 75%](upload://dbfTAMMRW1EgsWJef9kYYHF1f2.png) 

But the system I had in place for my chapters and WIPs made it difficult to just write a scene ahead of where I was even in the same chapter - ideally in Notion you would create a new page and write your scene in there, and then I guess copy it back to the main file.

---

# Designing a new solution

As I started Part 3 I decided to try and get my own system going. I wanted a few things:

* The ability to write where-ever inspiration struck
* The ability to write separate files, and be able to rearrange simply
* Something lightweight and fast, at least for the end-user

What I came up with is the system you see in the leading screenshot. If you're interested in the code and settings (and what the actual directory tree looks like, spoilers ahead), here it is on GitHub:

https://gist.github.com/sflavelle/7bc59eb837d476a666bb87120849b569

I took my existing chapters and files, split them as much as felt appropriate, and dropped them in a directory structure that's sorted by Part and then by Chapter. All of the chapter directories and scene files inside are of the format `01 Descriptor`. Inside is the text of that scene in Markdown, with any required formatting (plus the chapter title if it's the first scene of that chapter). Parts have a single file inside their directory that gives them their header, before you start recursing into subdirectories.

Once I'm happy with the content and want to convert it from Markdown into HTML, or into an eBook, the script I wrote will grab all of those .md files and pipe them into a tool called Pandoc, which does the heavy lifting of translating the Markdown into the different formats (in this case, HTML and ePub).

Sounds easy, right?

# Oh Hell No

As it turns out, getting this directory structure into Pandoc in a meaningful way was quite an exercise. Let's go over the issues I ran into. (This is going to get techy...)

## **You can't input a directory into Pandoc**

You can by all means input *multiple files* to the tool and output it into one merged file, but you can't give it a directory and tell it to convert everything inside into one file.

What you *can* do though, which I found out stumbling around the issue, is that if you provide Pandoc with a stream of text through stdin (that is, if you send text directly into Pandoc without specify an input file, it is capable of converting it.

Knowing that, and knowing a bit of the `find` command in Linux/macOS, I eventually settled on a command that would search the writing directory for all Markdown files, print their contents, and then send that as one complete stream into Pandoc.

Oops! It doesn't sort by default, usually. That's okay, I'll just add the `-s` switch to `find`. Now it's working pretty much as intended.

## **It required some tweaks to my file structure**

Not to say that it didn't go perfectly. This version revealed some issues with my current setup. Namely, the header files for each part would show up *after* their part was over, rather than at the beginning.

Once I realised *why* this was happening, renaming the header files from `part-header.md` to `00-part-header.md` was fairly trivial.

The other issue was that I would have to implement zero-padding for the chapter numbers for certain parts. This is because in the world of Windows, the sorting can be smart on occasion - it recognises that 1 comes before 2 comes before 12, because doing otherwise would be confusing to the end user. For macOS (and Linux, because really this was just a shell script) 12 would be *in the middle*, because from a string standpoint:

* The number 1 would be first as it's the /shortest/ and comes first from a alphanumerical standpoint
* 12 would be next because it *still has the number 1 first*

The solution for this? Zero padding. Because Chapter 2 had more than 9 chapters, adding a '0' to the *start of the filename* solves the issue and causes them to be checked first before proceeding through the rest of the files.

So, like the part header, `7 Metal Bork` became `07 Metal Bork`.

OK, so that is pretty much everything right? After a bit more configuration, the result looks great on macOS.

But I so a lot of my writing on Windows as well, and let's say I want to compile a new version there, too. Thanks to the *Windows Subsystem for Linux* (WSL) I can install those same Linux applications/utilities and run that script there too.

## **Windows sorts items differently.**

So you know how we just fixed the filenames so certain files would be shown first, because they should? On Windows that's not enough.

It turns out that some tools and some operating systems have what's called *depth-first search* - which basically means they'll search any subdirectories first, before coming back to look at what other files are in its own directory.

I tried a lot of different things with `find` to get it to do what I want on Windows, including finding different finding tools.

But in the end, I ended up dusting off Microsoft Powershell and beginning to learn that, to see if I could do what I wanted.

![image|689x274](upload://yBhLteptUWRSj0KypGwwLRNuiYl.png)
I got it pretty much perfect.
Left: macOS compile. Right: Windows 10 compile.

Somewhere along the line I realised that Powershell is actually cross-platform now - but it was only in the last few weeks that I actually put in the time to make the Powershell compile script the definitive version:

* Being able to compile specific parts or chapters, and not just the entire fic
* Copying all that text into a variable, and not leaving a file behind
* Using more of Powershell's tools to make getting paths easier between both systems

# And now we're here

So now the Powershell script has superseded the original bash script, and works cross-platform - using Powershell's own tools to get everything in order on Windows, and falling back on `find` with some Powershell assistance on macOS and Linux. Because the project folder is on Google Drive, I can edit it whereever I feel like, including on my phone (via iOS apps like Markdown Pro), and then when I get to a computer I can compile the full story whenever I feel like.

I will say, when I was thinking about working on code, for this or for my Discord bot project, I was not writing, so uh... whoops?

But as a result, now I have a system that will work with whatever text editing program I feel like using, I can get as granular as I like, I can write whatever I feel like and drop it in whereever I feel it might be needed...

I feel more free to write!