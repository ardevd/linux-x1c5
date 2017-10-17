# Linux on the 5th gen Thinkpad X1 Carbon

## Trackpoint

There are supposedly two different vendors for the Trackpoint on the X1C5. ALPS and Elantech. There seems to be multiple ALPS variants as well. Some users with the Elantech trackpoint experiences issues in Linux where neither the trackpoint nor touchpad will work at all unless the trackpoint is disabled in UEFI/BIOS.

Upon boot you'll see the following errors in dmesg if you are affected by this bug.

```
kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
kernel: psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
kernel: psmouse serio1: issuing reconnect request
```

By applying a patch to the kernel that adds the smbus pnp id of the trackpoint to the Synaptics driver and handling for smbus version 3, the trackpoint should function again. The Elantech patch is verified to work well but the unsupported ALPS variant is still being tested and developed.
