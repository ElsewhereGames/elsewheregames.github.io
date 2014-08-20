---
published: false
---

The development shop I am working for currently uses Perforce for version control. For a tool that costs hundreds of dollars per seat, I am amazed at how much it gets in my way during daily development tasks.  

## Perforce Tools
To interact with Perforce repositories, the primary GUI tool is the [Perforce Visual Client](http://www.perforce.com/product/components/perforce-visual-client). 
## Development Tools Integration
There is a plug-in for Visual Studio called [P4VS](http://www.perforce.com/product/components/visual-studio-plug-in), which lets you see file status and such right in your Solution Explorer. I didn't think it was possible, but I think this plug-in is buggier than Git integration with Eclipse:
 - Every time I open a project, I have to log in to Perforce. If I go into the options to connect to the server automatically, one of settings (usually the name of the workspace) gets mangled and I am presented with a dialog anyway.
 - File status never seems to update automatically. If I submit a file using P4V, the file will remain flagged as having been modified inside of Visual Studio until I force a refresh.

