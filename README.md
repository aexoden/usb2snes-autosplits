# USB2SNES Autosplits

This package contains splits and autosplits for LiveSplit for use with various SNES/SFC games.

## Game Compatibility

The currently supported games and categories are:

### Final Fantasy II/Final Fantasy IV

* Any% NoCW
* Any% No64
* Any% Glitchless
* All Bosses

Depending on their requirements, other categories may be compatible as well. I have not tested the Japanese version of
Final Fantasy IV, so it may or may not work. Eventually, full support will be added if I ever get around to running
those categories again.

### Final Fantasy V

* Any%
* Any% Glitchless

I have only tested this with the RPGe fan translation. It's entirely possible that the untranslated Japanese game will
also work, but I make no guarantees. Reports of success or failure are welcome. As with FF4, I'm perfectly willing to
add support if needed.

## Usage

The splits in the `splits` directory are standard LiveSplit split files. With the exception of glitchless Final
Fantasy V, all included splits include an accurately timed World Record comparison.

In order to use the autosplits, you will need to install the LiveSplit plugin from
<https://github.com/usb2snes/LiveSplit.USB2SNESSplitter>. You only need to place `LiveSplit.USB2SNESSplitter.dll` within
the `Components` folder of your LiveSplit installation.

In order to actually make use of the plugin, you will need a functional [USB2SNES](http://usb2snes.com/) or
[QUsb2Snes](https://skarsnik.github.io/QUsb2snes/) installation. QUsb2Snes is the superior option unless it doesn't work
for you for some reason. USB2SNES only works with an SD2SNES/FXPAK with appropriate firmware, while QUsb2Snes will
additionally work with various emulators (such as RetroArch, BizHawk or certain versions of Snes9x). Actually setting
this up for each of these options is currently beyond the scope of this README, but if someone wants to write up
instructions, I'm not opposed to adding them.

You will then need to configure your LiveSplit layout to add the `USB2SNES Auto Splitter` component.  Ensure your
device is detected by clicking the `Autodetect` button. Select the appropriate configuration file for your current game.
(Yes, this implies that you will need a separate layout for each game, unless you want to constantly reconfigure
things.)

At this point, you should go through the list of splits, choosing the appropriate option for each split. If you have
splits that match the names in the autosplit configuration exactly, they may be detected automatically. Otherwise, you
can choose from the dropdown. Currently, you must assign something to each of your splits (a plugin restriction).

## General Caveats

If you accidentally split manually, it can sometimes be difficult to undo splits, as they will automatically resplit if
the conditions are still met. (In particular, undoing an end of battle split outside of battle is essentially not
possible. You could, however, wait to be in a random battle to undo it.)

## Game-Specific Notes

### Final Fantasy II/Final Fantasy IV

The timer starts when you press A. As such, you should have the game on the new game screen before launching the splits,
unless you want them to start at completely irrelevant times. If there's enough interest, I can try to find a more
reliable way to detect this, but this has worked fine for me for months. Your mileage may vary.

Most battles have both a Begin and End option, which splits on the black screen at either the start or end of the
battle. The one exception is the grind fight, for two primary reasons:

1. The autosplits have no way of knowing which grind fight you intend to use. Many seeds have multiple potential grind
   fights, and a runner may choose to use any one of them for various reasons (personal preference, avoiding a back
   attack, etc.).
2. While most runners will be on step route and will know exactly where their grind fight options are, some runners may
   not be and could conceivably use the autosplits as a workaround to determine if the current fight is the correct
   fight. While it would be trivial to require any grind fight encounter be fully checked, this adds needless
   complication and combined with the previous reason, it's easier to simply leave this split as a manual split.

Because the plugin does not currently allow for unassigned splits, if you do choose to split at the start of the grind
fight, you should assign it to the `Manual Split` option, which should (in theory) be looking for an impossible
condition. (If you notice it actually triggering at some point, please let me know.) If you split slightly too early,
the grind end split may trigger immediately. In that case, simply undo it at some point before the end of the battle,
and it will pick up the actual end when it happens.

Don't interpret the above to mean that you must use all splits. It's perfectly fine to leave autosplit options unused.
You just must assign each of your splits to some autosplit option.

There are two options for Zeromus Death, depending on if you are playing the game normally or using uptCo. Be sure to
select the correct one. (Again, this implies that you will probably want separate layouts for No64 and NoCW.)

For the character joining splits, these always refer to the first time the character joins the party.

### Final Fantasy V

As with Final Fantasy IV, the timer starts on the press of the A button.

Similarly to Final Fantasy IV, the Exdeath Final Death split has two options, depending on if you are running Any% or
Glitchless.

There is currently no `Manual Split` option for this game, as it doesn't have the same issue of a common split that is
not given a corresponding autosplit option. If needed, one can be added.

## Authors

* Jason Lynch (Aexoden) <jason@calindora.com>

## Bug Reports/Feature Requests

Please report any bugs or make any feature requests at the
[Github project](https://github.com/aexoden/usb2snes-autosplits).