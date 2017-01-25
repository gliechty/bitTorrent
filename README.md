# Intro to BitTorrent

### What is it?

In a word... peer-to-peer (P2P) file sharing. 

### What problem does it solve?

In a normal client-server model, with many clients requesting the same file from a server, a server will crash if it gets overloaded. It's a one-way sorta thing. Like any relationship, with no give-and-take, things get strained. But wait...if Bob has a file, and I want it, and a computer is basically a server, and there are millions of people who have the same file (on as many servers), and millions that want it...why not just distribute these requests equally to avoid overload? Makes sense, right?

But, why the 'bit'?

Well, BT clients manage a download of a larger file in pieces...hundreds at a time. This makes the whole transfer part easier. When I download a movie, the first 1/100th (or 1/200th) piece can be shareable as soon as I download it. It's kind of like being able to push to github when I've only cloned the README, while the rest of the directory is still being brought down. To make the inevitable LOTR reference, this means you can start downloading the Fellowship of the Ring from my computer, as I'm watching it, before I even get to Bree.

Which leads us to...

### The Golden RULE!

Don't be a LEECHER. Be a SEEDER.

Bit torrent tracks your upload to download ratio, which, if too low, can make the community hate you (like a griefer). For the system to work, the your ability to download must be equal to others' proclivity to upload. The more SEEDERS there are (people uploading files) the faster the overall download speed will be across the community. People who just download files without uploading, to save on personal bandwidth, are considered to be just a notch up from the common hagfish. File sharing can only exist with this balance being maintained. Otherwise it's just...file mooching?

### Sounds sorta sketch, is it Legal?

Yes and No. Anything under creative commons (and/or something educational) is a YES. If under copyright, then no...on paper. To be safe, look for files with a large number of seeders and relatively few leechers, both for a faster download and to have a better sense of which side of the law you're on.

These countries are the safest:

(according to limevpn.com)

- Switzerland, the Land of Free Downloads (ok to download for personal use, not profit)
- The Netherlands (ok to share works of art)
- Mexico (they don't really have laws on this stuff)
- Spain (one of the first countries to recognize intent to make profit vs intent to share)

But this shows countries that download the most (spoiler alert: we're #1).

![map of biggest downloaders](https://i.kinja-img.com/gawker-media/image/upload/s--FHGsk0-d--/c_fit,fl_progressive,q_80,w_636/17zg6lnxf04rnjpg.jpg "top downloaders")

### How does it work/How do you use it?

To start torrenting, you need two things: a torrent client (like uTorrent) and a file to upload/download- that's it. 

Here's how it starts: 

Sally has a file >>> Richard requests it, and downloads >> Now they both have it, and both upload >> Susy wants the same file, requests it, and downloads at twice the speed (!) >> ad infinitum...

### The process in more detail:

To start your life as a torrenter, you first install a client (uTorrent being the most prevalent), and then create a .torrent file. This relatively small file contains meta-data about trackers, i.e. servers that point your computer to other computers (peers) that are sharing/downloading the file. You now can start swarming.

![Step 1](./assets/step2.PNG?raw=true "Step 1")

At first, you'll be the initial seeder. Imagine you have a file that can be broken into 10 parts. "Kevin" gets the first part, "Larry" gets the second, "Merry" gets the third, and so on throughout the 'cohort' of peers in your swarm. 

![Step 2](./assets/step3.PNG?raw=true "Step 2")

Here's where the magic happens. Everyone has their own little piece of the pie, but they can upload that piece and download others' simultaneously. The file sharing protocol favors altruistic peers, meaning it will connect by default with others who are uploading their chunks. 

![Step 3](./assets/step4.PNG?raw=true "Step 3")

Large files are transfered in pieces in the same way, each with an 'index' that identifies which part of the file it is. The client will keep track of these indexes, and sort the pieces no matter which order they are uploaded in. 

![Step 4](./assets/step5.PNG?raw=true "Step 4")

### The Code

C++ is a pretty dominant language used for open-source bitTorrent client libraries. libTorrent is perhaps the most prevalent of these. (uTorrent is one of the largest overall, and was originally written in Python. Now it's become closed-source. Booo.)

One of the basics to adding a torrent file to a session is the add_torrent_params constructor, 

struct add_torrent_params
{
   add_torrent_params (storage_constructor_type sc = default_storage_constructor);

   enum flags_t
   {
      flag_seed_mode,
      flag_override_resume_data,
      flag_upload_mode,
      flag_share_mode,
      flag_apply_ip_filter,
      flag_paused,
      flag_auto_managed,
      flag_duplicate_is_error,
      flag_merge_resume_trackers,
      flag_update_subscribe,
      flag_super_seeding,
      flag_sequential_download,
      flag_use_resume_save_path,
      flag_pinned,
      flag_merge_resume_http_seeds,
      flag_stop_when_ready,
   };

   int version;
   boost::shared_ptr<torrent_info> ti;
   std::vector<std::string> trackers;
   std::vector<std::string> url_seeds;
   std::vector<std::pair<std::string, int> > dht_nodes;
   std::string name;
   std::string save_path;
   std::vector<char> resume_data;
   storage_mode_t storage_mode;
   storage_constructor_type storage;
   void* userdata;
   std::vector<boost::uint8_t> file_priorities;
   std::string trackerid;
   std::string url;
   std::string uuid;
   std::string source_feed_url;
   boost::uint64_t flags;
   sha1_hash info_hash;
   int max_uploads;
   int max_connections;
   int upload_limit;
   int download_limit;
};
