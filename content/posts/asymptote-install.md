---
author: liyiyuan
comments: true
date: 2016-11-23 03:09:13+00:00
title: Asymptote Installation
---
**Computer condition:** Windows 10 
 
**Installation package:**    
Asymptote ([download](http://asymptote.sourceforge.net));
ghostscript ([download](http://downloads.ghostscript.com/public/));
gsview ([download](http://pages.cs.wisc.edu/~ghost/gsview/));
Python ([download](https://www.python.org/));
Imagemagick ([download](https://www.imagemagick.org/script/download.php)).

1.	**Install Asymptote** (compulsory):  
asymptote-xx-setup.exe (e.g. asymptote-2.38-setup.exe).   
Note: it has to be added to the environmental path. (My computer 
– Properties – system – advanced system settings – in “Advanced” tab, 
click “Environment Variables” – in “System variables”, choose “Path” 
section then “Edit” – Add the path where you install the Asymptote) 
( e.g. C:\Program Files (x86)\Asymptote)
2.	**Install ghostscript** (compulsory):   
Choose the version suitable for your computer (e.g. gs919w64.exe). 
Install it directly.
3.	**Install gsview** (compulsory):   
Gsview is used to view the default PostScript output. (e.g. gsv50w64.
exe). Double click and install it directly.
4.	**Configuration** (compulsory): 
Go to C:\user\your username\.asy( e.g. C:\user\Yiyuan\.asy), add a 
new file named “config.asy”, use notepad to open it, then put your own 
gsview/PDF viewer/ghostscriptinstallation path in the 2nd/3rd/4th line.    
   ```    
   import settings;
   psviewer="C:\Program Files\Ghostgum\gsview\gsview64.exe"
   pdfviewer="F:\Program Files (x86)\Adobe\Acrobat 11.0\Acrobat\Acrobat.exe"
   gs="C:\Program Files\gs\gs9.19\bin\gswin64c.exe"
   ```	

5.	**Install Python and Python PIL** (optional): 
Phtyon is only required if you wish to try out the graphical user 
interface. (e.g. python-2.7.12.msi & PIL-1.1.7.win32-py2.7.exe)    
Note: the version of python and python PIL should stay the same.
6.	**Install Imagemagick** (optional): 
Imagemagick is used ot change the graph formats other than EPS, PDF 
and PNG. (e.g. ImageMagick-7.0.2-6-Q16-x64-dll.exe) Install it 
directly.    
Note: during the installing process, you will be reminded to choose 
the Imagemagick functions you’d like to install, please make sure to 
click “convert”. Otherwise, the output format cannot be changed.

After all these installations, Asymptote can be used to draw an 
amazing picture. Write a test.asy file in notepad, in command prompt 
(“ctrl+R”, input “cmd” and “enter”), point the path to the test.asy 
file, input “asy –V test.asy”, then click “enter”, ready to get your 
own awesome graph, Yeah!

To change the format of graphs, just input “asy –f pdf test.asy” in 
cmd. (pdf is the format wanted).

