# Ubuntu Specific Stuff	


Boot from install media
interrupt boot by selecting Ubuntu (using up/down arrows), then hit 'e'
On the line ending with '---', replace the word "quiet" with

i915.enable_psr=0 i915.modeset=0 i915.enable_fbc=0

Then hit CTRL-X (which will initiate the boot sequence).


