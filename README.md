# Duumb - a Reaper JSFX realtime transfer function analyser

Duumb is an audio transfer function analyser. You simply feed it two signals,
and it will show you the difference between the signals' spectra. The intended
use is to give you some kind of visual feedback on what your PA and the room
are doing to your mix.

## Installation

Available via [ReaPack](https://reapack.com) - simply import the following URL:

```
https://github.com/jahudka/duumb-jsfx/raw/main/index.xml
```

Alternatively, you can download all the files in the `FX` folder and put them
anywhere in the Reaper `Effects` folder.

## Usage

The plugin needs two signals: a _measurement_ signal, which you'd typically
obtain using a measurement mic, and a _reference_ signal, which should be
the mono sum of what you're feeding into your PA, without any room correction
applied. This can usually be done using a matrix on your mixer. The recommended
routing and setup in Reaper is this:

1. Add three tracks: _Analyser_, _Measurement_ and _Reference_.
2. Make _Measurement_ and _Reference_ child tracks of _Analyser_.
3. Pan the _Measurement_ track all the way left and the _Reference_ track
   all the way right.
4. Turn off the Master / Parent send for the _Analyser_ track.
5. Record-enable both _Measurement_ and _Reference_ and enable input monitoring.
6. Select the appropriate audio inputs for _Measurement_ and _Reference_.
7. Add _Duumb_ to the _Analyser_ track.
8. Optionally, add a plugin which can delay the reference signal to the _Reference_
   track; this can be e.g. the _Time Adjustment / Delay_ JSFX provided with Reaper
   by default. Set the delay to a value which compensates the distance between
   the PA and the measurement mic (`delay in ms = distance in meters / 343`).
9. Optionally, add an EQ plugin (e.g. ReaEQ) on the _Reference_ track and set it
   to your preferred _house curve_ (for example, if you like your PA a little
   bottom-heavy, boost the low end).
10. Adjust the measurement mic's gain and / or the _Measurement_ and _Reference_
   track faders to get the two signals to approximately the same level.

### Options

Right now, the only thing you can configure is the range the analyser will show.
Right-click anywhere in the plugin window to bring up a menu where you can change this.
