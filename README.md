### bitTorrent

### Intro to Bt

#### What is it?

##### In a word... peer to peer file sharing (the thing people did before everyone got lazy and just did Netflix for watchng movies). 

### What problem does it solve?

In a normal client-server model, with many clients requesting the same file from a server, a server will crash if it gets overloaded. It's a one-way sorta thing. Like any relationship, with no give-and-take, things get strained. But wait...if Bob has a file, and I want it, and a computer is basically a server, and there are millions of people who have the same file (on as many servers), and millions that want it...why not just distribute these requests equally to avoid overload? Starting to make a lot more sense, right?

But, why the 'bit'?

Well, BT clients manage a download of a larger file in pieces...hundreds at a time. This makes the whole transfer part easier. When I download a movie, the first 1/100th (or 1/200th) piece can be shareable as soon as I download it. It's kind of like being able to push to github when I've only cloned the README, while the rest of the directory is still being brought down. To make the inevitable LOTR reference, this means you can start downloading the Fellowship of the Ring from my computer, as I'm watching it, before I even get to Bree.

Which leads us to...

### The Golden RULE!

Don't be a LEECHER. Be a SEEDER.

Bit torrent tracks your upload to download ratio, which, if too low, can make the community hate you (like a griefer). For the system to work, the your ability to download must be equal to others' proclivity to upload. The more SEEDERS there are (people uploading files) the faster the overall download speed will be across the community. People who just download files without uploading, to save on personal bandwidth, are considered to be just a notch up from a common hagfish. File sharing can only exist with this balance being maintained. Otherwise it's just...file stealing?

### But wait, is it Legal?

Yes and No. Anything under creative commons (and/or something educational) is a YES. If under copyright, then no...on paper. To be safe, look for files with a large number of seeders and relatively few leechers, both for a faster download and to have a better sense of which side of the law you're on.

These countries are the safest:


But this shows countries that download the most (spoiler alert: we're #1).

![map of biggest downloaders](https://i.kinja-img.com/gawker-media/image/upload/s--FHGsk0-d--/c_fit,fl_progressive,q_80,w_636/17zg6lnxf04rnjpg.jpg "top downloaders")

### How does it work/How do you use it?

To start torrenting, you need two things: a torrent Client (like uTorrent) and a file to download- that's it. 

Here's how it starts: 

Sally has a file >>> Richard requests it, and downloads >> Now they both have it, and both upload >> Susy wants the same file, requests it, and downloads at twice the speed (!) >> ad infinitum...

### The process in more detail:

To start your life as a torrenter, you first install a client (uTorrent being the most prevalent), and then download a .torrent file. This relatively small file contains meta-data about trackers, i.e. servers that point your computer to other computers (peers) that are uploading the file you ar requesting.

![Step 1](/assets/step1.png?raw=true "Step 1")


