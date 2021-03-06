- New blog!
I'm working on using the following stack 

-----------

  - Hugo
  - Vercel
  - Webpack
  - Gulp
  - FaunaDB
  - Percy
  - Sentry
  - ...and more: https://jarv.is/uses/
  
  ----------
  
  to set up a blog. Need to learn the markup, so will be practicing on here for a bit. Plan is to auto-generate based on github I suppose. Depends on the availability of the mobile app. 
 
 So why did I decide to create a blog? Well I just completed what I would call a "sprint", where you spend long hours on projects, often with little to nothing to show for it. 
 
 This weekend I redesigned my computer on a spare NVMe solid state hard drive. For those that don't know, that's where everything - literally - is stored, so you can typically swap them out and it's 
 like you are using an entirely different computer. 
 
 This past weekend I tried a build I have been wanting to do with Linux for some time now. 
 
 Essentially, this is what I set out to achieve:
 
 # Hypervisor
 - Hypervisor
     - Windows 10 VMX w/ GPU passthrough (dedicated GPU for CUDA)
     - Debian / Fedora based OS (Non-CUDA)
     - IPFire / pfSense / etc.
     
The hypervisor for this project was Xen in the super-hardened Qubes OS. A Qube is essentially a virtual computer that lets you interact with it without seeing a startup or login screen. What this boiled down
to was having about 5 Firefox installations by default. I was able to clean it up a bit and get to what I was trying to do, where each monitor has an OS and they can flip around quickly. Unfortunately, I ended
up wanting to put VMWare Workstation Pro within Windows 10, which was already inside of Xen. While Xen performed well even without the Nvidia drivers, I was not able to get virtualization to work within Xen for
yet another virtualization. 

The point of having the GPU passthrough is so that you get all the power of it without losing precious resources. New features have to be accounted for with virtualization and it is slower in the process and further down the pipline when they become available. For me now, it's not even that big of a deal, until you throw in OpenCL / CUDA / models. I tried to face swap myself onto Beyonce once (don't ask) and 30 seconds would have taken upwards of 3 days to do in HD. That's realism though. It's expensive, but get's us the new Lion King.

# What's the point of all of this? Why not just use a KVM?

## Conveience / Performance
A KVM lets you use one mouse and keyboard for multiple computers, which would achieve almost identically what I am doing aside from one thing: NVMe. It boils down to speed. Launch times. File copy rates. Processing power. This is why
it is typically housed in a beef uped server, but the equivalent cost would be upwards of $10,000 and I'm capable for the most part of achieving the same thing with a Workstation. Especially nowadays. My workstation is actually my 
gaming rig. 

## Security
Another important factor, especially with 20+ hours put into the build and a lifetime of content storage archived on it. Not to get too personal, but I personally struggle with mental health. While I'm a survivor, I have definitely been put to the test. It's one of the reason's I'm starting this blog, since no one knows what I do. ????

Sparing you the gory details, what I learned from it all was that there are some important factors with a computer or technology in general: 
- Security - It's mandatory to be not have files tampered with if you need the originals to not skew data. Most people attribute this to an antivirus, but to me it's called "hardened" and prevents them in the first place.
- Disaster Recoverability - This one is widely known, but the biggest disaster I was expecting where I live (in 30 years) was tossing my computer off the desk. To which it survived.
- Account Recoverability - This one upset me with el goog a bit. I managed to delete my phone number and account after a 20+ day debaccle with what I believed were some hackers. [If you know me, you would know I don't typically NEED an antivirus. PC runs prestine at all times. Phone too.] Needless to say, while I had backups exported, I lost a chunk of data and a time period of my life in the future, which matters a great deal to me. My mother had photos, I have the entire picture derivable with content. Data Science. How often can you go back and say "well, that's why I became that way, here's an alteration to my incoming messages to fix that in the future." This is where we are going, it's not here yet, but Facebook I know has some fun behind the scenes.

## Firewall
Most routers nowadays, even at the $600 mark, are 4-6 core 1.8 Ghz. While this is a good chunk of my PC, that's a good chunk of money. Why not dedicate a tiny Quadro for a hundred or so into some real intrusion detection and prevention with not just detecting the exploit, but looking for anomalies. (Said like Anenanenomies.) These routers still do not have this feature from what I have seen if you buy them at Best Buy. You need open source power-house software that rivals the big boys used in fortune 500's. Quantum was one of my nightmares as a young child. It's here. There paradigm has officially shifted. Super computing + brain power + good intel already gave us viruses like Stuxnet. What if that was common place? You can't LET it hit. You can't react once it does.

## Little Data

All that said, and the TLDR version: I want to put an additional firewall inside my PC with machine learning capabilities using my video game card when I'm not. Think "little data" instead of big data, using big data techniques, and achem, algorithms / trained models derived from partially trained detection models ran on little data. Crowdsources. That's all.

### My Current Specs are: 
- 32gb ram
- Ryzen 7 8 Core CPU
- NVIDIA RTX 2070
- 1TB NVMe

### Proposed monstrosity
- Ryzen 7 (Migrating towards a Threadripper, but alas no need yet)
- 64gb of RAM (using 32 already)
- NVIDIA RTX 20/30/40 series
- NVIDIA Quadro card (cheaper end, $100 used or something, log processing for 1 PC's worth of traffic so 1-2.5gbps)
- 2.5Gbps PCI-E Card or new mobo w/ one to save a slot. A consumer hybrid w/ a built in ARM processor would be fine too. If you're capable of designing something like that. Why not, it'd take 2 slots. Maybe dual 2.5Gbps slots w/ port mirroring the bridge/NAT. API calls to respond to threats. Encryption or not, there are still patterns. Defeats the purpose of using the processing power for logs for CPU/Memory though too.
- RAID of SATA SSD's using ZFS / SMB or maybe this new FS from Microsoft?
- Dual 1TB M.2 drives for storage / speed / redundancy / whatever depending on limitations. Only because I have them already.

About a $450 upgrade and it would fill the case. Every slot. An armor kit with all perks for the COD players. 

I was trying to maximize what I could possibly achieve with one PC reasonably before scaling into the $1000/item cards and grid processing power. Again this is for a workstation, for me that could be the equivalent to someone's livingroom or movie room, others (like me) a computer chair or recliner. It's my go-to. It has to be comfortable.

## How does this differ from a designer's workstation? AutoCAD? Etc.

A workstation doesn't dedicate resources to individual components, such as the network card. In a business, and not a home, security like that is centralized and abstracted. Similar to what I'm trying to achieve while adding flexibility of the operating system. It's a use case, although not common yet.

Some notable caveats that I ran into: OnlyKey/YubiKey support within the VM's w/o so many hoops. I caved and said I would just use it in Windows only and assigned the PCI device for that USB controller into the VM within Qubes OS. That's the equivalent of assigning a chunk of your PC as a ration to it's demon's that live within it. Typically one would have servers they could remote into, but alas we have not gone that direction yet in the home. I can see homes with media rooms buying their new "air conditior PC-equivalent" that servers the whole house. After all, even Britney Spears has wall of servers and it's not all that uncommon for California to need media equipment attached to it all for home automation. I would just decentralize mine, if I could get away with it. I know this all sounds farfetched, but it would be almost breathing so to speak compared to what people from East Texas are used to.

So after that long disorienting spill, after a tiring sprint to achieve this, I caved back to good ol Windows 10 and VMWare Workstation Pro. Doing something similar, achievably, but with some new bearable caveats: It's still not good enough or there yet for my pipeline in a workstation powerhouse of data that I want to feed it. ????

On that note. I'm watching the market. I know it would be achievable to start a business for gamer's to make some extra money. Rent that spare PC using that new 2.5Gbps DOCSIS 3.1 connection and network card to compute data. Large dataset in, small dataset out. Could help pay the internet bill if decentralized in a grid? Next evolution to Storj? 
