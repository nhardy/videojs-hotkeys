videojs-hotkeys
========================

A plugin for Video.js that enables keyboard hotkeys when the player has focus.
* Space bar toggles play/pause.
* Right and Left Arrow keys seek the video forwards and back.
* Up and Down Arrow keys increase and decrease the volume.
* M key toggles mute/unmute.
* F key toggles fullscreen off and on. (Does not work in Internet Explorer, it seems to be a limitation where scripts
cannot request fullscreen without a mouse click)
* Double-clicking with the mouse toggles fullscreen off and on.
* Number keys from 0-9 skip to a percentage of the video. 0 is 0% and 9 is 90%.

**Note: clicking any of the control buttons such as Play/Pause, Fullscreen, or Mute, will remove focus on the player
which appears to "break" the hotkeys.  This is for accessibility reasons so that people who do not use or know about
the hotkeys can still properly use the `Tab` key to highlight the control buttons and press `space` to toggle them.**

**To restore focus, just click on the video, or an empty part of the control bar at the bottom of the video player.**

**To override this behaviour, set the flag `alwaysCaptureHotkeys` to `true`.
This will "fix" hotkeys. For accessibility, the `Tab` key may be used in combination with the `Enter`/`Return` key to navigate and activate control buttons.**

![Empty control bar space](http://i.imgur.com/18WMTUw.png)

## Usage
Include the plugin:

### CDN version
You can either load the current release:
```html
<script src="//cdn.sc.gl/videojs-hotkeys/0.2/videojs.hotkeys.min.js"></script>
```
Or always load the latest version:
```html
<script src="//cdn.sc.gl/videojs-hotkeys/latest/videojs.hotkeys.min.js"></script>
```

### Self hosted
```html
<script src="/path/to/videojs.hotkeys.js"></script>
```

### Enable the plugin
Add hotkeys to your Videojs ready function.
```js
videojs('vidId').ready(function() {
  this.hotkeys({
    volumeStep: 0.1,
    seekStep: 5,
    enableMute: true,
    enableFullscreen: true,
    enableNumbers: true,
    alwaysCaptureHotkeys: false
  });
});
```

## Options

- `volumeStep` (decimal): The percentage to increase/decrease the volume level when using the Up and Down Arrow keys (default: `0.1`)
- `seekStep` (integer): The number of seconds to seek forward and backwards when using the Right and Left Arrow keys (default: `5`)
- `enableMute` (boolean): Enables the volume mute to be toggle by pressing the **M** key (default: `true`)
- `enableFullscreen` (boolean): Enables toggling the video fullscreen by pressing the **F** key (default: `true`)
- `enableNumbers` (boolean): Enables seeking the video by pressing the number keys (default `true`)
- `alwaysCaptureHotkeys` (boolean): Forces the capture of hotkeys, even when control elements are focused.
The **Enter**/**Return** key may be used instead to activate the control elements (default: `false`)
- `enableJogStyle` (boolean): Enables seeking the video in a broadcast-style jog by pressing the Up and Down Arrow keys.
`seekStep` will also need to be changed to get a proper broadcast-style jog.
This feature and the changes for seekStep are explained a bit more in [PR #12](https://github.com/ctd1500/videojs-hotkeys/pull/12) (default `false`)
(**Note:** This isn't a feature for everyone, and enabling JogStyle will disable the volume hotkeys)
