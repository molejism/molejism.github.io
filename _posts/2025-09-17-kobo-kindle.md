# Oh god I hate commercial ebooks


I hate amazon ebooks, I hate google play ebooks and now I hate kobo ebooks.

Some years ago I tried reading an amazon ebook without having a kindle nor a mobile app,
and realised the lengths to where the web reader went. I saw it was rendering text as an
image so that you can't select, copy and paste text in case you wanted to take notes. If I remember
correctly there was no way of downloading the ebook to read on your preferred application, much less
offline.

Google play books was a similar experience although a bit better.

But I don't remember exactly those cases and today I want to complain about Kobo.


## Kobo

Some time later I decided to buy a kindle to be able to read when I travel, given that the phone screen is too
uncomfortable. Sending ebooks bought in amazon is relatively easy.

However, today I bought a book from kobo, and tried to put it in my kindle. How hard can it be?

Well, fuck my life and fuck kobo and fuck adobe. And fuck amazon too.

### Download the ebook

The ebook from kobo has a DRM from adobe, and when I click "download" in my library in the kobo
website, it fucking downloads an xml containing a fucking link to the fucking kobo website. Do you
know what download means??

Ok, kobo has phone apps (which I'm not going to install because android is one of the most
insecure operating systems of all time), and desktop apps. I assume those apps will download the
book for simplicity, and if the app can read it offline, the data should be in my machine and I
should be able to read it too without the kobo app.

Let's install the desktop app. Oh right, it's only built for windows and mac, ffs. Right, install
wine and run the windows installer with it. The desktop app is running in my linux. At least that
was easy (once I read the suggestion that wine should work with it). I have to log in my account in
the desktop app, and then I can read the book I bought.

So if I disconnect from the network and restart the kobo desktop app, can it still open the book?
Yes, it can. That's good news. Probably it has the book somewhere in my disk. Let's do `lsof -p <PID>`
to see the opened files the process has. One of them is like
`~/.wine/drive_c/users/myuser/Local Settings/Application Data/Kobo/Kobo Desktop Edition/kepub/<uuid>`.

`file <the-file>` says it's an epub, but when I open it on calibre, the text is mangled, like I was
reading binary data. I assume this has to do with the adobe DRM.

### Remove the adobe DRM

The xml file I donwloaded from the website at the beginning has a .acsm extension, and some people
say that the file can be loaded in one of the adobe programs, and then take the
ebook out, but I have zero interest in installing anything from adobe, much less in linux.

I found the okob plugin for calibre under the [DeDRM
project](https://github.com/noDRM/DeDRM_tools/releases/tag/v10.0.3). Unzip, and install the plugin
from calibre.

In calibre I can load the file that the kobo desktop app had opened, and use the plugin with it. The
first attempts don't work for some reason, the okob de-DRM plugin can load the book but the text is
still mangled. After some attempts, I don't know what I did differently (deleted the file and
reopened) and the plugin managed to get the proper text. Hooray! In the past, from this point I managed to send
books to my kindle, so should be easy now.

### Transfer to kindle

In the past I found that the kindle doesn't like some formats, and the one that seems to work best
is azw3. From calibre I convert the epub to azw3, and then I connect with usb the kindle and copy
the azw3 file over.

Finally I can read the book I bought in the kindle I bought, and this whole process has felt like
I've been pirating! Fuck these companies, seriously.

The cherry on top is that the kindle refuses to show the cover, either in the book list or when the
kindle is stopped. Reading some forums it seems that "copying the file from calibre, disconnecting
the kindle, connecting again and fixing the metadata" might work, and it indeed fixes the cover
image in the book collection but not in when the kindle is off. Some people say that if I email the
file over to my kindle email address, amazon will convert the ebook properly and keep the cover
image, but fuck amazon and their data tracking workflows.

Well, I give up, I still managed to be able to read it in my kindle. Fuck DRMs. Fuck all the
companies making their products only work in their plaftorms, and fuck them for trying for us to not
really own what we buy. Fuck everyone individually who has spent time making this process so
difficult. And thanks to the free software community for giving me my freedoms back.

