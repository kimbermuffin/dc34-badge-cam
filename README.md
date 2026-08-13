# dc34-badge-cam

Photos captured on a DEF CON 34 Baosec-lite badge's onboard camera, browsable at:

https://ber.kim/dc34-badge-cam/

i really like shitty toy cameras and i have a few
it was just logical to turn a badge with a camera into a functional capture device.

i wanted it to have
- live-preview capture,
- color image support, and
- a ~*ring-buffer photo store*~
- a fast USB pull tool and
- the viewer.

this counts as badge hacking ok

## firmware

The custom firmware itself (the thing that actually makes the badge do this) lives in
[firmware/](firmware/) - prebuilt `.uf2` files you can flash onto your own Baosec-lite badge.
