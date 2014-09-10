---
published: true
---

My employer uses Perforce for version control. For a tool that costs hundreds of dollars per seat, I am amazed at how much it gets in my way during daily development tasks.  

## If Merging Wasn't Such a Chore, I Would Be So Happy

I had some minor gripes with Perforce (as you will see later on) before, but once my project got to a stage where creating a release and develop branch made sense, my frustrations reached a new high.

To start with, Perforce offers different ways of branching, [Branches and Streams](http://www.perforce.com/perforce/doc.current/manuals/p4guide/chapter.codelines.html). Sure, let's take the most difficult part of Version Control and introduce confusion with options which can't be clearly distinguished from each other without reading a manual. We settled on using branches, although, in hind-sight, streams appear to be a lot nicer. 

After I had some changes on the development branch that would also come in handy on the release branch, I started a merge operation. This is not the simple one-step process I was used to in [Git](http://git-scm.com/). Merging branches in any SCM roughly involves  these three steps:

1. Push a set files or change-sets from one branch to another
2. Resolve conflicts
3. Commit changes on the branch you merged to

In Git, this is a simple, one-step process. In Perforce, each of these steps has be done independently, unless you select some very specific options in the first step. Also, for a tool which uses change-sets, it defaults to merging specific files, which did not help the learning process.

## Bugs are Bad, MMKay

To interact with Perforce repositories, the primary GUI tool is the [Perforce Visual Client](http://www.perforce.com/product/components/perforce-visual-client). This tool seems to forget my password at random intervals, while I am working inside of it. It will then ask me to enter it three or four times in a row. Perhaps I entered it wrong, but there is no indication that this is the case.

On the IDE integration front, things are even worse. There is a plug-in for Visual Studio called [P4VS](http://www.perforce.com/product/components/visual-studio-plug-in), which lets you see file status and such right in your Solution Explorer. I didn't think it was possible, but I think this plug-in is buggier than Git integration with Eclipse:
 - Every time I open a project, I have to log in to Perforce. If I go into the options to connect to the server automatically, one of settings (usually the name of the workspace) gets mangled and I am presented with a dialog anyway.
 - File status never seems to update automatically. If I submit a file using P4V, the file will remain flagged as having been modified inside of Visual Studio until I force a refresh.

## I Feel Like I am Taking Crazy Pills

Yep, this sounds like a rant against a tool used by hundreds of thousands of developers every day. And it is. But the fact that this tool is used so widely is why I had to write about my frustrations with it. Perhap I am missing something, but I was far more productive with Git, wether it was in Linux or Windows.
