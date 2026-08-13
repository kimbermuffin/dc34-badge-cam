# Custom badge firmware

Prebuilt firmware for a DEF CON 34 Baosec-lite badge (Baochip), with the camera turned into a
general-purpose photo booth on top of the stock QR-scanning/light-mixing badge OS.

> [!WARNING]
> Flashing custom firmware onto your badge wipes the shared light-mixing key and puts the badge
> into developer mode. This is a one-way trip - there's no going back to the stock badge
> experience afterward.

## What's different from stock

- **Camera mode** in the badge menu: live black-and-white viewfinder, fire button to capture a
  color photo, left/right to browse stored shots, up to delete one.
- **Color capture** - the sensor's chroma data (previously discarded, only luma was kept) is now
  captured and stored, so photos come out in color instead of grayscale.
- **Photo booth loop** - after a capture, the badge briefly shows the shot, then automatically
  returns to the live viewfinder for the next one, cycling through a 12-slot ring buffer. Once
  full, it shows "FULL" instead of looping.
- **Fast USB pull** - a new `photo pullfast` console command streams an entire photo over serial
  in one shot instead of one round-trip per 640-byte chunk (~2s instead of ~3 minutes per photo).

See the [pull_photo.py](../../pull_photo.py) and [sync_photos.py](../../sync_photos.py) scripts
one level up for the host-side tooling that talks to this firmware over USB-CDC serial.

## Flashing

1. Hold any button on the badge while plugging it into USB. It enumerates as a mass-storage
   device named `BAOCHIP`.
2. Copy all three files here (`loader.uf2`, `xous.uf2`, `swap.uf2`) onto that volume.
3. Eject the volume.
4. Press any button to boot into the new firmware.
