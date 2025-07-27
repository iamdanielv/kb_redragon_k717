# Redragon K717 (Alcor) - 🚧 Custom QMK firmware

I bought this keyboard from amazon:
[Redragon K717](https://www.amazon.com/Redragon-K717-Programmable-Mechanical-Dampening/dp/B0DL578X3K)

but when I tried to write a custom firmware I wasn't able to get the provided source to work on my keyboard.

[Link to original source](https://github.com/hangshengkeji/qmk_firmware/tree/tri-mode/keyboards/et/k717)

I don't really want or need the wireless functionality, so I stripped out some of the code until I got it working.
The result of that work is here. It works, but no wireless. I've opened the case and unplugged the battery
just in case something I did would cause issues. I don't want an exploding battery on my desk. 🤯

It's a great size, but like all small keyboards, you really need extra layers to make it work.

Similarly to [my GK61](https://github.com/iamdanielv/kb_gk61), I wanted to program it.

## Custom Keyboard Software

Copy the folder structure from `redrgon\k717\` into the qmk repo `keyboard` directory.

## Messy code 🤢

Right now the code is a bit messy with big portions commented out. I hope to get some free time
and clean it up in the future. 
> [!CAUTION]
> **REMINDER**: The battery and wireless code were removed.
> You may want to unplug the battery from the PCB if you plan on using it as-is.

## ⚠️ Disclaimer

> [!CAUTION]
> This is a custom firmware that could break your keyboard. I took out a bunch of code related
> to wireless and battery management, so it might be dangerous to leave the battery plugged in.
> I've opened the case and disconnected the battery just in case.

> [!CAUTION]
> 🛑 **Use at your own risk!** 🛑
> I have tried my best to make sure everything works, but I may miss something.
>
> It works for my keyboard, but there may be revisions in the future that are not compatible. Use at your own risk!

## 🥳Thanks!

Thanks to [@hangshengkeji](https://github.com/hangshengkeji/) for providing most of the original code to get the base working.
It was close, but was missing some key portions.

## ⌨️ New Keymap

I've updated the **default** keymap to work with the current source. It can be used as a starting point for customization.

I created a **new keymap** `iamdanielv` that enables via, function keys, navigation, a num pad and layer for RGB / Keyboard management.

I use `6 layers` for my changes, `keyboard.json` specifies that in the following section:

```json
"dynamic_keymap": {
    "layer_count": 6
}
```

## 🖥️ Compiling

You can now use QMK builder with the following command:

```shell
qmk compile -kb redragon/k717 -km iamdanielv
```

> the `-j 0` uses parallel build to speed it up a bit

qmk should generate a new bin file: `redragon_k717_iamdanielv.bin` in your qmk_firmware folder.

For me it was: `C:\Users\<USER>\qmk_firmware\redragon_k717_iamdanielv.bin`

I've included a version of [my custom firmware](extras/redragon_k717_iamdanielv.bin) that works well for me. There you will also find the [original firmware](extras/k717_via_v16.hex) in case something goes horribly wrong.

- [Original](extras/k717_via_v16.hex)
- [Custom](extras/redragon_k717_iamdanielv.bin) - **Note:** Right now it has VIA enabled, but you can change that by compiling this repo.

## 🌐 Using via

In order to use via, you may have to upload the [json specification](extras/k717_1.json), it can be found under the `extras` folder.

## 🥾 Bootloader and Clearing eeprom

To prevent accidental KB Bootloader triggers, I have it hidden under a layer.

- To reboot and `enter bootloader mode`:
  - hold `Fn`, then triple tap the `q` key
- To `clear eeprom`:
  - hold `Fn`, then triple tap the `z` key
  - OR hold `RAlt`, then hold `RShift`, then triple tap the `z` key

## ⭐ Features

I use a `control layer` to modify the keyboard settings.

To enable the control layer

- Momentary - will be deactivated as soon as you release `Fn`:
  - hold `Fn`
- Toggle:
  - hold `Fn`, then double tap `Right CTL`

While on the Control Layer, you have the following available:

- `Q` - triple tap to `enter bootloader mode`
- `Z` - triple tap to `clear eeprom`

- `LCTL` - Swap Number row for Fn Keys (1 is F1 ... + is F12)
- `N` - Toggle NKRO
- `I` - Change Background Color HUE Down
- `O` - Change Background Color HUE Up
- `K` - Change Background Color SAT Down
- `L` - Change Background Color SAT Up
- `,` - Change Background Color VAL Down - RGB_VAD
- `.` - Change Background Color VAL Up - RGB_VAI
- `;` - RGB_SPD
- `'` - RGB_SPI
- `P` - RGB Matrix solid color
- `[` - RGB_RMOD
- `]` - RGB_RMD
- `\` - RGB_TOG -- this will turn off the colors, but still enable indicators

## 🎉 Conclusion and Next Steps

**That's it!** You now should be able to flash the custom firmware using qmk toolbox.

Let me know if you have any questions. I can be reached at [@IAmDanielV](https://twitter.com/IAmDanielV) or [@iamdanielv.bsky.social](https://bsky.app/profile/iamdanielv.bsky.social).
