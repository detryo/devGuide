---
title: "SafeCTRTransfer (MSET)"
permalink: /safectrtransfer-(mset).html
---

If you downgrade to 0.15.20 on a New 3DS PANDA or 2DS PANDA and leave Wireless Communication off, you can re-enable the wireless by removing the battery for several seconds then booting back up.
{: .notice--info}

If you've been using the New 3DS's microSD Management to transfer files to your SD card, this will no longer work on 2.1.0. Ensure you have a microSD card reader available before proceeding.
{: .notice--info}

To use the [magnet](https://en.wikipedia.org/wiki/Magnet_URI_scheme) links on this page, you will need a torrent client like [Deluge](http://dev.deluge-torrent.org/wiki/Download)
{: .notice--info}

**For now, connecting your device to the internet is REQUIRED to continue after the 2.1.0 CTRTransfer.**
{: .notice--warning}

**Disable the parental controls of your device before doing the 2.1.0 CTRTransfer. If you do not know the password, see [this](https://mkey.salthax.org/) site. If you cannot disable parental controls because the linked NNID is for a child under 13, you can instead set all parental control options to "do not restrict".**
{: .notice--warning}

**Performing a CTRTransfer will remove all user-installed tickets (which allow access to games) from your device until the created backup is restored.**
{: .notice--danger}

**Never format a 2DS while on a version <6.0.0 or you will be unable to complete initial setup and will BRICK!**
{: .notice--danger}

**Never update a New 3DS running 2.1.0 (an Old 3DS firmware) or you will BRICK! You MUST restore a NAND backup or CTRTransfer back to standard New 3DS firmware first!**
{: .notice--danger}

{% capture notice %}
**Putting a New 3DS on 2.1.0 in sleep mode is known to cause a BRICK!**    
**This only happens when shutting the lid _while your device is on_; this does not apply to turning your device off.**    
**Your device only enters sleep mode when the lid is closed. It is not on a timer or anything like that.**    
**Once on 2.1.0, you should continue without delay to avoid any possibility of this happening!**    
{% endcapture %}

<div class="notice--danger">{{ notice | markdownify }}</div>

#### Overview of steps

{% capture notice-2 %}

In this section, we will be flashing your device's [CTRNAND](https://www.3dbrew.org/wiki/Flash_Filesystem#CTR_partition) partition to 2.1.0 in order to take advantage of an oversight in 2.1.0 for the purpose of extracting the [OTP](https://www.3dbrew.org/wiki/OTP_Registers) unique to your device. This OTP file is required to install arm9loaderhax, and **cannot** be shared with other consoles.
<br><br>
This is accomplished by [installing a premade CTRTransfer image](https://www.reddit.com/r/3dshacks/comments/4zhe4a/) containing 2.1.0, copying your device specific files (such as `moveable.sed` and `SecureInfo_A`) to it, then fixing the title databases.

{% endcapture %}

<div class="notice--info">{{ notice-2 | markdownify }}</div>

#### What you need

* DS flashcart that works on your device version
* The latest release of [SafeCTRTransfer](https://github.com/d0k3/SafeCTRTransfer/releases/latest)
* The 0.17.6 MSET CIA for your region:
  +    <i class="fa fa-magnet" aria-hidden="true" title="This is a magnet link. Use a torrent client to download the file."></i> - [MSET 0.17.6 - EUR - PANDA / SNAKE](magnet:?xt=urn:btih:55a21347ed391dfb51a0c3a2771e2e2ab2d5668b&dn=mset-0.17.6-eur-panda.cia&tr=udp%3A%2F%2Ftorrent.gresille.org%3A80%2Fannounce&tr=http%3A%2F%2Ftracker1.wasabii.com.tw%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.filetracker.pl%3A8089%2Fannounce&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969%2Fannounce&tr=http%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2F9.rarbg.com%3A2710%2Fannounce&tr=udp%3A%2F%2Ftracker.yoshi210.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.tfile.me%2Fannounce&tr=http%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Fzer0day.ch%3A1337%2Fannounce&tr=http%3A%2F%2Ftracker.baravik.org%3A6970%2Fannounce&tr=http%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=http%3A%2F%2Ftorrent.gresille.org%2Fannounce&tr=http%3A%2F%2Fexplodie.org%3A6969%2Fannounce)    
  +    <i class="fa fa-magnet" aria-hidden="true" title="This is a magnet link. Use a torrent client to download the file."></i> - [MSET 0.17.6 - JPN - PANDA / SNAKE](magnet:?xt=urn:btih:597885912d2ab1de69cb1938470506fa6419d068&dn=mset-0.17.6-jpn-panda.cia&tr=udp%3A%2F%2Ftorrent.gresille.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=http%3A%2F%2Ftorrent.gresille.org%2Fannounce&tr=udp%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.yoshi210.com%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.tfile.me%2Fannounce&tr=udp%3A%2F%2Fzer0day.ch%3A1337%2Fannounce&tr=http%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=udp%3A%2F%2F9.rarbg.com%3A2710%2Fannounce&tr=udp%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.filetracker.pl%3A8089%2Fannounce&tr=http%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=http%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker1.wasabii.com.tw%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.baravik.org%3A6970%2Fannounce&tr=http%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce)     
  +    <i class="fa fa-magnet" aria-hidden="true" title="This is a magnet link. Use a torrent client to download the file."></i> - [MSET 0.17.6 - USA - PANDA / SNAKE](magnet:?xt=urn:btih:ade01f4e1bd8720ada571c6e51e0da1a23a0d5b3&dn=mset-0.17.6-usa-panda.cia&tr=udp%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.yoshi210.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=udp%3A%2F%2Fzer0day.ch%3A1337%2Fannounce&tr=http%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=http%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2F9.rarbg.com%3A2710%2Fannounce&tr=http%3A%2F%2Ftracker.tfile.me%2Fannounce&tr=udp%3A%2F%2Ftorrent.gresille.org%3A80%2Fannounce&tr=udp%3A%2F%2Ftracker.filetracker.pl%3A8089%2Fannounce&tr=http%3A%2F%2Ftracker1.wasabii.com.tw%3A6969%2Fannounce&tr=udp%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=http%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker.baravik.org%3A6970%2Fannounce&tr=http%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=http%3A%2F%2Ftorrent.gresille.org%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce)     
* The 0.15.20 PANDA / SNAKE ctrtransfer image
  +    <i class="fa fa-magnet" aria-hidden="true" title="This is a magnet link. Use a torrent client to download the file."></i> - [ctrtransfer - 0.15.20 - PANDA / SNAKE](magnet:?xt=urn:btih:74861c137162c3db10af9048c04f923e82e0331c&dn=ctrtransfer_CTR-0.15.20-panda_snake.zip&tr=udp%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce&tr=udp%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=udp%3A%2F%2F9.rarbg.com%3A2710%2Fannounce&tr=udp%3A%2F%2Ftracker.tiny-vps.com%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.coppersurfer.tk%3A6969%2Fannounce&tr=udp%3A%2F%2Fzer0day.ch%3A1337%2Fannounce&tr=udp%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=http%3A%2F%2Ftracker.tfile.me%2Fannounce&tr=udp%3A%2F%2Ftracker.leechers-paradise.org%3A6969%2Fannounce&tr=http%3A%2F%2Fexplodie.org%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.yoshi210.com%3A6969%2Fannounce&tr=http%3A%2F%2Ftracker1.wasabii.com.tw%3A6969%2Fannounce&tr=udp%3A%2F%2Ftracker.filetracker.pl%3A8089%2Fannounce&tr=http%3A%2F%2Fp4p.arenabg.com%3A1337%2Fannounce&tr=udp%3A%2F%2Ftorrent.gresille.org%3A80%2Fannounce&tr=http%3A%2F%2Ftracker.baravik.org%3A6970%2Fannounce&tr=http%3A%2F%2Ftracker.opentrackr.org%3A1337%2Fannounce&tr=http%3A%2F%2Ftorrent.gresille.org%2Fannounce&tr=http%3A%2F%2Ftracker.aletorrenty.pl%3A2710%2Fannounce)

#### Instructions

##### Section I - Prep Work

1. Install the 0.17.6 MSET CIA for your region using Dev Menu
1. Power off your device
1. Insert your SD card into your computer
1. Create a folder named `CTRTransfer` on the root of your SD card if it does not already exist
1. Copy the 0.15.20 `.bin` and `.bin.sha` from the CTRTransfer `.zip` to the `/CTRTransfer/` folder on your SD card
1. Copy `SafeCTRTransfer.dat` from the SafeCTRTransfer `.zip` to the root of your SD card
1. Reinsert your SD card into your device
1. Copy `SafeCTRTransfer.nds` from the SafeCTRTransfer `.zip` to your DS flashcart
1. Power on your device

##### Section II - Launch SafeCTRTransfer

1. Start your DS flashcart from your device
1. Boot `SafeCTRTransfer.nds` using your flashcart
1. Select the correct option for your device
  + N3DS PANDA / SNAKE -> "4.x NDG SafeCTRTransfer"
  + O3DS PANDA / SNAKE -> "4.x DG SafeCTRTransfer"
1. Reboot the system, then go to System Settings, then "Other Settings", then "Profile", then "Nintendo DS Profile"
1. If the exploit was successful, you will have booted into SafeCTRTransfer

##### Section III - CTRTransfer

1. Allow the SafeCTRTransfer initialization and safety checks to proceed automatically
  + If you get an error, ensure you have all files in the correct locations and that you have enough free space on your SD card as detailed in [Get Started](get-started)
1. When prompted, input the key combo given to confirm CTRTransfer to 2.1.0
  + This process will take some time
  + This process will automatically create a backup of your device's NAND at `/CTRTransfer/<serialnumber>_nand.bin`
  + If you get a critical error, [follow this troubleshooting guide](troubleshooting#ts_transfer)   
1. Once this process has completed, remove your SD card from your device to reboot
  + The reboot will take about 2 seconds to trigger
  + While on 2.1.0, your device will black screen on boot if your SD card is inserted before the home menu loads
  + Every time your device is rebooted on 2.1.0, you will need to take out your SD card before boot and put it back in after the home menu loads
  + For now, leave your SD card out as you will be copying files to it in the next page
  + This will be fixed once you restore your device in the next page

___

*(Screen distortions or discolorations are normal for some devices while on 2.1.0, they will go away once you restore your backup)*
{: .notice--info}

{% capture notice %}
**Putting a New 3DS on 2.1.0 in sleep mode is known to cause an UNRECOVERABLE brick!**    
**This only happens when shutting the lid _while your device is on_; this does not apply to turning your device off.**    
**Your device only enters sleep mode when the lid is closed. It is not on a timer or anything like that.**    
**Once on 2.1.0, you should continue without delay to avoid any possibility of this happening!**    
{% endcapture %}

<div class="notice--danger">{{ notice | markdownify }}</div>

Continue to [Installing arm9loaderhax](installing-arm9loaderhax)
{: .notice--primary}