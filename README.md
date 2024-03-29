# Dell XPS15 9520 Linux

At this time/point, this Repo is simply notes, anecdotes, etc.. of installing Linux on a my Dell XPS15.  

My XPS was shipped with a single 1TB NVM with Windows 11 installed.  I firstly booted and configured Windows 11 before I break everything.  
Once the system was running, I installed the 2nd 1TB drive.  (For the record:  rremoving the bottom cover was kind of a pain).

TL;DR:  The Dell XPS 15 9520 (2022) with 4k touch screen seems to run well with Fedora 37.  
Run fine with Ubuntu 22.04, as well.  

Both need some tweaks that are seriously minor, but have significant impacts:

* i915 (run time update for both Ubuntu and Fedora)
* i915 (boot time for Ubuntu)

## Details
### Hardware and OS
Hardware Model: Dell Inc. XPS 15 9520  
Memory: 32.0 GiB  
Processor: 12th Gen Intel® Core™ i9-12900HK × 20  
Graphics: NVIDIA GeForce RTX™ 3050 Ti Laptop GPU / Mesa Intel® Graphics (ADL GT2)  

OS Name: "Ubuntu" (Ubuntu 22.04.3 LTS)    
OS Name: Fedora Linux 37 (Workstation Edition)  

## Software Config
### Video Drivers
Fedora: I used akmod-nvidia from RPMfusion  
Ubuntu: Used the Software & Updates tool, then enabled the 535 driver (not the open one)
