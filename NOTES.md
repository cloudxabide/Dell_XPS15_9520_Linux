

## Boot Issue
```
Error: ../../grub-core/fs/fshelp.c:257:file `/boot/grub/grubenv not found"
```

After much looking around I was not able to determine how/why grub2 seemed to not be pointing to the correct location (/boot/grub2 - or something).

```
dnf -y reinstall grub2-common
```

## Spotify Client resolution is no bueno
Issue:  HiDPI resolution and the Linux Spotify Client do not play well together.  The "fix" is simple enough though.

Now, the spotify client is an interesting situation.  It seems you pull the bits down and build it yourself.  Whatever, I suppose.  

Curious whether I should just make a shell alias for this.
```
sudo sed -i -e 's/Exec=spotify/Exec=spotify --force-device-scale-factor=1.8/g'  /usr/share/applications/spotify.desktop

sudo find / -name "spotify.desktop" 
/usr/lib64/spotify-client/spotify.desktop
/usr/share/applications/spotify.desktop
/usr/share/spotify-client/spotify.desktop
```

## PowerTop 
Note: this will require some "playing" to get it right.  But, this is a good start.

```
sudo su -
dnf -y install powertop tlp tuned-utils thermald 
systemctl enable powertop --now
powertop --auto-tune
```

## CPU Scaling
I will consider scaling back the CPU - I don't need that much power in Linux... seriously.  
There is much still to review
```
grep CPU_SCALING /etc/tlp.conf 
```

I believe the optimal path is to create a new file in /etc/tlp.d
like...
```
tlp-stat -p | grep scaling_max_freq
echo "CPU_SCALING_MAX_FREQ_ON_AC=2450000
```
which is 1/2 of the "default" value?  4900000  
https://github.com/sharipov-ru/dell-xps-9560/blob/master/config/tlp

## Display Manager
Some folks mentioned falling back to X11.  I tried that, as I enjoyed X11 for decades - but... there were quirky/odd issues and I decided taking my chances with Wayland was the better option.  Wayland seems to have some quirkly issues:  like.. the desktop will hang for a bit intermittently - but, also seems to recover.  :shrug:
