# Video.js Guides | Video.js

**URL:** https://videojs.org/guides

## Video.js Guides

These guides cover a range of topics for users of Video.js

## Getting Started

*   [Embed a Video.js Player](/guides/embeds/)
*   [Video.js Setup](/guides/setup/)
*   [Video.js Options Reference](/guides/options/)
*   [FAQs](/guides/faqs/)

## General Usage

*   [Player Workflows](/guides/player-workflows/)
*   [Skins](/guides/skins/)
*   [Layout](/guides/layout/)
*   [Languages](/guides/languages/)
*   [Live Support](/guides/live/)
*   [Troubleshooting](/guides/troubleshooting/)

## Advanced Topics

*   [Debugging](/guides/debugging/)
*   [Video.js Plugins](/guides/plugins/)
*   [Components](/guides/components/)
*   [Event Target](/guides/event-target/)
*   [Modal Dialogs](/guides/modal-dialog/)
*   [Hooks](/guides/hooks/)
*   [Playback Technology ("Tech")](/guides/tech/)
*   [Middleware](/guides/middleware/)
*   [Picture-in-Picture Options](/guides/picture-in-picture/)
*   [Spatial Navigation](/guides/spatial-navigation/)

## Integrations

*   [Angular and Video.js](/guides/angular/)
*   [React and Video.js](/guides/react/)
*   [Vue and Video.js](/guides/vue/)
*   [Webpack and Video.js](/guides/webpack/)

## Tracks

*   [Text Tracks](/guides/text-tracks/)
*   [Audio Tracks](/guides/audio-tracks/)
*   [Video Tracks](/guides/video-tracks/)

## Migration Guides

*   [Video.js 7 to 8 Migration](/guides/videojs-7-to-8/)

---

# Video.js Options Reference | Video.js

**URL:** https://videojs.org/guides/options/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js Options Reference

## Table of Contents

*   [Standard <video> Element Options](#standard-video-element-options)
    *   [autoplay](#autoplay)
        *   [More info on autoplay support and changes:](#more-info-on-autoplay-support-and-changes)
    *   [controlBar.remainingTimeDisplay.displayNegative](#controlbarremainingtimedisplaydisplaynegative)
    *   [controls](#controls)
    *   [height](#height)
    *   [loop](#loop)
    *   [muted](#muted)
    *   [poster](#poster)
    *   [preload](#preload)
        *   ['auto'](#auto)
        *   ['metadata'](#metadata)
        *   ['none'](#none)
    *   [src](#src)
    *   [width](#width)
*   [Video.js-specific Options](#videojs-specific-options)
    *   [aspectRatio](#aspectratio)
    *   [audioOnlyMode](#audioonlymode)
    *   [audioPosterMode](#audiopostermode)
    *   [autoSetup](#autosetup)
    *   [breakpoints](#breakpoints)
    *   [children](#children)
    *   [disablePictureInPicture](#disablepictureinpicture)
    *   [enableDocumentPictureInPicture](#enabledocumentpictureinpicture)
    *   [enableSmoothSeeking](#enablesmoothseeking)
    *   [experimentalSvgIcons](#experimentalsvgicons)
    *   [fluid](#fluid)
    *   [fullscreen](#fullscreen)
        *   [options](#options)
    *   [id](#id)
    *   [inactivityTimeout](#inactivitytimeout)
    *   [language](#language)
    *   [languages](#languages)
    *   [liveui](#liveui)
    *   [liveTracker.trackingThreshold](#livetrackertrackingthreshold)
    *   [liveTracker.liveTolerance](#livetrackerlivetolerance)
    *   [nativeControlsForTouch](#nativecontrolsfortouch)
    *   [normalizeAutoplay](#normalizeautoplay)
    *   [notSupportedMessage](#notsupportedmessage)
    *   [noUITitleAttributes](#nouititleattributes)
    *   [playbackRates](#playbackrates)
    *   [playsinline](#playsinline)
    *   [plugins](#plugins)
    *   [posterImage](#posterimage)
    *   [preferFullWindow](#preferfullwindow)
    *   [responsive](#responsive)
    *   [restoreEl](#restoreel)
    *   [skipButtons](#skipbuttons)
    *   [skipButtons.forward](#skipbuttonsforward)
    *   [skipButtons.backward](#skipbuttonsbackward)
    *   [sources](#sources)
    *   [suppressNotSupportedError](#suppressnotsupportederror)
    *   [techCanOverridePoster](#techcanoverrideposter)
    *   [techOrder](#techorder)
    *   [userActions](#useractions)
    *   [userActions.click](#useractionsclick)
    *   [userActions.doubleClick](#useractionsdoubleclick)
    *   [userActions.hotkeys](#useractionshotkeys)
    *   [userActions.hotkeys.fullscreenKey](#useractionshotkeysfullscreenkey)
    *   [userActions.hotkeys.muteKey](#useractionshotkeysmutekey)
    *   [userActions.hotkeys.playPauseKey](#useractionshotkeysplaypausekey)
    *   [vtt.js](#vttjs)
    *   [Spatial Navigation](#spatial-navigation)
        *   [Properties](#properties)
        *   [Usage](#usage)
*   [Component Options](#component-options)
    *   [children](#children-1)
    *   [${componentName}](#componentname)
*   [Tech Options](#tech-options)
    *   [${techName}](#techname)
    *   [html5](#html5)
        *   [nativeControlsForTouch](#nativecontrolsfortouch-1)
        *   [nativeAudioTracks](#nativeaudiotracks)
        *   [nativeTextTracks](#nativetexttracks)
        *   [nativeVideoTracks](#nativevideotracks)
        *   [preloadTextTracks](#preloadtexttracks)

> **Note:** This document is only a reference for available options. To learn about passing options to Video.js, see [the setup guide](/guides/setup#options).

## [](/guides/options/#standard-video-element-options)Standard `<video>` Element Options

Each of these options is also available as a [standard `<video>` element attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Attributes); so, they can be defined in all three manners [outlined in the setup guide](/guides/setup#options). Typically, defaults are not listed as this is left to browser vendors.

### [](/guides/options/#autoplay)`autoplay`

> Type: `boolean|string` NOTE: At this point, the autoplay attribute and option are NOT a guarantee that your video will autoplay. NOTE2: If there is an attribute on the media element the option will be ignored. NOTE3: You cannot pass a string value in the attribute, you must pass it in the videojs options

Instead of using the `autoplay` attribute you should pass an `autoplay` option to the `videojs` function. The following values are valid:

*   a boolean value of `false`: the same as having no attribute on the video element, won't `autoplay`
*   a boolean value of `true`: the same as having attribute on the video element, will use browsers `autoplay`
*   a string value of `'muted'`: will mute the video element and then manually call `play()` on `loadstart`. This is likely to work.
*   a string value of `'play'`: will call `play()` on `loadstart`, similar to browsers `autoplay`
*   a string value of `'any'`: will call `play()` on `loadstart` and if the promise is rejected it will mute the video element then call `play()`.

To pass the option

```js
var player = videojs('my-video', {
  autoplay: 'muted'
});

// or

player.autoplay('muted');
```

#### [](/guides/options/#more-info-on-autoplay-support-and-changes)More info on autoplay support and changes:

*   See our blog post: [Autoplay Best Practices with Video.js](https://videojs.com/blog/autoplay-best-practices-with-video-js/)

### [](/guides/options/#controlbarremainingtimedisplaydisplaynegative)`controlBar.remainingTimeDisplay.displayNegative`

> Type: `boolean`

By default the remaining time display shows as negative time. To not show the negative sign set `controlBar.remainingTimeDisplay.displayNegative` to `false`.

### [](/guides/options/#controls)`controls`

> Type: `boolean`

Determines whether or not the player has controls that the user can interact with. Without controls the only way to start the video playing is with the `autoplay` attribute or through the Player API.

### [](/guides/options/#height)`height`

> Type: `string|number`

Sets the display height of the video player in pixels.

### [](/guides/options/#loop)`loop`

> Type: `boolean`

Causes the video to start over as soon as it ends.

### [](/guides/options/#muted)`muted`

> Type: `boolean`

Will silence any audio by default.

### [](/guides/options/#poster)`poster`

> Type: `string`

A URL to an image that displays before the video begins playing. This is often a frame of the video or a custom title screen. As soon as the user hits "play" the image will go away.

### [](/guides/options/#preload)`preload`

> Type: `string`

Suggests to the browser whether or not the video data should begin downloading as soon as the `<video>` element is loaded. Supported values are:

#### [](/guides/options/#auto)`'auto'`

Start loading the video immediately (if the browser supports it). Some mobile devices will not preload the video in order to protect their users' bandwidth/data usage. This is why the value is called 'auto' and not something more conclusive like `'true'`.

_This tends to be the most common and recommended value as it allows the browser to choose the best behavior._

#### [](/guides/options/#metadata)`'metadata'`

Load only the meta data of the video, which includes information like the duration and dimensions of the video. Sometimes, the meta data will be loaded by downloading a few frames of video.

#### [](/guides/options/#none)`'none'`

Don't preload any data. The browser will wait until the user hits "play" to begin downloading.

### [](/guides/options/#src)`src`

> Type: `string`

The source URL to a video source to embed.

### [](/guides/options/#width)`width`

> Type: `string|number`

Sets the display width of the video player in pixels.

## [](/guides/options/#videojs-specific-options)Video.js-specific Options

Each option is `undefined` by default unless otherwise specified.

### [](/guides/options/#aspectratio)`aspectRatio`

> Type: `string`

Puts the player in [fluid](/guides/options/#fluid) mode and the value is used when calculating the dynamic size of the player. The value should represent a ratio - two numbers separated by a colon (e.g. `"16:9"` or `"4:3"`).

Alternatively, the classes `vjs-16-9`, `vjs-9-16`, `vjs-4-3` or `vjs-1-1` can be added to the player.

### [](/guides/options/#audioonlymode)`audioOnlyMode`

> Type: `boolean` Default: `false`

If set to true, it asynchronously hides all player components except the control bar, as well as any specific controls that are needed only for video. This option can be set to `true` or `false` by calling `audioOnlyMode([true|false])` at runtime. When used as a setter, it returns a Promise. When used as a getter, it returns a Boolean.

### [](/guides/options/#audiopostermode)`audioPosterMode`

> Type: `boolean` Default: `false`

If set to true, it enables the poster viewer experience by hiding the video element and displaying the poster image persistently. This option can be set to `true` or `false` by calling `audioPosterMode([true|false])` at runtime.

### [](/guides/options/#autosetup)`autoSetup`

> Type: `boolean`

Prevents the player from running the autoSetup for media elements with `data-setup` attribute.

> **Note**: this must be set globally with `videojs.options.autoSetup = false` in the same tick as videojs source is loaded to take effect.

### [](/guides/options/#breakpoints)`breakpoints`

> Type: `Object`

When used with the [`responsive` option](/guides/options/#responsive), sets breakpoints that will configure how class names are toggled on the player to adjust the UI based on the player's dimensions.

By default, the breakpoints are:

| Class Name | Width Range |
| --- | --- |
| `vjs-layout-tiny` | 0-210 |
| `vjs-layout-x-small` | 211-320 |
| `vjs-layout-small` | 321-425 |
| `vjs-layout-medium` | 426-768 |
| `vjs-layout-large` | 769-1440 |
| `vjs-layout-x-large` | 1441-2560 |
| `vjs-layout-huge` | 2561+ |

While the class names cannot be changed, the width ranges can be configured via an object like this:

```js
breakpoints: {
  tiny: 300,
  xsmall: 400,
  small: 500,
  medium: 600,
  large: 700,
  xlarge: 800,
  huge: 900
}
```

*   The _keys_ of the `breakpoints` object are derived from the associated class names by removing the `vjs-layout-` prefix and any `-` characters.
*   The _values_ of the `breakpoints` object define the max width for a range.
*   Not all keys need to be defined. You can easily override a single breakpoint by passing an object with one key/value pair! Customized breakpoints will be merged with default breakpoints when the player is created.

When the player's size changes, the merged breakpoints will be inspected in the size order until a matching breakpoint is found.

That breakpoint's associated class name will be added as a class to the player. The previous breakpoint's class will be removed.

See the file `sandbox/responsive.html.example` for an example of a responsive player using the default breakpoints.

### [](/guides/options/#children)`children`

> Type: `Array|Object`

This option is inherited from the [`Component` base class](/guides/options/#component-options).

### [](/guides/options/#disablepictureinpicture)`disablePictureInPicture`

> Type: `boolean`

If `true`, switching the video element into picture-in-picture is disabled. Default is `false`.

This has no effect on Firefox's proprietary picture-in-picture mode which does not implement the standard picture-in-picture API.

This does not disable the document picture-in-picture mode which allows the player element to put into a PiP window.

### [](/guides/options/#enabledocumentpictureinpicture)`enableDocumentPictureInPicture`

> Type: `boolean`

_Since 8.3.0_

If `true`, the [documentPictureInPicture API](https://developer.chrome.com/docs/web-platform/document-picture-in-picture/) will be used for picture-in-picture, if available. Defaults to `false`, but may default to `true` when the feature has become established.

Supported by [Chrome and Edge from version 116](https://caniuse.com/mdn-api_documentpictureinpicture).

This is a different picture-in-picture mode than has previously been available, where the entire player element is windowed rather than just the video itself. Since there are scenarios where it would be desirable to allow PiP on the player but not PiP on the video alone (such as ads, overlays), the `disablePictureInPicture` option **only** disables the old-style picture-in-picture mode on the video.

### [](/guides/options/#enablesmoothseeking)`enableSmoothSeeking`

> Type: `boolean` Default: `false`

_Since 8.9.0_

If set to `true`, will provide a smoother seeking experience on mobile and desktop devices.

The following will enable the smooth seeking:

```js
videojs('my-player', {
  enableSmoothSeeking: true
});
```

Can also be modified after player creation:

```js
var player = videojs('my-player');

player.options({ enableSmoothSeeking: true });
```

### [](/guides/options/#experimentalsvgicons)`experimentalSvgIcons`

> Type: `boolean`

_Since 8.5.0_

If set to `true`, the icons used throughout the player from [videojs/font](https://github.com/videojs/font) will be replaced by SVGs stored in Video.js. Defaults to `false`, but may default to `true` when the feature has become established.

These SVGs were downloaded from [Font Awesome](https://fontawesome.com/icons) and [Google's Material UI](https://mui.com/material-ui/material-icons/).

You can view all of the icons available by renaming [`sandbox/svg-icons.html.example`](https://github.com/videojs/video.js/blob/main/sandbox/svg-icons.html.example) to `sandbox/svg-icons.html`, building Video.js with `npm run build`, and opening `sandbox/svg-icons.html` in your browser of choice.

Icons are expected to be added to a `Component` inside of the player using the [`setIcon`](/guides/components/#adding-a-component) method when customizing the player.

### [](/guides/options/#fluid)`fluid`

> Type: `boolean`

When `true`, the Video.js player will have a fluid size. In other words, it will scale to fit its container at the video's intrinsic aspect ratio, or at a specified [`aspectRatio`](/guides/options/#aspectRatio).

Also, if the `<video>` element has the `"vjs-fluid"`, this option is automatically set to `true`.

### [](/guides/options/#fullscreen)`fullscreen`

> Type: `Object` Default: `{options: {navigationUI: 'hide'}`

`fullscreen.options` can be set to pass in specific fullscreen options. At some point, it will be augmented with `element` and `handler` for more functionality.

#### [](/guides/options/#options)`options`

> Type: `Object` Default: `{navigationUI: 'hide'}`

See [The Fullscreen API Spec](https://fullscreen.spec.whatwg.org/#dictdef-fullscreenoptions) for more details.

### [](/guides/options/#id)`id`

> Type: `string`

If provided, and the element does not already have an `id`, this value is used as the `id` of the player element.

### [](/guides/options/#inactivitytimeout)`inactivityTimeout`

> Type: `number`

Video.js indicates that the user is interacting with the player by way of the `"vjs-user-active"` and `"vjs-user-inactive"` classes and the `"useractive"` event.

The `inactivityTimeout` determines how many milliseconds of inactivity is required before declaring the user inactive. A value of `0` indicates that there is no `inactivityTimeout` and the user will never be considered inactive.

### [](/guides/options/#language)`language`

> Type: `string`, Default: browser default or `'en'`

A [language code](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) matching one of the available languages in the player. This sets the initial language for a player, but it can always be changed.

Learn more about [languages in Video.js](/guides/languages).

### [](/guides/options/#languages)`languages`

> Type: `Object`

Customize which languages are available in a player. The keys of this object will be [language codes](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) and the values will be objects with English keys and translated values.

Learn more about [languages in Video.js](/guides/languages)

> **Note**: Generally, this option is not needed and it would be better to pass your custom languages to `videojs.addLanguage()`, so they are available in all players!

### [](/guides/options/#liveui)`liveui`

> Type: `boolean` Default: `false`

Allows the player to use the new live ui that includes:

*   A progress bar for seeking within the live window
*   A button that can be clicked to seek to the live edge with a circle indicating if you are at the live edge or not.

Without this option the progress bar will be hidden and in its place will be text that indicates `LIVE` playback. There will be no progress control and you will not be able click the text to seek to the live edge. `liveui` will default to `true` in a future version!

### [](/guides/options/#livetrackertrackingthreshold)`liveTracker.trackingThreshold`

> Type: `number` Default: `20`

An option for the liveTracker component of the player that controls when the liveui should be shown. By default if a stream has less than 20s on the seekBar then we do not show the new liveui even with the liveui option set.

### [](/guides/options/#livetrackerlivetolerance)`liveTracker.liveTolerance`

> Type: `number` Default: `15`

An option for the liveTracker component of the player that controls how far from the seekable end should be considered live playback. By default anything further than 15s from the live seekable edge is considered behind live and everything else is considered live. Any user interaction to seek backwards will ignore this value as a user would expect.

### [](/guides/options/#nativecontrolsfortouch)`nativeControlsForTouch`

> Type: `boolean`

Explicitly set a default value for [the associated tech option](/guides/options/#nativecontrolsfortouch).

### [](/guides/options/#normalizeautoplay)`normalizeAutoplay`

> Type: `boolean`

Specify whether setting `autoplay: true` and `<video autoplay>` should be treated the same as `autoplay: 'play'`, i.e. the `autoplay` attribute should be removed from (or not added to) the video element and `play()` be initiated manually by Video.js rather than the browser.

### [](/guides/options/#notsupportedmessage)`notSupportedMessage`

> Type: `string`

Allows overriding the default message that is displayed when Video.js cannot play back a media source.

### [](/guides/options/#nouititleattributes)`noUITitleAttributes`

> Type: `boolean` Default: `false`

Control whether UI elements have a `title` attribute. A `title` attribute is shown on mouse hover, which can be helpful for usability, but has drawbacks for accessibility. Setting `noUITitleAttributes` to `true` prevents the `title` attribute from being added to UI elements, allowing for more accessible tooltips to be added to controls by a plugin or external framework.

### [](/guides/options/#playbackrates)`playbackRates`

> Type: `Array`

An array of numbers strictly greater than 0, where 1 means regular speed (100%), 0.5 means half-speed (50%), 2 means double-speed (200%), etc. If specified, Video.js displays a control (of class `vjs-playback-rate`) allowing the user to choose playback speed from among the array of choices. The choices are presented in the specified order from bottom to top.

For example:

```js
videojs('my-player', {
  playbackRates: [0.5, 1, 1.5, 2]
});
```

### [](/guides/options/#playsinline)`playsinline`

> Type: `boolean`

_Since 6.1.0_

Indicates to the browser that non-fullscreen playback is preferred when fullscreen playback is the native default, such as in iOS Safari.

For example:

```js
videojs('my-player', {
  playsinline: true
});
```

### [](/guides/options/#plugins)`plugins`

> Type: `Object`

This supports having plugins be initialized automatically with custom options when the player is initialized - rather than requiring you to initialize them manually.

```js
videojs('my-player', {
  plugins: {
    foo: {bar: true},
    boo: {baz: false}
  }
});
```

The above is roughly equivalent to:

```js
var player = videojs('my-player');

player.foo({bar: true});
player.boo({baz: false});
```

Although, since the `plugins` option is an object, the order of initialization is not guaranteed!

See [the plugins guide](/guides/plugins) for more information on Video.js plugins.

### [](/guides/options/#posterimage)`posterImage`

> Type: `boolean`, Defaut: `true`

Setting this to false removes Video.js's poster element.

### [](/guides/options/#preferfullwindow)`preferFullWindow`

> Type: `boolean`, Defaut: `false`

Setting this to `true` will change fullscreen behaviour on devices which do not support the HTML5 fullscreen API but do support fullscreen on the video element, i.e. iPhone. Instead of making the video fullscreen, the player will be stretched to fill the browser window.

### [](/guides/options/#responsive)`responsive`

> Type: `boolean`, Default: `false`

Setting this option to `true` will cause the player to customize itself based on responsive breakpoints (see: [`breakpoints` option](/guides/options/#breakpoints)).

When this option is `false` (the default), responsive breakpoints will be ignored.

> Note this is about the responsiveness of the controls within the player, not responsive sizing of the player itself. For that, see [fluid](/guides/options/#fluid).

### [](/guides/options/#restoreel)`restoreEl`

> Type `boolean` or `Element`, Default: false

If set to `true`, a _copy_ of the placeholder element will be made before the player is initalised. If the player is disposed, the copy is put back into the DOM in the player's place.

If set to an HTML Element, that element would replace the disposed player instead.

### [](/guides/options/#skipbuttons)`skipButtons`

> Type: `Object`

_Since 8.2.0_

### [](/guides/options/#skipbuttonsforward)`skipButtons.forward`

> Type: `number`

_Since 8.2.0_

If specified, Video.js displays a control allowing the user to jump forward in a video by the specified number of seconds.

The following values are valid: **5 | 10 | 30**

```js
videojs('my-player', {
  controlBar: {
    skipButtons: {
      forward: 5
    }
  }
});
```

### [](/guides/options/#skipbuttonsbackward)`skipButtons.backward`

> Type: `number`

_Since 8.2.0_

If specified, Video.js displays a control allowing the user to jump back in a video by the specified number of seconds.

The following values are valid: **5 | 10 | 30**

```js
videojs('my-player', {
  controlBar: {
    skipButtons: {
      backward: 10
    }
  }
});
```

### [](/guides/options/#sources)`sources`

> Type: `Array`

An array of objects that mirror the native `<video>` element's capability to have a series of child `<source>` elements. This should be an array of objects with the `src` and `type` properties. For example:

```js
videojs('my-player', {
  sources: [{
    src: '//path/to/video.mp4',
    type: 'video/mp4'
  }, {
    src: '//path/to/video.webm',
    type: 'video/webm'
  }]
});
```

Using `<source>` elements will have the same effect:

```html
<video ...>
  <source src="//path/to/video.mp4" type="video/mp4">
  <source src="//path/to/video.webm" type="video/webm">
</video>
```

### [](/guides/options/#suppressnotsupportederror)`suppressNotSupportedError`

> Type: `boolean`

If set to true, then the no compatible source error will not be triggered immediately and instead will occur on the first user interaction. This is useful for Google's "mobile friendly" test tool, which can't play video but where you might not want to see an error displayed.

### [](/guides/options/#techcanoverrideposter)`techCanOverridePoster`

> Type: `boolean`

Gives the possibility to techs to override the player's poster and integrate into the player's poster life-cycle. This can be useful when multiple techs are used and each has to set their own poster any time a new source is played.

### [](/guides/options/#techorder)`techOrder`

> Type: `Array`, Default: `['html5']`

Defines the order in which Video.js techs are preferred. By default, this means that the `Html5` tech is preferred. Other registered techs will be added after this tech in the order in which they are registered.

### [](/guides/options/#useractions)`userActions`

> Type: `Object`

### [](/guides/options/#useractionsclick)`userActions.click`

> Type: `boolean|function`

Controls how clicking on the player/tech operates. If set to `false`, clicking is disabled and will no longer cause the player to toggle between paused and playing. If controls are disabled with `controls: false`, this will not call the handler function.

```js
videojs('my-player', {
  userActions: {
    click: false
  }
});
```

If undefined or set to `true`, clicking is enabled and toggles the player between paused and play. To override the default click handling, set `userActions.click` to a function which accepts a `click` event (in this example it will request Full Screen, the same as a `userActions.doubleClick`):

```js
function myClickHandler(event) = {
  // `this` is the player in this context

  if (this.isFullscreen()) {
      this.exitFullscreen();
    } else {
      this.requestFullscreen();
    }
};

videojs('my-player', {
  userActions: {
    click: myClickHandler
  }
});
```

### [](/guides/options/#useractionsdoubleclick)`userActions.doubleClick`

> Type: `boolean|function`

Controls how double-clicking on the player/tech operates. If set to `false`, double-clicking is disabled. If undefined or set to `true`, double-clicking is enabled and toggles fullscreen mode. To override the default double-click handling, set `userActions.doubleClick` to a function which accepts a `dblclick` event:

```js
function myDoubleClickHandler(event) = {
  // `this` is the player in this context

  this.pause();
};

videojs('my-player', {
  userActions: {
    doubleClick: myDoubleClickHandler
  }
});
```

### [](/guides/options/#useractionshotkeys)`userActions.hotkeys`

> Type: `boolean|function|object`

Controls how player-wide hotkeys operate. If set to `false`, or `undefined`, hotkeys are disabled. If set to `true` or an object (to allow definitions of `fullscreenKey` etc. below), hotkeys are enabled as described below. To override the default hotkey handling, set `userActions.hotkeys` to a function which accepts a `keydown` event. If controls are disabled with `controls: false`, this will not call the handler function.

```js
var player = videojs('my-player', {
  userActions: {
    hotkeys: function(event) {
      // `this` is the player in this context

      // `x` key = pause
      if (event.which === 88) {
        this.pause();
      }
      // `y` key = play
      if (event.which === 89) {
        this.play();
      }
    }
  }
});
```

Default hotkey handling is:

| Key | Action | Enabled by |
| :-: | --- | --- |
| `f` | toggle fullscreen | only enabled if a Fullscreen button is present in the Control Bar |
| `m` | toggle mute | always enabled, even if no Control Bar is present |
| `k` | toggle play/pause | always enabled, even if no Control Bar is present |
| `Space` | toggle play/pause | always enabled, even if no Control Bar is present |

Hotkeys require player focus first. Note that the `Space` key activates controls such as buttons and menus if that control has keyboard focus. The other hotkeys work regardless of which control in the player has focus.

### [](/guides/options/#useractionshotkeysfullscreenkey)`userActions.hotkeys.fullscreenKey`

> Type: `function`

Override the fullscreen key definition. If this is set, the function receives the `keydown` event; if the function returns `true`, then the fullscreen toggle action is performed.

```js
var player = videojs('my-player', {
  userActions: {
    hotkeys: {
      muteKey: function(event) {
        // disable mute key
      },
      fullscreenKey: function(event) {
        // override fullscreen to trigger when pressing the v key
        return (event.which === 86);
      }
    }
  }
});
```

### [](/guides/options/#useractionshotkeysmutekey)`userActions.hotkeys.muteKey`

> Type: `function`

Override the mute key definition. If this is set, the function receives the `keydown` event; if the function returns `true`, then the mute toggle action is performed.

### [](/guides/options/#useractionshotkeysplaypausekey)`userActions.hotkeys.playPauseKey`

> Type: `function`

Override the play/pause key definition. If this is set, the function receives the `keydown` event; if the function returns `true`, then the play/pause toggle action is performed.

### [](/guides/options/#vttjs)`vtt.js`

> Type: `string`

Allows overriding the default URL to vtt.js, which may be loaded asynchronously to polyfill support for `WebVTT`.

This option will be used in the "novtt" build of Video.js (i.e. `video.novtt.js`). Otherwise, vtt.js is bundled with Video.js.

### [](/guides/options/#spatial-navigation)Spatial Navigation

`spatialNavigation`

Type: `Object` Default: `{enabled: false, horizontalSeek: false}`

This option configures the Spatial Navigation within the Video.js player, enhancing accessibility and user experience on devices like smart TVs, where navigation through remote control is common.

#### [](/guides/options/#properties)Properties

*   **enabled** Type: `boolean` Default: `false` If set to `true`, enables the Spatial Navigation system in the player, allowing users to navigate through focusable components using the arrow keys on their remote control.
    
*   **horizontalSeek** Type: `boolean` Default: `false` When enabled, this allows users to use the left and right arrow keys for seeking through the video timeline, enhancing the navigation experience.
    

#### [](/guides/options/#usage)Usage

To enable Spatial Navigation with the default settings:

```js
var player = videojs('my-player', {
  spatialNavigation: {
    enabled: true
  }
});
```

To enable Spatial Navigation with horizontal seeking:

```js
var player = videojs('my-player', {
  spatialNavigation: {
    enabled: true,
    horizontalSeek: true
  }
});
```

## [](/guides/options/#component-options)Component Options

The Video.js player is a component. Like all components, you can define what children it includes, what order they appear in, and what options are passed to them.

This is meant to be a quick reference; so, for more detailed information on components in Video.js, check out the [components guide](/guides/components).

### [](/guides/options/#children-1)`children`

> Type: `Array|Object`

If an `Array` - which is the default - this is used to determine which children (by component name) and in which order they are created on a player (or other component):

```js
// The following code creates a player with ONLY bigPlayButton and
// controlBar child components.
videojs('my-player', {
  children: [
    'bigPlayButton',
    'controlBar'
  ]
});
```

The `children` options can also be passed as an `Object`. In this case, it is used to provide `options` for any/all children, including disabling them with `false`:

```js
// This player's ONLY child will be the controlBar. Clearly, this is not the
// ideal method for disabling a grandchild!
videojs('my-player', {
  children: {
    controlBar: {
      fullscreenToggle: false
    }
  }
});
```

### [](/guides/options/#componentname)`${componentName}`

> Type: `Object`

Components can be given custom options via the _lower-camel-case variant of the component name_ (e.g. `controlBar` for `ControlBar`). These can be nested in a representation of grandchild relationships. For example, to disable the fullscreen control:

```js
videojs('my-player', {
  controlBar: {
    fullscreenToggle: false
  }
});
```

## [](/guides/options/#tech-options)Tech Options

### [](/guides/options/#techname)`${techName}`

> Type: `Object`

Video.js playback technologies (i.e. "techs") can be given custom options as part of the options passed to the `videojs` function. They should be passed under the _lower-case variant of the tech name_ (e.g. `"html5"`).

### [](/guides/options/#html5)`html5`

#### [](/guides/options/#nativecontrolsfortouch-1)`nativeControlsForTouch`

> Type: `boolean`

Only supported by the `Html5` tech, this option can be set to `true` to force native controls for touch devices.

#### [](/guides/options/#nativeaudiotracks)`nativeAudioTracks`

> Type: `boolean`

Can be set to `false` to disable native audio track support. Most commonly used with [videojs-contrib-hls](https://github.com/videojs/videojs-contrib-hls).

#### [](/guides/options/#nativetexttracks)`nativeTextTracks`

> Type: `boolean`

Can be set to `false` to force emulation of text tracks instead of native support. The `nativeCaptions` option also exists, but is simply an alias to `nativeTextTracks`.

#### [](/guides/options/#nativevideotracks)`nativeVideoTracks`

> Type: `boolean`

Can be set to `false` to disable native video track support. Most commonly used with [videojs-contrib-hls](https://github.com/videojs/videojs-contrib-hls).

#### [](/guides/options/#preloadtexttracks)`preloadTextTracks`

> Type: `boolean`

Can be set to `false` to delay loading of non-active text tracks until use. This can cause a short delay when switching captions during which there may be missing captions.

The default behavior is to preload all text tracks.

---

# Video.js Setup | Video.js

**URL:** https://videojs.org/guides/setup/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js Setup

## Table of Contents

*   [Getting Video.js](#getting-videojs)
*   [Creating a Player](#creating-a-player)
    *   [Automatic Setup](#automatic-setup)
    *   [Manual Setup](#manual-setup)
    *   [Getting References to Players](#getting-references-to-players)
        *   [Using videojs](#using-videojs)
        *   [Using videojs.getPlayer()](#using-videojsgetplayer)
        *   [Using videojs.getPlayers() or videojs.players](#using-videojsgetplayers-or-videojsplayers)
*   [Options](#options)
    *   [Global Defaults](#global-defaults)
    *   [A Note on <video> Tag Attributes](#a-note-on-video-tag-attributes)
*   [Player Readiness](#player-readiness)
*   [Advanced Player Workflows](#advanced-player-workflows)

## [](/guides/setup/#getting-videojs)Getting Video.js

Video.js is officially available via CDN and npm.

Video.js works out of the box with not only HTML `<script>` and `<link>` tags, but also all major bundlers/packagers/builders, such as Browserify, Node, WebPack, etc.

Please refer to the [Getting Started](/getting-started) document for details.

## [](/guides/setup/#creating-a-player)Creating a Player

> **Note:** Video.js works with `<video>` _and_ `<audio>` elements, but for simplicity we'll refer only to `<video>` elements going forward.

Once you have Video.js [loaded on your page](/getting-started), you're ready to create a player!

The core strength of Video.js is that it decorates a [standard `<video>` element](https://www.w3.org/TR/html5/embedded-content-0.html#the-video-element) and emulates its associated [events and APIs](https://www.w3.org/2010/05/video/mediaevents.html), while providing a customizable DOM-based UI.

Video.js supports all attributes of the `<video>` element (such as `controls`, `preload`, etc), but it also supports [its own options](/guides/setup/#options). There are two ways to create a Video.js player and pass it options, but they both start with a standard `<video>` element with the attribute `class="video-js"`:

```html
<video class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

You can use a `<video-js>` element instead of `<video>`. Using a `<video>` element is undesirable in some circumstances, as the browser may show unstyled controls or try to load a source in the moments before the player initialises, which does not happen with the `<video-js>` custom element.

```html
<video-js>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video-js>
```

For a high-level overview of all the various embed options, check out the [embeds page](/guides/embeds), then follow the rest of this page.

### [](/guides/setup/#automatic-setup)Automatic Setup

By default, when your web page finishes loading, Video.js will scan for media elements that have the `data-setup` attribute. The `data-setup` attribute is used to pass options to Video.js. A minimal example looks like this:

```html
<video class="video-js" data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

> **Note:** You _must_ use single-quotes with `data-setup` as it is expected to contain JSON.

### [](/guides/setup/#manual-setup)Manual Setup

On the modern web, a `<video>` element often does not exist when the page finishes loading. In these cases, automatic setup is not possible, but manual setup is available via [the `videojs` function](https://docs.videojs.com/module-videojs.html).

One way to call this function is by providing it a string matching a `<video>` element's `id` attribute:

```html
<video id="my-player" class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

```js
videojs('my-player');
```

However, using an `id` attribute isn't always practical; so, the `videojs` function accepts a DOM element instead:

```html
<video class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

```js
videojs(document.querySelector('.video-js'));
```

### [](/guides/setup/#getting-references-to-players)Getting References to Players

Once players are created, Video.js keeps track of them internally. There are a few ways to get references to pre-existing players.

#### [](/guides/setup/#using-videojs)Using `videojs`

Calling `videojs()` with the ID of element of an already-existing player will return that player and will not create another one.

If there is no player matching the argument, it will attempt to create one.

#### [](/guides/setup/#using-videojsgetplayer)Using `videojs.getPlayer()`

Sometimes, you want to get a reference to a player without the potential side effects of calling `videojs()`. This can be acheived by calling `videojs.getPlayer()` with either a string matching the element's ID or the element itself.

#### [](/guides/setup/#using-videojsgetplayers-or-videojsplayers)Using `videojs.getPlayers()` or `videojs.players`

The `videojs.players` property exposes all known players. The method, `videojs.getPlayers()` simply returns the same object.

Players are stored on this object with keys matching their IDs.

> **Note:** A player created from an element without an ID will be assigned an automatically-generated ID.

## [](/guides/setup/#options)Options

> **Note:** This guide only covers how to pass options during player setup. For a complete reference on _all_ available options, see the [options guide](/guides/options).

There are three ways to pass options to Video.js. Because Video.js decorates an HTML5 `<video>` element, many of the options available are also available as [standard `<video>` tag attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Attributes):

```html
<video controls autoplay preload="auto" ...>
```

Alternatively, you can use the `data-setup` attribute to pass options as [JSON](https://json.org/example.html). This is also how you would set options that aren't standard to the `<video>` element:

```html
<video data-setup='{"controls": true, "autoplay": false, "preload": "auto"}'...>
```

> **Note:** You _must_ use single-quotes around the value of `data-setup` as it contains a JSON string which must use double quotes.

Finally, if you're not using the `data-setup` attribute to trigger the player setup, you can pass in an object of player options as the second argument to the `videojs` function:

```js
videojs('my-player', {
  controls: true,
  autoplay: false,
  preload: 'auto'
});
```

> **Note:** Do not use both `data-setup` and an options object.

### [](/guides/setup/#global-defaults)Global Defaults

Default options for all players can be found at `videojs.options` and can be changed directly. For example, to set `{autoplay: true}` for all future players:

```js
videojs.options.autoplay = true;
```

### [](/guides/setup/#a-note-on-video-tag-attributes)A Note on `<video>` Tag Attributes

Many attributes are so-called [boolean attributes](https://www.w3.org/TR/2011/WD-html5-20110525/common-microsyntaxes.html#boolean-attributes). This means they are either on or off. In these cases, the attribute _should have no value_ (or should have its name as its value) - its presence implies a true value and its absence implies a false value.

_These are incorrect:_

```html
<video controls="true" ...>
<video loop="true" ...>
<video controls="false" ...>
```

> **Note:** The example with `controls="false"` can be a point of confusion for new developers - it will actually turn controls _on_!

These are correct:

```html
<video controls ...>
<video loop="loop" ...>
<video ...>
```

## [](/guides/setup/#player-readiness)Player Readiness

Because Video.js techs have the potential to be loaded asynchronously, it isn't always safe to interact with a player immediately upon setup. For this reason, Video.js players have a concept of "readiness" which will be familiar to anyone who has used jQuery before.

Essentially, any number of ready callbacks can be defined for a Video.js player. There are three ways to pass these callbacks. In each example, we'll add an identical class to the player:

Pass a callback to the `videojs()` function as a third argument:

```js
// Passing `null` for the options argument.
videojs('my-player', null, function() {
  this.addClass('my-example');
});
```

Pass a callback to a player's `ready()` method:

```js
var player = videojs('my-player');

player.ready(function() {
  this.addClass('my-example');
});
```

Listen for the player's `"ready"` event:

```js
var player = videojs('my-player');

player.on('ready', function() {
  this.addClass('my-example');
});
```

In each case, the callback is called asynchronously.

An important distinction between the above methods is that adding an listener for `ready` with `on()` _must_ be done before the player is ready. With `player.ready()`, the function is called immediately if the player is already ready.

## [](/guides/setup/#advanced-player-workflows)Advanced Player Workflows

For a discussion of more advanced player workflows, see the [player workflows guide](/guides/player-workflows).

---

# Embed a Video.js Player | Video.js

**URL:** https://videojs.org/guides/embeds/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Embed a Video.js Player

## Table of Contents

*   [Embeds](#embeds)
    *   [<video> embed](#video-embed)
    *   [Player div ingest](#player-div-ingest)
    *   [<video-js> embed](#video-js-embed)
        *   [Custom Elements](#custom-elements)
*   [data-setup](#data-setup)

Video.js is meant to be an enhancement to the video element in HTML5 and for years, its embed code has been just a `<video>` element. Video.js then wraps the video element in a div that is used for us to place controls and anything else that's required for the player.

For a long time this was enough. In 2016, "div ingest" was added, and it allows the developer to give Video.js a player div to use instead of making it's own. This is partly to help with content reflow but also to help with iOS where you sometimes need to prime the video element and we re-create the video element when we create the player div. However, this is kind of weird to have a `<video>` element embed with a `<div>` wrapped around it. So, we built out a new embed, a `<video-js>` embed.

Below, the three kinds of embeds are detailed.

## [](/guides/embeds/#embeds)Embeds

### [](/guides/embeds/#video-embed)`<video>` embed

The classic Video.js embed. You can then initialize it via `data-setup` or via the `videojs` method.

```html
<!-- via data-setup -->
<video id="vid1" class="video-js" data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video>

<!-- via code -->
<video id="vid1" class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video>
```

```js
const player = videojs('vid1', {});
```

### [](/guides/embeds/#player-div-ingest)Player div ingest

The enhanced classic embed. You can also initialize it via `data-setup` or via the `videojs` method.

```html
<!-- via data-setup -->
<div data-vjs-player>
  <video id="vid1" class="video-js" data-setup='{}'>
    <source src="//vjs.zencdn.net/v/oceans.mp4">
  </video>
</div>

<!-- via code -->
<div data-vjs-player>
  <video id="vid1" class="video-js">
    <source src="//vjs.zencdn.net/v/oceans.mp4">
  </video>
</div>
```

```js
const player = videojs('vid1', {});
```

As you can see, it isn't much different from the classic `<video>` embed. It also does make it easier to work with [React](/guides/react).

### [](/guides/embeds/#video-js-embed)`<video-js>` embed

This is the [I Can't Believe It's Not Custom Elements](https://developers.google.com/web/fundamentals/web-components/customelements) embed code. It looks very much like the `<video>` embed but instead of `video` it's a `video-js` embed. This is useful for all the things that the player div ingest is useful for and it matches our library name!

```html
<!-- via data-setup -->
<video-js id="vid1" data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video-js>

<!-- via code -->
<video-js id="vid1">
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video-js>
```

```js
const player = videojs('vid1', {});
```

Adding `class="video-js"` with this embed is no longer necessary as it will automatically add the class `video-js` if missing.

#### [](/guides/embeds/#custom-elements)Custom Elements

Native Custom Elements support is relatively small according to [Can I Use](https://caniuse.com/#feat=custom-elementsv1) and because we didn't want to include a polyfill we're going with just an element called `video-js` rather than a full blown custom element.

## [](/guides/embeds/#data-setup)data-setup

This is an ease-of-use method for having Video.js set up the player automatically. It is an HTML attribute and it takes a JSON string representation of the [player options](/guides/options) as the value. Using the programmatic approach is probably preferable.

---

# FAQs | Video.js

**URL:** https://videojs.org/guides/faqs/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# FAQs

## Table of Contents

*   [Q: What is Video.js?](#q-what-is-videojs)
*   [Q: How do I install Video.js?](#q-how-do-i-install-videojs)
*   [Q: Is Video.js on bower?](#q-is-videojs-on-bower)
*   [Q: What do Video.js version numbers mean?](#q-what-do-videojs-version-numbers-mean)
*   [Q: How can I troubleshoot playback issues?](#q-how-can-i-troubleshoot-playback-issues)
*   [Q: A video does not play in a specific browser. Why?](#q-a-video-does-not-play-in-a-specific-browser-why)
*   [Q: Why does the entire video download before playback? Why does the video load for a long time?](#q-why-does-the-entire-video-download-before-playback-why-does-the-video-load-for-a-long-time)
*   [Q: I see an error thrown that mentions vdata12345. What is that?](#q-i-see-an-error-thrown-that-mentions-vdata12345-what-is-that)
*   [Q: I think I found a bug with Video.js or I want to add a feature. What should I do?](#q-i-think-i-found-a-bug-with-videojs-or-i-want-to-add-a-feature-what-should-i-do)
    *   [If you think that you can fix the issue or add the feature](#if-you-think-that-you-can-fix-the-issue-or-add-the-feature)
    *   [If you don't think you can fix the issue or add the feature](#if-you-dont-think-you-can-fix-the-issue-or-add-the-feature)
*   [Q: What is a reduced test case?](#q-what-is-a-reduced-test-case)
*   [Q: What media formats does Video.js support?](#q-what-media-formats-does-videojs-support)
*   [Q: How does Video.js choose which source to use?](#q-how-does-videojs-choose-which-source-to-use)
*   [Q: How do I autoplay a video?](#q-how-do-i-autoplay-a-video)
    *   [Q: How can I autoplay a video on a mobile device?](#q-how-can-i-autoplay-a-video-on-a-mobile-device)
*   [Q: How can I play RTMP video in Video.js?](#q-how-can-i-play-rtmp-video-in-videojs)
*   [Q: How can I hide the links to my video/subtitles/audio/tracks?](#q-how-can-i-hide-the-links-to-my-videosubtitlesaudiotracks)
*   [Q: Can I turn off Video.js logging?](#q-can-i-turn-off-videojs-logging)
*   [Q: What is a plugin?](#q-what-is-a-plugin)
*   [Q: How do I make a plugin for Video.js?](#q-how-do-i-make-a-plugin-for-videojs)
*   [Q: How do I add a button to Video.js?](#q-how-do-i-add-a-button-to-videojs)
*   [Q: Where can I find a list of Video.js plugins?](#q-where-can-i-find-a-list-of-videojs-plugins)
*   [Q: How can I get my plugin listed on the website?](#q-how-can-i-get-my-plugin-listed-on-the-website)
*   [Q: Where can I find a list of Video.js skins?](#q-where-can-i-find-a-list-of-videojs-skins)
*   [Q: Does Video.js work as an audio only player?](#q-does-videojs-work-as-an-audio-only-player)
*   [Q: Does Video.js support audio tracks?](#q-does-videojs-support-audio-tracks)
*   [Q: Does Video.js support video tracks?](#q-does-videojs-support-video-tracks)
*   [Q: Does Video.js support text tracks (captions, subtitles, etc)?](#q-does-videojs-support-text-tracks-captions-subtitles-etc)
*   [Q: Does Video.js support HLS (HTTP Live streaming) video?](#q-does-videojs-support-hls-http-live-streaming-video)
*   [Q: Does Video.js support MPEG DASH video?](#q-does-videojs-support-mpeg-dash-video)
*   [Q: Does Video.js support live video?](#q-does-videojs-support-live-video)
*   [Q: Can Video.js play YouTube videos?](#q-can-videojs-play-youtube-videos)
*   [Q: Can Video.js play Vimeo videos?](#q-can-videojs-play-vimeo-videos)
*   [Q: Does Video.js support DRM video?](#q-does-videojs-support-drm-video)
*   [Q: Does Video.js have any support for advertisement integrations?](#q-does-videojs-have-any-support-for-advertisement-integrations)
*   [Q: Can Video.js be required in node.js?](#q-can-videojs-be-required-in-nodejs)
*   [Q: Does Video.js work with webpack?](#q-does-videojs-work-with-webpack)
*   [Q: Does Video.js work with react?](#q-does-videojs-work-with-react)
*   [Q: Can the big play button be centered?](#q-can-the-big-play-button-be-centered)
*   [Q: Can the big play button be shown when paused?](#q-can-the-big-play-button-be-shown-when-paused)
*   [Q: Why is the picture-in-picture button different in Firefox?](#q-why-is-the-picture-in-picture-button-different-in-firefox)

## [](/guides/faqs/#q-what-is-videojs)Q: What is Video.js?

Video.js is an extendable framework/library around the native video element. It does the following:

*   Offers a plugin API so that different types of video can be handed to the native video element (e.g. [HLS](https://github.com/videojs/http-streaming), HTML5 video, etc).
*   Unifies the native video API across browsers (polyfilling support for features if necessary)
*   Offers an extendable and themable UI
*   Ensures accessibility for keyboard and screen reader users
*   Has a set of core plugins that offer support for additional video formats:
    *   HLS and DASH are supported natively.
    *   [videojs-contrib-dash](https://github.com/videojs/videojs-contrib-dash) can be used for more complete DASH support
*   Supports DRM video via a core plugin:
    *   [videojs-contrib-eme](https://github.com/videojs/videojs-contrib-eme)
*   Is extensible with lots of plugins offering support for all kinds of features. See the [plugin list on videojs.com](https://videojs.com/plugins)

## [](/guides/faqs/#q-how-do-i-install-videojs)Q: How do I install Video.js?

Currently Video.js can be installed using npm, serving a release file from a GitHub tag, or even using a CDN hosted version. For information on doing any of those see the [setup guide](/getting-started/).

## [](/guides/faqs/#q-is-videojs-on-bower)Q: Is Video.js on bower?

Versions prior to Video.js 6 support bower, however, as of Video.js 6, bower is no longer officially supported. Please see [issue #4012](https://github.com/videojs/video.js/issues/4012) for more information.

## [](/guides/faqs/#q-what-do-videojs-version-numbers-mean)Q: What do Video.js version numbers mean?

Video.js follows [semver](https://semver.org/) which means that the API should not change out from under a user unless there is a major version increase.

## [](/guides/faqs/#q-how-can-i-troubleshoot-playback-issues)Q: How can I troubleshoot playback issues?

See the [troubleshooting guide](/guides/troubleshooting). If troubleshooting does not solve your issue, please ask in [Slack](https://videojs.slack.com) or submit an [issue](/guides/faqs/#q-i-think-i-found-a-bug-with-videojs-or-i-want-to-add-a-feature-what-should-i-do).

When seeking help about a playback issue the problem is often specific to the video file used, the way the video is hosted or the browser, so make sure to include all of that information and a [reduced test case](/guides/faqs/#q-what-is-a-reduced-test-case).

## [](/guides/faqs/#q-a-video-does-not-play-in-a-specific-browser-why)Q: A video does not play in a specific browser. Why?

See the [troubleshooting guide](/guides/troubleshooting). If troubleshooting does not solve your issue, please ask in [Slack](https://videojs.slack.com) or submit an [issue](/guides/faqs/#q-i-think-i-found-a-bug-with-videojs-or-i-want-to-add-a-feature-what-should-i-do).

## [](/guides/faqs/#q-why-does-the-entire-video-download-before-playback-why-does-the-video-load-for-a-long-time)Q: Why does the entire video download before playback? Why does the video load for a long time?

See the [troubleshooting guide](/guides/troubleshooting). If troubleshooting does not solve your issue, please ask in [Slack](https://videojs.slack.com) or submit an [issue](/guides/faqs/#q-i-think-i-found-a-bug-with-videojs-or-i-want-to-add-a-feature-what-should-i-do).

## [](/guides/faqs/#q-i-see-an-error-thrown-that-mentions-vdata12345-what-is-that)Q: I see an error thrown that mentions `vdata12345`. What is that?

See the [troubleshooting guide](/guides/troubleshooting). If troubleshooting does not solve your issue, please ask in [Slack](https://videojs.slack.com) or submit an [issue](/guides/faqs/#q-i-think-i-found-a-bug-with-videojs-or-i-want-to-add-a-feature-what-should-i-do).

## [](/guides/faqs/#q-i-think-i-found-a-bug-with-videojs-or-i-want-to-add-a-feature-what-should-i-do)Q: I think I found a bug with Video.js or I want to add a feature. What should I do?

### [](/guides/faqs/#if-you-think-that-you-can-fix-the-issue-or-add-the-feature)If you think that you can fix the issue or add the feature

A pull request would be very welcome in the [Video.js repo](https://github.com/videojs/video.js/pulls). Make sure to follow the [contributing guide](https://github.com/videojs/video.js/blob/main/CONTRIBUTING.md#contributing-code) and the [pull request template](https://github.com/videojs/video.js/blob/main/.github/PULL_REQUEST_TEMPLATE.md).

### [](/guides/faqs/#if-you-dont-think-you-can-fix-the-issue-or-add-the-feature)If you don't think you can fix the issue or add the feature

Open an [issue on the Video.js repo](https://github.com/videojs/video.js/issues). Make sure that you follow the [issue template](https://github.com/videojs/video.js/blob/main/.github/ISSUE_TEMPLATE.md) and the [contributing guide](https://github.com/videojs/video.js/blob/main/CONTRIBUTING.md#filing-issues) so that we can better assist you with your issue.

## [](/guides/faqs/#q-what-is-a-reduced-test-case)Q: What is a reduced test case?

A reduced test case is an example of the problem that you are facing in isolation. Think of it as example page that reproduces the issue in the least amount of possible code.

It's important to add a reduced case. Even if the problem seems obvious it may not be to others. Having a example to refer to also makes the difference between somebody being able to take a look and immediately see what's wrong, and needing to take time to recreate what they think you are describing.

We have a [starter example](https://codepen.io/gkatsev/pen/GwZegv?editors=1000#0) for reduced test cases. To learn more about reduced test cases visit [css-tricks](https://css-tricks.com/reduced-test-cases/)

## [](/guides/faqs/#q-what-media-formats-does-videojs-support)Q: What media formats does Video.js support?

This depends on the formats supported by the browser's HTML5 video element, and the playback techs/plugins made available to Video.js. For more information on media formats see the [troubleshooting guide](/guides/troubleshooting).

## [](/guides/faqs/#q-how-does-videojs-choose-which-source-to-use)Q: How does Video.js choose which source to use?

When an array of sources is available, Video.js test each source in the order given. For each source, each tech in the [`techOrder`](/guides/options#techorder) will be checked to see if it can play it whether directly or via source handler (such as videojs-http-streaming). The first match will be chosen.

## [](/guides/faqs/#q-how-do-i-autoplay-a-video)Q: How do I autoplay a video?

Due to recent changes in autoplay behavior we no longer recommend using the `autoplay` attribute on the `video` element. It's still supported by Video.js but, many browsers, including Chrome, are changing their `autoplay` attribute behavior.

Instead we recommend using the `autoplay` option rather than the `autoplay` attribute, for more information on using that. see the [autoplay option](/guides/options#autoplay) in the Video.js options guide.

For more information on the autoplay changes see our [blog post](https://videojs.com/blog/autoplay-best-practices-with-video-js/).

### [](/guides/faqs/#q-how-can-i-autoplay-a-video-on-a-mobile-device)Q: How can I autoplay a video on a mobile device?

Most mobile devices have blocked autoplaying videos until recently. For mobile devices that don't support autoplaying, autoplay isn't supported by Video.js. For those devices that support autoplaying, like iOS10 and Chrome for Android 53+, you must mute the video or have a video without audio tracks to be able to play it.

We do not recommend doing this manually using attributes on the `video` element. Instead, you should pass the [autoplay option](/guides/options#autoplay) with a value of `'any'` or `'muted'`. See the previous link for more information on using that option.

> NOTE: At this point, the autoplay attribute and option are NOT a guarantee that your video will autoplay.

## [](/guides/faqs/#q-how-can-i-play-rtmp-video-in-videojs)Q: How can I play RTMP video in Video.js?

It is no longer possible to play RTMP as it requires Flash, and [Flash has reached end of life](https://www.adobe.com/products/flashplayer/end-of-life.html). No browser supports it.

## [](/guides/faqs/#q-how-can-i-hide-the-links-to-my-videosubtitlesaudiotracks)Q: How can I hide the links to my video/subtitles/audio/tracks?

It's impossible to hide the network requests a browser makes and difficult to sufficiently obfuscate URLs in the source. Techniques such as token authentication may help but are outside of the scope of Video.js.

For content that must be highly secure [videojs-contrib-eme](https://github.com/videojs/videojs-contrib-eme) adds DRM support.

## [](/guides/faqs/#q-can-i-turn-off-videojs-logging)Q: Can I turn off Video.js logging?

Yes! This can be achieved by adding the following code _after_ including Video.js, but _before_ creating any player(s):

```js
videojs.log.level('off');
```

For more information, including which logging levels are available, check out the [debugging guide](/guides/debugging).

## [](/guides/faqs/#q-what-is-a-plugin)Q: What is a plugin?

A plugin is a group of reusable functionality that can be re-used by others. For instance a plugin could add a button to Video.js that makes the video replay 10 times in a row before it stops playback for good. If such a plugin existed and was published users could include it on their page to share that functionality.

## [](/guides/faqs/#q-how-do-i-make-a-plugin-for-videojs)Q: How do I make a plugin for Video.js?

See the [plugin guide](/guides/plugins) for information on making a plugin for Video.js.

## [](/guides/faqs/#q-how-do-i-add-a-button-to-videojs)Q: How do I add a button to Video.js?

See the [components guide](/guides/components) for an example of adding a button to Video.js.

## [](/guides/faqs/#q-where-can-i-find-a-list-of-videojs-plugins)Q: Where can I find a list of Video.js plugins?

A list of plugins published to npm with the `videojs-plugin` keyword is maintained [on videojs.com](https://videojs.com/plugins).

## [](/guides/faqs/#q-how-can-i-get-my-plugin-listed-on-the-website)Q: How can I get my plugin listed on the website?

Add the 'videojs-plugin' [keyword to your array in package.json](https://docs.npmjs.com/files/package.json#keywords) and publish your package to npm. If you use the [plugin generator](https://github.com/videojs/generator-videojs-plugin) this will be done automatically for you. See the [plugins guide](/guides/plugins) for more information.

## [](/guides/faqs/#q-where-can-i-find-a-list-of-videojs-skins)Q: Where can I find a list of Video.js skins?

See the [Video.js GitHub wiki](https://github.com/videojs/video.js/wiki/Skins).

## [](/guides/faqs/#q-does-videojs-work-as-an-audio-only-player)Q: Does Video.js work as an audio only player?

Yes! It can be used to play audio only files in a `<video>` or `<audio>` tag.

## [](/guides/faqs/#q-does-videojs-support-audio-tracks)Q: Does Video.js support audio tracks?

Yes! See the [audio tracks guide](/guides/audio-tracks) for information on using audio tracks.

## [](/guides/faqs/#q-does-videojs-support-video-tracks)Q: Does Video.js support video tracks?

Alternate video tracks support is in development. See [video tracks guide](/guides/video-tracks) for more information on using video tracks.

## [](/guides/faqs/#q-does-videojs-support-text-tracks-captions-subtitles-etc)Q: Does Video.js support text tracks (captions, subtitles, etc)?

Yes! See the [text tracks guide](/guides/text-tracks) for information on using text tracks.

## [](/guides/faqs/#q-does-videojs-support-hls-http-live-streaming-video)Q: Does Video.js support HLS (HTTP Live streaming) video?

Video.js supports HLS. It will play using native support if the HTML5 element supports HLS (e.g. Safari, iOS, legacy Edge, or Chrome for Android). On other browsers, it will play using our playback engine [videojs-http-streaming](https://github.com/videojs/http-streaming).

Note that for non-native playback of HLS it is essential that the server hosting the video sets [CORS headers](https://enable-cors.org).

## [](/guides/faqs/#q-does-videojs-support-mpeg-dash-video)Q: Does Video.js support MPEG DASH video?

Video.js provides support for some DASH streams with our playback engine [videojs-http-streaming](https://github.com/videojs/http-streaming).

Alternatively, [videojs-contrib-dash](https://github.com/videojs/videojs-contrib-dash) package can be used.

Like HLS, DASH streams require [CORS headers](https://enable-cors.org).

## [](/guides/faqs/#q-does-videojs-support-live-video)Q: Does Video.js support live video?

Yes! Common formats for live are HLS or DASH. In the past RTMP was commonly used for live, but it is no longer possible to play in any browser.

## [](/guides/faqs/#q-can-videojs-play-youtube-videos)Q: Can Video.js play YouTube videos?

There is an official plugin that adds support, [videojs-youtube](https://github.com/videojs/videojs-youtube).

## [](/guides/faqs/#q-can-videojs-play-vimeo-videos)Q: Can Video.js play Vimeo videos?

There is an official plugin that adds support, [videojs-vimeo](https://github.com/videojs/videojs-vimeo).

## [](/guides/faqs/#q-does-videojs-support-drm-video)Q: Does Video.js support DRM video?

There is an official plugin that adds support, [videojs-contrib-eme](https://github.com/videojs/videojs-contrib-eme).

## [](/guides/faqs/#q-does-videojs-have-any-support-for-advertisement-integrations)Q: Does Video.js have any support for advertisement integrations?

There is an official plugin that adds core advertising support, [videojs-contrib-ads](https://github.com/videojs/videojs-contrib-ads). Further plugins build on this which handle the communication with the ad server and display of the ad, for instance [Google's IMA plugin](https://github.com/googleads/videojs-ima).

## [](/guides/faqs/#q-can-videojs-be-required-in-nodejs)Q: Can Video.js be required in node.js?

Yes! Video.js is [published on NPM](https://www.npmjs.com/package/video.js).

## [](/guides/faqs/#q-does-videojs-work-with-webpack)Q: Does Video.js work with webpack?

Yes! See the [Webpack and Video.js configuration guide](/guides/webpack).

## [](/guides/faqs/#q-does-videojs-work-with-react)Q: Does Video.js work with react?

Yes! See [ReactJS integration example](/guides/react).

## [](/guides/faqs/#q-can-the-big-play-button-be-centered)Q: Can the big play button be centered?

The default skin offsets the button to not obscure the poster image, but just add a `vjs-big-play-centered` class to the player to have it centred.

## [](/guides/faqs/#q-can-the-big-play-button-be-shown-when-paused)Q: Can the big play button be shown when paused?

Add a `vjs-show-big-play-button-on-pause` class to the player to display the button when paused.

## [](/guides/faqs/#q-why-is-the-picture-in-picture-button-different-in-firefox)Q: Why is the picture-in-picture button different in Firefox?

Firefox does not support the HTML video Picture-in-Picture (PIP) API, so it is not possible to have a custom button in the Video.js controls. Firefox has its own overlay PIP button, and its [own logic for whether to display it](https://firefox-source-docs.mozilla.org/toolkit/components/pictureinpicture/pictureinpicture/index.html#the-picture-in-picture-toggle).

---

# Skins | Video.js

**URL:** https://videojs.org/guides/skins/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Skins

## Table of Contents

*   [Default Skin](#default-skin)
*   [Additional <style> Elements](#additional-style-elements)
    *   [Disabling Additional <style> Elements](#disabling-additional-style-elements)
        *   [Effect on Player#width() and Player#height()](#effect-on-playerwidth-and-playerheight)
*   [Icons](#icons)
*   [Creating a Skin](#creating-a-skin)
    *   [Add a Custom Class to the Player](#add-a-custom-class-to-the-player)
    *   [Customize Styles](#customize-styles)

## [](/guides/skins/#default-skin)Default Skin

When you include the Video.js CSS file (`video-js.min.css`), the default Video.js skin is applied. That means that customizing the look of a Video.js player is a matter of taking advantage of the cascading aspect of CSS to override styles.

## [](/guides/skins/#additional-style-elements)Additional `<style>` Elements

In addition to the Video.js CSS file, there are some styles generated automatically by JavaScript and included in the `<head>` as `<style>` elements.

*   The `"vjs-styles-defaults"` element sets default dimensions for all Video.js players on the page.
*   A `"vjs-styles-dimensions"` element is created for _each_ player on the page and is used to adjust its size. This styling is handled in this manner to allow you to override it with custom CSS without relying on scripting or `!important` to overcome inline styles.

### [](/guides/skins/#disabling-additional-style-elements)Disabling Additional `<style>` Elements

In some cases, particularly with web applications using frameworks that may manage the `<head>` element (e.g. React, Ember, Angular, etc), these `<style>` elements are not desirable. They can be suppressed by setting `window.VIDEOJS_NO_DYNAMIC_STYLE = true` before including Video.js.

_This disables all CSS-based player sizing. Players will have no `height` or `width` by default!_ Even dimensional attributes, such as `width="600" height="300"` will be _ignored_. When using this global, you will need to set their own dimensions in a way that makes sense for their website or web app.

#### [](/guides/skins/#effect-on-playerwidth-and-playerheight)Effect on `Player#width()` and `Player#height()`

When `VIDEOJS_NO_DYNAMIC_STYLE` is set, `Player#width()` and `Player#height()` will apply any width and height that is set directly to the `<video>` element (or whichever element the current tech uses).

## [](/guides/skins/#icons)Icons

Video.js ships with a number of icons built into the skin via an icon font.

You can view all of the icons available in the default skin by renaming [`sandbox/icons.html.example`](https://github.com/videojs/video.js/blob/main/sandbox/icons.html.example) to `sandbox/icons.html`, building Video.js with `npm run build`, and opening `sandbox/icons.html` in your browser of choice.

If the [`experimentalSvgIcons`](/guides/options/#experimentalSvgIcons) option is enabled on the player, you can use the [`setIcon`](/guides/components/#adding-a-component) method to add icons to a custom `Component`. Follow the steps above using [`sandbox/svg-icons.html.example`](https://github.com/videojs/video.js/blob/main/sandbox/svg-icons.html.example) to view the available icons.

## [](/guides/skins/#creating-a-skin)Creating a Skin

The recommended process for creating a skin is to override the styles provided by the default skin. In this way, you don't need to start from scratch.

### [](/guides/skins/#add-a-custom-class-to-the-player)Add a Custom Class to the Player

The most convenient way to create a hook in the player for your skin is to add a class to it. You can do this by adding a class to the initial `<video>` element:

```html
<video class="vjs-matrix video-js">...</video>
```

Or via JavaScript:

```js
var player = videojs('my-player');

player.addClass('vjs-matrix');
```

> **Note:** The `vjs-` prefix is a convention for all classes that are contained in a Video.js player.

### [](/guides/skins/#customize-styles)Customize Styles

The first step in overriding default styles with custom ones is to determine which selectors and properties need overriding. As an example, let's say we don't like the default color of controls (white) and we want to change them to a bright green (say, `#00ff00`).

To do this, we'll use your browser's developer tools to inspect the player and figure out which selectors we need to use to adjust those styles - and we'll add our custom `.vjs-matrix` selector to ensure our final selectors are specific enough to override the default skin.

In this case, we'll need the following:

```css
/* Change all text and icon colors in the player. */
.vjs-matrix.video-js {
  color: #00ff00;
}

/* Change the border of the big play button. */
.vjs-matrix .vjs-big-play-button {
  border-color: #00ff00;
}

/* Change the color of various "bars". */
.vjs-matrix .vjs-volume-level,
.vjs-matrix .vjs-play-progress,
.vjs-matrix .vjs-slider-bar {
  background: #00ff00;
}
```

Finally, we can save that as a `videojs-matrix.css` file and include it _after_ the Video.js CSS:

```html
<link rel="stylesheet" type="text/css" href="path/to/video-js.min.css">
<link rel="stylesheet" type="text/css" href="path/to/videojs-matrix.css">
```

If you create a skin you're particularly proud of, you can share it by adding a link on the [Skins wiki page](https://github.com/videojs/video.js/wiki/Skins). One way to create shareable skins is by forking [this example on CodePen](https://codepen.io/heff/pen/EarCt).

---

# Player Workflows | Video.js

**URL:** https://videojs.org/guides/player-workflows/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Player Workflows

## Table of Contents

*   [Accessing a player that has already been created on a page](#accessing-a-player-that-has-already-been-created-on-a-page)
*   [Removing Players](#removing-players)
    *   [dispose()](#dispose)
    *   [Checking if a Player is Disposed](#checking-if-a-player-is-disposed)
    *   [Signs of an Undisposed Player](#signs-of-an-undisposed-player)
*   [Showing and Hiding a Player](#showing-and-hiding-a-player)
*   [Changing the volume of a player](#changing-the-volume-of-a-player)
*   [Making the player fullscreen](#making-the-player-fullscreen)
*   [Using Playback information functions](#using-playback-information-functions)
*   [Dealing with the source or the poster on the player](#dealing-with-the-source-or-the-poster-on-the-player)
*   [Accessing the Tech on the player](#accessing-the-tech-on-the-player)
*   [Using Video.js with...](#using-videojs-with)
    *   [jQuery](#jquery)
    *   [React](#react)
    *   [Ember](#ember)
    *   [Angular](#angular)
    *   [Vue](#vue)

This document outlines many considerations for using Video.js for advanced player workflows. Be sure to read [the setup guide](/guides/setup) first!

## [](/guides/player-workflows/#accessing-a-player-that-has-already-been-created-on-a-page)Accessing a player that has already been created on a page

After an instance has been created it can be accessed globally in two ways:

1.  By calling `videojs('example_video_id');`
2.  By using it directly via `videojs.players.example_video_id;`

## [](/guides/player-workflows/#removing-players)Removing Players

No matter the term used for it, web applications are becoming common. Not everything is a static, load-once-and-done web page anymore! This means that developers need to be able to manage the full lifecycle of a video player - from creation to destruction. Video.js supports player removal through the `dispose()` method.

### [](/guides/player-workflows/#dispose)[`dispose()`](https://docs.videojs.com/Player.html#dispose)

This method is available on all Video.js players and [components](https://docs.videojs.com/Component.html#dispose). It is _the only_ supported method of removing a Video.js player from both the DOM and memory. For example, the following code sets up a player and then disposes it when media playback is complete:

```js
var player = videojs('my-player');

player.on('ended', function() {
  this.dispose();
});
```

Calling `dispose()` will have a few effects:

1.  Trigger a `"dispose"` event on the player, allowing for any custom cleanup tasks that need to be run by your integration.
2.  Remove all event listeners from the player.
3.  Remove the player's DOM element(s).
4.  If the [`restoreEl`](/guides/options#restoreel) option was used, then the player's DOM elements are replaced with the stored element, a copy of the original placeholder element if it were set to `true`.

Additionally, these actions are recursively applied to _all_ the player's child components.

> **Note**: Do _not_ remove players via standard DOM removal methods: this will leave listeners and other objects in memory that you might not be able to clean up!

### [](/guides/player-workflows/#checking-if-a-player-is-disposed)Checking if a Player is Disposed

At times, it is useful to know whether or not a player reference in your code is stale. The `isDisposed()` method is available on all components (including players) for this purpose.

### [](/guides/player-workflows/#signs-of-an-undisposed-player)Signs of an Undisposed Player

Seeing an error such as:

```text
TypeError: this.el_.vjs_getProperty is not a function
```

or

```text
TypeError: Cannot read property 'vdata1234567890' of null
```

Suggests that a player or component was removed from the DOM without using `dispose()`. It usually means something tried to trigger an event on it or call a method on it.

## [](/guides/player-workflows/#showing-and-hiding-a-player)Showing and Hiding a Player

It is not recommended that you attempt to toggle the visibility or display of a Video.js player. Instead, players should be created and [disposed](/guides/player-workflows/#removing-players) as needed.

This is relevant to use cases such as displaying a player in a modal/overlay. Rather than keeping a hidden Video.js player in a DOM element, it's recommended that you create the player when the modal opens and dispose it when the modal closes.

This is particularly relevant where memory/resource usage is concerned (e.g. mobile devices).

Depending on the libraries/frameworks in use, an implementation might look something like this:

```js
modal.on('show', function() {
  var videoEl = modal.findEl('video');
  modal.player = videojs(videoEl);
});

modal.on('hide', function() {
  modal.player.dispose();
});
```

## [](/guides/player-workflows/#changing-the-volume-of-a-player)Changing the volume of a player

Volume for a player can be changed through the `volume` function on a player. The volume function accepts a number from 0-1. Calling it without an argument will return the current volume.

Example

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // get
  var howLoudIsIt = myPlayer.volume();
  // set
  myPlayer.volume(0.5); // Set volume to half
});
```

Volume can also be muted (without actually changing the volume value) using the `muted` function. Calling it without an argument will return the current status of muted on the player.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // get, should be false
  console.log(myPlayer.muted());
  // set to true
  myPlayer.muted(true);
  // get should be true
  console.log(myPlayer.muted());
});
```

## [](/guides/player-workflows/#making-the-player-fullscreen)Making the player fullscreen

To check if the player is currently fullscreen call the `isFullscreen` function on a player like so.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // get, should be false
  console.log(myPlayer.isFullscreen());

  // set, tell the player it's in fullscreen
  myPlayer.isFullscreen(true);

  // get, should be true
  console.log(myPlayer.isFullscreen());
});
```

To request that the player enter fullscreen call `requestFullscreen`.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.requestFullscreen();
});
```

To exit fullscreen call `exitFullscreen`

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.requestFullscreen();
  myPlayer.exitFullscreen();
});
```

## [](/guides/player-workflows/#using-playback-information-functions)Using Playback information functions

`play` can be used to start playback on a player that has a source.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.play();
});
```

`pause` can be used to pause playback on a player that is playing.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.play();
  myPlayer.pause();
});
```

`paused` can be used to determine if a player is currently paused.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});

myPlayer.ready(function() {
  // true
  console.log(myPlayer.paused());
  // false
  console.log(!myPlayer.paused());

  myPlayer.play();
  // false
  console.log(myPlayer.paused());
  // true
  console.log(!myPlayer.paused());

  myPlayer.pause();
  // true
  console.log(myPlayer.paused());
  // false
  console.log(!myPlayer.paused());
});
```

`currentTime` will give you the currentTime (in seconds) that playback is currently occuring at.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // set current time to 2 minutes into the video
  myPlayer.currentTime(120);

  // get the current time, should be 120 seconds
  var whereYouAt = myPlayer.currentTime();
});
```

`duration` will give you the total duration of the video that is playing

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  var lengthOfVideo = myPlayer.duration();
});
```

`remainingTime` will give you the seconds that are remaing in the video.

```js
var myPlayer = videojs('some-player-id');
myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
   myPlayer.currentTime(10);

   // should be 10 seconds less than duration
   console.log(myPlayer.remainingTime());
});
```

`buffered` will give you a timeRange object representing the current ranges of time that are ready to be played at a future time.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  var bufferedTimeRange = myPlayer.buffered();

  // number of different ranges of time have been buffered.
  // Usually 1
  var numberOfRanges = bufferedTimeRange.length,

  // Time in seconds when the first range starts.
  // Usually 0
  var firstRangeStart = bufferedTimeRange.start(0),

  // Time in seconds when the first range ends
  var firstRangeEnd = bufferedTimeRange.end(0),

  // Length in seconds of the first time range
  var firstRangeLength = firstRangeEnd - firstRangeStart;
});
```

`bufferedPercent` will give you the the current percentage of the video that is buffered.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // example 0.11 aka 11%
  var howMuchIsDownloaded = myPlayer.bufferedPercent();
});
```

## [](/guides/player-workflows/#dealing-with-the-source-or-the-poster-on-the-player)Dealing with the source or the poster on the player

Passing a source to the player via the API. (this can also be done using options)

```js
var myPlayer = videojs('some-player-id');

myPlayer.src('http://www.example.com/path/to/video.mp4');
```

When a string is provided as the source, Video.js will try to infer the video type from the file extension, but this inference will not work in all cases. It is recommended that the source is provided as an object including the type, as below.

**Source Object (or element):** A javascript object containing information about the source file. Use this method if you want the player to determine if it can support the file using the type information.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
```

**Array of Source Objects:** To provide multiple versions of the source so that it can be played using HTML5 across browsers you can use an array of source objects. Video.js will detect which version is supported and load that file.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src([
  {type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'},
  {type: 'video/webm', src: 'http://www.example.com/path/to/video.webm'},
  {type: 'video/ogg', src: 'http://www.example.com/path/to/video.ogv'}
]);
```

Changing or setting the poster via the API. (this can also be done with options)

```js
var myPlayer = videojs('example_video_1');

// set
myPlayer.poster('http://example.com/myImage.jpg');

// get
console.log(myPlayer.poster());
// 'http://example.com/myImage.jpg'
```

## [](/guides/player-workflows/#accessing-the-tech-on-the-player)Accessing the Tech on the player

The tech on the player can be accessed via `tech()`. Passing any argument will silence the warning that is logged.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
   // tech() will log warning without any argument
   var tech = myPlayer.tech(false);
});
```

## [](/guides/player-workflows/#using-videojs-with)Using Video.js with...

### [](/guides/player-workflows/#jquery)jQuery

### [](/guides/player-workflows/#react)React

See [ReactJS integration example](/guides/react)

### [](/guides/player-workflows/#ember)Ember

### [](/guides/player-workflows/#angular)Angular

See [Angular integration example](/docs/guides/angular.md)

### [](/guides/player-workflows/#vue)Vue

See [Vue integration example](/guides/vue)

---

# Layout | Video.js

**URL:** https://videojs.org/guides/layout/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Layout

## Table of Contents

*   [Fluid Mode](#fluid-mode)
    *   [Classes](#classes)
    *   [Enabling Fluid Mode](#enabling-fluid-mode)
    *   [Setting Aspect Ratio](#setting-aspect-ratio)
    *   [Disabling Fluid Mode](#disabling-fluid-mode)
*   [Fill Mode](#fill-mode)
    *   [Class](#class)
    *   [Enabling Fill Mode](#enabling-fill-mode)
    *   [Disabling Fill Mode](#disabling-fill-mode)
*   [Responsive Mode](#responsive-mode)
    *   [Class](#class-1)
    *   [Enabling Responsive Mode](#enabling-responsive-mode)
    *   [Disabling Responsive Mode](#disabling-responsive-mode)
    *   [Customizing Breakpoints](#customizing-breakpoints)
    *   [Restoring Default Breakpoints](#restoring-default-breakpoints)

Video.js generally lays out the player to the dimensions that are set as attributes or via CSS, like other DOM elements. However, we provide a few ways to make the player be more fluid.

## [](/guides/layout/#fluid-mode)Fluid Mode

Video.js has a fluid mode that keeps the player sized to a particular aspect ratio.

By default, fluid mode will use the intrinsic size of the video once loaded but you can change it with classes or with the `aspectRatio` option.

Enabling fluid mode will disable fill mode. If both are enabled, fluid mode takes precedence.

You can enable fluid in a few ways:

*   Add `vjs-fluid`, `vjs-16-9`, or `vjs-4-3` as a class to the player element.
*   pass `fluid` option to the player.
*   call `player.fluid(true)`.
*   pass `aspectRatio` option to the player.
*   call `player.aspectRatio('16:9')`.

### [](/guides/layout/#classes)Classes

There are five classes associated with fluid mode, `vjs-fluid`, `vjs-16-9`, `vjs-4-3`, `vjs-9-16` and `vjs-1-1`.

`vjs-fluid` turns on the general fluid mode which will wait for the video to load to calculate the aspect ratio of the video.

Alternatively, because 16:9, 4:3, 9:16 and 1:1 aspect ratios are so common, we provided them as classes by default for you to use if you know that your videos are 16:9 or , 4:3, 9:16 or 1:1.

### [](/guides/layout/#enabling-fluid-mode)Enabling Fluid Mode

You can pass in the `fluid` option to the player or call `player.fluid(true)`. This will enable the generic fluid mode.

```js
var player = videojs('vid1', {
  fluid: true
});
```

```js
var player = videojs('vid2');

player.fluid(true);
```

### [](/guides/layout/#setting-aspect-ratio)Setting Aspect Ratio

You can specify an aspect ratio for us to use if you don't want to use the intrinsic values from the video element or if you have a specific ratio in mind. It works as either a method call or an option to the player.

This option is in the form of two integers separated by a colon like so `16:9` or `4:3`.

```js
// make a vertical video
var player = videojs('vid1', {
  aspectRatio: '9:16'
});
```

```js
var player = videojs('vid2');

// make a square video
player.aspectRatio('1:1');
```

### [](/guides/layout/#disabling-fluid-mode)Disabling Fluid Mode

You can disable fluid mode by remove the associated classes or by calling passing in `false` to the method.

```js
player.fluid(false);
```

## [](/guides/layout/#fill-mode)Fill Mode

Fill mode will make the player fit and fill out its container. This is often useful if you have a responsive website and already have a container for Video.js that resizes properly to your design. It can be set either via a class or an option.

If fill is enabled, it'll turn off fluid mode. If the player is configured with both fluid and fill options, fluid mode takes precedence.

### [](/guides/layout/#class)Class

There's just one class for this one: `vjs-fill`. When available, Video.js will enter fill mode.

### [](/guides/layout/#enabling-fill-mode)Enabling Fill Mode

You can pass in the `fill` option to the player or call `player.fill(true)`. This will enable fill mode.

```js
var player = videojs('vid1', {
  fill: true
});
```

```js
var player = videojs('vid2');

player.fill(true);
```

### [](/guides/layout/#disabling-fill-mode)Disabling Fill Mode

You can disable fill mode by removing the associated class or by passing `false` in to the method.

```js
player.fill(false);
```

## [](/guides/layout/#responsive-mode)Responsive Mode

Responsive mode will make the player's UI customize itself based on the size of the player. This is useful if you have embeds of varying sizes - or if you want a fluid/fill player to adjust its UI based on its size.

Responsive mode is independent of fluid mode or fill mode - it only deals with the arrangements of the UI within the player, not with the size of the player. However, it is often useful to use responsive mode in conjunction with either fluid mode or fill mode!

### [](/guides/layout/#class-1)Class

A player in responsive mode will add and remove classes based on its size breakpoints. The default breakpoints, classes, and sizes are outlined below:

| Name | Class | Min. Width | Max. Width |
| --- | --- | --- | --- |
| `tiny` | `vjs-layout-tiny` | 0 | 210 |
| `xsmall` | `vjs-layout-x-small` | 211 | 320 |
| `small` | `vjs-layout-small` | 321 | 425 |
| `medium` | `vjs-layout-medium` | 426 | 768 |
| `large` | `vjs-layout-large` | 769 | 1440 |
| `xlarge` | `vjs-layout-x-large` | 1441 | 2560 |
| `huge` | `vjs-layout-huge` | 2561 | Infinity |

### [](/guides/layout/#enabling-responsive-mode)Enabling Responsive Mode

You can enable responsive mode by passing the `responsive` option or by calling `player.responsive(true)`.

```js
var player = videojs('vid1', {
  responsive: true
});
```

```js
var player = videojs('vid2');

player.responsive(true);
```

### [](/guides/layout/#disabling-responsive-mode)Disabling Responsive Mode

You can disable responsive mode by passing `false` to the method.

```js
player.responsive(false);
```

### [](/guides/layout/#customizing-breakpoints)Customizing Breakpoints

The default breakpoints can be customized by passing the `breakpoints` option or by calling `player.breakpoints({...})`.

```js
var player = videojs('vid1', {
  breakpoints: {
    medium: 500
  }
});
```

```js
var player = videojs('vid2');

player.breakpoints({
  medium: 500
});
```

The breakpoints object should have keys matching the **Name** from the table above and values matching the **Max. Width** from the table above. The **Min. Width** is calculated by adding one to the previous breakpoint's **Max. Width**.

Anytime breakpoints are customized, previous customizations are discarded.

### [](/guides/layout/#restoring-default-breakpoints)Restoring Default Breakpoints

The default breakpoints can be restored by calling `player.breakpoints(true)`.

```js
var player = videojs('vid1');

player.breakpoints(true);
```

This is only useful if breakpoints had previously been customized.

---

# Languages | Video.js

**URL:** https://videojs.org/guides/languages/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Languages

## Table of Contents

*   [Using Video.js Languages](#using-videojs-languages)
*   [Contributing to Video.js Translations](#contributing-to-videojs-translations)
    *   [JSON Format](#json-format)
    *   [File Naming](#file-naming)
    *   [Updating an Existing Translation](#updating-an-existing-translation)
    *   [Writing a New Translation](#writing-a-new-translation)
    *   [Adding Languages via the API](#adding-languages-via-the-api)
    *   [Per-Player Translations](#per-player-translations)
    *   [Setting Player Language](#setting-player-language)
    *   [Determining Player Language](#determining-player-language)
        *   [Internal Language Selection](#internal-language-selection)
*   [References](#references)

Video.js includes localization support to present text in a language other than the default English where appropriate.

For an up-to-date list of the languages Video.js supports, see the [languages folder (`lang`)](/lang). Some translations may be less complete than others - see the [translations needed doc](https://github.com/videojs/video.js/blob/main/docs/translations-needed.md) for a table of strings that are missing from the translations available. Contributions are welcome to update those that are incomplete.

## [](/guides/languages/#using-videojs-languages)Using Video.js Languages

Video.js ships with multiple translations (in `dist/lang/`) in JavaScript files. Add the lang script for each language you need to support. Each of these files can be included in a web page to provide support for that language in _all_ Video.js players:

```html
<script src="//example.com/path/to/video.min.js"></script>
<script src="//example.com/path/to/lang/es.js"></script>
```

## [](/guides/languages/#contributing-to-videojs-translations)Contributing to Video.js Translations

We welcome new translations and improvements to existing ones! Please see the [contributing document](https://github.com/videojs/video.js/blob/main/CONTRIBUTING.md) to get started contributing to Video.js and continue reading for specifics on how to contribute to translations of Video.js.

### [](/guides/languages/#json-format)JSON Format

Video.js uses a JSON object to describe a language, where the keys are English and the values are the target language. For example, a Spanish translation might look like this:

```json
{
  "Play": "Reproducción",
  "Pause": "Pausa",
  "Current Time": "Tiempo reproducido",
  "Duration": "Duración total",
  "Remaining Time": "Tiempo restante",
}
```

### [](/guides/languages/#file-naming)File Naming

Translations are found in the `lang/` directory.

Each file's name should be the [standard language code](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) that is most appropriate, with a `.json` extension. For example, "es.json" for Spanish or "zh-CN.json" for simplified Chinese.

### [](/guides/languages/#updating-an-existing-translation)Updating an Existing Translation

If there is a [missing translation](https://github.com/videojs/video.js/blob/main/docs/translations-needed.md), mistake, or room for improvement in an existing translation, don't hesitate to open a pull request!

1.  Edit the relevant JSON file and make the necessary changes.
2.  Verify the language compiles by running the language specific build `npm run build:lang` or the full build `npm run build`.
3.  Verify the translation appears properly in the player UI.
4.  Run `npm run docs:lang` to update the [missing translation document](https://github.com/videojs/video.js/blob/main/docs/translations-needed.md).
5.  Commit and open a pull request on GitHub.

### [](/guides/languages/#writing-a-new-translation)Writing a New Translation

The process for writing an entirely new translation is virtually identical to the process for [updating an existing translation](/guides/languages/#updating-an-existing-translation) except that the new translation JSON file needs to be created.

The template for new language files is the English file ([lang/en.json](/lang/en.json)). This file is always up-to-date with strings that need translations.

The first step to writing a new translation is to copy the English file:

```shell-session
cp lang/en.json lang/${NEW_LANG_CODE}.json
```

Otherwise, the process is the same as [updating an existing translation](/guides/languages/#updating-an-existing-translation).

### [](/guides/languages/#adding-languages-via-the-api)Adding Languages via the API

In addition to the stand-alone scripts provided by Video.js, the API supports manual definition of new languages via the `addLanguage` method. It takes two arguments: the [standard language code](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) and a [language definition object](/guides/languages/#json-format).

```js
videojs.addLanguage('es', {
  Play: 'Reproducción',
  Pause: 'Pausa',
  'Current Time': 'Tiempo reproducido',
  'Duration': 'Duración total',
  'Remaining Time': 'Tiempo restante',
  ...
});
```

`addLanguage()` will overwrite existing translations if the object includes strings previously translated. However text that has already been localised will not be updated after generation.

### [](/guides/languages/#per-player-translations)Per-Player Translations

In addition to providing languages to Video.js itself, individual `Player` instances can be provided custom language support via [the `languages` option](/guides/options#languages):

```js
// Provide a custom definition of Spanish to this player.
videojs('my-player', {
  languages: {
    es: {
      Play: 'Reproducir'
    }
  }
});
```

### [](/guides/languages/#setting-player-language)Setting Player Language

The language used by a player instance may be set via [the `language` option](/guides/options#language):

```js
// Set the language to Spanish for this player.
videojs('my-player', {
  language: 'es'
});
```

The `language` method of the player _can_ be used to set the language after instantiation with `language('es')`. However, this is generally not useful as it does not update text that is already in place.

### [](/guides/languages/#determining-player-language)Determining Player Language

The player language is set to one of the following in descending priority:

*   The language [specified in options](/guides/languages/#setting-default-player-language)
*   The language specified by a `lang` attribute on the player element.
*   The language specified by the closest parent element with a `lang` attribute, up to and including the `<html>` element.
*   The browser language preference; the first language if more than one is configured
*   English

#### [](/guides/languages/#internal-language-selection)Internal Language Selection

*   Language codes are considered case-insensitively (e.g. `en-US` == `en-us`).
*   If there is no match for a language code with a subcode (e.g. `en-us`), a match for the primary code (e.g. `en`) is used if available.

## [](/guides/languages/#references)References

For information on translation/localization in plugins, see [the plugins guide](/guides/plugins).

Standard languages codes [are defined by the IANA](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry).

For all existing/supported languages, please see the [languages folder (`lang/`)](/lang) folder located in the project root.

---

# Live Support | Video.js

**URL:** https://videojs.org/guides/live/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Live Support

## Table of Contents

*   [The default live user interface](#the-default-live-user-interface)
*   [The new user interface](#the-new-user-interface)
*   [LiveTracker](#livetracker)
    *   [The seekableendchange event](#the-seekableendchange-event)
    *   [The liveedgechange event](#the-liveedgechange-event)
    *   [startTracking() and stopTracking()](#starttracking-and-stoptracking)
    *   [seekableEnd()](#seekableend)
    *   [seekableStart()](#seekablestart)
    *   [liveWindow()](#livewindow)
    *   [atLiveEdge() and behindLiveEdge()](#atliveedge-and-behindliveedge)
    *   [liveCurrentTime()](#livecurrenttime)
    *   [pastSeekEnd()](#pastseekend)
    *   [isTracking() and isLive()](#istracking-and-islive)
    *   [seekToLiveEdge()](#seektoliveedge)

> Note the "old" live user interface is currently the default, see the section on [the new user interface](/guides/live/#the-new-user-interface) for information on setting that up.

## [](/guides/live/#the-default-live-user-interface)The default live user interface

The default user interface hides the `ProgressControl` component on the controlbar and shows the `LiveDisplay` component when Video.js detects that the video that it is playing is live (via a `durationchange` event).

> Note: It does this by adding the `vjs-live` class to the player and the showing/hiding of components is all handled in css.

This makes the player have to hide the progress bar, seek bar, and display text indicating that the player is live. All of those will be shown again if a non-live video is switched to (via another `durationchange` event).

To view a sample of this user interface please:

1.  clone the repository, and move into that directory
2.  run `npm install` or `npm ci` to install all necessary packages
3.  run `npm start` to start the local server
4.  open `http://localhost:9999/sandbox/live.html` in a web browser

## [](/guides/live/#the-new-user-interface)The new user interface

> Note: This user interface will not work on Android due to the native live HLS implementation not supporting seekable ranges during live streams. We recommend overriding the native hls implementation with @videojs/http-streaming; this will make the new liveui work.

The new user interface is currently opt-in to prevent breaking backwards compatibility. We feel that the new user interface is much better and it will likely become the new default in the next major version. If you want to use the new user interface you will have to pass `{liveui: true}` during player setup. This can be done in two ways:

Using `data-setup`

```html
  <video-js data-setup='{"liveui": true}'>
  </video-js>
```

Using the `videojs` function

```js
var player = videojs('some-player-id', {liveui: true});
```

The new user interface shows the `ProgressControl` component on the control bar, hides the `LiveDisplay` component, and shows the new `SeekToLive` component when Video.js detects that the video that it is playing is live (via a `durationchange` event). Along with the `ProgressControl` update we also updated all the time tooltips on the player to indicate a negative number from the live current time, rather than seeking to a specific time.

> Note: It does this by adding the `vjs-live` and `vjs-liveui` class to the player and the showing/hiding of components is all handled in css.

The new live user interface shows the progress/seek bar and lets the user seek backwards/forwards within the live window. Next, it adds a button, via the `SeekToLive` component that can be clicked when the user is behind live that will seek to the live current time. That same button indicates if the `currentTime` of the player is live via a grey circle when not live and a red circle when live.

To view a sample of this user interface please:

1.  clone the repository, and move into that directory
2.  run `npm install` or `npm ci` to install all necessary packages
3.  run `npm start` to start the local server
4.  open `http://localhost:9999/sandbox/liveui.html` in a web browser

## [](/guides/live/#livetracker)LiveTracker

> Note: this component can be turned off by passing `liveTracker: false` to the player during initialization.

Along with the new liveui we implemented an API that can be used regardless of which user interface is in use. This API is a child of the player and should be on the player at `player.liveTracker`. `LiveTracker` provides several useful helper functions and events for dealing with live playback, all of which are used and tested internally. Internally this component keeps track of the live current time through a function that runs on a 30ms interval.

### [](/guides/live/#the-seekableendchange-event)The seekableendchange event

The live tracker will fire this event every time that the `seekableEnd` for the player changes. This is used internally to keep our `pastSeekEnd()` function up to date.

### [](/guides/live/#the-liveedgechange-event)The liveedgechange event

As the name implies the live tracker will fire this event when it detects that the current time is no longer at the live edge.

### [](/guides/live/#starttracking-and-stoptracking)startTracking() and stopTracking()

These functions can be called to arbitrarily start/stop tracking live playback. Normally these are handled by automatically when the player triggers a `durationchange` with a duration of `Infinity`. You won't want to call them unless you are doing something fairly specific.

### [](/guides/live/#seekableend)seekableEnd()

seekableEnd gets the time in seconds of the furthest seekable end. For instance if we have an array of seekable `TimeRanges` where the first element in the array is the `start()` second and the last is the `end()` second:

```js
// seekable index 0: 0 is start, 1 is end
// seekable index 1: 2 is the start, 3 is the end
const seekableExample = [[0, 1], [2, 3]];
```

seekableEnd would return `3` as that is the furthest seekable point for the current media.

> Note: that if Infinity is anywhere in seekable end, this will return Infinity

### [](/guides/live/#seekablestart)seekableStart()

seekableStart gets the time in seconds of the earliest seekable start. For instance if we have an array of seekable `TimeRanges` where the first element in the array is the `start()` second and the last is the `end()` second:

```js
// seekable index 0: 0 is start, 1 is end
// seekable index 1: 2 is the start, 3 is the end
const seekableExample = [[0, 1], [2, 3]];
```

seekableStart would return `0` as that is the first seekable point for the current media.

> Note: that if Infinity is anywhere in seekable start, this will return Infinity

### [](/guides/live/#livewindow)liveWindow()

This function gets the amount of time between the `seekableStart()` and the `liveCurrentTime()`. We use this internally to update the total length of our bars, such as the progress/seek bar.

### [](/guides/live/#atliveedge-and-behindliveedge)atLiveEdge() and behindLiveEdge()

Determines if the currentTime of the player is close enough to live to be considered live. We make sure it's close enough, rather than absolutely live, because there are too many factors to determine when live actually is. We consider the currentTime live when it is within two seekable increments and 70ms (two ticks of the live tracking interval). The seekable increment is a number that is determined by the amount that seekable end changes as playback continues. See the `seekableendchange` event and the `pastSeekEnd()` function for more info.

### [](/guides/live/#livecurrenttime)liveCurrentTime()

live current time is our best approximation of what the live current time is. Internally it uses the `pastSeekEnd()` function and adds that to the `seekableEnd()` function. It is possible for this function to return `Infinity`.

### [](/guides/live/#pastseekend)pastSeekEnd()

This is the main value that we use to track if the player is live or not. Every `30ms` we add `0.03` seconds to this value and every `seekableendchange` it is reset to 0 and `0.03` is added to it right away.

### [](/guides/live/#istracking-and-islive)isTracking() and isLive()

`isTracking` and `isLive` do the same thing they tell you if the `LiveTracker` is currently tracking live playback and since we assume that live tracking will only be done during live they should be the same.

### [](/guides/live/#seektoliveedge)seekToLiveEdge()

This function sets the players `currentTime` to the result of the `liveCurrentTime()` function.

---

# Troubleshooting | Video.js

**URL:** https://videojs.org/guides/troubleshooting/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Troubleshooting

## Table of Contents

*   [Problems with media formats](#problems-with-media-formats)
    *   [Choosing a video format](#choosing-a-video-format)
        *   [I want to have a single source and don't care about live/adaptive streaming:](#i-want-to-have-a-single-source-and-dont-care-about-liveadaptive-streaming)
        *   [I need adaptive streaming or live streaming](#i-need-adaptive-streaming-or-live-streaming)
    *   [Make sure you are using formats that Video.js can play:](#make-sure-you-are-using-formats-that-videojs-can-play)
    *   [Make sure that the codec used in the file container is supported:](#make-sure-that-the-codec-used-in-the-file-container-is-supported)
    *   [If you are using Flash videos:](#if-you-are-using-flash-videos)
*   [Problems when hosting media](#problems-when-hosting-media)
*   [Problems with fullscreen](#problems-with-fullscreen)
*   [Problems with playback](#problems-with-playback)
*   [Video.js Errors](#videojs-errors)
    *   [vdata123456 errors](#vdata123456-errors)
    *   [Uncaught ReferenceError: X is not defined](#uncaught-referenceerror-x-is-not-defined)

## [](/guides/troubleshooting/#problems-with-media-formats)Problems with media formats

### [](/guides/troubleshooting/#choosing-a-video-format)Choosing a video format

#### [](/guides/troubleshooting/#i-want-to-have-a-single-source-and-dont-care-about-liveadaptive-streaming)I want to have a single source and don't care about live/adaptive streaming:

Most browsers now play [MP4 with h264](https://caniuse.com/#feat=mpeg4) video. If you want to have a single source, and neither live streaming nor adaptive streaming is a consideration, MP4 with h264 video and acc audio is a good choice.

The most common browsers which do not support MP4 are found on Linux, where the user might need to install additional codec support, and in some cases won't want to. You can supply an array of alternate sources. [webm](https://caniuse.com/#feat=webm) and/or [ogv](https://caniuse.com/#feat=ogv) are useful as fallback, but neither are supported by all browsers that support MP4.

#### [](/guides/troubleshooting/#i-need-adaptive-streaming-or-live-streaming)I need adaptive streaming or live streaming

Video.js 7+ supports HLS and MPEG-DASH as standard as it includes [http-streaming](https://github.com/videojs/http-streaming), which uses [Media Source Extensions](https://caniuse.com/#feat=mediasource) to play these formats in modern browsers. If choosing a single format, HLS is more convenient as iOS and some Android browsers which do not support MSE do have native HLS support.

HLS is not possible on IE 11 on Windows 7, which does not support MSE.

For older Video.js versions, [http-streaming](https://github.com/videojs/http-streaming) or its predecessors [videojs-contrib-hls](https://github.com/videojs/videojs-contrib-hls) and [videojs-contrib-dash](https://github.com/videojs/videojs-contrib-dash) add similar support, but for best results use the latest Video.js.

### [](/guides/troubleshooting/#make-sure-you-are-using-formats-that-videojs-can-play)Make sure you are using formats that Video.js can play:

*   Does your browser/OS support the type of media that you are trying to play?
*   Do you have a Video.js plugin that will add support for a media format to Video.js? For example [videojs-youtube](https://github.com/videojs/videojs-youtube)
*   Verify that you are using the correct [mime-type/content-type](https://www.iana.org/assignments/media-types/media-types.xhtml#video) for your videos. This is used to determine if Video.js can play a certain type of media.

### [](/guides/troubleshooting/#make-sure-that-the-codec-used-in-the-file-container-is-supported)Make sure that the codec used in the file container is supported:

*   The MP4 format can contain video and audio data in many codecs, but MP4 playback in browsers typically only supports h264 video and MP3 or AAC audio.
*   The file extension does not always reflect the file contents. For example some low end phones save video in 3GP format but give it an MP4 extension. These files will not play.

### [](/guides/troubleshooting/#if-you-are-using-flash-videos)If you are using Flash videos:

*   [Flash has reached end of life](https://www.adobe.com/products/flashplayer/end-of-life.html) and is no longer supported in browsers.

## [](/guides/troubleshooting/#problems-when-hosting-media)Problems when hosting media

*   Your server _must_ properly support byte-range requests as Chrome and Safari rely on them:
    *   Most servers support this by default.
    *   If you are proxying the media files via a server side script (PHP), this script must implement ranges. PHP does not do this by default.
    *   The impact of not doing this ranges from seeking being broken to no playback at all (on iOS).
*   Your server must return the correct [mime-type/content-type](https://www.iana.org/assignments/media-types/media-types.xhtml#video) header for the media being sent.
*   Your server must implement [CORS (cross-origin resource)](https://enable-cors.org/) headers if:
    *   You are using formats like HLS or MPEG-DASH and your media is served from a different domain than your page.
    *   You are using [text tracks](/guides/text-tracks) (captions, subtitles, etc.) and they are being served from a different domain than your page.

## [](/guides/troubleshooting/#problems-with-fullscreen)Problems with fullscreen

*   If your player is in an iframe, that iframe _and_ any parent iframes must have the following attributes for fullscreen to be allowed:
    *   `allowfullscreen`
    *   `webkitallowfullscreen`
    *   `mozallowfullscreen`

## [](/guides/troubleshooting/#problems-with-playback)Problems with playback

*   Make sure that the media host supports byte-range requests, this could be breaking playback. See [Problems when hosting media](/guides/troubleshooting/#problems-when-hosting-media) for more info.
*   If your media is taking a long time to start playback or the entire mediadownloads before playback:
    *   It is likely that metadata for the media has not been included at the start of the media. In MP4 terms this is called the "moov atom". Many encoders are configured to do this by default, others may require you to choose a "fast start" or "optimize for streaming" option.

## [](/guides/troubleshooting/#videojs-errors)Video.js Errors

### [](/guides/troubleshooting/#vdata123456-errors)vdata123456 errors

This error is thrown when an element that is associated with a component is removed from the DOM but the event handlers associated with the element are not removed. This is almost always due to event listeners not being disposed when dispose is called on a component.

To fix this issue please make sure that all event listeners are cleaned up on dispose.

### [](/guides/troubleshooting/#uncaught-referenceerror-x-is-not-defined)Uncaught ReferenceError: X is not defined

Errors like this, where `X` will vary, can be caused by transpilation breaking code that is used in web workers. See the [webpack guide](/guides/webpack) for details of how to prevent this.

---

# Debugging | Video.js

**URL:** https://videojs.org/guides/debugging/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Debugging

## Table of Contents

*   [Logging](#logging)
    *   [API Overview](#api-overview)
    *   [Log Safely](#log-safely)
    *   [Log Objects Usefully](#log-objects-usefully)
    *   [Creating new Loggers](#creating-new-loggers)
    *   [Log Levels](#log-levels)
    *   [Available Log Levels](#available-log-levels)
    *   [Debug Logging](#debug-logging)
    *   [History](#history)
        *   [History filtering](#history-filtering)

## [](/guides/debugging/#logging)Logging

Video.js includes `videojs.log`, a lightweight wrapper around a subset of [the `console` API](https://developer.mozilla.org/en-US/docs/Web/API/Console). The available methods are `videojs.log`, `videojs.log.debug`, `videojs.log.warn`, and `videojs.log.error`.

### [](/guides/debugging/#api-overview)API Overview

Most of these methods should be fairly self-explanatory, but for complete details, see [the API docs](https://docs.videojs.com/).

| Method | Alias Of | Matching Level(s) |
| --- | --- | --- |
| `videojs.log()` | `console.log` | all, debug, info |
| `videojs.log.debug()` | `console.debug` | all, debug |
| `videojs.log.warn()` | `console.warn` | all, debug, info, warn |
| `videojs.log.error()` | `console.error` | all, debug, info, warn, error |
| `videojs.log.createLogger()` | n/a | n/a |
| `videojs.log.level()` | n/a | n/a |
| `videojs.log.history()` | n/a | n/a |
| `videojs.log.history.clear()` | n/a | n/a |
| `videojs.log.history.disable()` | n/a | n/a |
| `videojs.log.history.enable()` | n/a | n/a |
| `videojs.log.history.filter()` | n/a | n/a |

For descriptions of these features, please refer to the sections below.

### [](/guides/debugging/#log-safely)Log Safely

Unlike the `console`, it's safe to leave `videojs.log` calls in your code. They won't throw errors when the `console` doesn't exist.

### [](/guides/debugging/#log-objects-usefully)Log Objects Usefully

Similar to the `console`, any number of mixed-type values can be passed to `videojs.log` methods:

```js
videojs.log('this is a string', {butThis: 'is an object'});
```

### [](/guides/debugging/#creating-new-loggers)Creating new Loggers

Sometimes, you want to make a new module or plugin and log messages with a label. Kind of how all these logs are prepended with `VIDEOJS:`. You can do that via the `createLogger` method. It takes a name and gives you back a log object like `videojs.log`. Here's an example:

```js
const mylogger = videojs.log.createLogger('mylogger');

mylogger('hello world!');
// > VIDEOJS: mylogger: hello world!

// We can even chain it further
const anotherlogger = mylogger.createLogger('anotherlogger');

anotherlogger('well, hello there');
// > VIDEOJS: mylogger: anotherlogger: well, hello there
```

### [](/guides/debugging/#log-levels)Log Levels

Unlike the `console`, `videojs.log` includes the concept of logging levels. These levels toggle logging methods on or off.

Levels are exposed through the `videojs.log.level` method. This method acts as both a getter and setter for the current logging level. With no arguments, it returns the current logging level:

```js
videojs.log.level(); // "info"
```

By passing a string, the logging level can be changed to one of the available logging levels:

```js
videojs.log.level('error'); // show only error messages and suppress others
videojs.log('foo'); // does nothing
videojs.log.warn('foo'); // does nothing
videojs.log.error('foo'); // logs "foo" as an error
```

### [](/guides/debugging/#available-log-levels)Available Log Levels

*   **info** (default): only show `log`, `log.warn`, and `log.error` messages
*   **all**: enables all logging methods
*   **error**: only show `log.error` messages
*   **off**: disable all logging methods
*   **warn**: only show `log.warn` _and_ `log.error` messages
*   **debug**: show `log`, `log.debug`, `log.warn`, and `log.error` messages

### [](/guides/debugging/#debug-logging)Debug Logging

Although the log levels attempt to match their `window.console` counterparts, `window.console.debug` is not available on all platforms. As such, it will use the closest comparable method, falling back from `window.console.debug` to `window.console.info` to `window.console.log`, and ultimately to nothing if none of those methods are available.

### [](/guides/debugging/#history)History

> **Note:** In Video.js 5, `videojs.log.history` was an array. As of Video.js 6, it is a function which returns an array. This change was made to provide a richer, safer logging history API. You can also filter the history based on the name of the logger.

By default, the `videojs.log` module tracks a history of _everything_ passed to it regardless of logging level:

```js
videojs.log.history(); // an array of everything that's been logged up to now
```

This will work even when logging is set to **off**.

This can be useful, but it can also be a source of memory leaks. For example, logged objects will be retained in history even if references are removed everywhere else!

To avoid this problem, history can be disabled or enabled via method calls (using the `disable` and `enable` methods respectively). Disabling history is as easy as:

```js
videojs.log.history.disable();
```

Finally, the history (if enabled) can be cleared at any time via:

```js
videojs.log.history.clear();
```

#### [](/guides/debugging/#history-filtering)History filtering

If you want to find all the history that was created by a particular logger, you can do so via `history.filter()`. Given a specific logger with name `foo`, you can pass `foo` to `history.filter()` and get all items logger by foo. Let me show you an example:

```js
const mylogger = videojs.log.createLogger('mylogger');
const anotherlogger = mylogger.createLogger('anotherlogger');

videojs.log('hello');
mylogger('how are you');
anotherlogger('today');

videojs.log.history.filter('VIDEOJS');
// > [['VIDEOJS:', 'hello'], ['VIDEOJS: mylogger:', 'how are you'], ['VIDEOJS: mylogger: anotherlogger:', 'today']]
videojs.log.history.filter('mylogger');
// > [['VIDEOJS:    mylogger:', 'how are you'], ['VIDEOJS: mylogger: anotherlogger:', 'today']]
videojs.log.history.filter('anotherlogger');
// > [['VIDEOJS: mylogger: anotherlogger:', 'today']]
```

---

# Components | Video.js

**URL:** https://videojs.org/guides/components/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Components

## Table of Contents

*   [What is a Component?](#what-is-a-component)
*   [Adding a Component](#adding-a-component)
*   [Creating a Component](#creating-a-component)
*   [Component Children](#component-children)
    *   [Basic Example](#basic-example)
    *   [Using Options](#using-options)
*   [Event Listening](#event-listening)
    *   [Using on](#using-on)
    *   [Using off](#using-off)
    *   [Using one](#using-one)
    *   [Using trigger](#using-trigger)
*   [Default Component Tree](#default-component-tree)
*   [Specific Component Details](#specific-component-details)
    *   [Play Toggle](#play-toggle)
    *   [Volume Panel](#volume-panel)
    *   [Text Track Settings](#text-track-settings)
    *   [Resize Manager](#resize-manager)

**NOTE:** This guide is focused on Video.js 8+. It no longer mentions use of the `videojs.extend()` method, which was removed in 8.0. Please see [our migration guide](/guides/videojs-7-to-8/) for further information!

The architecture of the Video.js player is centered around components.

The `Player` class and all classes representing player controls and other UI elements inherit from the `Component` class. This architecture makes it easy to construct the user interface of the Video.js player in a tree-like structure that mirrors the DOM.

## [](/guides/components/#what-is-a-component)What is a Component?

A component is a JavaScript object that has the following features:

*   An associated DOM element, in almost all cases.
*   An association to a `Player` object.
*   The ability to manage any number of child components.
*   The ability to listen for and trigger events.
*   A lifecycle of initialization and disposal.

For more specifics on the programmatic interface of a component, see [the component API docs](https://docs.videojs.com/Component.html).

## [](/guides/components/#adding-a-component)Adding a Component

An instance of a component can be created with `new Component()`.

```js
// Creating an instance of a button
var player = videojs('some-video-id');
var Button = videojs.getComponent('Button');
var button = new Button(player, {
  clickHandler: function(event) {
    videojs.log('Clicked');
  }
});

console.log(button.el());
```

The above code will output

```html
<button class="vjs-control vjs-button" type="button" aria-disabled="false">
  <span class="vjs-icon-placeholder" aria-hidden="true"></span>
  <span class="vjs-control-text" aria-live="polite"></span>
</button>
```

Note that this has created the button, but not added it to the DOM. Adding it as a child of a component will add it to the DOM.

```js
player.getChild('ControlBar').addChild(button);
```

Alternatively by passing the name of a component to `addChild`, a new instance of the component will be created and added in one step.

```js
// Creating an instance of a button and addingit to the player's control bar
var player = videojs('some-video-id');
var button = player.getChild('ControlBar').addChild('button', {
  clickHandler: function(event) {
    videojs.log('Clicked');
  }
});

console.log(button.el());
// will have the same html result as the previous example
```

Buttons should have text. The default buttons don't display their text, but it is present for screenreaders and displayed by browsers as a tooltip. The text of the button can be set as an option:

```js
const myButton = player.getChild('ControlBar').addChild('button', {controlText: 'My button'});
```

To have the control text displayed, add a `vjs-visibile-text` class to the button.

```js
const myButton = player.getChild('ControlBar').addChild('button', {
  controlText: 'My button',
  className: 'vjs-visible-text'
});
```

Classes and control text could also be set after a button is created.

```js
myButton.controlText('My button');
myButton.addClass('vjs-visible-text');
```

When the [`experimentalSvgIcons`](/guides/options/#experimentalSvgIcons) option is enabled on the player, icons can be added or replaced on any `Component` using the `setIcon` method.

You can view all of the icons available by renaming [`sandbox/svg-icons.html.example`](https://github.com/videojs/video.js/blob/main/sandbox/svg-icons.html.example) to `sandbox/svg-icons.html`, building Video.js with `npm run build`, and opening `sandbox/svg-icons.html` in your browser of choice.

```js
myButton.setIcon('play');
```

## [](/guides/components/#creating-a-component)Creating a Component

Video.js components are es6 classes that can be extended using class syntax and registered with Video.js to add new features and UI to the player.

There are a few functions used for creating and registering components:

*   `videojs.getComponent(String name)`: Retrieves component classes from Video.js.
*   `videojs.registerComponent(String name, Function Comp)`: Registers component classes with Video.js.

This example creates a title bar component, as a class extending `Component`.

```js
// Get the Component base class from Video.js
const Component = videojs.getComponent('Component');

class TitleBar extends Component {

  // The constructor of a component receives two arguments: the
  // player it will be associated with and an object of options.
  constructor(player, options = {}) {

    // It is important to invoke the superclass before anything else, 
    // to get all the features of components out of the box!
    super(player, options);

    // If a `text` option was passed in, update the text content of 
    // the component.
    if (options.text) {
      this.updateTextContent(options.text);
    }
  }

  // The `createEl` function of a component creates its DOM element.
  createEl() {
    return videojs.dom.createEl('div', {

      // Prefixing classes of elements within a player with "vjs-" 
      // is a convention used in Video.js.
      className: 'vjs-title-bar'
    });
  }

  // This function could be called at any time to update the text 
  // contents of the component.
  updateTextContent(text) {

    // If no text was provided, default to "Title Unknown"
    if (typeof text !== 'string') {
      text = 'Title Unknown';
    }

    // Use Video.js utility DOM methods to manipulate the content
    // of the component's element.
    videojs.emptyEl(this.el());
    videojs.appendContent(this.el(), text);
  }
}
```

Note that due to the removal of the `extend()` function, to extend a component when transpiling to ES5, you will need to utilize the following syntax.

```js
// My ES5 constructor function extending Component
function MyComponent(arguments) {
  Component.call(this, arguments);
}

MyComponent.prototype = Object.create(Component.prototype);
```

Once the component is created, it can be registered, and used in a player.

```js
// Register the component with Video.js, so it can be used in players.
videojs.registerComponent('TitleBar', TitleBar);

// Create a player.
var player = videojs('my-player');

// Add the TitleBar as a child of the player and provide it some text 
// in its options.
player.addChild('TitleBar', {text: 'The Title of The Video!'});
```

A live example is in [this JSBin](https://jsbin.com/vobacas/edit?html,css,js,output).

## [](/guides/components/#component-children)Component Children

Again, refer to [the component API docs](https://docs.videojs.com/Component.html) for complete details on methods available for managing component structures.

### [](/guides/components/#basic-example)Basic Example

When a child component is added to a parent component, Video.js inserts the element of the child into the element of the parent. For example, adding a component like this:

```js
// Add a "BigPlayButton" component to the player. Its element will be appended to the player's element.
player.addChild('BigPlayButton');
```

Results in a DOM that looks like this:

```html
<!-- Player Element -->
<div class="video-js">
  <!-- BigPlayButton Element -->
  <div class="vjs-big-play-button"></div>
</div>
```

Conversely, removing child components will remove the child component's element from the DOM:

```js
player.removeChild('BigPlayButton');
```

Results in a DOM that looks like this:

```html
<!-- Player Element -->
<div class="video-js">
</div>
```

### [](/guides/components/#using-options)Using Options

Pass in options for child constructors and options for children of the child.

```js
var player = videojs('some-vid-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myButton = myComponent.addChild('MyButton', {
  text: 'Press Me',
  buttonChildExample: {
    buttonChildOption: true
  }
});
```

Children can also be added via options when a component is initialized.

> Note: Include a 'name' key which will be used if two child components of the same type that need different options.

```js
// MyComponent is from the above example
var myComp = new MyComponent(player, {
  children: ['button', {
    name: 'button',
    someOtherOption: true
  }, {
    name: 'button',
    someOtherOption: false
  }]
});
```

## [](/guides/components/#event-listening)Event Listening

### [](/guides/components/#using-on)Using `on`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function() {
  var myComponent = this;
  console.log('myFunc called');
};

myComponent.on('eventType', myFunc);
myComponent.trigger('eventType');
// logs 'myFunc called'
```

The context of `myFunc` will be `myComponent` unless it is bound. You can add a listener to another element or component.

```js
var otherComponent = new Component(player);

// myComponent/myFunc is from the above example
myComponent.on(otherComponent.el(), 'eventName', myFunc);
myComponent.on(otherComponent, 'eventName', myFunc);

otherComponent.trigger('eventName');
// logs 'myFunc called' twice
```

### [](/guides/components/#using-off)Using `off`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function() {
  var myComponent = this;
  console.log('myFunc called');
};
myComponent.on('eventType', myFunc);
myComponent.trigger('eventType');
// logs 'myFunc called'

myComponent.off('eventType', myFunc);
myComponent.trigger('eventType');
// does nothing
```

If myFunc gets excluded, _all_ listeners for the event type will get removed. If eventType gets excluded, _all_ listeners will get removed from the component. You can use `off` to remove listeners that get added to other elements or components using:

`myComponent.on(otherComponent...`

In this case both the event type and listener function are **REQUIRED**.

```js
var otherComponent = new Component(player);

// myComponent/myFunc is from the above example
myComponent.on(otherComponent.el(), 'eventName', myFunc);
myComponent.on(otherComponent, 'eventName', myFunc);

otherComponent.trigger('eventName');
// logs 'myFunc called' twice
myComponent.off(otherComponent.el(), 'eventName', myFunc);
myComponent.off(otherComponent, 'eventName', myFunc);
otherComponent.trigger('eventName');
// does nothing
```

### [](/guides/components/#using-one)Using `one`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function() {
  var myComponent = this;
  console.log('myFunc called');
};
myComponent.one('eventName', myFunc);
myComponent.trigger('eventName');
// logs 'myFunc called'

myComponent.trigger('eventName');
// does nothing
```

You can also add a listener to another element or component that will get triggered only once.

```js
var otherComponent = new Component(player);

// myComponent/myFunc is from the above example
myComponent.one(otherComponent.el(), 'eventName', myFunc);
myComponent.one(otherComponent, 'eventName', myFunc);

otherComponent.trigger('eventName');
// logs 'myFunc called' twice

otherComponent.trigger('eventName');
// does nothing
```

### [](/guides/components/#using-trigger)Using `trigger`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function(data) {
  var myComponent = this;
  console.log('myFunc called');
  console.log(data);
};
myComponent.one('eventName', myFunc);
myComponent.trigger('eventName');
// logs 'myFunc called' and 'undefined'

myComponent.trigger({'type':'eventName'});
// logs 'myFunc called' and 'undefined'

myComponent.trigger('eventName', {data: 'some data'});
// logs 'myFunc called' and "{data: 'some data'}"

myComponent.trigger({'type':'eventName'}, {data: 'some data'});
// logs 'myFunc called' and "{data: 'some data'}"
```

## [](/guides/components/#default-component-tree)Default Component Tree

The default component structure of the Video.js player looks something like this:

```text
Player
├── MediaLoader (has no DOM element)
├── PosterImage
├── TextTrackDisplay
├── LoadingSpinner
├── BigPlayButton
├── LiveTracker (has no DOM element)
├─┬ ControlBar
│ ├── PlayToggle
│ ├── VolumePanel
│ ├── CurrentTimeDisplay (hidden by default)
│ ├── TimeDivider (hidden by default)
│ ├── DurationDisplay (hidden by default)
│ ├─┬ ProgressControl (hidden during live playback, except when liveui: true)
│ │ └─┬ SeekBar
│ │   ├── LoadProgressBar
│ │   ├── MouseTimeDisplay
│ │   └── PlayProgressBar
│ ├── LiveDisplay (hidden during VOD playback)
│ ├── SeekToLive (hidden during VOD playback)
│ ├── RemainingTimeDisplay
│ ├── CustomControlSpacer (has no UI)
│ ├── PlaybackRateMenuButton (hidden, unless playback tech supports rate changes)
│ ├── ChaptersButton (hidden, unless there are relevant tracks)
│ ├── DescriptionsButton (hidden, unless there are relevant tracks)
│ ├── SubsCapsButton (hidden, unless there are relevant tracks)
│ ├── AudioTrackButton (hidden, unless there are relevant tracks)
│ ├── PictureInPictureToggle
│ └── FullscreenToggle
├── ErrorDisplay (hidden, until there is an error)
├── TextTrackSettings
└── ResizeManager (hidden)
```

## [](/guides/components/#specific-component-details)Specific Component Details

### [](/guides/components/#play-toggle)Play Toggle

The `PlayToggle` has one option `replay` which can show or hide replay icon. This can be set by passing `{replay: false}` as the default behavior replay icon is shown after video end playback.

Example of how to hide a replay icon

```js
let player = videojs('myplayer', {
  controlBar: {
    playToggle: {
      replay: false
    }
  }
});
```

### [](/guides/components/#volume-panel)Volume Panel

The `VolumePanel` includes the `MuteToggle` and the `VolumeControl` Components, which will be hidden if volume changes are not supported. There is one important option for the `VolumePanel` which can make your `VolumeControl` appear vertically over the `MuteToggle`. This can be set by passing `VolumePanel` `{inline: false}` as the default behavior is a horizontal `VolumeControl` with `{inline: true}`.

Example of a vertical `VolumeControl`

```js
let player = videojs('myplayer', {
  controlBar: {
    volumePanel: {
      inline: false
    }
  }
});
```

### [](/guides/components/#text-track-settings)Text Track Settings

The text track settings component is only available when using emulated text tracks.

### [](/guides/components/#resize-manager)Resize Manager

This new component is in charge of triggering a `playerresize` event when the player size changed. It uses the ResizeObserver if available or a polyfill was provided. It has no element when using the ResizeObserver. If a ResizeObserver is not available, it will fallback to an iframe element and listen to its resize event via a debounced handler.

A ResizeObserver polyfill can be passed in like so:

```js
var player = videojs('myplayer', {
  resizeManager: {
    ResizeObserver: ResizeObserverPoylfill
  }
});
```

To force using the iframe fallback, pass in `null` as the `ResizeObserver`:

```js
var player = videojs('myplayer', {
  resizeManager: {
    ResizeObserver: null
  }
});
```

The ResizeManager can also just be disabled like so:

```js
var player = videojs('myplayer', {
  resizeManager: false
});
```

---

# Video.js Plugins | Video.js

**URL:** https://videojs.org/guides/plugins/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js Plugins

## Table of Contents

*   [Writing a Basic Plugin](#writing-a-basic-plugin)
    *   [Write a JavaScript Function](#write-a-javascript-function)
    *   [Register a Basic Plugin](#register-a-basic-plugin)
*   [Writing an Advanced Plugin](#writing-an-advanced-plugin)
    *   [Write a JavaScript Class/Constructor](#write-a-javascript-classconstructor)
    *   [Register an Advanced Plugin](#register-an-advanced-plugin)
    *   [Key Differences from Basic Plugins](#key-differences-from-basic-plugins)
        *   [The Value of this](#the-value-of-this)
        *   [The Player Plugin Name Property](#the-player-plugin-name-property)
    *   [Features of Advanced Plugins](#features-of-advanced-plugins)
        *   [Events](#events)
        *   [Statefulness](#statefulness)
        *   [Lifecycle](#lifecycle)
        *   [Version](#version)
        *   [Logging](#logging)
    *   [Advanced Example Advanced Plugin](#advanced-example-advanced-plugin)
*   [Setting up a Plugin](#setting-up-a-plugin)
    *   [Plugin Setup Events](#plugin-setup-events)
*   [References](#references)

**NOTE:** This guide is focused on Video.js 8+. It no longer mentions use of the `videojs.extend()` method, which was removed in 8.0. Please see [our migration guide](/guides/videojs-7-to-8/) for further information!

One of the great strengths of Video.js is its ecosystem of plugins that allow authors from all over the world to share their video player customizations. This includes everything from the simplest UI tweaks to new [playback technologies and source handlers](/guides/tech)!

Because we view plugins as such an important part of Video.js, the organization is committed to maintaining a robust set of tools for plugin authorship:

*   [generator-videojs-plugin](https://github.com/videojs/generator-videojs-plugin)
    
    A [Yeoman](http://yeoman.io) generator for scaffolding a Video.js plugin project. Additionally, it offers a set of [conventions for plugin authorship](https://github.com/videojs/generator-videojs-plugin/blob/master/docs/conventions.md) that, if followed, make authorship, contribution, and usage consistent and predictable.
    
    In short, the generator sets up plugin authors to focus on writing their plugin - not messing with tools.
    

## [](/guides/plugins/#writing-a-basic-plugin)Writing a Basic Plugin

If you've written a Video.js plugin before, the basic plugin concept should be familiar. It's similar to a jQuery plugin in that the core idea is that you're adding a method to the player.

### [](/guides/plugins/#write-a-javascript-function)Write a JavaScript Function

A basic plugin is a plain JavaScript function:

```js
function examplePlugin(options) {

  if (options.customClass) {
    this.addClass(options.customClass);
  }

  this.on('playing', function() {
    videojs.log('playback began!');
  });
}
```

By convention, plugins are passed an `options` object; however, you can realistically accept whatever arguments you want. This example plugin will add a custom class (whatever is passed in as `options.customClass`) and, whenever playback begins, it will log a message to the browser console.

> **Note:** The value of `this` in the plugin function is the player instance; so, you have access to [its complete API](https://docs.videojs.com/Player.html).

### [](/guides/plugins/#register-a-basic-plugin)Register a Basic Plugin

Now that we have a function that does something with a player, all that's left is to register the plugin with Video.js:

```js
videojs.registerPlugin('examplePlugin', examplePlugin);
```

After that, any player will automatically have an `examplePlugin` method on its prototype!

> **Note:** The only stipulation with the name of the plugin is that it cannot conflict with any existing plugin or player method.

## [](/guides/plugins/#writing-an-advanced-plugin)Writing an Advanced Plugin

Video.js 6 introduced advanced plugins: these are plugins that share a similar API with basic plugins, but are class-based and offer a range of extra features out of the box.

While reading the following sections, you may want to refer to the [Plugin API docs](https://docs.videojs.com/Plugin.html) for more detail.

### [](/guides/plugins/#write-a-javascript-classconstructor)Write a JavaScript Class/Constructor

If you're familiar with creating [components](/guides/components), this process is similar. An advanced plugin starts with a JavaScript class:

```js
const Plugin = videojs.getPlugin('plugin');

class ExamplePlugin extends Plugin {

  constructor(player, options) {
    super(player, options);

    if (options.customClass) {
      player.addClass(options.customClass);
    }

    player.on('playing', function() {
      videojs.log('playback began!');
    });
  }
}
```

For now, this example advanced plugin does the exact same thing as the basic plugin described above - not to worry, we will make it more interesting as we continue!

### [](/guides/plugins/#register-an-advanced-plugin)Register an Advanced Plugin

The registration process for advanced plugins is identical to [the process for basic plugins](/guides/plugins/#register-a-basic-plugin).

```js
videojs.registerPlugin('examplePlugin', ExamplePlugin);
```

### [](/guides/plugins/#key-differences-from-basic-plugins)Key Differences from Basic Plugins

Advanced plugins have two key differences from basic plugins that are important to understand before describing their advanced features.

#### [](/guides/plugins/#the-value-of-this)The Value of `this`

With basic plugins, the value of `this` in the plugin function will be the _player_.

With advanced plugins, the value of `this` is the _instance of the plugin class_. The player is passed to the plugin constructor as its first argument (and is automatically applied to the plugin instance as the `player` property) and any further arguments are passed after that.

#### [](/guides/plugins/#the-player-plugin-name-property)The Player Plugin Name Property

Both basic plugins and advanced plugins are set up by calling a method on a player with a name matching the plugin (e.g., `player.examplePlugin()`).

However, with advanced plugins, this method acts like a factory function and it is _replaced_ for the current player by a new function which returns the plugin instance:

```js
// `examplePlugin` has not been called, so it is a factory function.
player.examplePlugin();

// `examplePlugin` is now a function that returns the same instance of
// `ExamplePlugin` that was generated by the previous call.
player.examplePlugin().someMethodName();
```

With basic plugins, the method does not change - it is always the same function. It is up to the authors of basic plugins to deal with multiple calls to their plugin function.

### [](/guides/plugins/#features-of-advanced-plugins)Features of Advanced Plugins

Up to this point, our example advanced plugin is functionally identical to our example basic plugin. However, advanced plugins bring with them a great deal of benefit that is not built into basic plugins.

#### [](/guides/plugins/#events)Events

Like components, advanced plugins offer an implementation of events. This includes:

*   The ability to listen for events on the plugin instance using `on` or `one`:
    
    ```js
    player.examplePlugin().on('example-event', function() {
      videojs.log('example plugin received an example-event');
    });
    ```
    
*   The ability to `trigger` custom events on a plugin instance:
    
    ```js
    player.examplePlugin().trigger('example-event');
    ```
    
*   The ability to stop listening to custom events on a plugin instance using `off`:
    
    ```js
    player.examplePlugin().off('example-event');
    ```
    

By offering a built-in events system, advanced plugins offer a wider range of options for code structure with a pattern familiar to most web developers.

##### [](/guides/plugins/#extra-event-data)Extra Event Data

All events triggered by plugins include an additional data object as a second argument. This object has three properties:

*   `name`: The name of the plugin (e.g. `"examplePlugin"`) as a string.
*   `plugin`: The plugin constructor (e.g. `ExamplePlugin`).
*   `instance`: The plugin constructor instance.

#### [](/guides/plugins/#statefulness)Statefulness

A new concept introduced for advanced plugins is _statefulness_. This is similar to React components' `state` property and `setState` method.

Advanced plugin instances each have a `state` property, which is a plain JavaScript object - it can contain any keys and values the plugin author wants.

A default `state` can be provided by adding a static property to a plugin constructor:

```js
ExamplePlugin.defaultState = {
  customClass: 'default-custom-class'
};
```

When the `state` is updated via the `setState` method, the plugin instance fires a `"statechanged"` event, but _only if something changed!_ This event can be used as a signal to update the DOM or perform some other action. The event object passed to listeners for this event includes, an object describing the changes that occurred on the `state` property:

```js
player.examplePlugin().on('statechanged', function(e) {
  if (e.changes && e.changes.customClass) {
    this.player
      .removeClass(e.changes.customClass.from)
      .addClass(e.changes.customClass.to);
  }
});

player.examplePlugin().setState({customClass: 'another-custom-class'});
```

#### [](/guides/plugins/#lifecycle)Lifecycle

Like components, advanced plugins have a lifecycle. They can be created with their factory function and they can be destroyed using their `dispose` method:

```js
// set up a example plugin instance
player.examplePlugin();

// dispose of it anytime thereafter
player.examplePlugin().dispose();
```

The `dispose` method has several effects:

*   Triggers a `"dispose"` event on the plugin instance.
*   Cleans up all event listeners on the plugin instance, which helps avoid errors caused by events being triggered after an object is cleaned up.
*   Removes plugin state and references to the player to avoid memory leaks.
*   Reverts the player's named property (e.g. `player.examplePlugin`) _back_ to the original factory function, so the plugin can be set up again.

In addition, if the player is disposed, the disposal of all its advanced plugin instances will be triggered as well.

#### [](/guides/plugins/#version)Version

Adding a version number to a plugin is done by defining a `VERSION` property on the plugin before registering it:

```js
ExamplePlugin.VERSION = '1.0.1';

videojs.registerPlugin('examplePlugin', ExamplePlugin);
```

Retrieve it using `videojs.getPluginVersion`:

```js
var version = videojs.getPluginVersion('examplePlugin');
console.log(version);  // 1.0.1
```

Note that the [plugin generator](https://github.com/videojs/generator-videojs-plugin) already takes care of adding a version number for you.

#### [](/guides/plugins/#logging)Logging

By default, each advanced plugin instance has its own `log` property much like `videojs` and `Player` instances do. The log messages will be prefixed with the player's ID and the plugin's name:

```js
player.examplePlugin().log('hello world!');
```

The above will log the following:

```text
VIDEOJS: $PLAYER_ID: examplePlugin: hello world!
```

The `log` function will also have all the methods/properties of the default `videojs.log`; such as, `error()`, `warn()`, `level()`, etc.

> **NOTE:** This method is added in the constructor and it _will not_ override any predefined `log` property of the plugin's prototype.

### [](/guides/plugins/#advanced-example-advanced-plugin)Advanced Example Advanced Plugin

What follows is a complete ES6 advanced plugin that logs a custom message when the player's state changes between playing and pause. It uses all the described advanced features:

```js
import videojs from 'video.js';

const Plugin = videojs.getPlugin('plugin');

class Advanced extends Plugin {

  constructor(player, options) {
    super(player, options);

    // Whenever the player emits a playing or pause event, we update the
    // state if necessary.
    this.on(player, ['playing', 'pause'], this.updateState);
    this.on('statechanged', this.logState);
  }

  dispose() {
    super.dispose();
    videojs.log('the advanced plugin is being disposed');
  }

  updateState() {
    this.setState({playing: !this.player.paused()});
  }

  logState(changed) {
    videojs.log(`the player is now ${this.state.playing ? 'playing' : 'paused'}`);
  }
}

videojs.registerPlugin('advanced', Advanced);

const player = videojs('example-player');

player.advanced();

// This will begin playback, which will trigger a "playing" event, which will
// update the state of the plugin, which will cause a message to be logged.
player.play();

// This will pause playback, which will trigger a "paused" event, which will
// update the state of the plugin, which will cause a message to be logged.
player.pause();

player.advanced().dispose();

// This will begin playback, but the plugin has been disposed, so it will not
// log any messages.
player.play();
```

This example may be a bit pointless in reality, but it demonstrates the sort of flexibility offered by advanced plugins over basic plugins.

## [](/guides/plugins/#setting-up-a-plugin)Setting up a Plugin

There are two ways to set up (or initialize) a plugin on a player. Both ways work identically for both basic and advanced plugins.

The first way is during creation of the player. Using the `plugins` option, a plugin can be automatically set up on a player:

```js
videojs('example-player', {
  plugins: {
    examplePlugin: {
      customClass: 'example-class'
    }
  }
});
```

Otherwise, a plugin can be manually set up:

```js
var player = videojs('example-player');
player.examplePlugin({customClass: 'example-class'});
```

These two methods are functionally identical - use whichever you prefer!

### [](/guides/plugins/#plugin-setup-events)Plugin Setup Events

Occasionally, a use-case arises where some code needs to wait for a plugin to be initialized. As of Video.js 6, this can be achieved by listening for `pluginsetup` events on the player.

For any given plugin initialization, there are four events to be aware of:

*   `beforepluginsetup`: Triggered immediately before any plugin is initialized.
*   `beforepluginsetup:examplePlugin` Triggered immediately before the `examplePlugin` is initialized.
*   `pluginsetup`: Triggered after any plugin is initialized.
*   `pluginsetup:examplePlugin`: Triggered after the `examplePlugin` is initialized.

These events work for both basic and advanced plugins. They are triggered on the player and each includes an object of [extra event data](/guides/plugins/#extra-event-data) as a second argument to its listeners.

## [](/guides/plugins/#references)References

*   [Player API](https://docs.videojs.com/Player.html)
*   [Plugin API](https://docs.videojs.com/Plugin.html)
*   [Plugin Generator](https://github.com/videojs/generator-videojs-plugin)
*   [Plugin Conventions](https://github.com/videojs/generator-videojs-plugin/blob/master/docs/conventions.md)

---

# Event Target | Video.js

**URL:** https://videojs.org/guides/event-target/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Event Target

## Table of Contents

*   [Overview](#overview)
*   [on() and addEventListener()](#on-and-addeventlistener)
*   [off() and removeEventListener()](#off-and-removeeventlistener)
*   [one()](#one)
*   [trigger() and dispatchEvent()](#trigger-and-dispatchevent)

## [](/guides/event-target/#overview)Overview

Events in Video.js are setup so that they mimic the DOM API that is used on object, but also have helpful shorthand functions with the same functionality.

## [](/guides/event-target/#on-and-addeventlistener)`on()` and `addEventListener()`

This function is used to add an event listener to an EventTarget.

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

foo.on('bar', handleBar);

// This causes any `event listeners` for the `bar` event to get called
// see {@link EventTarget#trigger} for more information
foo.trigger('bar');
// logs 'bar was triggered'
```

## [](/guides/event-target/#off-and-removeeventlistener)`off()` and `removeEventListener()`

This function is used to remove an listener function from an EventTarget.

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

// adds an `event listener` for the `bar` event
// see {@link EventTarget#on} for more info
foo.on('bar', handleBar);

// runs all `event listeners` for the `bar` event
// see {@link EventTarget#trigger} for more info
foo.trigger('bar');
// logs 'bar was triggered'

foo.off('bar', handleBar);
foo.trigger('bar');
// does nothing
```

## [](/guides/event-target/#one)`one()`

This function is used to only have an event listener called once and never again.

Using `on()` and `off()` to mimic `one()` (not recommended)

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
  // after the first trigger remove this handler
  foo.off('bar', handleBar);
};

foo.on('bar', handleBar);
foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('bar');
// does nothing
```

Using `one()`

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

// removed after the first trigger
foo.one('bar', handleBar);
foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('bar');
// does nothing
```

## [](/guides/event-target/#trigger-and-dispatchevent)`trigger()` and `dispatchEvent()`

This function is used to trigger an event on an EventTarget which will cause all listeners to run.

> Note: if 'click' is in `EventTarget.allowedEvents_`, trigger will attempt to call the `onClick` function if it exists.

```js
var foo = new EventTarget();
var handleBar = function() {
  console.log('bar was triggered');
};

foo.on('bar', handleBar);
foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('bar');
// logs 'bar was triggered'

foo.trigger('foo');
// does nothing
```

---

# Modal Dialogs | Video.js

**URL:** https://videojs.org/guides/modal-dialog/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Modal Dialogs

## Table of Contents

*   [Creating a ModalDialog](#creating-a-modaldialog)
    *   [Example Using createModal()](#example-using-createmodal)
    *   [Example Using the ModalDialog Constructor](#example-using-the-modaldialog-constructor)
*   [Styling Modals Independently](#styling-modals-independently)

The `ModalDialog` component is part of Video.js core and provides a baked-in UI for full-player overlays.

## [](/guides/modal-dialog/#creating-a-modaldialog)Creating a ModalDialog

Aside from the [built-in Video.js component-creation methods](/guides/components#creating-a-component), the player includes a `createModal()` helper method.

We'll demonstrate both approaches in this document by creating a modal that opens when the player becomes paused and resumes playback when it is closed.

### [](/guides/modal-dialog/#example-using-createmodal)Example Using `createModal()`

The `createModal()` method is intended for creating one-off modals that need to open for some temporary purpose. Therefore, they open themselves immediately upon creation and, by default, dispose themselves immediately upon closing.

```js
var player = videojs('my-player');

player.on('pause', function() {

  // Modals are temporary by default. They dispose themselves when they are
  // closed; so, we can create a new one each time the player is paused and
  // not worry about leaving extra nodes hanging around.
  var modal = player.createModal('This is a modal!');

  // When the modal closes, resume playback.
  modal.on('modalclose', function() {
    player.play();
  });
});
```

The `createModal()` method also takes a second argument - an object containing options for the modal. Refer to [the API documentation](https://docs.videojs.com/ModalDialog.html) for a full set of options.

### [](/guides/modal-dialog/#example-using-the-modaldialog-constructor)Example Using the `ModalDialog` Constructor

Unlike when using `createModal()`, a modal created with any of the [common component creation methods](/guides/components#creating-a-component) _does not_ open by default. This makes this approach better suited to modals that are expected to live in the DOM indefinitely.

```js
var player = videojs('my-player');
var ModalDialog = videojs.getComponent('ModalDialog');

var modal = new ModalDialog(player, {

  // We don't want this modal to go away when it closes.
  temporary: false
});

player.addChild(modal);

player.on('pause', function() {
  modal.open();
});

player.on('play', function() {
  modal.close();
});
```

Both of these examples are equivalent when it comes to the user's experience. Implementors should use whichever better suits their use-case.

## [](/guides/modal-dialog/#styling-modals-independently)Styling Modals Independently

A common need for modals is to style them independently from one another. The recommended approach for this is to add a custom class to your modal and target that using CSS:

```js
modal.addClass('vjs-my-fancy-modal');
```

---

# Hooks | Video.js

**URL:** https://videojs.org/guides/hooks/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Hooks

## Table of Contents

*   [Current Hooks](#current-hooks)
    *   [beforesetup](#beforesetup)
        *   [Example](#example)
    *   [setup](#setup)
        *   [Example](#example-1)
    *   [beforeerror](#beforeerror)
        *   [Example](#example-2)
    *   [error](#error)
        *   [Example](#example-3)
*   [Usage](#usage)
    *   [Adding](#adding)
        *   [Example](#example-4)
    *   [Adding Once](#adding-once)
        *   [Example](#example-5)
    *   [Getting](#getting)
        *   [Example](#example-6)
    *   [Removing](#removing)
        *   [Example](#example-7)

Hooks exist so that users can globally hook into certain Video.js lifecycle moments.

## [](/guides/hooks/#current-hooks)Current Hooks

Currently, the following hooks are available:

### [](/guides/hooks/#beforesetup)beforesetup

`beforesetup` occurs just before a player is created. This allows:

*   Modification of the options passed to the Video.js function (e.g., `videojs('some-id, options)`).
*   Modification of the DOM video element that will be used for the player that will be created.

`beforesetup` hook functions should:

*   Take two arguments:
    1.  `videoEl`: DOM `<video>` element that Video.js is going to use to create a player.
    2.  `options`: The options object that Video.js was called with and will be passed to the player during creation.
*   Return an options object that will be merged with the originally provided options.

#### [](/guides/hooks/#example)Example

```js
videojs.hook('beforesetup', function(videoEl, options) {

  // videoEl will be the video element with id="some-id" since that
  // gets passed to videojs() below. On subsequent calls, it will be
  // different.

  videoEl.className += ' some-super-class';

  // autoplay will be true here, since we passed it as such.
  if (options.autoplay) {
    options.autoplay = false
  }

  // Options that are returned here will be merged with old options.
  //
  // In this example options will now be:
  //   {autoplay: false, controls: true}
  //
  // This has the practical effect of always disabling autoplay no matter
  // what options are passed to videojs().
  return options;
});

// Create a new player.
videojs('some-id', {autoplay: true, controls: true});
```

### [](/guides/hooks/#setup)setup

`setup` occurs just after a player is created. This allows:

*   Plugins or other custom functionality to initialize on the player.
*   Changes to the player object itself.

`setup` hook functions:

*   Take one argument:
    1.  `player`: the player that Video.js created
*   Don't have to return anything

#### [](/guides/hooks/#example-1)Example

```js
videojs.registerPlugin('foo', function() {

  // This basic plugin will add the "some-super-class" class to a player.
  this.addClass('some-super-class');
});

videojs.hook('setup', function(player) {

  // Initialize the foo plugin after any player is created.
  player.foo();
});

// Create a new player.
videojs('some-id', {autoplay: true, controls: true});
```

### [](/guides/hooks/#beforeerror)beforeerror

`beforeerror` occurs just as we get an error on the player. This allows plugins or other custom code to intercept the error and modify it to be something else. `error` can be [one of multiple things](https://docs.videojs.com/mediaerror#MediaError), most commonly an object with a `code` property or `null` which means that the current error should be cleared.

`beforeerror` hook functions:

*   Take two arguments:
    1.  The `player` that the error is happening on.
    2.  The `error` object that was passed in.
*   Return an error object that should replace the error

#### [](/guides/hooks/#example-2)Example

```js
videojs.hook('beforeerror', function(player, err) {
  const error = player.error();

  // prevent current error from being cleared out
  if (err === null) {
    return error;
  }

  // but allow changing to a new error
  return err;
});
```

### [](/guides/hooks/#error)error

`error` occurs after the player has errored out, after `beforeerror` has allowed updating the error, and after an `error` event has been triggered on the player in question. It is purely an informative event which allows you to get all errors from all players.

`error` hook functions:

*   Take two arguments:
    1.  `player`: the player that the error occurred on
    2.  `error`: the Error object that was resolved with the `beforeerror` hooks
*   Don't have to return anything

#### [](/guides/hooks/#example-3)Example

```js
videojs.hook('error', function(player, err) {
  console.log(`player ${player.id()} has errored out with code ${err.code} ${err.message}`);
});
```

## [](/guides/hooks/#usage)Usage

### [](/guides/hooks/#adding)Adding

Hooks can be added using `videojs.hook(<name>, function)` before running the `videojs()` function.

#### [](/guides/hooks/#example-4)Example

```js
videojs.hook('beforesetup', function(videoEl, options) {
  // This hook will be called twice. Once for "vid1" and once for "vid2".
  // The options will match what is passed to videojs() for each of them.
});

videojs.hook('setup', function(player) {
  // This hook will be called twice. Once for "vid1" and once for "vid2".
  // The player value will be the player that is created for each element.
});

videojs('vid1', {autoplay: false});
videojs('vid2', {autoplay: true});
```

After adding your hooks, they will automatically be run at the correct time in the Video.js lifecycle.

### [](/guides/hooks/#adding-once)Adding Once

In some cases, you may only want your hook to run once. In these cases, use `videojs.hookOnce(<name>, function)` before running the `videojs()` function.

#### [](/guides/hooks/#example-5)Example

```js
videojs.hookOnce('beforesetup', function(videoEl, options) {
  // This hook will be called once for "vid1", but not for "vid2".
  // The options will match what is passed to videojs().
});

videojs.hookOnce('setup', function(player) {
  // This hook will be called once for "vid1", but not for "vid2".
  // The player value will be the player that is created for each element.
});

videojs('vid1', {autoplay: false});
videojs('vid2', {autoplay: true});
```

### [](/guides/hooks/#getting)Getting

To access the array of functions that currently exists for any hook, use the `videojs.hooks` function.

#### [](/guides/hooks/#example-6)Example

```js
// Get an array of all the 'beforesetup' hooks.
var beforeSetupHooks = videojs.hooks('beforesetup');

// Get an array of all the 'setup' hooks.
var setupHooks = videojs.hooks('setup');
```

### [](/guides/hooks/#removing)Removing

To stop hooks from being executed during any future Video.js lifecycles you can remove them using `videojs.removeHook`.

#### [](/guides/hooks/#example-7)Example

```js
var beforeSetup = function(videoEl, options) {};

// Add the hook.
videojs.hook('beforesetup', beforeSetup);

// Remove the same hook.
videojs.removeHook('beforesetup', beforeSetup);
```

---

# Playback Technology ("Tech") | Video.js

**URL:** https://videojs.org/guides/tech/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Playback Technology ("Tech")

## Table of Contents

*   [Building an API Wrapper](#building-an-api-wrapper)
*   [Required Methods](#required-methods)
*   [Required Events](#required-events)
*   [Optional Events (include if supported)](#optional-events-include-if-supported)
*   [Adding Playback Technology](#adding-playback-technology)
    *   [Tag Method:](#tag-method)
    *   [Object Method:](#object-method)
    *   [Posters](#posters)
*   [Technology Ordering](#technology-ordering)
*   [Flash Technology](#flash-technology)

Playback Technology refers to the specific browser or plugin technology used to play the video or audio. When using HTML5, the playback technology is the video or audio element. When using the [videojs-youtube](https://github.com/videojs/videojs-youtube) tech, the playback technology is the YouTube player. The tech also includes an API wrapper to translate between the Video.js controls and API to the specific playback technology used.

Essentially we're using html5 and plugins only as video decoders, and using HTML and JavaScript to create a consistent API and skinning experience across all of them.

In addition to techs there are source handlers. Source handlers add the capability to play additional source types to techs. For example, the [http-streaming](https://github.com/videojs/http-streaming) source handler (included with Video.js 7+ by default) enables the HTML5 tech to play HLS and DASH.

## [](/guides/tech/#building-an-api-wrapper)Building an API Wrapper

We'll write a more complete guide on writing a wrapper soon, but for now the best resource is the [Video.js](https://github.com/videojs/video.js/tree/main/src/js/tech) source where you can see how the HTML5 API wrapper is created.

## [](/guides/tech/#required-methods)Required Methods

canPlayType play pause currentTime volume duration buffered supportsFullScreen

## [](/guides/tech/#required-events)Required Events

loadstart play pause playing ended volumechange durationchange error

## [](/guides/tech/#optional-events-include-if-supported)Optional Events (include if supported)

timeupdate progress enterFullScreen exitFullScreen

## [](/guides/tech/#adding-playback-technology)Adding Playback Technology

When additional techs are added they are automatically added to the `techOrder`. You can modify the `techOrder` to change the priority of each tech.

### [](/guides/tech/#tag-method)Tag Method:

```html
<video data-setup='{"techOrder": ["html5", "other supported tech"]}'>
```

### [](/guides/tech/#object-method)Object Method:

```js
videojs("videoID", {
  techOrder: ["html5", "other supported tech"]
});
```

### [](/guides/tech/#posters)Posters

By default, techs will have to handle their own posters and are somewhat locked out of the player's poster lifecycle. However, when the player is initialized with the `techCanOverridePoster` option it will be possible for techs to integrate into that lifecycle and the player's `PosterImage` component to be used.

Techs can check if they have this capability by checking the `canOverridePoster` boolean in their options.

**`techCanOverridePoster` requirements**

*   `poster()` which returns the tech's current poster url
*   `setPoster()` which updates the tech's poster url and triggers a `posterchange` event which the player will handle

## [](/guides/tech/#technology-ordering)Technology Ordering

When Video.js is given an array of sources, which to use is determined by finding the first supported source / tech combination. Each tech will be queried in the order specified in `techOrder` whether it can play the first source. The first match wins. If no tech can play the first source, then the next will be tested. It's important to set the `type` of each source correctly for this test to be accurate.

> These examples use the obsolete [Flash tech](https://www.adobe.com/products/flashplayer/end-of-life.html) for illustration of tech ordering with techs which have a greater degree of overlap in sources they can play

For example, given the following video element, assuming the videojs-flash tech is available:

```html
<!-- "techOrder": ["html5", "flash"] -->
<video>
  <source src="http://your.static.provider.net/path/to/video.m3u8" type="application/x-mpegURL">
  <source src="http://your.static.provider.net/path/to/video.mp4" type="video/mp4">
</video>
```

The HLS source will be tested first. The first tech is html5.

*   Safari can play HLS in a standard HTML5 video element, so HLS will be played using the html5 tech.
*   Chrome can't play HLS in the standard HTML5 video element on its own, but the [http-streaming](https://github.com/videojs/http-streaming) source handler (included in Video.js 7+ by default) _can_ play HLS via [Media Source Extensions](https://en.wikipedia.org/wiki/Media_Source_Extensions) in HTML5. So HLS will be played in the html5 tech.
*   IE 10 can't play HLS natively, and doesn't support Media Source Extensions. As the source cannot be played in HTML5, the Flash tech will be tested.

Now take the same sources again but without videojs-flash:

```html
<!-- "techOrder": ["html5"] -->
<video>
  <source src="http://your.static.provider.net/path/to/video.m3u8" type="application/x-mpegURL">
  <source src="http://your.static.provider.net/path/to/video.mp4" type="video/mp4">
</video>
```

*   Safari can play HLS in a standard HTML5 video element, so HLS will be played using the html5 tech.
*   Chrome will play HLS in the html5 tech using the [http-streaming](https://github.com/videojs/http-streaming) source handler via [Media Source Extensions](https://en.wikipedia.org/wiki/Media_Source_Extensions).
*   IE 10 can't play HLS in either the html5 or Flash tech. Next the MP4 source will be tested. MP4 can be played by HTML5, so that source-tech pair will be used.

## [](/guides/tech/#flash-technology)Flash Technology

Flash is no longer supported as it has reached [end of life](https://www.adobe.com/products/flashplayer/end-of-life.html).

---

# Picture-in-Picture Options | Video.js

**URL:** https://videojs.org/guides/picture-in-picture/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Picture-in-Picture Options

## Table of Contents

*   [Picture-in-Picture Types](#picture-in-picture-types)
    *   [Video element PiP](#video-element-pip)
    *   [Document PiP](#document-pip)
    *   [Browser native PiP](#browser-native-pip)
*   [Options](#options)

Picture-in-picture (PiP) is a mode where the video is shown in a window on top of the browser, so the video can be watched while multitasking. Browsers have different PiP capabilities and the options available differ.

## [](/guides/picture-in-picture/#picture-in-picture-types)Picture-in-Picture Types

*   Video element PiP
*   Document PiP
*   Browser native - the browser's proprietary PiP implementation that is not controllable by API

### [](/guides/picture-in-picture/#video-element-pip)Video element PiP

This picture-in-picture mode is now available on most browsers but notably not Firefox. The video element can be put into a separate window.

This mode has limitations which may make it unsuitable for some use cases. Since only the video is in the PiP window, Video.js player controls will not be displayed, nor will emulated text tracks or any overlays or interactive elements. This mode is also not useful if the video source will change, especially for advertising. If needed, it [can be disabled](/guides/options/#disablepictureinpicture).

By default this mode is enabled if the browser supports the [picture-in-picture API](https://developer.mozilla.org/en-US/docs/Web/API/Picture-in-Picture_API). If the Document PiP mode is enabled on a browser that supports it, that will take precedence.

### [](/guides/picture-in-picture/#document-pip)Document PiP

_Added in v8.3.0_

[Document picture-in-picture](https://developer.chrome.com/docs/web-platform/document-picture-in-picture/) is an improved approach where the whole player element can be placed in a PiP window rather than just the video. This allows player controls, text tracks, overlays to be used.

Currently this is supported on Chrome and Edge 116 and above. The player at [videojs.com](/) will use this mode on supported browsers.

At this time this mode defaults to off, but [can be simply enabled with a player option](/guides/options/#enabledocumentpictureinpicture). If enabled, and supported by the browser, this takes prcedence over the video picture-in-picture mode.

### [](/guides/picture-in-picture/#browser-native-pip)Browser native PiP

Firefox does not implement the picture-in-picture API. Instead it has a proprietary picture-in-picture mode. It displays a PiP button on top of the video.

It is not possible to customize or remove this button programatically, nor is it possible to initiate PiP from a custom control. The Video.js picture-in-picture options have no effect.

## [](/guides/picture-in-picture/#options)Options

The video element PiP (vPiP) [`disablePictureInPicture`](/guides/options/#disablepictureinpicture) and document PiP (docPiP) [`enableDocumentPictureInPicture`](/guides/options/#enabledocumentpictureinpicture) options work independently of each other, so it's possible to use the improved document PiP mode on browsers that support it while disabling the video element PiP mode on browsers that don't.

| disablePictureInPicture | enableDocumentPictureInPicture | Effect\* |
| --- | --- | --- |
| `false` (default) | `false` (default) | vPiP used on browsers that support it. |
| `false` (default) | `true` | docPiP will be used if the browser supports it, otherwise vPiP used on browsers that support it. |
| `true` | `true` | docPiP will be used if the browser supports it. vPiP will not be used. |
| `true` | `false` (default) | Neither docPiP not vPiP will be used. |

_\* None of these options can have any effect on Firefox's behaviour._

---

# Middleware | Video.js

**URL:** https://videojs.org/guides/middleware/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Middleware

## Table of Contents

*   [Understanding Middleware](#understanding-middleware)
    *   [setSource](#setsource)
    *   [setTech](#settech)
    *   [Middleware Setters](#middleware-setters)
    *   [Middleware Getters](#middleware-getters)
    *   [Middleware Mediators](#middleware-mediators)
    *   [Termination and Mediators](#termination-and-mediators)
*   [Using Middleware](#using-middleware)
    *   [Terminating Mediator Methods](#terminating-mediator-methods)

Middleware is a Video.js feature that allows interaction with and modification of how the `Player` and `Tech` talk to each other. For more in-depth information, check out our [feature spotlight](https://videojs.com/blog/feature-spotlight-middleware/).

## [](/guides/middleware/#understanding-middleware)Understanding Middleware

Middleware are functions that return an object, a class instance, a prototype, etc, scoped to the Player with methods matching those on the `Tech`. There are currently a limited set of allowed methods that will be understood by middleware. These are: `buffered`, `currentTime`, `setCurrentTime`, `setMuted`, `setVolume`, `duration`, `muted`, `seekable`, `played`, `play`, `pause`, `paused` and `volume`. These allowed methods are split into three categories: [getters](/guides/middleware/#middleware-getters), [setters](/guides/middleware/#middleware-setters), and [mediators](/guides/middleware/#middleware-mediators).

There are a few special methods that affect middleware: `setSource` and `setTech`. These are called internally by Video.js when you call `player.src()`.

### [](/guides/middleware/#setsource)setSource

> _NOTE_: In versions of Video.js 7.0.5 and older, `setSource` was required for all middleware and had be included in the returned objects.

This method will setup the routing between a specific source and middleware and eventually sets the source on the `Tech`.

If your middleware is not manipulating, redirecting or rejecting the source, you may leave this method out on newer versions of Video.js. Doing so will select middleware implicitly.

In versions 7.0.5 and older, to get your middleware selected, you can pass along the source by doing the following:

```js
videojs.use('*', function(player) {
  return {
    setSource: function(srcObj, next) {
      // pass null as the first argument to indicate that the source is not rejected
      next(null, srcObj);
    }
  };
});
```

### [](/guides/middleware/#settech)setTech

`setTech` is a method that associates middleware with a specific `Tech` once it has been selected by the `Player`, after middleware make a decision on which source to set. This does not need to be included in your middleware.

### [](/guides/middleware/#middleware-setters)Middleware Setters

```text
+----------+                      +----------+
|          |  setter middleware   |          |
|          +---------------------->          |
|  Player  |                      |   Tech   |
|          <----------------------+          |
|          |  getter middleware   |          |
+----------+                      +----------+
```

Setters will be called on the `Player` first and run through middleware in the order they were registered in (from left to right in the diagram) before calling the method, with its arguments, on the `Tech`.

### [](/guides/middleware/#middleware-getters)Middleware Getters

Getters are called on the `Tech` first and are run though middleware in reverse of the order they were registered in (from right to left in the diagram) before returning the result to the `Player`.

### [](/guides/middleware/#middleware-mediators)Middleware Mediators

Mediators are methods that not only change the state of the `Tech`, but also return some value back to the `Player`. Currently, these are `play` and `pause`.

Mediators are called on the `Player` first, run through middleware in the order they were registered (from left to right in the below diagram), then called on the `Tech`. The result is returned to the `Player` unchanged, while calling the middleware in the reverse order of how they were registered (from right to left in the diagram.) For more information on mediators, check out the [mediator section](/guides/middleware/#termination-and-mediators).

```text
+----------+                      +----------+
|          |                      |          |
|          +---mediate-to-tech---->          |
|  Player  |                      |   Tech   |
|          <--mediate-to-player---+          |
|          |                      |          |
+----------+                      +----------+
```

### [](/guides/middleware/#termination-and-mediators)Termination and Mediators

Mediators make a round trip: starting at the `Player`, mediating to the `Tech` and returning the result to the `Player` again. A `call{method}` method must be supplied by the middleware which is used when mediating to the `Tech`. On the way back to the `Player`, the `{method}` will be called instead, with 2 arguments: `terminated`, a Boolean indicating whether a middleware terminated during the mediation to the tech portion, and `value`, which is the value returned from the `Tech`.

```text
+----------+                      +----------+
|          |                      |          |
|          +----+call{method}+---->          |
|  Player  |                      |   Tech   |
|          <------+{method}+------+          |
|          |                      |          |
+----------+                      +----------+
```

A skeleton of a middleware with Mediator methods is given below:

```js
var myMiddleware = function(player) {
  return {
    callPlay: function() {
      // mediating to the Tech
      ...
    },
    play: function(terminated, value) {
      // mediating back to the Player
      ...
    },
    ...
  };
};
```

Middleware termination occurs when a middleware method decides to stop mediating to the `Tech`. We'll see more examples of this in the [next section](/guides/middleware/#terminating-mediator-methods).

## [](/guides/middleware/#using-middleware)Using Middleware

Middleware are registered to a video MIME type, and will be run for any source with that type.

```js
videojs.use('video/mp4', myMiddleware);
```

You can also register a middleware on all sources by registering it on `*`.

```js
videojs.use('*', myMiddleware);
```

Your middleware should be a function that is scoped to a player and returns an object, class instance, etc, with methods on it that match those on the `Tech`. An example of a middleware that returns an object is below:

```js
var myMiddleware = function(player) {
  return {
    setSource: function(srcObj, next) {
      // pass null as the first argument to indicate that the source is not rejected
      next(null, srcObj);
    },
    currentTime: function(ct) {
      return ct / 2;
    },
    setCurrentTime: function(time) {
      return time * 2;
    }
  };
};

videojs.use('*', myMiddleware);
```

And the same example with `setSource` omitted:

```js
var myMiddleware = function(player) {
  return {
    currentTime: function(ct) {
      return ct / 2;
    },
    setCurrentTime: function(time) {
      return time * 2;
    }
  };
};

videojs.use('*', myMiddleware);
```

This middleware gives the appearance of the video source playing at double its speed, by halving the time we _get_ from the `Tech`, and doubling the time we _set_ on the `Tech`.

An example of a middleware that uses Mediator methods is below:

```js
var myMiddleware = function(player) {
  return {
    setSource: function(srcObj, next) {
      // pass null as the first argument to indicate that the source is not rejected
      next(null, srcObj);
    },
    callPlay: function() {
      // Do nothing, thereby allowing play() to be called on the Tech
    },
    play: function(terminated, value) {
      if (terminated) {
        console.log('The play was middleware terminated.');

      // the value is a play promise
      } else if (value && value.then) {
        value
          .then(function() {
            console.log('The play succeeded!')
          })
          .catch(function (err) {
            console.log('The play was rejected', err);
          });
      }
    }
  };
};

videojs.use('*', myMiddleware);
```

This middleware allows the call to `play()` to go through to the `Tech`, and checks in `play` whether the play succeeded or not. A more detailed example can be found in our [sandbox](https://github.com/videojs/video.js/blob/main/sandbox/middleware-play.html.example).

### [](/guides/middleware/#terminating-mediator-methods)Terminating Mediator Methods

Mediator methods can terminate, by doing the following:

```js
var myMiddleware = function(player) {
  return {
    setSource: function(srcObj, next) {
      // pass null as the first argument to indicate that the source is not rejected
      next(null, srcObj);
    },
    callPlay: function() {
      // Terminate by returning the middleware terminator
      return videojs.middleware.TERMINATOR;
    },
    play: function(terminated, value) {
      // the terminated argument should be true here.
      if (terminated) {
        console.log('The play was middleware terminated.');
      }
    }
  };
};

videojs.use('*', myMiddleware);
```

This middleware always terminates calls to `play()` by returning the `TERMINATOR` in `callPlay`. In `play` we are able to see that the call to `play()` was terminated and was never called on the `Tech`.

---

# Spatial Navigation | Video.js

**URL:** https://videojs.org/guides/spatial-navigation/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Spatial Navigation

## Table of Contents

*   [Spatial Navigation Class](#spatial-navigation-class)
    *   [Methods](#methods)
*   [Video.js Options Reference - spatialNavigation](#videojs-options-reference---spatialnavigation)
    *   [Properties:](#properties)
*   [Enable Spatial Navigation](#enable-spatial-navigation)
*   [Start Spatial Navigation](#start-spatial-navigation)
*   [Spatial Navigation Events](#spatial-navigation-events)
    *   [focusableComponentsChanged](#focusablecomponentschanged)
    *   [endOfFocusableComponents](#endoffocusablecomponents)

Spatial Navigation in Video.js enhances user experience and accessibility on smart TV devices. This functionality enables seamless navigation through interactive elements within the player using remote control arrow keys.

## [](/guides/spatial-navigation/#spatial-navigation-class)Spatial Navigation Class

The Spatial Navigation Class within Video.js offers essential functionality, allowing users to effortlessly navigate through focusable components.

### [](/guides/spatial-navigation/#methods)Methods

*   `start()` - Starts the Spatial Navigation system by adding keydown event listeners to the player.
*   `stop()` - Stops the Spatial Navigation by removing the keydown event listener from the player and updating the internal state.
*   `pause()` - Temporarily disables the Spatial Navigation functionality without removing the event listeners.
*   `resume()` - Re-enables the Spatial Navigation functionality after it has been paused.
*   `updateFocusableComponents()` - Updates and retrieves the list of focusable components within the player.
*   `findSuitableDOMChild(component)` - Finds a suitable child element within a component.
*   `getCurrentComponent()` - Retrieves the currently focused component.
*   `add(component)` - Adds a new component to the focusable components list if it meets the focusability criteria.
*   `remove(component)` - Removes a specified component from the focusable components list.
*   `clear()` - Clears the list of focusable components.
*   `move(direction)` - Navigates to the next focusable component based on the specified direction.
*   `refocusComponent()` - Focuses on the last focused component.
*   `focus(component)` - Sets focus on a specific component if it is focusable, or finds a focusable child within it to focus on.

**Difference between Stop and Pause**

On a technical level `stop()` removes the event listener `onKeyDown` added by the spatial-navigation when the `start()` function is called, whereas `pause()` manages a flag in the `onKeyDown` handler function: when `pause()` is true the `move()` function is not called inside that event listener.

## [](/guides/spatial-navigation/#videojs-options-reference---spatialnavigation)Video.js Options Reference - spatialNavigation

To configure Spatial Navigation within Video.js, you can utilize the following option:

`spatialNavigation`

> Type: `Object` Default: `{enabled:false, horizontalSeek:false}`

Enables Spatial Navigation and specifies additional properties.

### [](/guides/spatial-navigation/#properties)Properties:

*   `enabled`
    
    > Type: `boolean`, Default: `false`
    
    Enables Spatial Navigation within the player.
    
*   `horizontalSeek`
    
    > Type: `boolean`, Default: `false`
    
    Enables horizontal navigation seek functionality, using right and left RCU arrow keys.
    

## [](/guides/spatial-navigation/#enable-spatial-navigation)Enable Spatial Navigation

If you are already using any React/Angular/Vue/other spatial-navigation solution, you should just enable Spatial Navigation in Video.js using the following code:

```js
var player = videojs('my-player', {
  spatialNavigation: {
    enabled: true,
    horizontalSeek: true
  }
});
```

This will instantiate the SpatialNavigation class.

## [](/guides/spatial-navigation/#start-spatial-navigation)Start Spatial Navigation

In case you don’t use any React/Angular/Vue/other spatial-navigation solution, you must also start the Spatial Navigation. In this way Spatial Navigation will start listening for keydown events within the Video.js player.

```js
var player = videojs('my-player');

player.ready(function() {
  player.spatialNavigation.start();
});
```

## [](/guides/spatial-navigation/#spatial-navigation-events)Spatial Navigation Events

Spatial Navigation provides two custom events that you can listen to:

### [](/guides/spatial-navigation/#focusablecomponentschanged)focusableComponentsChanged

```js
var player = videojs('my-player');

player.ready(function() {
  player.spatialNavigation.on('focusableComponentsChanged', event => {
    console.log('Focusable elements changed:', event.focusableComponents);
  });
});
```

### [](/guides/spatial-navigation/#endoffocusablecomponents)endOfFocusableComponents

This event serves as a notification to the developer or the application when there are no more focusable components available in the desired direction within the player interface. By detecting this event, developers can implement logic to seamlessly transition focus to alternative elements, ensuring a smooth and intuitive user experience beyond the confines of the player interface.

```js
var player = videojs('my-player');

player.ready(function() {
  // Add an event listener to check when the player has no more element to focus
  player.spatialNavigation.on('endOfFocusableComponents', event => {
    // Your logic here
  });
});
```

---

# Angular and Video.js | Video.js

**URL:** https://videojs.org/guides/angular/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Angular and Video.js

This is a basic Angular and Video.js player implementation. This example component instantiates the player on `OnInit` and destroys it on `OnDestroy`:

```ts
import {Component, ElementRef, Input, OnDestroy, OnInit, ViewChild, ViewEncapsulation} from '@angular/core';
import videojs from 'video.js';

@Component({
  selector: 'app-vjs-player',
  template: `
    <video #target class="video-js" controls muted playsinline preload="none"></video>
  `,
  styleUrls: [
    './vjs-player.component.css'
  ],
  encapsulation: ViewEncapsulation.None,
})

export class VjsPlayerComponent implements OnInit, OnDestroy {
  @ViewChild('target', {static: true}) target: ElementRef;

  // See options: https://videojs.com/guides/options
  @Input() options: {
      fluid: boolean,
      aspectRatio: string,
      autoplay: boolean,
      sources: {
          src: string,
          type: string,
      }[],
  };

  player: videojs.Player;

  constructor(
    private elementRef: ElementRef,
  ) {}

  // Instantiate a Video.js player OnInit
  ngOnInit() {
    this.player = videojs(this.target.nativeElement, this.options, function onPlayerReady() {
      console.log('onPlayerReady', this);
    });
  }

  // Dispose the player OnDestroy
  ngOnDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  }
}
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```html
<app-vjs-player [options]="{autoplay: true, controls: true, sources: [{ src: '/path/to/video.mp4', type: 'video/mp4' }]}"></app-vjs-player>
```

Don't forget to include the Video.js CSS, located at `video.js/dist/video-js.css`!

---

# React and Video.js | Video.js

**URL:** https://videojs.org/guides/react/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# React and Video.js

## Table of Contents

*   [React Functional Component and useEffect Example](#react-functional-component-and-useeffect-example)
*   [React Class Component Example](#react-class-component-example)
*   [Using a React Component within a Video.js Component](#using-a-react-component-within-a-videojs-component)

These are several React and Video.js player implementations and examples.

Don't forget to include the Video.js CSS, located at `video.js/dist/video-js.css`!

## [](/guides/react/#react-functional-component-and-useeffect-example)React Functional Component and `useEffect` Example

```jsx
import React from 'react';
import videojs from 'video.js';
import 'video.js/dist/video-js.css';

export const VideoJS = (props) => {
  const videoRef = React.useRef(null);
  const playerRef = React.useRef(null);
  const {options, onReady} = props;

  React.useEffect(() => {

    // Make sure Video.js player is only initialized once
    if (!playerRef.current) {
      // The Video.js player needs to be _inside_ the component el for React 18 Strict Mode. 
      const videoElement = document.createElement("video-js");

      videoElement.classList.add('vjs-big-play-centered');
      videoRef.current.appendChild(videoElement);

      const player = playerRef.current = videojs(videoElement, options, () => {
        videojs.log('player is ready');
        onReady && onReady(player);
      });

    // You could update an existing player in the `else` block here
    // on prop change, for example:
    } else {
      const player = playerRef.current;

      player.autoplay(options.autoplay);
      player.src(options.sources);
    }
  }, [options, videoRef]);

  // Dispose the Video.js player when the functional component unmounts
  React.useEffect(() => {
    const player = playerRef.current;

    return () => {
      if (player && !player.isDisposed()) {
        player.dispose();
        playerRef.current = null;
      }
    };
  }, [playerRef]);

  return (
    <div data-vjs-player>
      <div ref={videoRef} />
    </div>
  );
}

export default VideoJS;
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```jsx
import React from 'react';

// This imports the functional component from the previous sample.
import VideoJS from './VideoJS'

const App = () => {
  const playerRef = React.useRef(null);

  const videoJsOptions = {
    autoplay: true,
    controls: true,
    responsive: true,
    fluid: true,
    sources: [{
      src: '/path/to/video.mp4',
      type: 'video/mp4'
    }]
  };

  const handlePlayerReady = (player) => {
    playerRef.current = player;

    // You can handle player events here, for example:
    player.on('waiting', () => {
      videojs.log('player is waiting');
    });

    player.on('dispose', () => {
      videojs.log('player will dispose');
    });
  };

  return (
    <>
      <div>Rest of app here</div>
      <VideoJS options={videoJsOptions} onReady={handlePlayerReady} />
      <div>Rest of app here</div>
    </>
  );
}
```

## [](/guides/react/#react-class-component-example)React Class Component Example

This example component instantiates the Video.js player on `componentDidMount` and destroys it on `componentWillUnmount`.

```jsx
import React from 'react';
import videojs from 'video.js';
import 'video.js/dist/video-js.css';

export default class VideoPlayer extends React.Component {

  // Instantiate a Video.js player when the component mounts
  componentDidMount() {
    this.player = videojs(this.videoNode, this.props, () => {
      videojs.log('onPlayerReady', this);
    });
  }

  // Dispose the player when the component will unmount
  componentWillUnmount() {
    if (this.player) {
      this.player.dispose();
    }
  }

  // Wrap the player in a `div` with a `data-vjs-player` attribute, so Video.js
  // won't create additional wrapper in the DOM.
  //
  // See: https://github.com/videojs/video.js/pull/3856
  render() {
    return (
      <div data-vjs-player>
        <video ref={node => this.videoNode = node} className="video-js"></video>
      </div>
    );
  }
}
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```jsx
const videoJsOptions = {
  autoplay: true,
  controls: true,
  sources: [{
    src: '/path/to/video.mp4',
    type: 'video/mp4'
  }]
}

return <VideoPlayer {...videoJsOptions} />
```

## [](/guides/react/#using-a-react-component-within-a-videojs-component)Using a React Component within a Video.js Component

This example demonstrates using a React component within a Video.js component inside a Video.js player. Through this approach, developers can manage their custom Video.js components through React.

First, a normal React component is created:

```jsx
import {Component} from 'react';

export default class ExampleReactComponent extends Component {
  render() {
    return (
      <div>{this.props.text}</div>
    );
  }
};
```

Within this component, the `vjsBridgeComponent` is available on its `props`. Through this object, methods of the `vjsBridgeComponent` are available.

The Video.js player can be referenced within this React component via the same means:

```jsx
const player = this.props.vjsBridgeComponent.player();
```

Next, a Video.js component is created.

This component renders the React component into itself. Basically, the Video.js component is acting as a bridge between the Video.js player and the React component:

```jsx
import ExampleReactComponent from './example-react-component';
import ReactDOM from 'react-dom';
import videojs from 'video.js';

const VjsComponent = videojs.getComponent('Component');

class ExampleVjsBridgeComponent extends VjsComponent {

  constructor(player, options) {
    super(player, options);

    // Bind the current class context to the mountReactComponent method
    this.mountReactComponent = this.mountReactComponent.bind(this);

    // When player is ready, call method to mount the React component
    player.ready(() => this.mountReactComponent());

    // Remove the React root when this component is destroyed
    this.on('dispose', () => ReactDOM.unmountComponentAtNode(this.el()));
  }

  // This method renders the ExampleReactComponent into the DOM element of
  // the Video.js component, `this.el()`.
  mountReactComponent() {
    ReactDOM.render(
      <ExampleReactComponent vjsBridgeComponent={this} text='Example React Component' />,
      this.el()
    );
  }
}

// Make sure to register the Video.js component so Video.js knows it exists
videojs.registerComponent('exampleVjsBridgeComponent', ExampleVjsBridgeComponent);

export default ExampleVjsBridgeComponent;
```

Finally, the Video.js bridge component can be added to the player like so:

```jsx

// ...

  // Instantiate a Video.js player when the component mounts
  componentDidMount() {
    this.player = videojs(this.videoNode, this.props, () => {
      videojs.log('onPlayerReady', this);
    });

    // Add the ExampleVjsBridgeComponent as a child of the player (or
    // of another component within the player, such as the control bar).
    //
    // You can pass options to your bridge component using the second argument
    // to this method.
    this.player.addChild('exampleVjsBridgeComponent', {});
  }

// ...
```

---

# Webpack and Video.js | Video.js

**URL:** https://videojs.org/guides/webpack/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Webpack and Video.js

## Table of Contents

*   [Video.js CSS:](#videojs-css)

Video.js and official libraries and plugins work in a Webpack-based build environment, however some configuration may be needed to ensure code that is executed in workers is not broken by transpilation.

The solutions [documented by the Mapbox project](https://docs.mapbox.com/mapbox-gl-js/guides/install/#targeting-transpilation-to-es6-with-browserslist) apply:

1.  Either set the production `browserslist` to

```text
">0.2%",
"not dead",
"not op_mini all",
"not safari < 10",
"not chrome < 51",
"not android < 5",
"not ie < 12"
```

2.  Or import using the ! syntax

```js
// eslint-disable-next-line import/no-webpack-loader-syntax
import videojs from "!video.js";
```

## [](/guides/webpack/#videojs-css)Video.js CSS:

You may need to add [`style-loader`](https://webpack.js.org/loaders/style-loader/) to your Webpack configuration.

Then add the CSS that the player requires, add the following to the file where the player is also included or initialized:

```js
require('!style-loader!css-loader!video.js/dist/video-js.css')
```

---

# Text Tracks | Video.js

**URL:** https://videojs.org/guides/text-tracks/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Text Tracks

## Table of Contents

*   [A Note on "Remote" Text Tracks](#a-note-on-remote-text-tracks)
*   [Creating the Text File](#creating-the-text-file)
*   [Adding Text Tracks to Video.js](#adding-text-tracks-to-videojs)
    *   [track Attributes](#track-attributes)
        *   [kind](#kind)
        *   [label](#label)
        *   [default](#default)
        *   [srclang](#srclang)
    *   [Text Tracks from Another Domain](#text-tracks-from-another-domain)
*   [Working with Text Tracks](#working-with-text-tracks)
    *   [Showing Tracks Programmatically](#showing-tracks-programmatically)
    *   [Listen for a Cue Becoming Active](#listen-for-a-cue-becoming-active)
*   [Emulated Text Tracks](#emulated-text-tracks)
    *   [Text Track Settings](#text-track-settings)
*   [Text Track Precedence](#text-track-precedence)
*   [API](#api)
    *   [Remote Text Tracks](#remote-text-tracks)
    *   [Text Tracks](#text-tracks)

Text tracks are a feature of HTML5 for displaying time-triggered text to the end-user. Video.js offers a cross-browser implementation of text tracks.

## [](/guides/text-tracks/#a-note-on-remote-text-tracks)A Note on "Remote" Text Tracks

Video.js refers to so-called "remote" text tracks. This is a convenient term for tracks that have an associated `<track>` element rather than those that do not.

Either can be created programmatically, but _only remote text tracks can be removed from a player._ For that reason, we recommend _only_ using remote text tracks.

## [](/guides/text-tracks/#creating-the-text-file)Creating the Text File

Timed text requires a text file in [WebVTT](https://dev.w3.org/html5/webvtt/) format. This format defines a list of "cues" that have a start time, an end time, and text to display. [Microsoft has a builder](https://dev.modern.ie/testdrive/demos/captionmaker/) that can help you get started on the file.

> **Note:** When creating captions, there are additional [caption formatting techniques](https://www.theneitherworld.com/mcpoodle/SCC_TOOLS/DOCS/SCC_FORMAT.HTML#style) to make captions more meaningful, like brackets around sound effects (e.g. `[ birds chirping ]`).
> 
> For a more in depth style guide for captioning, see the [Captioning Key](https://www.dcmp.org/captioningkey/), but keep in mind not all features are supported by WebVTT or (more likely) the Video.js WebVTT implementation.

## [](/guides/text-tracks/#adding-text-tracks-to-videojs)Adding Text Tracks to Video.js

Once you have your WebVTT files created, you can add them to your `video` element using the `track` tag. Similar to `source` elements, `track` elements should be added as children of the `video` element:

```html
<video
  class="video-js"
  controls
  preload="auto"
  width="640"
  height="264"
  data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
  <track kind="captions" src="//example.com/path/to/captions.vtt" srclang="en" label="English" default>
</video>
```

Video.js will automatically read `track` elements from the `video` element. Tracks (remote and non-remote) can also be added programmatically.

### [](/guides/text-tracks/#track-attributes)`track` Attributes

#### [](/guides/text-tracks/#kind)`kind`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#text-track-kind)

One of the track types supported by Video.js:

*   `"subtitles"` (default): Translations of the dialogue in the video for when audio is available but not understood. Subtitles are shown over the video.
*   `"captions"`: Transcription of the dialogue, sound effects, musical cues, and other audio information for viewer who are deaf/hard of hearing, or the video is muted. Captions are also shown over the video.
*   `"chapters"`: Chapter titles that are used to create navigation within the video. Typically, these are in the form of a list of chapters that the viewer can use to navigate the video.
*   `"descriptions"`: Text descriptions of the action in the content for when the video portion isn't available or because the viewer is blind or not using a screen. Descriptions are read by a screen reader or turned into a separate audio track.
*   `"metadata"`: Tracks that have data meant for JavaScript to parse and do something with. These aren't shown to the user.

#### [](/guides/text-tracks/#label)`label`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#text-track-label)

Short descriptive text for the track that will used in the user interface. For example, in a menu for selecting a captions language.

#### [](/guides/text-tracks/#default)`default`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-track-default)

The boolean `default` attribute can be used to indicate that a track's mode should start as `"showing"`. Otherwise, the viewer would need to select their language from a captions or subtitles menu.

> **Note:** For chapters, `default` is required if you want the chapters menu to show.

#### [](/guides/text-tracks/#srclang)`srclang`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-track-srclang)

The valid [BCP 47](https://tools.ietf.org/html/bcp47) code for the language of the text track, e.g. `"en"` for English or `"es"` for Spanish.

For supported language translations, please see the [languages folder (/lang)](https://github.com/videojs/video.js/tree/main/lang) folder located in the Video.js root and refer to the [languages guide](/guides/languages) for more information on languages in Video.js.

### [](/guides/text-tracks/#text-tracks-from-another-domain)Text Tracks from Another Domain

Because Video.js loads the text track file via JavaScript, the [same-origin policy](https://en.wikipedia.org/wiki/Same_origin_policy) applies. If you'd like to have a player served from one domain, but the text track served from another, you'll need to [enable CORS](https://enable-cors.org/) on the server that is serving your text tracks.

In addition to enabling CORS, you will need to add the [`crossorigin` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_settings_attributes) to the video element itself. This attribute has two possible values `"anonymous"` and `"use-credentials"`. Most users will want to use `"anonymous"` with cross-origin tracks:

```html
<video class="video-js" crossorigin="anonymous">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <track src="//example.com/oceans.vtt" kind="captions" srclang="en" label="English">
</video>
```

One thing to be aware of is that the video files themselves will _also_ need CORS headers. This is because some browsers apply the `crossorigin` attribute to the video source itself and not just the tracks. This is considered a [security concern by the spec](https://html.spec.whatwg.org/multipage/embedded-content.html#security-and-privacy-considerations).

## [](/guides/text-tracks/#working-with-text-tracks)Working with Text Tracks

### [](/guides/text-tracks/#showing-tracks-programmatically)Showing Tracks Programmatically

Certain use cases call for turning captions on and off programmatically rather than forcing the user to do so themselves. This can be easily achieved by modifying the `mode` property of the text tracks.

The `mode` can be one of three values `"disabled"`, `"hidden"`, and `"showing"`. When a text track's `mode` is `"disabled"`, the track does not show on screen as the video is playing.

When the `mode` is set to `"showing"`, the track is visible to the viewer and updates while the video is playing.

```js
// Get all text tracks for the current player.
var tracks = player.textTracks();

for (var i = 0; i < tracks.length; i++) {
  var track = tracks[i];

  // Find the English captions track and mark it as "showing".
  if (track.kind === 'captions' && track.language === 'en') {
    track.mode = 'showing';
  }
}
```

### [](/guides/text-tracks/#listen-for-a-cue-becoming-active)Listen for a Cue Becoming Active

One of the supported values for `mode` is `"hidden"`. This `mode` means that the track will update as the video is playing, but it won't be visible to the viewer. This is most useful for tracks where `kind="metadata"`.

A common use case for metadata text tracks is to use them to trigger behaviors when their cues become active. For this purpose, tracks emit a `"cuechange"` event.

```js
// Get all text tracks for the current player.
var tracks = player.textTracks();
var metadataTrack;

for (var i = 0; i < tracks.length; i++) {
  var track = tracks[i];

  // Find the metadata track that's labeled "ads".
  if (track.kind === 'metadata' && track.label === 'ads') {
    track.mode = 'hidden';

    // Store it for usage outside of the loop.
    metadataTrack = track;
  }
}

// Add a listener for the "cuechange" event and start ad playback.
metadataTrack.addEventListener('cuechange', function() {
  player.ads.startLinearAdMode();
});
```

## [](/guides/text-tracks/#emulated-text-tracks)Emulated Text Tracks

By default, Video.js will use native text tracks and fall back to emulated text tracks if the native functionality is broken, incomplete, or non-existent.

The Video.js API and TextTrack objects were modeled after the W3C specification. Video.js uses [Mozilla's vtt.js](https://github.com/mozilla/vtt.js) library to parse and display emulated text tracks.

To disable native text track functionality and force Video.js to use emulated text tracks always, the `nativeTextTracks` option can be passed to a tech:

```js
// Create a player, passing `nativeTextTracks: false` to the HTML5 tech.
var player = videojs('myvideo', {
  html5: {
    nativeTextTracks: false
  }
});
```

### [](/guides/text-tracks/#text-track-settings)Text Track Settings

When using emulated text tracks, captions will have an additional item in the menu called "Caption Settings". This allows the user to alter how captions are styled on screen.

This feature can be disabled by turning off the `TextTrackSettings` component and hiding the menu item.

```js
var player = videojs('myvideo', {
  // Make the text track settings dialog not initialize.
  textTrackSettings: false
});
```

```css
/* Hide the captions settings item from the captions menu. */
.vjs-texttrack-settings {
  display: none;
}
```

## [](/guides/text-tracks/#text-track-precedence)Text Track Precedence

In general, `"descriptions"` tracks are of lower precedence than `"captions"` and `"subtitles"`. What this mean for developers using Video.js?

*   If you are using the `default` attribute, Video.js will choose the first track that is marked as `default` and turn it on. If there are multiple tracks marked `default`, it will turn on the first `"captions"` or `"subtitles"` track _before_ any `"descriptions"` tracks.
    *   This only applied to the emulated text track support, native text tracks behavior will change depending on the browser.
*   If a track is selected from the menu, Video.js will turn off all the other tracks of the same kind. While this suggests Video.js supports both `"subtitles"` and `"captions"` being turned on simultaneously, this is currently not the case; Video.js only supports one track being displayed at a time.
    *   This means that for emulated text tracks, Video.js will display the first enabled `"subtitles"` or `"captions"` track.
    *   When native text tracks are supported, other tracks of the same kind will still be disabled, but it is possible that multiple text tracks are shown.
    *   If a `"descriptions"` track is selected and subsequently a `"subtitles"` or `"captions"` track is selected, the `"descriptions"` track is disabled and its menu button is also disabled.
*   When enabling a track programmatically, Video.js performs minimal enforcement.
    *   For emulated text tracks, Video.js chooses the first track that's `"showing"` - again choosing `"subtitles"` or `"captions"` over `"descriptions"`.
    *   For native text tracks, this behavior depends on the browser. Some browsers will allow multiple text tracks, but others will disable all other tracks when a new one is selected.

## [](/guides/text-tracks/#api)API

For more complete information, refer to the [Video.js API docs](https://docs.videojs.com/).

### [](/guides/text-tracks/#remote-text-tracks)Remote Text Tracks

As mentioned [above](/guides/text-tracks/#a-note-on-remote-text-tracks), remote text tracks represent the recommended API offered by Video.js as they can be removed.

*   `Player#remoteTextTracks()`
    
*   `Player#remoteTextTrackEls()`
    
*   `Player#addRemoteTextTrack(Object options)`
    
    Available options are the same as the [available `track` attributes](/guides/text-tracks/#track-attributes). And `language` is a supported option as an alias for the `srclang` attribute - either works here.
    
    **Note**: If you need a callback, instead of a callback you could use the technique below:
    
    ```js
    const trackEl = player.addRemoteTextTrack({src: 'en.vtt'}, false);
    trackEl.addEventListener('load', function() {
      // your callback goes here
    });
    ```
    
*   `Player#removeRemoteTextTrack(HTMLTrackElement|TextTrack)`
    

### [](/guides/text-tracks/#text-tracks)Text Tracks

It is generally recommended that you use _remote_ text tracks rather than these purely programmatic text tracks for the majority of use-cases.

*   `Player#textTracks()`
    
*   `Player#addTextTrack(String kind, [String label [, String language]])`
    
    > **Note:** Non-remote text tracks are intended for _purely programmatic usage_ of tracks and have the important limitation that they _cannot be removed once created_.
    > 
    > The standard `addTextTrack` does **not** have a corresponding `removeTextTrack` method; so, we actually discourage the use of this method!
    
*   `TextTrackList()`
    
*   `TextTrack()`

---

# Vue and Video.js | Video.js

**URL:** https://videojs.org/guides/vue/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Vue and Video.js

This is a basic Vue and Video.js player implementation. This example component instantiates the player on `mounted` and destroys it on `beforeDestroy`:

```jsx
<template>
  <div>
    <video ref="videoPlayer" class="video-js"></video>
  </div>
</template>

<script>
import videojs from 'video.js';

export default {
  name: 'VideoPlayer',
  props: {
    options: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  data() {
    return {
      player: null
    }
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, this.options, () => {
      this.player.log('onPlayerReady', this);
    });
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  }
}
</script>
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```jsx
<template>
  <div>
    <video-player :options="videoOptions" />
  </div>
</template>

<script>
import VideoPlayer from '@/components/VideoPlayer.vue';

export default {
  name: 'VideoExample',
  components: {
    VideoPlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: true,
        controls: true,
        sources: [
          {
            src:
              '/path/to/video.mp4',
              type: 'video/mp4'
          }
        ]
      }
    };
  }
};
</script>
```

Don't forget to include the Video.js CSS, located at `video.js/dist/video-js.css`!

---

# Audio Tracks | Video.js

**URL:** https://videojs.org/guides/audio-tracks/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Audio Tracks

## Table of Contents

*   [Caveats](#caveats)
*   [Working with Audio Tracks](#working-with-audio-tracks)
    *   [Add an Audio Track to the Player](#add-an-audio-track-to-the-player)
    *   [Listen for an Audio Track Becoming Enabled](#listen-for-an-audio-track-becoming-enabled)
    *   [Removing an Audio Track from the Player](#removing-an-audio-track-from-the-player)
*   [API](#api)
    *   [videojs.AudioTrack](#videojsaudiotrack)
        *   [id](#id)
        *   [kind](#kind)
        *   [label](#label)
        *   [language](#language)
        *   [enabled](#enabled)

Audio tracks are a feature of HTML5 video for providing alternate audio track selections to the user, so that a track other than the main track can be played. Video.js offers a cross-browser implementation of audio tracks, providing the playback technology supports audio tracks.

Audio tracks are supported in Video.js's MSE playback engine for HLS and DASH. Safari also supports audio tracks for native playback of HLS and MP4. **Other browsers do not support audio tracks for native playback including MP4**, so it is not possible to work with MP4 audio tracks in Chrome or Firefox for example.

## [](/guides/audio-tracks/#caveats)Caveats

*   It is not possible to add audio tracks through HTML like you can with text tracks. They must be added programmatically.
*   Video.js only stores track representations. Switching audio tracks for playback is _not handled by Video.js_ and must be handled elsewhere - for example, [http-streaming](https://github.com/videojs/http-streaming) handles switching audio tracks to support track selection through the UI.

## [](/guides/audio-tracks/#working-with-audio-tracks)Working with Audio Tracks

### [](/guides/audio-tracks/#add-an-audio-track-to-the-player)Add an Audio Track to the Player

```js
// Create a player.
var player = videojs('my-player');

// Create a track object.
var track = new videojs.AudioTrack({
  id: 'my-spanish-audio-track',
  kind: 'translation',
  label: 'Spanish',
  language: 'es'
});

// Add the track to the player's audio track list.
player.audioTracks().addTrack(track);
```

### [](/guides/audio-tracks/#listen-for-an-audio-track-becoming-enabled)Listen for an Audio Track Becoming Enabled

When a track is enabled or disabled on an `AudioTrackList`, a `change` event will be fired. You can listen for that event and do something with it.

> NOTE: The initial `AudioTrack` selection (usually the main track that is selected) should not fire a `change` event.

```js
// Get the current player's AudioTrackList object.
var audioTrackList = player.audioTracks();

// Listen to the "change" event.
audioTrackList.addEventListener('change', function() {

  // Log the currently enabled AudioTrack label.
  for (var i = 0; i < audioTrackList.length; i++) {
    var track = audioTrackList[i];

    if (track.enabled) {
      videojs.log(track.label);
      return;
    }
  }
});
```

### [](/guides/audio-tracks/#removing-an-audio-track-from-the-player)Removing an Audio Track from the Player

Assuming a player already exists and has an audio track that you want to remove, you might do something like the following:

```js
// Get the track we created in an earlier example.
var track = player.audioTracks().getTrackById('my-spanish-audio-track');

// Remove it from the audio track list.
player.audioTracks().removeTrack(track);
```

## [](/guides/audio-tracks/#api)API

For more complete information, refer to the [Video.js API docs](https://docs.videojs.com/), specifically:

*   `Player#audioTracks`
*   `AudioTrackList`
*   `AudioTrack`

### [](/guides/audio-tracks/#videojsaudiotrack)`videojs.AudioTrack`

This class is based on [the `AudioTrack` standard](https://html.spec.whatwg.org/multipage/embedded-content.html#audiotrack) and can be used to create new audio track objects.

Each property below is available as an option to the `AudioTrack` constructor.

#### [](/guides/audio-tracks/#id)`id`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-id)

A unique identifier for this track. Video.js will generate one if not given.

#### [](/guides/audio-tracks/#kind)`kind`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-kind)

Video.js supports standard `kind` values for `AudioTracks`:

*   `"alternative"`: A possible alternative to the main track.
*   `"descriptions"`: An audio description of a video track.
*   `"main"`: The primary audio track for this video.
*   `"main-desc"`: The primary audio track, mixed with audio descriptions.
*   `"translation"`: A translated version of the main audio track.
*   `"commentary"`: Commentary on the primary audio track, e.g. a director's commentary.
*   `""` (default): No explicit kind, or the kind given by the track's metadata is not recognized by the user agent.

#### [](/guides/audio-tracks/#label)`label`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-label)

The label for the track that will be shown to the user. For example, in a menu that lists the different languages available as alternate audio tracks.

#### [](/guides/audio-tracks/#language)`language`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-language)

The valid [BCP 47](https://tools.ietf.org/html/bcp47) code for the language of the audio track, e.g. `"en"` for English or `"es"` for Spanish.

For supported language translations, please see the [languages folder (/lang)](https://github.com/videojs/video.js/tree/main/lang) located in the Video.js root and refer to the [languages guide](/guides/languages/) for more information on languages in Video.js.

#### [](/guides/audio-tracks/#enabled)`enabled`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-enabled)

Whether or not this track should be playing.

In Video.js, we only allow one track to be enabled at a time; so, if you enable more than one, the last one to be enabled will end up being the only one. While the spec allows for more than one track to be enabled, Safari and most implementations only allow one audio track to be enabled at a time.

---

# Video.js 7 to 8 Migration | Video.js

**URL:** https://videojs.org/guides/videojs-7-to-8/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js 7 to 8 Migration

## Table of Contents

*   [IE11 Support](#ie11-support)
*   [Removals](#removals)
    *   [videojs.extend()](#videojsextend)
    *   [firstplay Event](#firstplay-event)
    *   [Setting ARIA Attributes as Properties](#setting-aria-attributes-as-properties)
*   [Deprecations](#deprecations)
    *   [Newly Deprecated Functions](#newly-deprecated-functions)
    *   [Older Deprecated Functions](#older-deprecated-functions)

This guide describes backward incompatible changes made between Video.js 7 and Video.js 8 and how to migrate your implementation, if needed.

## [](/guides/videojs-7-to-8/#ie11-support)IE11 Support

Video.js 8 removes support for IE11. Attempting to use Video.js 8 in IE11 will cause errors to be thrown. There is no migration path here; so, if you must have IE11 support, use an older version of Video.js.

## [](/guides/videojs-7-to-8/#removals)Removals

### [](/guides/videojs-7-to-8/#videojsextend)`videojs.extend()`

The `videojs.extend()` function is removed from Video.js 8.

Video.js now uses native ES6 classes internally and the `extend()` function only worked with plain function prototypes. It did not work with ES6 classes, so it has been removed.

At the most basic level, the old way to create a component using `extend()` was:

```js
const Component = videojs.getComponent('Component');

const MyComponent = videojs.extend(Component, {
  constructor: function(player, options) {
    Component.call(this, player, options);
  }
});

videojs.registerComponent('MyComponent', MyComponent);
```

Going forward, only ES6 classes are supported. The equivalent would be:

```js
const Component = videojs.getComponent('Component');

class MyComponent extends Component {
  constructor(player, options) {
    super(player, options);
  }
}

videojs.registerComponent('MyComponent', MyComponent);
```

> **NOTE:** It should also be mentioned that native classes that have been already transpiled will not work with native `extend`! For example, current plugin build tools will transpile `class`es into plain constructor functions, which cannot be `extend`ed.

### [](/guides/videojs-7-to-8/#firstplay-event)`firstplay` Event

The `firstplay` event was removed from Video.js 8.

Instead of listening for the `firstplay` event, use `one()` to bind a callback to the first occurrence of the `play` event, like this:

```js
player.ready(() => {
  player.one('play', callback);
});
```

### [](/guides/videojs-7-to-8/#setting-aria-attributes-as-properties)Setting ARIA Attributes as Properties

In previous versions of Video.js, you could call the various flavors of `createEl()` with both DOM properties and attribute names in its second argument.

While there is a one-to-one mapping of properties to attributes in most cases, setting ARIA attribute names (i.e. `aria-label` vs. `ariaLabel`) through this mechanism is no longer supported:

```js
// NO LONGER SUPPORTED!!!
videojs.dom.createEl('div', {id: 'example', 'aria-label': 'My Label'});
```

_Attempting to set these types of attributes in the second argument of `createEl()` functions will still set properties of those names on the DOM object, but **they will not set attributes or the standard DOM properties**._

Instead, these must be set using the third argument, like this:

```js
videojs.dom.createEl('div', {id: 'example'}, {'aria-label': 'My Label'});
```

Alternatively, ARIA attributes can be set in their property name form:

```js
videojs.dom.createEl('div', {id: 'example', ariaLabel: 'My Label'});
```

## [](/guides/videojs-7-to-8/#deprecations)Deprecations

Many functions were deprecated in Video.js 8 (or earlier). Below are lists of those functions.

### [](/guides/videojs-7-to-8/#newly-deprecated-functions)Newly Deprecated Functions

These functions are newly deprecated in Video.js 8, but should be replaced to suppress deprecation warnings and prepare for Video.js 9.

| Deprecated Function | Instead, use... |
| --- | --- |
| `videojs.bind` | native `Function.prototype.bind` |
| `videojs.computedStyle` | `videojs.dom.computedStyle` |
| `videojs.createTimeRange` | `videojs.time.createTimeRanges` |
| `videojs.createTimeRanges` | `videojs.time.createTimeRanges` |
| `videojs.defineLazyProperty` | `videojs.obj.defineLazyProperty` |
| `videojs.formatTime` | `videojs.time.formatTime` |
| `videojs.isCrossOrigin` | `videojs.url.isCrossOrigin` |
| `videojs.mergeOptions` | `videojs.obj.merge` |
| `videojs.parseUrl` | `videojs.url.parseUrl` |
| `videojs.resetFormatTime` | `videojs.time.resetFormatTime` |
| `videojs.setFormatTime` | `videojs.time.setFormatTime` |

Each of these functions will log a deprecation warning the first time they are used... but only the first time so as not to be _too_ noisy!

_These deprecated functions will be removed in Video.js 9.0!_

### [](/guides/videojs-7-to-8/#older-deprecated-functions)Older Deprecated Functions

There are still a number of older functions that remain usable, but deprecated:

| Deprecated Function | Instead, use... |
| --- | --- |
| `videojs.addClass` | `videojs.dom.addClass` |
| `videojs.appendContent` | `videojs.dom.appendContent` |
| `videojs.createEl` | `videojs.dom.createEl` |
| `videojs.emptyEl` | `videojs.dom.emptyEl` |
| `videojs.getAttributes` | `videojs.dom.getAttributes` |
| `videojs.hasClass` | `videojs.dom.hasClass` |
| `videojs.insertContent` | `videojs.dom.insertContent` |
| `videojs.isEl` | `videojs.dom.isEl` |
| `videojs.isTextNode` | `videojs.dom.isTextNode` |
| `videojs.plugin` | `videojs.registerPlugin` |
| `videojs.removeClass` | `videojs.dom.removeClass` |
| `videojs.setAttributes` | `videojs.dom.setAttributes` |
| `videojs.toggleClass` | `videojs.dom.toggleClass` |

_These deprecated functions will be removed in Video.js 9.0!_

---

# Video Tracks | Video.js

**URL:** https://videojs.org/guides/video-tracks/

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video Tracks

## Table of Contents

*   [Caveats](#caveats)
*   [Working with Video Tracks](#working-with-video-tracks)
    *   [Add a Video Track to the Player](#add-a-video-track-to-the-player)
    *   [Listen for a Video Track Becoming Enabled](#listen-for-a-video-track-becoming-enabled)
    *   [Removing an Video Track from the Player](#removing-an-video-track-from-the-player)
*   [API](#api)
    *   [videojs.VideoTrack](#videojsvideotrack)
        *   [id](#id)
        *   [kind](#kind)
        *   [label](#label)
        *   [language](#language)
        *   [selected](#selected)

> **Note:** While video tracks [are a standard](https://html.spec.whatwg.org/multipage/embedded-content.html#videotrack), there are no compatible implementations at this time. This is an experimental technology!

Video tracks are a feature of HTML5 video for providing alternate video tracks to the user, so they can change the type of video they want to watch. Video.js offers a cross-browser implementation of video tracks.

## [](/guides/video-tracks/#caveats)Caveats

*   It is not possible to add video tracks through HTML like you can with text tracks. They must be added programmatically.
*   Video.js only stores track representations. Switching video tracks for playback is _not handled by Video.js_ and must be handled elsewhere.

## [](/guides/video-tracks/#working-with-video-tracks)Working with Video Tracks

### [](/guides/video-tracks/#add-a-video-track-to-the-player)Add a Video Track to the Player

```js
// Create a player.
var player = videojs('my-player');

// Create a track object.
var track = new videojs.VideoTrack({
  id: 'my-alternate-video-track',
  kind: 'commentary',
  label: 'Director\'s Commentary',
  language: 'en'
});

// Add the track to the player's video track list.
player.videoTracks().addTrack(track);
```

### [](/guides/video-tracks/#listen-for-a-video-track-becoming-enabled)Listen for a Video Track Becoming Enabled

When a track is enabled or disabled on an `VideoTrackList`, a `change` event will be fired. You can listen for that event and do something with it.

> NOTE: The initial `VideoTrack` selection (usually the main track that is selected) should not fire a `change` event.

```js
// Get the current player's VideoTrackList object.
var videoTrackList = player.videoTracks();

// Listen to the "change" event.
videoTrackList.addEventListener('change', function() {

  // Log the currently enabled VideoTrack label.
  for (var i = 0; i < videoTrackList.length; i++) {
    var track = videoTrackList[i];

    if (track.enabled) {
      videojs.log(track.label);
      return;
    }
  }
});
```

### [](/guides/video-tracks/#removing-an-video-track-from-the-player)Removing an Video Track from the Player

Assuming a player already exists and has an video track that you want to remove, you might do something like the following:

```js
// Get the track we created in an earlier example.
var track = player.videoTracks().getTrackById('my-alternate-video-track');

// Remove it from the video track list.
player.videoTracks().removeTrack(track);
```

## [](/guides/video-tracks/#api)API

For more complete information, refer to the [Video.js API docs](https://docs.videojs.com/), specifically:

*   `Player#videoTracks`
*   `VideoTrackList`
*   `VideoTrack`

### [](/guides/video-tracks/#videojsvideotrack)`videojs.VideoTrack`

This class is based on [the `VideoTrack` standard](https://html.spec.whatwg.org/multipage/embedded-content.html#videotrack) and can be used to create new video track objects.

Each property below is available as an option to the `VideoTrack` constructor.

#### [](/guides/video-tracks/#id)`id`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-id)

A unique identifier for this track. Video.js will generate one if not given.

#### [](/guides/video-tracks/#kind)`kind`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-kind)

Video.js supports standard `kind` values for `VideoTracks`:

*   `"alternative"`: A possible alternative to the main track.
*   `"captions"`: The main video track with burned in captions
*   `"main"`: The main video track.
*   `"sign"`: The main video track with added sign language overlay.
*   `"subtitles"`: The main video track with burned in subtitles.
*   `"commentary"`: The main video track with burned in commentary.
*   `""` (default): No explicit kind, or the kind given by the track's metadata is not recognized by the user agent.

#### [](/guides/video-tracks/#label)`label`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-label)

The label for the track that will be shown to the user. For example, in a menu that lists the different captions available as alternate video tracks.

#### [](/guides/video-tracks/#language)`language`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-language)

The valid [BCP 47](https://tools.ietf.org/html/bcp47) code for the language of the video track, e.g. `"en"` for English or `"es"` for Spanish.

For supported language translations, please see the [languages folder (/lang)](https://github.com/videojs/video.js/tree/main/lang) folder located in the Video.js root and refer to the [languages guide](/guides/languages) for more information on languages in Video.js.

#### [](/guides/video-tracks/#selected)`selected`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-selected)

Whether or not this track should be playing. Only one video track may be selected at a time.

---

# Video.js Setup | Video.js

**URL:** https://videojs.org/guides/setup

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js Setup

## Table of Contents

*   [Getting Video.js](#getting-videojs)
*   [Creating a Player](#creating-a-player)
    *   [Automatic Setup](#automatic-setup)
    *   [Manual Setup](#manual-setup)
    *   [Getting References to Players](#getting-references-to-players)
        *   [Using videojs](#using-videojs)
        *   [Using videojs.getPlayer()](#using-videojsgetplayer)
        *   [Using videojs.getPlayers() or videojs.players](#using-videojsgetplayers-or-videojsplayers)
*   [Options](#options)
    *   [Global Defaults](#global-defaults)
    *   [A Note on <video> Tag Attributes](#a-note-on-video-tag-attributes)
*   [Player Readiness](#player-readiness)
*   [Advanced Player Workflows](#advanced-player-workflows)

## [](/guides/setup/#getting-videojs)Getting Video.js

Video.js is officially available via CDN and npm.

Video.js works out of the box with not only HTML `<script>` and `<link>` tags, but also all major bundlers/packagers/builders, such as Browserify, Node, WebPack, etc.

Please refer to the [Getting Started](/getting-started) document for details.

## [](/guides/setup/#creating-a-player)Creating a Player

> **Note:** Video.js works with `<video>` _and_ `<audio>` elements, but for simplicity we'll refer only to `<video>` elements going forward.

Once you have Video.js [loaded on your page](/getting-started), you're ready to create a player!

The core strength of Video.js is that it decorates a [standard `<video>` element](https://www.w3.org/TR/html5/embedded-content-0.html#the-video-element) and emulates its associated [events and APIs](https://www.w3.org/2010/05/video/mediaevents.html), while providing a customizable DOM-based UI.

Video.js supports all attributes of the `<video>` element (such as `controls`, `preload`, etc), but it also supports [its own options](/guides/setup/#options). There are two ways to create a Video.js player and pass it options, but they both start with a standard `<video>` element with the attribute `class="video-js"`:

```html
<video class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

You can use a `<video-js>` element instead of `<video>`. Using a `<video>` element is undesirable in some circumstances, as the browser may show unstyled controls or try to load a source in the moments before the player initialises, which does not happen with the `<video-js>` custom element.

```html
<video-js>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video-js>
```

For a high-level overview of all the various embed options, check out the [embeds page](/guides/embeds), then follow the rest of this page.

### [](/guides/setup/#automatic-setup)Automatic Setup

By default, when your web page finishes loading, Video.js will scan for media elements that have the `data-setup` attribute. The `data-setup` attribute is used to pass options to Video.js. A minimal example looks like this:

```html
<video class="video-js" data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

> **Note:** You _must_ use single-quotes with `data-setup` as it is expected to contain JSON.

### [](/guides/setup/#manual-setup)Manual Setup

On the modern web, a `<video>` element often does not exist when the page finishes loading. In these cases, automatic setup is not possible, but manual setup is available via [the `videojs` function](https://docs.videojs.com/module-videojs.html).

One way to call this function is by providing it a string matching a `<video>` element's `id` attribute:

```html
<video id="my-player" class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

```js
videojs('my-player');
```

However, using an `id` attribute isn't always practical; so, the `videojs` function accepts a DOM element instead:

```html
<video class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
</video>
```

```js
videojs(document.querySelector('.video-js'));
```

### [](/guides/setup/#getting-references-to-players)Getting References to Players

Once players are created, Video.js keeps track of them internally. There are a few ways to get references to pre-existing players.

#### [](/guides/setup/#using-videojs)Using `videojs`

Calling `videojs()` with the ID of element of an already-existing player will return that player and will not create another one.

If there is no player matching the argument, it will attempt to create one.

#### [](/guides/setup/#using-videojsgetplayer)Using `videojs.getPlayer()`

Sometimes, you want to get a reference to a player without the potential side effects of calling `videojs()`. This can be acheived by calling `videojs.getPlayer()` with either a string matching the element's ID or the element itself.

#### [](/guides/setup/#using-videojsgetplayers-or-videojsplayers)Using `videojs.getPlayers()` or `videojs.players`

The `videojs.players` property exposes all known players. The method, `videojs.getPlayers()` simply returns the same object.

Players are stored on this object with keys matching their IDs.

> **Note:** A player created from an element without an ID will be assigned an automatically-generated ID.

## [](/guides/setup/#options)Options

> **Note:** This guide only covers how to pass options during player setup. For a complete reference on _all_ available options, see the [options guide](/guides/options).

There are three ways to pass options to Video.js. Because Video.js decorates an HTML5 `<video>` element, many of the options available are also available as [standard `<video>` tag attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Attributes):

```html
<video controls autoplay preload="auto" ...>
```

Alternatively, you can use the `data-setup` attribute to pass options as [JSON](https://json.org/example.html). This is also how you would set options that aren't standard to the `<video>` element:

```html
<video data-setup='{"controls": true, "autoplay": false, "preload": "auto"}'...>
```

> **Note:** You _must_ use single-quotes around the value of `data-setup` as it contains a JSON string which must use double quotes.

Finally, if you're not using the `data-setup` attribute to trigger the player setup, you can pass in an object of player options as the second argument to the `videojs` function:

```js
videojs('my-player', {
  controls: true,
  autoplay: false,
  preload: 'auto'
});
```

> **Note:** Do not use both `data-setup` and an options object.

### [](/guides/setup/#global-defaults)Global Defaults

Default options for all players can be found at `videojs.options` and can be changed directly. For example, to set `{autoplay: true}` for all future players:

```js
videojs.options.autoplay = true;
```

### [](/guides/setup/#a-note-on-video-tag-attributes)A Note on `<video>` Tag Attributes

Many attributes are so-called [boolean attributes](https://www.w3.org/TR/2011/WD-html5-20110525/common-microsyntaxes.html#boolean-attributes). This means they are either on or off. In these cases, the attribute _should have no value_ (or should have its name as its value) - its presence implies a true value and its absence implies a false value.

_These are incorrect:_

```html
<video controls="true" ...>
<video loop="true" ...>
<video controls="false" ...>
```

> **Note:** The example with `controls="false"` can be a point of confusion for new developers - it will actually turn controls _on_!

These are correct:

```html
<video controls ...>
<video loop="loop" ...>
<video ...>
```

## [](/guides/setup/#player-readiness)Player Readiness

Because Video.js techs have the potential to be loaded asynchronously, it isn't always safe to interact with a player immediately upon setup. For this reason, Video.js players have a concept of "readiness" which will be familiar to anyone who has used jQuery before.

Essentially, any number of ready callbacks can be defined for a Video.js player. There are three ways to pass these callbacks. In each example, we'll add an identical class to the player:

Pass a callback to the `videojs()` function as a third argument:

```js
// Passing `null` for the options argument.
videojs('my-player', null, function() {
  this.addClass('my-example');
});
```

Pass a callback to a player's `ready()` method:

```js
var player = videojs('my-player');

player.ready(function() {
  this.addClass('my-example');
});
```

Listen for the player's `"ready"` event:

```js
var player = videojs('my-player');

player.on('ready', function() {
  this.addClass('my-example');
});
```

In each case, the callback is called asynchronously.

An important distinction between the above methods is that adding an listener for `ready` with `on()` _must_ be done before the player is ready. With `player.ready()`, the function is called immediately if the player is already ready.

## [](/guides/setup/#advanced-player-workflows)Advanced Player Workflows

For a discussion of more advanced player workflows, see the [player workflows guide](/guides/player-workflows).

---

# Video.js Plugins | Video.js

**URL:** https://videojs.org/guides/plugins

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js Plugins

## Table of Contents

*   [Writing a Basic Plugin](#writing-a-basic-plugin)
    *   [Write a JavaScript Function](#write-a-javascript-function)
    *   [Register a Basic Plugin](#register-a-basic-plugin)
*   [Writing an Advanced Plugin](#writing-an-advanced-plugin)
    *   [Write a JavaScript Class/Constructor](#write-a-javascript-classconstructor)
    *   [Register an Advanced Plugin](#register-an-advanced-plugin)
    *   [Key Differences from Basic Plugins](#key-differences-from-basic-plugins)
        *   [The Value of this](#the-value-of-this)
        *   [The Player Plugin Name Property](#the-player-plugin-name-property)
    *   [Features of Advanced Plugins](#features-of-advanced-plugins)
        *   [Events](#events)
        *   [Statefulness](#statefulness)
        *   [Lifecycle](#lifecycle)
        *   [Version](#version)
        *   [Logging](#logging)
    *   [Advanced Example Advanced Plugin](#advanced-example-advanced-plugin)
*   [Setting up a Plugin](#setting-up-a-plugin)
    *   [Plugin Setup Events](#plugin-setup-events)
*   [References](#references)

**NOTE:** This guide is focused on Video.js 8+. It no longer mentions use of the `videojs.extend()` method, which was removed in 8.0. Please see [our migration guide](/guides/videojs-7-to-8/) for further information!

One of the great strengths of Video.js is its ecosystem of plugins that allow authors from all over the world to share their video player customizations. This includes everything from the simplest UI tweaks to new [playback technologies and source handlers](/guides/tech)!

Because we view plugins as such an important part of Video.js, the organization is committed to maintaining a robust set of tools for plugin authorship:

*   [generator-videojs-plugin](https://github.com/videojs/generator-videojs-plugin)
    
    A [Yeoman](http://yeoman.io) generator for scaffolding a Video.js plugin project. Additionally, it offers a set of [conventions for plugin authorship](https://github.com/videojs/generator-videojs-plugin/blob/master/docs/conventions.md) that, if followed, make authorship, contribution, and usage consistent and predictable.
    
    In short, the generator sets up plugin authors to focus on writing their plugin - not messing with tools.
    

## [](/guides/plugins/#writing-a-basic-plugin)Writing a Basic Plugin

If you've written a Video.js plugin before, the basic plugin concept should be familiar. It's similar to a jQuery plugin in that the core idea is that you're adding a method to the player.

### [](/guides/plugins/#write-a-javascript-function)Write a JavaScript Function

A basic plugin is a plain JavaScript function:

```js
function examplePlugin(options) {

  if (options.customClass) {
    this.addClass(options.customClass);
  }

  this.on('playing', function() {
    videojs.log('playback began!');
  });
}
```

By convention, plugins are passed an `options` object; however, you can realistically accept whatever arguments you want. This example plugin will add a custom class (whatever is passed in as `options.customClass`) and, whenever playback begins, it will log a message to the browser console.

> **Note:** The value of `this` in the plugin function is the player instance; so, you have access to [its complete API](https://docs.videojs.com/Player.html).

### [](/guides/plugins/#register-a-basic-plugin)Register a Basic Plugin

Now that we have a function that does something with a player, all that's left is to register the plugin with Video.js:

```js
videojs.registerPlugin('examplePlugin', examplePlugin);
```

After that, any player will automatically have an `examplePlugin` method on its prototype!

> **Note:** The only stipulation with the name of the plugin is that it cannot conflict with any existing plugin or player method.

## [](/guides/plugins/#writing-an-advanced-plugin)Writing an Advanced Plugin

Video.js 6 introduced advanced plugins: these are plugins that share a similar API with basic plugins, but are class-based and offer a range of extra features out of the box.

While reading the following sections, you may want to refer to the [Plugin API docs](https://docs.videojs.com/Plugin.html) for more detail.

### [](/guides/plugins/#write-a-javascript-classconstructor)Write a JavaScript Class/Constructor

If you're familiar with creating [components](/guides/components), this process is similar. An advanced plugin starts with a JavaScript class:

```js
const Plugin = videojs.getPlugin('plugin');

class ExamplePlugin extends Plugin {

  constructor(player, options) {
    super(player, options);

    if (options.customClass) {
      player.addClass(options.customClass);
    }

    player.on('playing', function() {
      videojs.log('playback began!');
    });
  }
}
```

For now, this example advanced plugin does the exact same thing as the basic plugin described above - not to worry, we will make it more interesting as we continue!

### [](/guides/plugins/#register-an-advanced-plugin)Register an Advanced Plugin

The registration process for advanced plugins is identical to [the process for basic plugins](/guides/plugins/#register-a-basic-plugin).

```js
videojs.registerPlugin('examplePlugin', ExamplePlugin);
```

### [](/guides/plugins/#key-differences-from-basic-plugins)Key Differences from Basic Plugins

Advanced plugins have two key differences from basic plugins that are important to understand before describing their advanced features.

#### [](/guides/plugins/#the-value-of-this)The Value of `this`

With basic plugins, the value of `this` in the plugin function will be the _player_.

With advanced plugins, the value of `this` is the _instance of the plugin class_. The player is passed to the plugin constructor as its first argument (and is automatically applied to the plugin instance as the `player` property) and any further arguments are passed after that.

#### [](/guides/plugins/#the-player-plugin-name-property)The Player Plugin Name Property

Both basic plugins and advanced plugins are set up by calling a method on a player with a name matching the plugin (e.g., `player.examplePlugin()`).

However, with advanced plugins, this method acts like a factory function and it is _replaced_ for the current player by a new function which returns the plugin instance:

```js
// `examplePlugin` has not been called, so it is a factory function.
player.examplePlugin();

// `examplePlugin` is now a function that returns the same instance of
// `ExamplePlugin` that was generated by the previous call.
player.examplePlugin().someMethodName();
```

With basic plugins, the method does not change - it is always the same function. It is up to the authors of basic plugins to deal with multiple calls to their plugin function.

### [](/guides/plugins/#features-of-advanced-plugins)Features of Advanced Plugins

Up to this point, our example advanced plugin is functionally identical to our example basic plugin. However, advanced plugins bring with them a great deal of benefit that is not built into basic plugins.

#### [](/guides/plugins/#events)Events

Like components, advanced plugins offer an implementation of events. This includes:

*   The ability to listen for events on the plugin instance using `on` or `one`:
    
    ```js
    player.examplePlugin().on('example-event', function() {
      videojs.log('example plugin received an example-event');
    });
    ```
    
*   The ability to `trigger` custom events on a plugin instance:
    
    ```js
    player.examplePlugin().trigger('example-event');
    ```
    
*   The ability to stop listening to custom events on a plugin instance using `off`:
    
    ```js
    player.examplePlugin().off('example-event');
    ```
    

By offering a built-in events system, advanced plugins offer a wider range of options for code structure with a pattern familiar to most web developers.

##### [](/guides/plugins/#extra-event-data)Extra Event Data

All events triggered by plugins include an additional data object as a second argument. This object has three properties:

*   `name`: The name of the plugin (e.g. `"examplePlugin"`) as a string.
*   `plugin`: The plugin constructor (e.g. `ExamplePlugin`).
*   `instance`: The plugin constructor instance.

#### [](/guides/plugins/#statefulness)Statefulness

A new concept introduced for advanced plugins is _statefulness_. This is similar to React components' `state` property and `setState` method.

Advanced plugin instances each have a `state` property, which is a plain JavaScript object - it can contain any keys and values the plugin author wants.

A default `state` can be provided by adding a static property to a plugin constructor:

```js
ExamplePlugin.defaultState = {
  customClass: 'default-custom-class'
};
```

When the `state` is updated via the `setState` method, the plugin instance fires a `"statechanged"` event, but _only if something changed!_ This event can be used as a signal to update the DOM or perform some other action. The event object passed to listeners for this event includes, an object describing the changes that occurred on the `state` property:

```js
player.examplePlugin().on('statechanged', function(e) {
  if (e.changes && e.changes.customClass) {
    this.player
      .removeClass(e.changes.customClass.from)
      .addClass(e.changes.customClass.to);
  }
});

player.examplePlugin().setState({customClass: 'another-custom-class'});
```

#### [](/guides/plugins/#lifecycle)Lifecycle

Like components, advanced plugins have a lifecycle. They can be created with their factory function and they can be destroyed using their `dispose` method:

```js
// set up a example plugin instance
player.examplePlugin();

// dispose of it anytime thereafter
player.examplePlugin().dispose();
```

The `dispose` method has several effects:

*   Triggers a `"dispose"` event on the plugin instance.
*   Cleans up all event listeners on the plugin instance, which helps avoid errors caused by events being triggered after an object is cleaned up.
*   Removes plugin state and references to the player to avoid memory leaks.
*   Reverts the player's named property (e.g. `player.examplePlugin`) _back_ to the original factory function, so the plugin can be set up again.

In addition, if the player is disposed, the disposal of all its advanced plugin instances will be triggered as well.

#### [](/guides/plugins/#version)Version

Adding a version number to a plugin is done by defining a `VERSION` property on the plugin before registering it:

```js
ExamplePlugin.VERSION = '1.0.1';

videojs.registerPlugin('examplePlugin', ExamplePlugin);
```

Retrieve it using `videojs.getPluginVersion`:

```js
var version = videojs.getPluginVersion('examplePlugin');
console.log(version);  // 1.0.1
```

Note that the [plugin generator](https://github.com/videojs/generator-videojs-plugin) already takes care of adding a version number for you.

#### [](/guides/plugins/#logging)Logging

By default, each advanced plugin instance has its own `log` property much like `videojs` and `Player` instances do. The log messages will be prefixed with the player's ID and the plugin's name:

```js
player.examplePlugin().log('hello world!');
```

The above will log the following:

```text
VIDEOJS: $PLAYER_ID: examplePlugin: hello world!
```

The `log` function will also have all the methods/properties of the default `videojs.log`; such as, `error()`, `warn()`, `level()`, etc.

> **NOTE:** This method is added in the constructor and it _will not_ override any predefined `log` property of the plugin's prototype.

### [](/guides/plugins/#advanced-example-advanced-plugin)Advanced Example Advanced Plugin

What follows is a complete ES6 advanced plugin that logs a custom message when the player's state changes between playing and pause. It uses all the described advanced features:

```js
import videojs from 'video.js';

const Plugin = videojs.getPlugin('plugin');

class Advanced extends Plugin {

  constructor(player, options) {
    super(player, options);

    // Whenever the player emits a playing or pause event, we update the
    // state if necessary.
    this.on(player, ['playing', 'pause'], this.updateState);
    this.on('statechanged', this.logState);
  }

  dispose() {
    super.dispose();
    videojs.log('the advanced plugin is being disposed');
  }

  updateState() {
    this.setState({playing: !this.player.paused()});
  }

  logState(changed) {
    videojs.log(`the player is now ${this.state.playing ? 'playing' : 'paused'}`);
  }
}

videojs.registerPlugin('advanced', Advanced);

const player = videojs('example-player');

player.advanced();

// This will begin playback, which will trigger a "playing" event, which will
// update the state of the plugin, which will cause a message to be logged.
player.play();

// This will pause playback, which will trigger a "paused" event, which will
// update the state of the plugin, which will cause a message to be logged.
player.pause();

player.advanced().dispose();

// This will begin playback, but the plugin has been disposed, so it will not
// log any messages.
player.play();
```

This example may be a bit pointless in reality, but it demonstrates the sort of flexibility offered by advanced plugins over basic plugins.

## [](/guides/plugins/#setting-up-a-plugin)Setting up a Plugin

There are two ways to set up (or initialize) a plugin on a player. Both ways work identically for both basic and advanced plugins.

The first way is during creation of the player. Using the `plugins` option, a plugin can be automatically set up on a player:

```js
videojs('example-player', {
  plugins: {
    examplePlugin: {
      customClass: 'example-class'
    }
  }
});
```

Otherwise, a plugin can be manually set up:

```js
var player = videojs('example-player');
player.examplePlugin({customClass: 'example-class'});
```

These two methods are functionally identical - use whichever you prefer!

### [](/guides/plugins/#plugin-setup-events)Plugin Setup Events

Occasionally, a use-case arises where some code needs to wait for a plugin to be initialized. As of Video.js 6, this can be achieved by listening for `pluginsetup` events on the player.

For any given plugin initialization, there are four events to be aware of:

*   `beforepluginsetup`: Triggered immediately before any plugin is initialized.
*   `beforepluginsetup:examplePlugin` Triggered immediately before the `examplePlugin` is initialized.
*   `pluginsetup`: Triggered after any plugin is initialized.
*   `pluginsetup:examplePlugin`: Triggered after the `examplePlugin` is initialized.

These events work for both basic and advanced plugins. They are triggered on the player and each includes an object of [extra event data](/guides/plugins/#extra-event-data) as a second argument to its listeners.

## [](/guides/plugins/#references)References

*   [Player API](https://docs.videojs.com/Player.html)
*   [Plugin API](https://docs.videojs.com/Plugin.html)
*   [Plugin Generator](https://github.com/videojs/generator-videojs-plugin)
*   [Plugin Conventions](https://github.com/videojs/generator-videojs-plugin/blob/master/docs/conventions.md)

---

# Languages | Video.js

**URL:** https://videojs.org/guides/languages

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Languages

## Table of Contents

*   [Using Video.js Languages](#using-videojs-languages)
*   [Contributing to Video.js Translations](#contributing-to-videojs-translations)
    *   [JSON Format](#json-format)
    *   [File Naming](#file-naming)
    *   [Updating an Existing Translation](#updating-an-existing-translation)
    *   [Writing a New Translation](#writing-a-new-translation)
    *   [Adding Languages via the API](#adding-languages-via-the-api)
    *   [Per-Player Translations](#per-player-translations)
    *   [Setting Player Language](#setting-player-language)
    *   [Determining Player Language](#determining-player-language)
        *   [Internal Language Selection](#internal-language-selection)
*   [References](#references)

Video.js includes localization support to present text in a language other than the default English where appropriate.

For an up-to-date list of the languages Video.js supports, see the [languages folder (`lang`)](/lang). Some translations may be less complete than others - see the [translations needed doc](https://github.com/videojs/video.js/blob/main/docs/translations-needed.md) for a table of strings that are missing from the translations available. Contributions are welcome to update those that are incomplete.

## [](/guides/languages/#using-videojs-languages)Using Video.js Languages

Video.js ships with multiple translations (in `dist/lang/`) in JavaScript files. Add the lang script for each language you need to support. Each of these files can be included in a web page to provide support for that language in _all_ Video.js players:

```html
<script src="//example.com/path/to/video.min.js"></script>
<script src="//example.com/path/to/lang/es.js"></script>
```

## [](/guides/languages/#contributing-to-videojs-translations)Contributing to Video.js Translations

We welcome new translations and improvements to existing ones! Please see the [contributing document](https://github.com/videojs/video.js/blob/main/CONTRIBUTING.md) to get started contributing to Video.js and continue reading for specifics on how to contribute to translations of Video.js.

### [](/guides/languages/#json-format)JSON Format

Video.js uses a JSON object to describe a language, where the keys are English and the values are the target language. For example, a Spanish translation might look like this:

```json
{
  "Play": "Reproducción",
  "Pause": "Pausa",
  "Current Time": "Tiempo reproducido",
  "Duration": "Duración total",
  "Remaining Time": "Tiempo restante",
}
```

### [](/guides/languages/#file-naming)File Naming

Translations are found in the `lang/` directory.

Each file's name should be the [standard language code](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) that is most appropriate, with a `.json` extension. For example, "es.json" for Spanish or "zh-CN.json" for simplified Chinese.

### [](/guides/languages/#updating-an-existing-translation)Updating an Existing Translation

If there is a [missing translation](https://github.com/videojs/video.js/blob/main/docs/translations-needed.md), mistake, or room for improvement in an existing translation, don't hesitate to open a pull request!

1.  Edit the relevant JSON file and make the necessary changes.
2.  Verify the language compiles by running the language specific build `npm run build:lang` or the full build `npm run build`.
3.  Verify the translation appears properly in the player UI.
4.  Run `npm run docs:lang` to update the [missing translation document](https://github.com/videojs/video.js/blob/main/docs/translations-needed.md).
5.  Commit and open a pull request on GitHub.

### [](/guides/languages/#writing-a-new-translation)Writing a New Translation

The process for writing an entirely new translation is virtually identical to the process for [updating an existing translation](/guides/languages/#updating-an-existing-translation) except that the new translation JSON file needs to be created.

The template for new language files is the English file ([lang/en.json](/lang/en.json)). This file is always up-to-date with strings that need translations.

The first step to writing a new translation is to copy the English file:

```shell-session
cp lang/en.json lang/${NEW_LANG_CODE}.json
```

Otherwise, the process is the same as [updating an existing translation](/guides/languages/#updating-an-existing-translation).

### [](/guides/languages/#adding-languages-via-the-api)Adding Languages via the API

In addition to the stand-alone scripts provided by Video.js, the API supports manual definition of new languages via the `addLanguage` method. It takes two arguments: the [standard language code](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) and a [language definition object](/guides/languages/#json-format).

```js
videojs.addLanguage('es', {
  Play: 'Reproducción',
  Pause: 'Pausa',
  'Current Time': 'Tiempo reproducido',
  'Duration': 'Duración total',
  'Remaining Time': 'Tiempo restante',
  ...
});
```

`addLanguage()` will overwrite existing translations if the object includes strings previously translated. However text that has already been localised will not be updated after generation.

### [](/guides/languages/#per-player-translations)Per-Player Translations

In addition to providing languages to Video.js itself, individual `Player` instances can be provided custom language support via [the `languages` option](/guides/options#languages):

```js
// Provide a custom definition of Spanish to this player.
videojs('my-player', {
  languages: {
    es: {
      Play: 'Reproducir'
    }
  }
});
```

### [](/guides/languages/#setting-player-language)Setting Player Language

The language used by a player instance may be set via [the `language` option](/guides/options#language):

```js
// Set the language to Spanish for this player.
videojs('my-player', {
  language: 'es'
});
```

The `language` method of the player _can_ be used to set the language after instantiation with `language('es')`. However, this is generally not useful as it does not update text that is already in place.

### [](/guides/languages/#determining-player-language)Determining Player Language

The player language is set to one of the following in descending priority:

*   The language [specified in options](/guides/languages/#setting-default-player-language)
*   The language specified by a `lang` attribute on the player element.
*   The language specified by the closest parent element with a `lang` attribute, up to and including the `<html>` element.
*   The browser language preference; the first language if more than one is configured
*   English

#### [](/guides/languages/#internal-language-selection)Internal Language Selection

*   Language codes are considered case-insensitively (e.g. `en-US` == `en-us`).
*   If there is no match for a language code with a subcode (e.g. `en-us`), a match for the primary code (e.g. `en`) is used if available.

## [](/guides/languages/#references)References

For information on translation/localization in plugins, see [the plugins guide](/guides/plugins).

Standard languages codes [are defined by the IANA](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry).

For all existing/supported languages, please see the [languages folder (`lang/`)](/lang) folder located in the project root.

---

# Components | Video.js

**URL:** https://videojs.org/guides/components

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Components

## Table of Contents

*   [What is a Component?](#what-is-a-component)
*   [Adding a Component](#adding-a-component)
*   [Creating a Component](#creating-a-component)
*   [Component Children](#component-children)
    *   [Basic Example](#basic-example)
    *   [Using Options](#using-options)
*   [Event Listening](#event-listening)
    *   [Using on](#using-on)
    *   [Using off](#using-off)
    *   [Using one](#using-one)
    *   [Using trigger](#using-trigger)
*   [Default Component Tree](#default-component-tree)
*   [Specific Component Details](#specific-component-details)
    *   [Play Toggle](#play-toggle)
    *   [Volume Panel](#volume-panel)
    *   [Text Track Settings](#text-track-settings)
    *   [Resize Manager](#resize-manager)

**NOTE:** This guide is focused on Video.js 8+. It no longer mentions use of the `videojs.extend()` method, which was removed in 8.0. Please see [our migration guide](/guides/videojs-7-to-8/) for further information!

The architecture of the Video.js player is centered around components.

The `Player` class and all classes representing player controls and other UI elements inherit from the `Component` class. This architecture makes it easy to construct the user interface of the Video.js player in a tree-like structure that mirrors the DOM.

## [](/guides/components/#what-is-a-component)What is a Component?

A component is a JavaScript object that has the following features:

*   An associated DOM element, in almost all cases.
*   An association to a `Player` object.
*   The ability to manage any number of child components.
*   The ability to listen for and trigger events.
*   A lifecycle of initialization and disposal.

For more specifics on the programmatic interface of a component, see [the component API docs](https://docs.videojs.com/Component.html).

## [](/guides/components/#adding-a-component)Adding a Component

An instance of a component can be created with `new Component()`.

```js
// Creating an instance of a button
var player = videojs('some-video-id');
var Button = videojs.getComponent('Button');
var button = new Button(player, {
  clickHandler: function(event) {
    videojs.log('Clicked');
  }
});

console.log(button.el());
```

The above code will output

```html
<button class="vjs-control vjs-button" type="button" aria-disabled="false">
  <span class="vjs-icon-placeholder" aria-hidden="true"></span>
  <span class="vjs-control-text" aria-live="polite"></span>
</button>
```

Note that this has created the button, but not added it to the DOM. Adding it as a child of a component will add it to the DOM.

```js
player.getChild('ControlBar').addChild(button);
```

Alternatively by passing the name of a component to `addChild`, a new instance of the component will be created and added in one step.

```js
// Creating an instance of a button and addingit to the player's control bar
var player = videojs('some-video-id');
var button = player.getChild('ControlBar').addChild('button', {
  clickHandler: function(event) {
    videojs.log('Clicked');
  }
});

console.log(button.el());
// will have the same html result as the previous example
```

Buttons should have text. The default buttons don't display their text, but it is present for screenreaders and displayed by browsers as a tooltip. The text of the button can be set as an option:

```js
const myButton = player.getChild('ControlBar').addChild('button', {controlText: 'My button'});
```

To have the control text displayed, add a `vjs-visibile-text` class to the button.

```js
const myButton = player.getChild('ControlBar').addChild('button', {
  controlText: 'My button',
  className: 'vjs-visible-text'
});
```

Classes and control text could also be set after a button is created.

```js
myButton.controlText('My button');
myButton.addClass('vjs-visible-text');
```

When the [`experimentalSvgIcons`](/guides/options/#experimentalSvgIcons) option is enabled on the player, icons can be added or replaced on any `Component` using the `setIcon` method.

You can view all of the icons available by renaming [`sandbox/svg-icons.html.example`](https://github.com/videojs/video.js/blob/main/sandbox/svg-icons.html.example) to `sandbox/svg-icons.html`, building Video.js with `npm run build`, and opening `sandbox/svg-icons.html` in your browser of choice.

```js
myButton.setIcon('play');
```

## [](/guides/components/#creating-a-component)Creating a Component

Video.js components are es6 classes that can be extended using class syntax and registered with Video.js to add new features and UI to the player.

There are a few functions used for creating and registering components:

*   `videojs.getComponent(String name)`: Retrieves component classes from Video.js.
*   `videojs.registerComponent(String name, Function Comp)`: Registers component classes with Video.js.

This example creates a title bar component, as a class extending `Component`.

```js
// Get the Component base class from Video.js
const Component = videojs.getComponent('Component');

class TitleBar extends Component {

  // The constructor of a component receives two arguments: the
  // player it will be associated with and an object of options.
  constructor(player, options = {}) {

    // It is important to invoke the superclass before anything else, 
    // to get all the features of components out of the box!
    super(player, options);

    // If a `text` option was passed in, update the text content of 
    // the component.
    if (options.text) {
      this.updateTextContent(options.text);
    }
  }

  // The `createEl` function of a component creates its DOM element.
  createEl() {
    return videojs.dom.createEl('div', {

      // Prefixing classes of elements within a player with "vjs-" 
      // is a convention used in Video.js.
      className: 'vjs-title-bar'
    });
  }

  // This function could be called at any time to update the text 
  // contents of the component.
  updateTextContent(text) {

    // If no text was provided, default to "Title Unknown"
    if (typeof text !== 'string') {
      text = 'Title Unknown';
    }

    // Use Video.js utility DOM methods to manipulate the content
    // of the component's element.
    videojs.emptyEl(this.el());
    videojs.appendContent(this.el(), text);
  }
}
```

Note that due to the removal of the `extend()` function, to extend a component when transpiling to ES5, you will need to utilize the following syntax.

```js
// My ES5 constructor function extending Component
function MyComponent(arguments) {
  Component.call(this, arguments);
}

MyComponent.prototype = Object.create(Component.prototype);
```

Once the component is created, it can be registered, and used in a player.

```js
// Register the component with Video.js, so it can be used in players.
videojs.registerComponent('TitleBar', TitleBar);

// Create a player.
var player = videojs('my-player');

// Add the TitleBar as a child of the player and provide it some text 
// in its options.
player.addChild('TitleBar', {text: 'The Title of The Video!'});
```

A live example is in [this JSBin](https://jsbin.com/vobacas/edit?html,css,js,output).

## [](/guides/components/#component-children)Component Children

Again, refer to [the component API docs](https://docs.videojs.com/Component.html) for complete details on methods available for managing component structures.

### [](/guides/components/#basic-example)Basic Example

When a child component is added to a parent component, Video.js inserts the element of the child into the element of the parent. For example, adding a component like this:

```js
// Add a "BigPlayButton" component to the player. Its element will be appended to the player's element.
player.addChild('BigPlayButton');
```

Results in a DOM that looks like this:

```html
<!-- Player Element -->
<div class="video-js">
  <!-- BigPlayButton Element -->
  <div class="vjs-big-play-button"></div>
</div>
```

Conversely, removing child components will remove the child component's element from the DOM:

```js
player.removeChild('BigPlayButton');
```

Results in a DOM that looks like this:

```html
<!-- Player Element -->
<div class="video-js">
</div>
```

### [](/guides/components/#using-options)Using Options

Pass in options for child constructors and options for children of the child.

```js
var player = videojs('some-vid-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myButton = myComponent.addChild('MyButton', {
  text: 'Press Me',
  buttonChildExample: {
    buttonChildOption: true
  }
});
```

Children can also be added via options when a component is initialized.

> Note: Include a 'name' key which will be used if two child components of the same type that need different options.

```js
// MyComponent is from the above example
var myComp = new MyComponent(player, {
  children: ['button', {
    name: 'button',
    someOtherOption: true
  }, {
    name: 'button',
    someOtherOption: false
  }]
});
```

## [](/guides/components/#event-listening)Event Listening

### [](/guides/components/#using-on)Using `on`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function() {
  var myComponent = this;
  console.log('myFunc called');
};

myComponent.on('eventType', myFunc);
myComponent.trigger('eventType');
// logs 'myFunc called'
```

The context of `myFunc` will be `myComponent` unless it is bound. You can add a listener to another element or component.

```js
var otherComponent = new Component(player);

// myComponent/myFunc is from the above example
myComponent.on(otherComponent.el(), 'eventName', myFunc);
myComponent.on(otherComponent, 'eventName', myFunc);

otherComponent.trigger('eventName');
// logs 'myFunc called' twice
```

### [](/guides/components/#using-off)Using `off`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function() {
  var myComponent = this;
  console.log('myFunc called');
};
myComponent.on('eventType', myFunc);
myComponent.trigger('eventType');
// logs 'myFunc called'

myComponent.off('eventType', myFunc);
myComponent.trigger('eventType');
// does nothing
```

If myFunc gets excluded, _all_ listeners for the event type will get removed. If eventType gets excluded, _all_ listeners will get removed from the component. You can use `off` to remove listeners that get added to other elements or components using:

`myComponent.on(otherComponent...`

In this case both the event type and listener function are **REQUIRED**.

```js
var otherComponent = new Component(player);

// myComponent/myFunc is from the above example
myComponent.on(otherComponent.el(), 'eventName', myFunc);
myComponent.on(otherComponent, 'eventName', myFunc);

otherComponent.trigger('eventName');
// logs 'myFunc called' twice
myComponent.off(otherComponent.el(), 'eventName', myFunc);
myComponent.off(otherComponent, 'eventName', myFunc);
otherComponent.trigger('eventName');
// does nothing
```

### [](/guides/components/#using-one)Using `one`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function() {
  var myComponent = this;
  console.log('myFunc called');
};
myComponent.one('eventName', myFunc);
myComponent.trigger('eventName');
// logs 'myFunc called'

myComponent.trigger('eventName');
// does nothing
```

You can also add a listener to another element or component that will get triggered only once.

```js
var otherComponent = new Component(player);

// myComponent/myFunc is from the above example
myComponent.one(otherComponent.el(), 'eventName', myFunc);
myComponent.one(otherComponent, 'eventName', myFunc);

otherComponent.trigger('eventName');
// logs 'myFunc called' twice

otherComponent.trigger('eventName');
// does nothing
```

### [](/guides/components/#using-trigger)Using `trigger`

```js
var player = videojs('some-player-id');
var Component = videojs.getComponent('Component');
var myComponent = new Component(player);
var myFunc = function(data) {
  var myComponent = this;
  console.log('myFunc called');
  console.log(data);
};
myComponent.one('eventName', myFunc);
myComponent.trigger('eventName');
// logs 'myFunc called' and 'undefined'

myComponent.trigger({'type':'eventName'});
// logs 'myFunc called' and 'undefined'

myComponent.trigger('eventName', {data: 'some data'});
// logs 'myFunc called' and "{data: 'some data'}"

myComponent.trigger({'type':'eventName'}, {data: 'some data'});
// logs 'myFunc called' and "{data: 'some data'}"
```

## [](/guides/components/#default-component-tree)Default Component Tree

The default component structure of the Video.js player looks something like this:

```text
Player
├── MediaLoader (has no DOM element)
├── PosterImage
├── TextTrackDisplay
├── LoadingSpinner
├── BigPlayButton
├── LiveTracker (has no DOM element)
├─┬ ControlBar
│ ├── PlayToggle
│ ├── VolumePanel
│ ├── CurrentTimeDisplay (hidden by default)
│ ├── TimeDivider (hidden by default)
│ ├── DurationDisplay (hidden by default)
│ ├─┬ ProgressControl (hidden during live playback, except when liveui: true)
│ │ └─┬ SeekBar
│ │   ├── LoadProgressBar
│ │   ├── MouseTimeDisplay
│ │   └── PlayProgressBar
│ ├── LiveDisplay (hidden during VOD playback)
│ ├── SeekToLive (hidden during VOD playback)
│ ├── RemainingTimeDisplay
│ ├── CustomControlSpacer (has no UI)
│ ├── PlaybackRateMenuButton (hidden, unless playback tech supports rate changes)
│ ├── ChaptersButton (hidden, unless there are relevant tracks)
│ ├── DescriptionsButton (hidden, unless there are relevant tracks)
│ ├── SubsCapsButton (hidden, unless there are relevant tracks)
│ ├── AudioTrackButton (hidden, unless there are relevant tracks)
│ ├── PictureInPictureToggle
│ └── FullscreenToggle
├── ErrorDisplay (hidden, until there is an error)
├── TextTrackSettings
└── ResizeManager (hidden)
```

## [](/guides/components/#specific-component-details)Specific Component Details

### [](/guides/components/#play-toggle)Play Toggle

The `PlayToggle` has one option `replay` which can show or hide replay icon. This can be set by passing `{replay: false}` as the default behavior replay icon is shown after video end playback.

Example of how to hide a replay icon

```js
let player = videojs('myplayer', {
  controlBar: {
    playToggle: {
      replay: false
    }
  }
});
```

### [](/guides/components/#volume-panel)Volume Panel

The `VolumePanel` includes the `MuteToggle` and the `VolumeControl` Components, which will be hidden if volume changes are not supported. There is one important option for the `VolumePanel` which can make your `VolumeControl` appear vertically over the `MuteToggle`. This can be set by passing `VolumePanel` `{inline: false}` as the default behavior is a horizontal `VolumeControl` with `{inline: true}`.

Example of a vertical `VolumeControl`

```js
let player = videojs('myplayer', {
  controlBar: {
    volumePanel: {
      inline: false
    }
  }
});
```

### [](/guides/components/#text-track-settings)Text Track Settings

The text track settings component is only available when using emulated text tracks.

### [](/guides/components/#resize-manager)Resize Manager

This new component is in charge of triggering a `playerresize` event when the player size changed. It uses the ResizeObserver if available or a polyfill was provided. It has no element when using the ResizeObserver. If a ResizeObserver is not available, it will fallback to an iframe element and listen to its resize event via a debounced handler.

A ResizeObserver polyfill can be passed in like so:

```js
var player = videojs('myplayer', {
  resizeManager: {
    ResizeObserver: ResizeObserverPoylfill
  }
});
```

To force using the iframe fallback, pass in `null` as the `ResizeObserver`:

```js
var player = videojs('myplayer', {
  resizeManager: {
    ResizeObserver: null
  }
});
```

The ResizeManager can also just be disabled like so:

```js
var player = videojs('myplayer', {
  resizeManager: false
});
```

---

# Embed a Video.js Player | Video.js

**URL:** https://videojs.org/guides/embeds

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Embed a Video.js Player

## Table of Contents

*   [Embeds](#embeds)
    *   [<video> embed](#video-embed)
    *   [Player div ingest](#player-div-ingest)
    *   [<video-js> embed](#video-js-embed)
        *   [Custom Elements](#custom-elements)
*   [data-setup](#data-setup)

Video.js is meant to be an enhancement to the video element in HTML5 and for years, its embed code has been just a `<video>` element. Video.js then wraps the video element in a div that is used for us to place controls and anything else that's required for the player.

For a long time this was enough. In 2016, "div ingest" was added, and it allows the developer to give Video.js a player div to use instead of making it's own. This is partly to help with content reflow but also to help with iOS where you sometimes need to prime the video element and we re-create the video element when we create the player div. However, this is kind of weird to have a `<video>` element embed with a `<div>` wrapped around it. So, we built out a new embed, a `<video-js>` embed.

Below, the three kinds of embeds are detailed.

## [](/guides/embeds/#embeds)Embeds

### [](/guides/embeds/#video-embed)`<video>` embed

The classic Video.js embed. You can then initialize it via `data-setup` or via the `videojs` method.

```html
<!-- via data-setup -->
<video id="vid1" class="video-js" data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video>

<!-- via code -->
<video id="vid1" class="video-js">
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video>
```

```js
const player = videojs('vid1', {});
```

### [](/guides/embeds/#player-div-ingest)Player div ingest

The enhanced classic embed. You can also initialize it via `data-setup` or via the `videojs` method.

```html
<!-- via data-setup -->
<div data-vjs-player>
  <video id="vid1" class="video-js" data-setup='{}'>
    <source src="//vjs.zencdn.net/v/oceans.mp4">
  </video>
</div>

<!-- via code -->
<div data-vjs-player>
  <video id="vid1" class="video-js">
    <source src="//vjs.zencdn.net/v/oceans.mp4">
  </video>
</div>
```

```js
const player = videojs('vid1', {});
```

As you can see, it isn't much different from the classic `<video>` embed. It also does make it easier to work with [React](/guides/react).

### [](/guides/embeds/#video-js-embed)`<video-js>` embed

This is the [I Can't Believe It's Not Custom Elements](https://developers.google.com/web/fundamentals/web-components/customelements) embed code. It looks very much like the `<video>` embed but instead of `video` it's a `video-js` embed. This is useful for all the things that the player div ingest is useful for and it matches our library name!

```html
<!-- via data-setup -->
<video-js id="vid1" data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video-js>

<!-- via code -->
<video-js id="vid1">
  <source src="//vjs.zencdn.net/v/oceans.mp4">
</video-js>
```

```js
const player = videojs('vid1', {});
```

Adding `class="video-js"` with this embed is no longer necessary as it will automatically add the class `video-js` if missing.

#### [](/guides/embeds/#custom-elements)Custom Elements

Native Custom Elements support is relatively small according to [Can I Use](https://caniuse.com/#feat=custom-elementsv1) and because we didn't want to include a polyfill we're going with just an element called `video-js` rather than a full blown custom element.

## [](/guides/embeds/#data-setup)data-setup

This is an ease-of-use method for having Video.js set up the player automatically. It is an HTML attribute and it takes a JSON string representation of the [player options](/guides/options) as the value. Using the programmatic approach is probably preferable.

---

# Video.js Options Reference | Video.js

**URL:** https://videojs.org/guides/options

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video.js Options Reference

## Table of Contents

*   [Standard <video> Element Options](#standard-video-element-options)
    *   [autoplay](#autoplay)
        *   [More info on autoplay support and changes:](#more-info-on-autoplay-support-and-changes)
    *   [controlBar.remainingTimeDisplay.displayNegative](#controlbarremainingtimedisplaydisplaynegative)
    *   [controls](#controls)
    *   [height](#height)
    *   [loop](#loop)
    *   [muted](#muted)
    *   [poster](#poster)
    *   [preload](#preload)
        *   ['auto'](#auto)
        *   ['metadata'](#metadata)
        *   ['none'](#none)
    *   [src](#src)
    *   [width](#width)
*   [Video.js-specific Options](#videojs-specific-options)
    *   [aspectRatio](#aspectratio)
    *   [audioOnlyMode](#audioonlymode)
    *   [audioPosterMode](#audiopostermode)
    *   [autoSetup](#autosetup)
    *   [breakpoints](#breakpoints)
    *   [children](#children)
    *   [disablePictureInPicture](#disablepictureinpicture)
    *   [enableDocumentPictureInPicture](#enabledocumentpictureinpicture)
    *   [enableSmoothSeeking](#enablesmoothseeking)
    *   [experimentalSvgIcons](#experimentalsvgicons)
    *   [fluid](#fluid)
    *   [fullscreen](#fullscreen)
        *   [options](#options)
    *   [id](#id)
    *   [inactivityTimeout](#inactivitytimeout)
    *   [language](#language)
    *   [languages](#languages)
    *   [liveui](#liveui)
    *   [liveTracker.trackingThreshold](#livetrackertrackingthreshold)
    *   [liveTracker.liveTolerance](#livetrackerlivetolerance)
    *   [nativeControlsForTouch](#nativecontrolsfortouch)
    *   [normalizeAutoplay](#normalizeautoplay)
    *   [notSupportedMessage](#notsupportedmessage)
    *   [noUITitleAttributes](#nouititleattributes)
    *   [playbackRates](#playbackrates)
    *   [playsinline](#playsinline)
    *   [plugins](#plugins)
    *   [posterImage](#posterimage)
    *   [preferFullWindow](#preferfullwindow)
    *   [responsive](#responsive)
    *   [restoreEl](#restoreel)
    *   [skipButtons](#skipbuttons)
    *   [skipButtons.forward](#skipbuttonsforward)
    *   [skipButtons.backward](#skipbuttonsbackward)
    *   [sources](#sources)
    *   [suppressNotSupportedError](#suppressnotsupportederror)
    *   [techCanOverridePoster](#techcanoverrideposter)
    *   [techOrder](#techorder)
    *   [userActions](#useractions)
    *   [userActions.click](#useractionsclick)
    *   [userActions.doubleClick](#useractionsdoubleclick)
    *   [userActions.hotkeys](#useractionshotkeys)
    *   [userActions.hotkeys.fullscreenKey](#useractionshotkeysfullscreenkey)
    *   [userActions.hotkeys.muteKey](#useractionshotkeysmutekey)
    *   [userActions.hotkeys.playPauseKey](#useractionshotkeysplaypausekey)
    *   [vtt.js](#vttjs)
    *   [Spatial Navigation](#spatial-navigation)
        *   [Properties](#properties)
        *   [Usage](#usage)
*   [Component Options](#component-options)
    *   [children](#children-1)
    *   [${componentName}](#componentname)
*   [Tech Options](#tech-options)
    *   [${techName}](#techname)
    *   [html5](#html5)
        *   [nativeControlsForTouch](#nativecontrolsfortouch-1)
        *   [nativeAudioTracks](#nativeaudiotracks)
        *   [nativeTextTracks](#nativetexttracks)
        *   [nativeVideoTracks](#nativevideotracks)
        *   [preloadTextTracks](#preloadtexttracks)

> **Note:** This document is only a reference for available options. To learn about passing options to Video.js, see [the setup guide](/guides/setup#options).

## [](/guides/options/#standard-video-element-options)Standard `<video>` Element Options

Each of these options is also available as a [standard `<video>` element attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#Attributes); so, they can be defined in all three manners [outlined in the setup guide](/guides/setup#options). Typically, defaults are not listed as this is left to browser vendors.

### [](/guides/options/#autoplay)`autoplay`

> Type: `boolean|string` NOTE: At this point, the autoplay attribute and option are NOT a guarantee that your video will autoplay. NOTE2: If there is an attribute on the media element the option will be ignored. NOTE3: You cannot pass a string value in the attribute, you must pass it in the videojs options

Instead of using the `autoplay` attribute you should pass an `autoplay` option to the `videojs` function. The following values are valid:

*   a boolean value of `false`: the same as having no attribute on the video element, won't `autoplay`
*   a boolean value of `true`: the same as having attribute on the video element, will use browsers `autoplay`
*   a string value of `'muted'`: will mute the video element and then manually call `play()` on `loadstart`. This is likely to work.
*   a string value of `'play'`: will call `play()` on `loadstart`, similar to browsers `autoplay`
*   a string value of `'any'`: will call `play()` on `loadstart` and if the promise is rejected it will mute the video element then call `play()`.

To pass the option

```js
var player = videojs('my-video', {
  autoplay: 'muted'
});

// or

player.autoplay('muted');
```

#### [](/guides/options/#more-info-on-autoplay-support-and-changes)More info on autoplay support and changes:

*   See our blog post: [Autoplay Best Practices with Video.js](https://videojs.com/blog/autoplay-best-practices-with-video-js/)

### [](/guides/options/#controlbarremainingtimedisplaydisplaynegative)`controlBar.remainingTimeDisplay.displayNegative`

> Type: `boolean`

By default the remaining time display shows as negative time. To not show the negative sign set `controlBar.remainingTimeDisplay.displayNegative` to `false`.

### [](/guides/options/#controls)`controls`

> Type: `boolean`

Determines whether or not the player has controls that the user can interact with. Without controls the only way to start the video playing is with the `autoplay` attribute or through the Player API.

### [](/guides/options/#height)`height`

> Type: `string|number`

Sets the display height of the video player in pixels.

### [](/guides/options/#loop)`loop`

> Type: `boolean`

Causes the video to start over as soon as it ends.

### [](/guides/options/#muted)`muted`

> Type: `boolean`

Will silence any audio by default.

### [](/guides/options/#poster)`poster`

> Type: `string`

A URL to an image that displays before the video begins playing. This is often a frame of the video or a custom title screen. As soon as the user hits "play" the image will go away.

### [](/guides/options/#preload)`preload`

> Type: `string`

Suggests to the browser whether or not the video data should begin downloading as soon as the `<video>` element is loaded. Supported values are:

#### [](/guides/options/#auto)`'auto'`

Start loading the video immediately (if the browser supports it). Some mobile devices will not preload the video in order to protect their users' bandwidth/data usage. This is why the value is called 'auto' and not something more conclusive like `'true'`.

_This tends to be the most common and recommended value as it allows the browser to choose the best behavior._

#### [](/guides/options/#metadata)`'metadata'`

Load only the meta data of the video, which includes information like the duration and dimensions of the video. Sometimes, the meta data will be loaded by downloading a few frames of video.

#### [](/guides/options/#none)`'none'`

Don't preload any data. The browser will wait until the user hits "play" to begin downloading.

### [](/guides/options/#src)`src`

> Type: `string`

The source URL to a video source to embed.

### [](/guides/options/#width)`width`

> Type: `string|number`

Sets the display width of the video player in pixels.

## [](/guides/options/#videojs-specific-options)Video.js-specific Options

Each option is `undefined` by default unless otherwise specified.

### [](/guides/options/#aspectratio)`aspectRatio`

> Type: `string`

Puts the player in [fluid](/guides/options/#fluid) mode and the value is used when calculating the dynamic size of the player. The value should represent a ratio - two numbers separated by a colon (e.g. `"16:9"` or `"4:3"`).

Alternatively, the classes `vjs-16-9`, `vjs-9-16`, `vjs-4-3` or `vjs-1-1` can be added to the player.

### [](/guides/options/#audioonlymode)`audioOnlyMode`

> Type: `boolean` Default: `false`

If set to true, it asynchronously hides all player components except the control bar, as well as any specific controls that are needed only for video. This option can be set to `true` or `false` by calling `audioOnlyMode([true|false])` at runtime. When used as a setter, it returns a Promise. When used as a getter, it returns a Boolean.

### [](/guides/options/#audiopostermode)`audioPosterMode`

> Type: `boolean` Default: `false`

If set to true, it enables the poster viewer experience by hiding the video element and displaying the poster image persistently. This option can be set to `true` or `false` by calling `audioPosterMode([true|false])` at runtime.

### [](/guides/options/#autosetup)`autoSetup`

> Type: `boolean`

Prevents the player from running the autoSetup for media elements with `data-setup` attribute.

> **Note**: this must be set globally with `videojs.options.autoSetup = false` in the same tick as videojs source is loaded to take effect.

### [](/guides/options/#breakpoints)`breakpoints`

> Type: `Object`

When used with the [`responsive` option](/guides/options/#responsive), sets breakpoints that will configure how class names are toggled on the player to adjust the UI based on the player's dimensions.

By default, the breakpoints are:

| Class Name | Width Range |
| --- | --- |
| `vjs-layout-tiny` | 0-210 |
| `vjs-layout-x-small` | 211-320 |
| `vjs-layout-small` | 321-425 |
| `vjs-layout-medium` | 426-768 |
| `vjs-layout-large` | 769-1440 |
| `vjs-layout-x-large` | 1441-2560 |
| `vjs-layout-huge` | 2561+ |

While the class names cannot be changed, the width ranges can be configured via an object like this:

```js
breakpoints: {
  tiny: 300,
  xsmall: 400,
  small: 500,
  medium: 600,
  large: 700,
  xlarge: 800,
  huge: 900
}
```

*   The _keys_ of the `breakpoints` object are derived from the associated class names by removing the `vjs-layout-` prefix and any `-` characters.
*   The _values_ of the `breakpoints` object define the max width for a range.
*   Not all keys need to be defined. You can easily override a single breakpoint by passing an object with one key/value pair! Customized breakpoints will be merged with default breakpoints when the player is created.

When the player's size changes, the merged breakpoints will be inspected in the size order until a matching breakpoint is found.

That breakpoint's associated class name will be added as a class to the player. The previous breakpoint's class will be removed.

See the file `sandbox/responsive.html.example` for an example of a responsive player using the default breakpoints.

### [](/guides/options/#children)`children`

> Type: `Array|Object`

This option is inherited from the [`Component` base class](/guides/options/#component-options).

### [](/guides/options/#disablepictureinpicture)`disablePictureInPicture`

> Type: `boolean`

If `true`, switching the video element into picture-in-picture is disabled. Default is `false`.

This has no effect on Firefox's proprietary picture-in-picture mode which does not implement the standard picture-in-picture API.

This does not disable the document picture-in-picture mode which allows the player element to put into a PiP window.

### [](/guides/options/#enabledocumentpictureinpicture)`enableDocumentPictureInPicture`

> Type: `boolean`

_Since 8.3.0_

If `true`, the [documentPictureInPicture API](https://developer.chrome.com/docs/web-platform/document-picture-in-picture/) will be used for picture-in-picture, if available. Defaults to `false`, but may default to `true` when the feature has become established.

Supported by [Chrome and Edge from version 116](https://caniuse.com/mdn-api_documentpictureinpicture).

This is a different picture-in-picture mode than has previously been available, where the entire player element is windowed rather than just the video itself. Since there are scenarios where it would be desirable to allow PiP on the player but not PiP on the video alone (such as ads, overlays), the `disablePictureInPicture` option **only** disables the old-style picture-in-picture mode on the video.

### [](/guides/options/#enablesmoothseeking)`enableSmoothSeeking`

> Type: `boolean` Default: `false`

_Since 8.9.0_

If set to `true`, will provide a smoother seeking experience on mobile and desktop devices.

The following will enable the smooth seeking:

```js
videojs('my-player', {
  enableSmoothSeeking: true
});
```

Can also be modified after player creation:

```js
var player = videojs('my-player');

player.options({ enableSmoothSeeking: true });
```

### [](/guides/options/#experimentalsvgicons)`experimentalSvgIcons`

> Type: `boolean`

_Since 8.5.0_

If set to `true`, the icons used throughout the player from [videojs/font](https://github.com/videojs/font) will be replaced by SVGs stored in Video.js. Defaults to `false`, but may default to `true` when the feature has become established.

These SVGs were downloaded from [Font Awesome](https://fontawesome.com/icons) and [Google's Material UI](https://mui.com/material-ui/material-icons/).

You can view all of the icons available by renaming [`sandbox/svg-icons.html.example`](https://github.com/videojs/video.js/blob/main/sandbox/svg-icons.html.example) to `sandbox/svg-icons.html`, building Video.js with `npm run build`, and opening `sandbox/svg-icons.html` in your browser of choice.

Icons are expected to be added to a `Component` inside of the player using the [`setIcon`](/guides/components/#adding-a-component) method when customizing the player.

### [](/guides/options/#fluid)`fluid`

> Type: `boolean`

When `true`, the Video.js player will have a fluid size. In other words, it will scale to fit its container at the video's intrinsic aspect ratio, or at a specified [`aspectRatio`](/guides/options/#aspectRatio).

Also, if the `<video>` element has the `"vjs-fluid"`, this option is automatically set to `true`.

### [](/guides/options/#fullscreen)`fullscreen`

> Type: `Object` Default: `{options: {navigationUI: 'hide'}`

`fullscreen.options` can be set to pass in specific fullscreen options. At some point, it will be augmented with `element` and `handler` for more functionality.

#### [](/guides/options/#options)`options`

> Type: `Object` Default: `{navigationUI: 'hide'}`

See [The Fullscreen API Spec](https://fullscreen.spec.whatwg.org/#dictdef-fullscreenoptions) for more details.

### [](/guides/options/#id)`id`

> Type: `string`

If provided, and the element does not already have an `id`, this value is used as the `id` of the player element.

### [](/guides/options/#inactivitytimeout)`inactivityTimeout`

> Type: `number`

Video.js indicates that the user is interacting with the player by way of the `"vjs-user-active"` and `"vjs-user-inactive"` classes and the `"useractive"` event.

The `inactivityTimeout` determines how many milliseconds of inactivity is required before declaring the user inactive. A value of `0` indicates that there is no `inactivityTimeout` and the user will never be considered inactive.

### [](/guides/options/#language)`language`

> Type: `string`, Default: browser default or `'en'`

A [language code](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) matching one of the available languages in the player. This sets the initial language for a player, but it can always be changed.

Learn more about [languages in Video.js](/guides/languages).

### [](/guides/options/#languages)`languages`

> Type: `Object`

Customize which languages are available in a player. The keys of this object will be [language codes](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) and the values will be objects with English keys and translated values.

Learn more about [languages in Video.js](/guides/languages)

> **Note**: Generally, this option is not needed and it would be better to pass your custom languages to `videojs.addLanguage()`, so they are available in all players!

### [](/guides/options/#liveui)`liveui`

> Type: `boolean` Default: `false`

Allows the player to use the new live ui that includes:

*   A progress bar for seeking within the live window
*   A button that can be clicked to seek to the live edge with a circle indicating if you are at the live edge or not.

Without this option the progress bar will be hidden and in its place will be text that indicates `LIVE` playback. There will be no progress control and you will not be able click the text to seek to the live edge. `liveui` will default to `true` in a future version!

### [](/guides/options/#livetrackertrackingthreshold)`liveTracker.trackingThreshold`

> Type: `number` Default: `20`

An option for the liveTracker component of the player that controls when the liveui should be shown. By default if a stream has less than 20s on the seekBar then we do not show the new liveui even with the liveui option set.

### [](/guides/options/#livetrackerlivetolerance)`liveTracker.liveTolerance`

> Type: `number` Default: `15`

An option for the liveTracker component of the player that controls how far from the seekable end should be considered live playback. By default anything further than 15s from the live seekable edge is considered behind live and everything else is considered live. Any user interaction to seek backwards will ignore this value as a user would expect.

### [](/guides/options/#nativecontrolsfortouch)`nativeControlsForTouch`

> Type: `boolean`

Explicitly set a default value for [the associated tech option](/guides/options/#nativecontrolsfortouch).

### [](/guides/options/#normalizeautoplay)`normalizeAutoplay`

> Type: `boolean`

Specify whether setting `autoplay: true` and `<video autoplay>` should be treated the same as `autoplay: 'play'`, i.e. the `autoplay` attribute should be removed from (or not added to) the video element and `play()` be initiated manually by Video.js rather than the browser.

### [](/guides/options/#notsupportedmessage)`notSupportedMessage`

> Type: `string`

Allows overriding the default message that is displayed when Video.js cannot play back a media source.

### [](/guides/options/#nouititleattributes)`noUITitleAttributes`

> Type: `boolean` Default: `false`

Control whether UI elements have a `title` attribute. A `title` attribute is shown on mouse hover, which can be helpful for usability, but has drawbacks for accessibility. Setting `noUITitleAttributes` to `true` prevents the `title` attribute from being added to UI elements, allowing for more accessible tooltips to be added to controls by a plugin or external framework.

### [](/guides/options/#playbackrates)`playbackRates`

> Type: `Array`

An array of numbers strictly greater than 0, where 1 means regular speed (100%), 0.5 means half-speed (50%), 2 means double-speed (200%), etc. If specified, Video.js displays a control (of class `vjs-playback-rate`) allowing the user to choose playback speed from among the array of choices. The choices are presented in the specified order from bottom to top.

For example:

```js
videojs('my-player', {
  playbackRates: [0.5, 1, 1.5, 2]
});
```

### [](/guides/options/#playsinline)`playsinline`

> Type: `boolean`

_Since 6.1.0_

Indicates to the browser that non-fullscreen playback is preferred when fullscreen playback is the native default, such as in iOS Safari.

For example:

```js
videojs('my-player', {
  playsinline: true
});
```

### [](/guides/options/#plugins)`plugins`

> Type: `Object`

This supports having plugins be initialized automatically with custom options when the player is initialized - rather than requiring you to initialize them manually.

```js
videojs('my-player', {
  plugins: {
    foo: {bar: true},
    boo: {baz: false}
  }
});
```

The above is roughly equivalent to:

```js
var player = videojs('my-player');

player.foo({bar: true});
player.boo({baz: false});
```

Although, since the `plugins` option is an object, the order of initialization is not guaranteed!

See [the plugins guide](/guides/plugins) for more information on Video.js plugins.

### [](/guides/options/#posterimage)`posterImage`

> Type: `boolean`, Defaut: `true`

Setting this to false removes Video.js's poster element.

### [](/guides/options/#preferfullwindow)`preferFullWindow`

> Type: `boolean`, Defaut: `false`

Setting this to `true` will change fullscreen behaviour on devices which do not support the HTML5 fullscreen API but do support fullscreen on the video element, i.e. iPhone. Instead of making the video fullscreen, the player will be stretched to fill the browser window.

### [](/guides/options/#responsive)`responsive`

> Type: `boolean`, Default: `false`

Setting this option to `true` will cause the player to customize itself based on responsive breakpoints (see: [`breakpoints` option](/guides/options/#breakpoints)).

When this option is `false` (the default), responsive breakpoints will be ignored.

> Note this is about the responsiveness of the controls within the player, not responsive sizing of the player itself. For that, see [fluid](/guides/options/#fluid).

### [](/guides/options/#restoreel)`restoreEl`

> Type `boolean` or `Element`, Default: false

If set to `true`, a _copy_ of the placeholder element will be made before the player is initalised. If the player is disposed, the copy is put back into the DOM in the player's place.

If set to an HTML Element, that element would replace the disposed player instead.

### [](/guides/options/#skipbuttons)`skipButtons`

> Type: `Object`

_Since 8.2.0_

### [](/guides/options/#skipbuttonsforward)`skipButtons.forward`

> Type: `number`

_Since 8.2.0_

If specified, Video.js displays a control allowing the user to jump forward in a video by the specified number of seconds.

The following values are valid: **5 | 10 | 30**

```js
videojs('my-player', {
  controlBar: {
    skipButtons: {
      forward: 5
    }
  }
});
```

### [](/guides/options/#skipbuttonsbackward)`skipButtons.backward`

> Type: `number`

_Since 8.2.0_

If specified, Video.js displays a control allowing the user to jump back in a video by the specified number of seconds.

The following values are valid: **5 | 10 | 30**

```js
videojs('my-player', {
  controlBar: {
    skipButtons: {
      backward: 10
    }
  }
});
```

### [](/guides/options/#sources)`sources`

> Type: `Array`

An array of objects that mirror the native `<video>` element's capability to have a series of child `<source>` elements. This should be an array of objects with the `src` and `type` properties. For example:

```js
videojs('my-player', {
  sources: [{
    src: '//path/to/video.mp4',
    type: 'video/mp4'
  }, {
    src: '//path/to/video.webm',
    type: 'video/webm'
  }]
});
```

Using `<source>` elements will have the same effect:

```html
<video ...>
  <source src="//path/to/video.mp4" type="video/mp4">
  <source src="//path/to/video.webm" type="video/webm">
</video>
```

### [](/guides/options/#suppressnotsupportederror)`suppressNotSupportedError`

> Type: `boolean`

If set to true, then the no compatible source error will not be triggered immediately and instead will occur on the first user interaction. This is useful for Google's "mobile friendly" test tool, which can't play video but where you might not want to see an error displayed.

### [](/guides/options/#techcanoverrideposter)`techCanOverridePoster`

> Type: `boolean`

Gives the possibility to techs to override the player's poster and integrate into the player's poster life-cycle. This can be useful when multiple techs are used and each has to set their own poster any time a new source is played.

### [](/guides/options/#techorder)`techOrder`

> Type: `Array`, Default: `['html5']`

Defines the order in which Video.js techs are preferred. By default, this means that the `Html5` tech is preferred. Other registered techs will be added after this tech in the order in which they are registered.

### [](/guides/options/#useractions)`userActions`

> Type: `Object`

### [](/guides/options/#useractionsclick)`userActions.click`

> Type: `boolean|function`

Controls how clicking on the player/tech operates. If set to `false`, clicking is disabled and will no longer cause the player to toggle between paused and playing. If controls are disabled with `controls: false`, this will not call the handler function.

```js
videojs('my-player', {
  userActions: {
    click: false
  }
});
```

If undefined or set to `true`, clicking is enabled and toggles the player between paused and play. To override the default click handling, set `userActions.click` to a function which accepts a `click` event (in this example it will request Full Screen, the same as a `userActions.doubleClick`):

```js
function myClickHandler(event) = {
  // `this` is the player in this context

  if (this.isFullscreen()) {
      this.exitFullscreen();
    } else {
      this.requestFullscreen();
    }
};

videojs('my-player', {
  userActions: {
    click: myClickHandler
  }
});
```

### [](/guides/options/#useractionsdoubleclick)`userActions.doubleClick`

> Type: `boolean|function`

Controls how double-clicking on the player/tech operates. If set to `false`, double-clicking is disabled. If undefined or set to `true`, double-clicking is enabled and toggles fullscreen mode. To override the default double-click handling, set `userActions.doubleClick` to a function which accepts a `dblclick` event:

```js
function myDoubleClickHandler(event) = {
  // `this` is the player in this context

  this.pause();
};

videojs('my-player', {
  userActions: {
    doubleClick: myDoubleClickHandler
  }
});
```

### [](/guides/options/#useractionshotkeys)`userActions.hotkeys`

> Type: `boolean|function|object`

Controls how player-wide hotkeys operate. If set to `false`, or `undefined`, hotkeys are disabled. If set to `true` or an object (to allow definitions of `fullscreenKey` etc. below), hotkeys are enabled as described below. To override the default hotkey handling, set `userActions.hotkeys` to a function which accepts a `keydown` event. If controls are disabled with `controls: false`, this will not call the handler function.

```js
var player = videojs('my-player', {
  userActions: {
    hotkeys: function(event) {
      // `this` is the player in this context

      // `x` key = pause
      if (event.which === 88) {
        this.pause();
      }
      // `y` key = play
      if (event.which === 89) {
        this.play();
      }
    }
  }
});
```

Default hotkey handling is:

| Key | Action | Enabled by |
| :-: | --- | --- |
| `f` | toggle fullscreen | only enabled if a Fullscreen button is present in the Control Bar |
| `m` | toggle mute | always enabled, even if no Control Bar is present |
| `k` | toggle play/pause | always enabled, even if no Control Bar is present |
| `Space` | toggle play/pause | always enabled, even if no Control Bar is present |

Hotkeys require player focus first. Note that the `Space` key activates controls such as buttons and menus if that control has keyboard focus. The other hotkeys work regardless of which control in the player has focus.

### [](/guides/options/#useractionshotkeysfullscreenkey)`userActions.hotkeys.fullscreenKey`

> Type: `function`

Override the fullscreen key definition. If this is set, the function receives the `keydown` event; if the function returns `true`, then the fullscreen toggle action is performed.

```js
var player = videojs('my-player', {
  userActions: {
    hotkeys: {
      muteKey: function(event) {
        // disable mute key
      },
      fullscreenKey: function(event) {
        // override fullscreen to trigger when pressing the v key
        return (event.which === 86);
      }
    }
  }
});
```

### [](/guides/options/#useractionshotkeysmutekey)`userActions.hotkeys.muteKey`

> Type: `function`

Override the mute key definition. If this is set, the function receives the `keydown` event; if the function returns `true`, then the mute toggle action is performed.

### [](/guides/options/#useractionshotkeysplaypausekey)`userActions.hotkeys.playPauseKey`

> Type: `function`

Override the play/pause key definition. If this is set, the function receives the `keydown` event; if the function returns `true`, then the play/pause toggle action is performed.

### [](/guides/options/#vttjs)`vtt.js`

> Type: `string`

Allows overriding the default URL to vtt.js, which may be loaded asynchronously to polyfill support for `WebVTT`.

This option will be used in the "novtt" build of Video.js (i.e. `video.novtt.js`). Otherwise, vtt.js is bundled with Video.js.

### [](/guides/options/#spatial-navigation)Spatial Navigation

`spatialNavigation`

Type: `Object` Default: `{enabled: false, horizontalSeek: false}`

This option configures the Spatial Navigation within the Video.js player, enhancing accessibility and user experience on devices like smart TVs, where navigation through remote control is common.

#### [](/guides/options/#properties)Properties

*   **enabled** Type: `boolean` Default: `false` If set to `true`, enables the Spatial Navigation system in the player, allowing users to navigate through focusable components using the arrow keys on their remote control.
    
*   **horizontalSeek** Type: `boolean` Default: `false` When enabled, this allows users to use the left and right arrow keys for seeking through the video timeline, enhancing the navigation experience.
    

#### [](/guides/options/#usage)Usage

To enable Spatial Navigation with the default settings:

```js
var player = videojs('my-player', {
  spatialNavigation: {
    enabled: true
  }
});
```

To enable Spatial Navigation with horizontal seeking:

```js
var player = videojs('my-player', {
  spatialNavigation: {
    enabled: true,
    horizontalSeek: true
  }
});
```

## [](/guides/options/#component-options)Component Options

The Video.js player is a component. Like all components, you can define what children it includes, what order they appear in, and what options are passed to them.

This is meant to be a quick reference; so, for more detailed information on components in Video.js, check out the [components guide](/guides/components).

### [](/guides/options/#children-1)`children`

> Type: `Array|Object`

If an `Array` - which is the default - this is used to determine which children (by component name) and in which order they are created on a player (or other component):

```js
// The following code creates a player with ONLY bigPlayButton and
// controlBar child components.
videojs('my-player', {
  children: [
    'bigPlayButton',
    'controlBar'
  ]
});
```

The `children` options can also be passed as an `Object`. In this case, it is used to provide `options` for any/all children, including disabling them with `false`:

```js
// This player's ONLY child will be the controlBar. Clearly, this is not the
// ideal method for disabling a grandchild!
videojs('my-player', {
  children: {
    controlBar: {
      fullscreenToggle: false
    }
  }
});
```

### [](/guides/options/#componentname)`${componentName}`

> Type: `Object`

Components can be given custom options via the _lower-camel-case variant of the component name_ (e.g. `controlBar` for `ControlBar`). These can be nested in a representation of grandchild relationships. For example, to disable the fullscreen control:

```js
videojs('my-player', {
  controlBar: {
    fullscreenToggle: false
  }
});
```

## [](/guides/options/#tech-options)Tech Options

### [](/guides/options/#techname)`${techName}`

> Type: `Object`

Video.js playback technologies (i.e. "techs") can be given custom options as part of the options passed to the `videojs` function. They should be passed under the _lower-case variant of the tech name_ (e.g. `"html5"`).

### [](/guides/options/#html5)`html5`

#### [](/guides/options/#nativecontrolsfortouch-1)`nativeControlsForTouch`

> Type: `boolean`

Only supported by the `Html5` tech, this option can be set to `true` to force native controls for touch devices.

#### [](/guides/options/#nativeaudiotracks)`nativeAudioTracks`

> Type: `boolean`

Can be set to `false` to disable native audio track support. Most commonly used with [videojs-contrib-hls](https://github.com/videojs/videojs-contrib-hls).

#### [](/guides/options/#nativetexttracks)`nativeTextTracks`

> Type: `boolean`

Can be set to `false` to force emulation of text tracks instead of native support. The `nativeCaptions` option also exists, but is simply an alias to `nativeTextTracks`.

#### [](/guides/options/#nativevideotracks)`nativeVideoTracks`

> Type: `boolean`

Can be set to `false` to disable native video track support. Most commonly used with [videojs-contrib-hls](https://github.com/videojs/videojs-contrib-hls).

#### [](/guides/options/#preloadtexttracks)`preloadTextTracks`

> Type: `boolean`

Can be set to `false` to delay loading of non-active text tracks until use. This can cause a short delay when switching captions during which there may be missing captions.

The default behavior is to preload all text tracks.

---

# React and Video.js | Video.js

**URL:** https://videojs.org/guides/react

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# React and Video.js

## Table of Contents

*   [React Functional Component and useEffect Example](#react-functional-component-and-useeffect-example)
*   [React Class Component Example](#react-class-component-example)
*   [Using a React Component within a Video.js Component](#using-a-react-component-within-a-videojs-component)

These are several React and Video.js player implementations and examples.

Don't forget to include the Video.js CSS, located at `video.js/dist/video-js.css`!

## [](/guides/react/#react-functional-component-and-useeffect-example)React Functional Component and `useEffect` Example

```jsx
import React from 'react';
import videojs from 'video.js';
import 'video.js/dist/video-js.css';

export const VideoJS = (props) => {
  const videoRef = React.useRef(null);
  const playerRef = React.useRef(null);
  const {options, onReady} = props;

  React.useEffect(() => {

    // Make sure Video.js player is only initialized once
    if (!playerRef.current) {
      // The Video.js player needs to be _inside_ the component el for React 18 Strict Mode. 
      const videoElement = document.createElement("video-js");

      videoElement.classList.add('vjs-big-play-centered');
      videoRef.current.appendChild(videoElement);

      const player = playerRef.current = videojs(videoElement, options, () => {
        videojs.log('player is ready');
        onReady && onReady(player);
      });

    // You could update an existing player in the `else` block here
    // on prop change, for example:
    } else {
      const player = playerRef.current;

      player.autoplay(options.autoplay);
      player.src(options.sources);
    }
  }, [options, videoRef]);

  // Dispose the Video.js player when the functional component unmounts
  React.useEffect(() => {
    const player = playerRef.current;

    return () => {
      if (player && !player.isDisposed()) {
        player.dispose();
        playerRef.current = null;
      }
    };
  }, [playerRef]);

  return (
    <div data-vjs-player>
      <div ref={videoRef} />
    </div>
  );
}

export default VideoJS;
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```jsx
import React from 'react';

// This imports the functional component from the previous sample.
import VideoJS from './VideoJS'

const App = () => {
  const playerRef = React.useRef(null);

  const videoJsOptions = {
    autoplay: true,
    controls: true,
    responsive: true,
    fluid: true,
    sources: [{
      src: '/path/to/video.mp4',
      type: 'video/mp4'
    }]
  };

  const handlePlayerReady = (player) => {
    playerRef.current = player;

    // You can handle player events here, for example:
    player.on('waiting', () => {
      videojs.log('player is waiting');
    });

    player.on('dispose', () => {
      videojs.log('player will dispose');
    });
  };

  return (
    <>
      <div>Rest of app here</div>
      <VideoJS options={videoJsOptions} onReady={handlePlayerReady} />
      <div>Rest of app here</div>
    </>
  );
}
```

## [](/guides/react/#react-class-component-example)React Class Component Example

This example component instantiates the Video.js player on `componentDidMount` and destroys it on `componentWillUnmount`.

```jsx
import React from 'react';
import videojs from 'video.js';
import 'video.js/dist/video-js.css';

export default class VideoPlayer extends React.Component {

  // Instantiate a Video.js player when the component mounts
  componentDidMount() {
    this.player = videojs(this.videoNode, this.props, () => {
      videojs.log('onPlayerReady', this);
    });
  }

  // Dispose the player when the component will unmount
  componentWillUnmount() {
    if (this.player) {
      this.player.dispose();
    }
  }

  // Wrap the player in a `div` with a `data-vjs-player` attribute, so Video.js
  // won't create additional wrapper in the DOM.
  //
  // See: https://github.com/videojs/video.js/pull/3856
  render() {
    return (
      <div data-vjs-player>
        <video ref={node => this.videoNode = node} className="video-js"></video>
      </div>
    );
  }
}
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```jsx
const videoJsOptions = {
  autoplay: true,
  controls: true,
  sources: [{
    src: '/path/to/video.mp4',
    type: 'video/mp4'
  }]
}

return <VideoPlayer {...videoJsOptions} />
```

## [](/guides/react/#using-a-react-component-within-a-videojs-component)Using a React Component within a Video.js Component

This example demonstrates using a React component within a Video.js component inside a Video.js player. Through this approach, developers can manage their custom Video.js components through React.

First, a normal React component is created:

```jsx
import {Component} from 'react';

export default class ExampleReactComponent extends Component {
  render() {
    return (
      <div>{this.props.text}</div>
    );
  }
};
```

Within this component, the `vjsBridgeComponent` is available on its `props`. Through this object, methods of the `vjsBridgeComponent` are available.

The Video.js player can be referenced within this React component via the same means:

```jsx
const player = this.props.vjsBridgeComponent.player();
```

Next, a Video.js component is created.

This component renders the React component into itself. Basically, the Video.js component is acting as a bridge between the Video.js player and the React component:

```jsx
import ExampleReactComponent from './example-react-component';
import ReactDOM from 'react-dom';
import videojs from 'video.js';

const VjsComponent = videojs.getComponent('Component');

class ExampleVjsBridgeComponent extends VjsComponent {

  constructor(player, options) {
    super(player, options);

    // Bind the current class context to the mountReactComponent method
    this.mountReactComponent = this.mountReactComponent.bind(this);

    // When player is ready, call method to mount the React component
    player.ready(() => this.mountReactComponent());

    // Remove the React root when this component is destroyed
    this.on('dispose', () => ReactDOM.unmountComponentAtNode(this.el()));
  }

  // This method renders the ExampleReactComponent into the DOM element of
  // the Video.js component, `this.el()`.
  mountReactComponent() {
    ReactDOM.render(
      <ExampleReactComponent vjsBridgeComponent={this} text='Example React Component' />,
      this.el()
    );
  }
}

// Make sure to register the Video.js component so Video.js knows it exists
videojs.registerComponent('exampleVjsBridgeComponent', ExampleVjsBridgeComponent);

export default ExampleVjsBridgeComponent;
```

Finally, the Video.js bridge component can be added to the player like so:

```jsx

// ...

  // Instantiate a Video.js player when the component mounts
  componentDidMount() {
    this.player = videojs(this.videoNode, this.props, () => {
      videojs.log('onPlayerReady', this);
    });

    // Add the ExampleVjsBridgeComponent as a child of the player (or
    // of another component within the player, such as the control bar).
    //
    // You can pass options to your bridge component using the second argument
    // to this method.
    this.player.addChild('exampleVjsBridgeComponent', {});
  }

// ...
```

---

# Player Workflows | Video.js

**URL:** https://videojs.org/guides/player-workflows

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Player Workflows

## Table of Contents

*   [Accessing a player that has already been created on a page](#accessing-a-player-that-has-already-been-created-on-a-page)
*   [Removing Players](#removing-players)
    *   [dispose()](#dispose)
    *   [Checking if a Player is Disposed](#checking-if-a-player-is-disposed)
    *   [Signs of an Undisposed Player](#signs-of-an-undisposed-player)
*   [Showing and Hiding a Player](#showing-and-hiding-a-player)
*   [Changing the volume of a player](#changing-the-volume-of-a-player)
*   [Making the player fullscreen](#making-the-player-fullscreen)
*   [Using Playback information functions](#using-playback-information-functions)
*   [Dealing with the source or the poster on the player](#dealing-with-the-source-or-the-poster-on-the-player)
*   [Accessing the Tech on the player](#accessing-the-tech-on-the-player)
*   [Using Video.js with...](#using-videojs-with)
    *   [jQuery](#jquery)
    *   [React](#react)
    *   [Ember](#ember)
    *   [Angular](#angular)
    *   [Vue](#vue)

This document outlines many considerations for using Video.js for advanced player workflows. Be sure to read [the setup guide](/guides/setup) first!

## [](/guides/player-workflows/#accessing-a-player-that-has-already-been-created-on-a-page)Accessing a player that has already been created on a page

After an instance has been created it can be accessed globally in two ways:

1.  By calling `videojs('example_video_id');`
2.  By using it directly via `videojs.players.example_video_id;`

## [](/guides/player-workflows/#removing-players)Removing Players

No matter the term used for it, web applications are becoming common. Not everything is a static, load-once-and-done web page anymore! This means that developers need to be able to manage the full lifecycle of a video player - from creation to destruction. Video.js supports player removal through the `dispose()` method.

### [](/guides/player-workflows/#dispose)[`dispose()`](https://docs.videojs.com/Player.html#dispose)

This method is available on all Video.js players and [components](https://docs.videojs.com/Component.html#dispose). It is _the only_ supported method of removing a Video.js player from both the DOM and memory. For example, the following code sets up a player and then disposes it when media playback is complete:

```js
var player = videojs('my-player');

player.on('ended', function() {
  this.dispose();
});
```

Calling `dispose()` will have a few effects:

1.  Trigger a `"dispose"` event on the player, allowing for any custom cleanup tasks that need to be run by your integration.
2.  Remove all event listeners from the player.
3.  Remove the player's DOM element(s).
4.  If the [`restoreEl`](/guides/options#restoreel) option was used, then the player's DOM elements are replaced with the stored element, a copy of the original placeholder element if it were set to `true`.

Additionally, these actions are recursively applied to _all_ the player's child components.

> **Note**: Do _not_ remove players via standard DOM removal methods: this will leave listeners and other objects in memory that you might not be able to clean up!

### [](/guides/player-workflows/#checking-if-a-player-is-disposed)Checking if a Player is Disposed

At times, it is useful to know whether or not a player reference in your code is stale. The `isDisposed()` method is available on all components (including players) for this purpose.

### [](/guides/player-workflows/#signs-of-an-undisposed-player)Signs of an Undisposed Player

Seeing an error such as:

```text
TypeError: this.el_.vjs_getProperty is not a function
```

or

```text
TypeError: Cannot read property 'vdata1234567890' of null
```

Suggests that a player or component was removed from the DOM without using `dispose()`. It usually means something tried to trigger an event on it or call a method on it.

## [](/guides/player-workflows/#showing-and-hiding-a-player)Showing and Hiding a Player

It is not recommended that you attempt to toggle the visibility or display of a Video.js player. Instead, players should be created and [disposed](/guides/player-workflows/#removing-players) as needed.

This is relevant to use cases such as displaying a player in a modal/overlay. Rather than keeping a hidden Video.js player in a DOM element, it's recommended that you create the player when the modal opens and dispose it when the modal closes.

This is particularly relevant where memory/resource usage is concerned (e.g. mobile devices).

Depending on the libraries/frameworks in use, an implementation might look something like this:

```js
modal.on('show', function() {
  var videoEl = modal.findEl('video');
  modal.player = videojs(videoEl);
});

modal.on('hide', function() {
  modal.player.dispose();
});
```

## [](/guides/player-workflows/#changing-the-volume-of-a-player)Changing the volume of a player

Volume for a player can be changed through the `volume` function on a player. The volume function accepts a number from 0-1. Calling it without an argument will return the current volume.

Example

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // get
  var howLoudIsIt = myPlayer.volume();
  // set
  myPlayer.volume(0.5); // Set volume to half
});
```

Volume can also be muted (without actually changing the volume value) using the `muted` function. Calling it without an argument will return the current status of muted on the player.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // get, should be false
  console.log(myPlayer.muted());
  // set to true
  myPlayer.muted(true);
  // get should be true
  console.log(myPlayer.muted());
});
```

## [](/guides/player-workflows/#making-the-player-fullscreen)Making the player fullscreen

To check if the player is currently fullscreen call the `isFullscreen` function on a player like so.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // get, should be false
  console.log(myPlayer.isFullscreen());

  // set, tell the player it's in fullscreen
  myPlayer.isFullscreen(true);

  // get, should be true
  console.log(myPlayer.isFullscreen());
});
```

To request that the player enter fullscreen call `requestFullscreen`.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.requestFullscreen();
});
```

To exit fullscreen call `exitFullscreen`

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.requestFullscreen();
  myPlayer.exitFullscreen();
});
```

## [](/guides/player-workflows/#using-playback-information-functions)Using Playback information functions

`play` can be used to start playback on a player that has a source.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.play();
});
```

`pause` can be used to pause playback on a player that is playing.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  myPlayer.play();
  myPlayer.pause();
});
```

`paused` can be used to determine if a player is currently paused.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});

myPlayer.ready(function() {
  // true
  console.log(myPlayer.paused());
  // false
  console.log(!myPlayer.paused());

  myPlayer.play();
  // false
  console.log(myPlayer.paused());
  // true
  console.log(!myPlayer.paused());

  myPlayer.pause();
  // true
  console.log(myPlayer.paused());
  // false
  console.log(!myPlayer.paused());
});
```

`currentTime` will give you the currentTime (in seconds) that playback is currently occuring at.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // set current time to 2 minutes into the video
  myPlayer.currentTime(120);

  // get the current time, should be 120 seconds
  var whereYouAt = myPlayer.currentTime();
});
```

`duration` will give you the total duration of the video that is playing

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  var lengthOfVideo = myPlayer.duration();
});
```

`remainingTime` will give you the seconds that are remaing in the video.

```js
var myPlayer = videojs('some-player-id');
myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
   myPlayer.currentTime(10);

   // should be 10 seconds less than duration
   console.log(myPlayer.remainingTime());
});
```

`buffered` will give you a timeRange object representing the current ranges of time that are ready to be played at a future time.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  var bufferedTimeRange = myPlayer.buffered();

  // number of different ranges of time have been buffered.
  // Usually 1
  var numberOfRanges = bufferedTimeRange.length,

  // Time in seconds when the first range starts.
  // Usually 0
  var firstRangeStart = bufferedTimeRange.start(0),

  // Time in seconds when the first range ends
  var firstRangeEnd = bufferedTimeRange.end(0),

  // Length in seconds of the first time range
  var firstRangeLength = firstRangeEnd - firstRangeStart;
});
```

`bufferedPercent` will give you the the current percentage of the video that is buffered.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
  // example 0.11 aka 11%
  var howMuchIsDownloaded = myPlayer.bufferedPercent();
});
```

## [](/guides/player-workflows/#dealing-with-the-source-or-the-poster-on-the-player)Dealing with the source or the poster on the player

Passing a source to the player via the API. (this can also be done using options)

```js
var myPlayer = videojs('some-player-id');

myPlayer.src('http://www.example.com/path/to/video.mp4');
```

When a string is provided as the source, Video.js will try to infer the video type from the file extension, but this inference will not work in all cases. It is recommended that the source is provided as an object including the type, as below.

**Source Object (or element):** A javascript object containing information about the source file. Use this method if you want the player to determine if it can support the file using the type information.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
```

**Array of Source Objects:** To provide multiple versions of the source so that it can be played using HTML5 across browsers you can use an array of source objects. Video.js will detect which version is supported and load that file.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src([
  {type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'},
  {type: 'video/webm', src: 'http://www.example.com/path/to/video.webm'},
  {type: 'video/ogg', src: 'http://www.example.com/path/to/video.ogv'}
]);
```

Changing or setting the poster via the API. (this can also be done with options)

```js
var myPlayer = videojs('example_video_1');

// set
myPlayer.poster('http://example.com/myImage.jpg');

// get
console.log(myPlayer.poster());
// 'http://example.com/myImage.jpg'
```

## [](/guides/player-workflows/#accessing-the-tech-on-the-player)Accessing the Tech on the player

The tech on the player can be accessed via `tech()`. Passing any argument will silence the warning that is logged.

```js
var myPlayer = videojs('some-player-id');

myPlayer.src({type: 'video/mp4', src: 'http://www.example.com/path/to/video.mp4'});
myPlayer.ready(function() {
   // tech() will log warning without any argument
   var tech = myPlayer.tech(false);
});
```

## [](/guides/player-workflows/#using-videojs-with)Using Video.js with...

### [](/guides/player-workflows/#jquery)jQuery

### [](/guides/player-workflows/#react)React

See [ReactJS integration example](/guides/react)

### [](/guides/player-workflows/#ember)Ember

### [](/guides/player-workflows/#angular)Angular

See [Angular integration example](/docs/guides/angular.md)

### [](/guides/player-workflows/#vue)Vue

See [Vue integration example](/guides/vue)

---

# Troubleshooting | Video.js

**URL:** https://videojs.org/guides/troubleshooting

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Troubleshooting

## Table of Contents

*   [Problems with media formats](#problems-with-media-formats)
    *   [Choosing a video format](#choosing-a-video-format)
        *   [I want to have a single source and don't care about live/adaptive streaming:](#i-want-to-have-a-single-source-and-dont-care-about-liveadaptive-streaming)
        *   [I need adaptive streaming or live streaming](#i-need-adaptive-streaming-or-live-streaming)
    *   [Make sure you are using formats that Video.js can play:](#make-sure-you-are-using-formats-that-videojs-can-play)
    *   [Make sure that the codec used in the file container is supported:](#make-sure-that-the-codec-used-in-the-file-container-is-supported)
    *   [If you are using Flash videos:](#if-you-are-using-flash-videos)
*   [Problems when hosting media](#problems-when-hosting-media)
*   [Problems with fullscreen](#problems-with-fullscreen)
*   [Problems with playback](#problems-with-playback)
*   [Video.js Errors](#videojs-errors)
    *   [vdata123456 errors](#vdata123456-errors)
    *   [Uncaught ReferenceError: X is not defined](#uncaught-referenceerror-x-is-not-defined)

## [](/guides/troubleshooting/#problems-with-media-formats)Problems with media formats

### [](/guides/troubleshooting/#choosing-a-video-format)Choosing a video format

#### [](/guides/troubleshooting/#i-want-to-have-a-single-source-and-dont-care-about-liveadaptive-streaming)I want to have a single source and don't care about live/adaptive streaming:

Most browsers now play [MP4 with h264](https://caniuse.com/#feat=mpeg4) video. If you want to have a single source, and neither live streaming nor adaptive streaming is a consideration, MP4 with h264 video and acc audio is a good choice.

The most common browsers which do not support MP4 are found on Linux, where the user might need to install additional codec support, and in some cases won't want to. You can supply an array of alternate sources. [webm](https://caniuse.com/#feat=webm) and/or [ogv](https://caniuse.com/#feat=ogv) are useful as fallback, but neither are supported by all browsers that support MP4.

#### [](/guides/troubleshooting/#i-need-adaptive-streaming-or-live-streaming)I need adaptive streaming or live streaming

Video.js 7+ supports HLS and MPEG-DASH as standard as it includes [http-streaming](https://github.com/videojs/http-streaming), which uses [Media Source Extensions](https://caniuse.com/#feat=mediasource) to play these formats in modern browsers. If choosing a single format, HLS is more convenient as iOS and some Android browsers which do not support MSE do have native HLS support.

HLS is not possible on IE 11 on Windows 7, which does not support MSE.

For older Video.js versions, [http-streaming](https://github.com/videojs/http-streaming) or its predecessors [videojs-contrib-hls](https://github.com/videojs/videojs-contrib-hls) and [videojs-contrib-dash](https://github.com/videojs/videojs-contrib-dash) add similar support, but for best results use the latest Video.js.

### [](/guides/troubleshooting/#make-sure-you-are-using-formats-that-videojs-can-play)Make sure you are using formats that Video.js can play:

*   Does your browser/OS support the type of media that you are trying to play?
*   Do you have a Video.js plugin that will add support for a media format to Video.js? For example [videojs-youtube](https://github.com/videojs/videojs-youtube)
*   Verify that you are using the correct [mime-type/content-type](https://www.iana.org/assignments/media-types/media-types.xhtml#video) for your videos. This is used to determine if Video.js can play a certain type of media.

### [](/guides/troubleshooting/#make-sure-that-the-codec-used-in-the-file-container-is-supported)Make sure that the codec used in the file container is supported:

*   The MP4 format can contain video and audio data in many codecs, but MP4 playback in browsers typically only supports h264 video and MP3 or AAC audio.
*   The file extension does not always reflect the file contents. For example some low end phones save video in 3GP format but give it an MP4 extension. These files will not play.

### [](/guides/troubleshooting/#if-you-are-using-flash-videos)If you are using Flash videos:

*   [Flash has reached end of life](https://www.adobe.com/products/flashplayer/end-of-life.html) and is no longer supported in browsers.

## [](/guides/troubleshooting/#problems-when-hosting-media)Problems when hosting media

*   Your server _must_ properly support byte-range requests as Chrome and Safari rely on them:
    *   Most servers support this by default.
    *   If you are proxying the media files via a server side script (PHP), this script must implement ranges. PHP does not do this by default.
    *   The impact of not doing this ranges from seeking being broken to no playback at all (on iOS).
*   Your server must return the correct [mime-type/content-type](https://www.iana.org/assignments/media-types/media-types.xhtml#video) header for the media being sent.
*   Your server must implement [CORS (cross-origin resource)](https://enable-cors.org/) headers if:
    *   You are using formats like HLS or MPEG-DASH and your media is served from a different domain than your page.
    *   You are using [text tracks](/guides/text-tracks) (captions, subtitles, etc.) and they are being served from a different domain than your page.

## [](/guides/troubleshooting/#problems-with-fullscreen)Problems with fullscreen

*   If your player is in an iframe, that iframe _and_ any parent iframes must have the following attributes for fullscreen to be allowed:
    *   `allowfullscreen`
    *   `webkitallowfullscreen`
    *   `mozallowfullscreen`

## [](/guides/troubleshooting/#problems-with-playback)Problems with playback

*   Make sure that the media host supports byte-range requests, this could be breaking playback. See [Problems when hosting media](/guides/troubleshooting/#problems-when-hosting-media) for more info.
*   If your media is taking a long time to start playback or the entire mediadownloads before playback:
    *   It is likely that metadata for the media has not been included at the start of the media. In MP4 terms this is called the "moov atom". Many encoders are configured to do this by default, others may require you to choose a "fast start" or "optimize for streaming" option.

## [](/guides/troubleshooting/#videojs-errors)Video.js Errors

### [](/guides/troubleshooting/#vdata123456-errors)vdata123456 errors

This error is thrown when an element that is associated with a component is removed from the DOM but the event handlers associated with the element are not removed. This is almost always due to event listeners not being disposed when dispose is called on a component.

To fix this issue please make sure that all event listeners are cleaned up on dispose.

### [](/guides/troubleshooting/#uncaught-referenceerror-x-is-not-defined)Uncaught ReferenceError: X is not defined

Errors like this, where `X` will vary, can be caused by transpilation breaking code that is used in web workers. See the [webpack guide](/guides/webpack) for details of how to prevent this.

---

# Debugging | Video.js

**URL:** https://videojs.org/guides/debugging

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Debugging

## Table of Contents

*   [Logging](#logging)
    *   [API Overview](#api-overview)
    *   [Log Safely](#log-safely)
    *   [Log Objects Usefully](#log-objects-usefully)
    *   [Creating new Loggers](#creating-new-loggers)
    *   [Log Levels](#log-levels)
    *   [Available Log Levels](#available-log-levels)
    *   [Debug Logging](#debug-logging)
    *   [History](#history)
        *   [History filtering](#history-filtering)

## [](/guides/debugging/#logging)Logging

Video.js includes `videojs.log`, a lightweight wrapper around a subset of [the `console` API](https://developer.mozilla.org/en-US/docs/Web/API/Console). The available methods are `videojs.log`, `videojs.log.debug`, `videojs.log.warn`, and `videojs.log.error`.

### [](/guides/debugging/#api-overview)API Overview

Most of these methods should be fairly self-explanatory, but for complete details, see [the API docs](https://docs.videojs.com/).

| Method | Alias Of | Matching Level(s) |
| --- | --- | --- |
| `videojs.log()` | `console.log` | all, debug, info |
| `videojs.log.debug()` | `console.debug` | all, debug |
| `videojs.log.warn()` | `console.warn` | all, debug, info, warn |
| `videojs.log.error()` | `console.error` | all, debug, info, warn, error |
| `videojs.log.createLogger()` | n/a | n/a |
| `videojs.log.level()` | n/a | n/a |
| `videojs.log.history()` | n/a | n/a |
| `videojs.log.history.clear()` | n/a | n/a |
| `videojs.log.history.disable()` | n/a | n/a |
| `videojs.log.history.enable()` | n/a | n/a |
| `videojs.log.history.filter()` | n/a | n/a |

For descriptions of these features, please refer to the sections below.

### [](/guides/debugging/#log-safely)Log Safely

Unlike the `console`, it's safe to leave `videojs.log` calls in your code. They won't throw errors when the `console` doesn't exist.

### [](/guides/debugging/#log-objects-usefully)Log Objects Usefully

Similar to the `console`, any number of mixed-type values can be passed to `videojs.log` methods:

```js
videojs.log('this is a string', {butThis: 'is an object'});
```

### [](/guides/debugging/#creating-new-loggers)Creating new Loggers

Sometimes, you want to make a new module or plugin and log messages with a label. Kind of how all these logs are prepended with `VIDEOJS:`. You can do that via the `createLogger` method. It takes a name and gives you back a log object like `videojs.log`. Here's an example:

```js
const mylogger = videojs.log.createLogger('mylogger');

mylogger('hello world!');
// > VIDEOJS: mylogger: hello world!

// We can even chain it further
const anotherlogger = mylogger.createLogger('anotherlogger');

anotherlogger('well, hello there');
// > VIDEOJS: mylogger: anotherlogger: well, hello there
```

### [](/guides/debugging/#log-levels)Log Levels

Unlike the `console`, `videojs.log` includes the concept of logging levels. These levels toggle logging methods on or off.

Levels are exposed through the `videojs.log.level` method. This method acts as both a getter and setter for the current logging level. With no arguments, it returns the current logging level:

```js
videojs.log.level(); // "info"
```

By passing a string, the logging level can be changed to one of the available logging levels:

```js
videojs.log.level('error'); // show only error messages and suppress others
videojs.log('foo'); // does nothing
videojs.log.warn('foo'); // does nothing
videojs.log.error('foo'); // logs "foo" as an error
```

### [](/guides/debugging/#available-log-levels)Available Log Levels

*   **info** (default): only show `log`, `log.warn`, and `log.error` messages
*   **all**: enables all logging methods
*   **error**: only show `log.error` messages
*   **off**: disable all logging methods
*   **warn**: only show `log.warn` _and_ `log.error` messages
*   **debug**: show `log`, `log.debug`, `log.warn`, and `log.error` messages

### [](/guides/debugging/#debug-logging)Debug Logging

Although the log levels attempt to match their `window.console` counterparts, `window.console.debug` is not available on all platforms. As such, it will use the closest comparable method, falling back from `window.console.debug` to `window.console.info` to `window.console.log`, and ultimately to nothing if none of those methods are available.

### [](/guides/debugging/#history)History

> **Note:** In Video.js 5, `videojs.log.history` was an array. As of Video.js 6, it is a function which returns an array. This change was made to provide a richer, safer logging history API. You can also filter the history based on the name of the logger.

By default, the `videojs.log` module tracks a history of _everything_ passed to it regardless of logging level:

```js
videojs.log.history(); // an array of everything that's been logged up to now
```

This will work even when logging is set to **off**.

This can be useful, but it can also be a source of memory leaks. For example, logged objects will be retained in history even if references are removed everywhere else!

To avoid this problem, history can be disabled or enabled via method calls (using the `disable` and `enable` methods respectively). Disabling history is as easy as:

```js
videojs.log.history.disable();
```

Finally, the history (if enabled) can be cleared at any time via:

```js
videojs.log.history.clear();
```

#### [](/guides/debugging/#history-filtering)History filtering

If you want to find all the history that was created by a particular logger, you can do so via `history.filter()`. Given a specific logger with name `foo`, you can pass `foo` to `history.filter()` and get all items logger by foo. Let me show you an example:

```js
const mylogger = videojs.log.createLogger('mylogger');
const anotherlogger = mylogger.createLogger('anotherlogger');

videojs.log('hello');
mylogger('how are you');
anotherlogger('today');

videojs.log.history.filter('VIDEOJS');
// > [['VIDEOJS:', 'hello'], ['VIDEOJS: mylogger:', 'how are you'], ['VIDEOJS: mylogger: anotherlogger:', 'today']]
videojs.log.history.filter('mylogger');
// > [['VIDEOJS:    mylogger:', 'how are you'], ['VIDEOJS: mylogger: anotherlogger:', 'today']]
videojs.log.history.filter('anotherlogger');
// > [['VIDEOJS: mylogger: anotherlogger:', 'today']]
```

---

# Video Tracks | Video.js

**URL:** https://videojs.org/guides/video-tracks

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Video Tracks

## Table of Contents

*   [Caveats](#caveats)
*   [Working with Video Tracks](#working-with-video-tracks)
    *   [Add a Video Track to the Player](#add-a-video-track-to-the-player)
    *   [Listen for a Video Track Becoming Enabled](#listen-for-a-video-track-becoming-enabled)
    *   [Removing an Video Track from the Player](#removing-an-video-track-from-the-player)
*   [API](#api)
    *   [videojs.VideoTrack](#videojsvideotrack)
        *   [id](#id)
        *   [kind](#kind)
        *   [label](#label)
        *   [language](#language)
        *   [selected](#selected)

> **Note:** While video tracks [are a standard](https://html.spec.whatwg.org/multipage/embedded-content.html#videotrack), there are no compatible implementations at this time. This is an experimental technology!

Video tracks are a feature of HTML5 video for providing alternate video tracks to the user, so they can change the type of video they want to watch. Video.js offers a cross-browser implementation of video tracks.

## [](/guides/video-tracks/#caveats)Caveats

*   It is not possible to add video tracks through HTML like you can with text tracks. They must be added programmatically.
*   Video.js only stores track representations. Switching video tracks for playback is _not handled by Video.js_ and must be handled elsewhere.

## [](/guides/video-tracks/#working-with-video-tracks)Working with Video Tracks

### [](/guides/video-tracks/#add-a-video-track-to-the-player)Add a Video Track to the Player

```js
// Create a player.
var player = videojs('my-player');

// Create a track object.
var track = new videojs.VideoTrack({
  id: 'my-alternate-video-track',
  kind: 'commentary',
  label: 'Director\'s Commentary',
  language: 'en'
});

// Add the track to the player's video track list.
player.videoTracks().addTrack(track);
```

### [](/guides/video-tracks/#listen-for-a-video-track-becoming-enabled)Listen for a Video Track Becoming Enabled

When a track is enabled or disabled on an `VideoTrackList`, a `change` event will be fired. You can listen for that event and do something with it.

> NOTE: The initial `VideoTrack` selection (usually the main track that is selected) should not fire a `change` event.

```js
// Get the current player's VideoTrackList object.
var videoTrackList = player.videoTracks();

// Listen to the "change" event.
videoTrackList.addEventListener('change', function() {

  // Log the currently enabled VideoTrack label.
  for (var i = 0; i < videoTrackList.length; i++) {
    var track = videoTrackList[i];

    if (track.enabled) {
      videojs.log(track.label);
      return;
    }
  }
});
```

### [](/guides/video-tracks/#removing-an-video-track-from-the-player)Removing an Video Track from the Player

Assuming a player already exists and has an video track that you want to remove, you might do something like the following:

```js
// Get the track we created in an earlier example.
var track = player.videoTracks().getTrackById('my-alternate-video-track');

// Remove it from the video track list.
player.videoTracks().removeTrack(track);
```

## [](/guides/video-tracks/#api)API

For more complete information, refer to the [Video.js API docs](https://docs.videojs.com/), specifically:

*   `Player#videoTracks`
*   `VideoTrackList`
*   `VideoTrack`

### [](/guides/video-tracks/#videojsvideotrack)`videojs.VideoTrack`

This class is based on [the `VideoTrack` standard](https://html.spec.whatwg.org/multipage/embedded-content.html#videotrack) and can be used to create new video track objects.

Each property below is available as an option to the `VideoTrack` constructor.

#### [](/guides/video-tracks/#id)`id`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-id)

A unique identifier for this track. Video.js will generate one if not given.

#### [](/guides/video-tracks/#kind)`kind`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-kind)

Video.js supports standard `kind` values for `VideoTracks`:

*   `"alternative"`: A possible alternative to the main track.
*   `"captions"`: The main video track with burned in captions
*   `"main"`: The main video track.
*   `"sign"`: The main video track with added sign language overlay.
*   `"subtitles"`: The main video track with burned in subtitles.
*   `"commentary"`: The main video track with burned in commentary.
*   `""` (default): No explicit kind, or the kind given by the track's metadata is not recognized by the user agent.

#### [](/guides/video-tracks/#label)`label`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-label)

The label for the track that will be shown to the user. For example, in a menu that lists the different captions available as alternate video tracks.

#### [](/guides/video-tracks/#language)`language`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-language)

The valid [BCP 47](https://tools.ietf.org/html/bcp47) code for the language of the video track, e.g. `"en"` for English or `"es"` for Spanish.

For supported language translations, please see the [languages folder (/lang)](https://github.com/videojs/video.js/tree/main/lang) folder located in the Video.js root and refer to the [languages guide](/guides/languages) for more information on languages in Video.js.

#### [](/guides/video-tracks/#selected)`selected`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-videotrack-selected)

Whether or not this track should be playing. Only one video track may be selected at a time.

---

# Audio Tracks | Video.js

**URL:** https://videojs.org/guides/audio-tracks

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Audio Tracks

## Table of Contents

*   [Caveats](#caveats)
*   [Working with Audio Tracks](#working-with-audio-tracks)
    *   [Add an Audio Track to the Player](#add-an-audio-track-to-the-player)
    *   [Listen for an Audio Track Becoming Enabled](#listen-for-an-audio-track-becoming-enabled)
    *   [Removing an Audio Track from the Player](#removing-an-audio-track-from-the-player)
*   [API](#api)
    *   [videojs.AudioTrack](#videojsaudiotrack)
        *   [id](#id)
        *   [kind](#kind)
        *   [label](#label)
        *   [language](#language)
        *   [enabled](#enabled)

Audio tracks are a feature of HTML5 video for providing alternate audio track selections to the user, so that a track other than the main track can be played. Video.js offers a cross-browser implementation of audio tracks, providing the playback technology supports audio tracks.

Audio tracks are supported in Video.js's MSE playback engine for HLS and DASH. Safari also supports audio tracks for native playback of HLS and MP4. **Other browsers do not support audio tracks for native playback including MP4**, so it is not possible to work with MP4 audio tracks in Chrome or Firefox for example.

## [](/guides/audio-tracks/#caveats)Caveats

*   It is not possible to add audio tracks through HTML like you can with text tracks. They must be added programmatically.
*   Video.js only stores track representations. Switching audio tracks for playback is _not handled by Video.js_ and must be handled elsewhere - for example, [http-streaming](https://github.com/videojs/http-streaming) handles switching audio tracks to support track selection through the UI.

## [](/guides/audio-tracks/#working-with-audio-tracks)Working with Audio Tracks

### [](/guides/audio-tracks/#add-an-audio-track-to-the-player)Add an Audio Track to the Player

```js
// Create a player.
var player = videojs('my-player');

// Create a track object.
var track = new videojs.AudioTrack({
  id: 'my-spanish-audio-track',
  kind: 'translation',
  label: 'Spanish',
  language: 'es'
});

// Add the track to the player's audio track list.
player.audioTracks().addTrack(track);
```

### [](/guides/audio-tracks/#listen-for-an-audio-track-becoming-enabled)Listen for an Audio Track Becoming Enabled

When a track is enabled or disabled on an `AudioTrackList`, a `change` event will be fired. You can listen for that event and do something with it.

> NOTE: The initial `AudioTrack` selection (usually the main track that is selected) should not fire a `change` event.

```js
// Get the current player's AudioTrackList object.
var audioTrackList = player.audioTracks();

// Listen to the "change" event.
audioTrackList.addEventListener('change', function() {

  // Log the currently enabled AudioTrack label.
  for (var i = 0; i < audioTrackList.length; i++) {
    var track = audioTrackList[i];

    if (track.enabled) {
      videojs.log(track.label);
      return;
    }
  }
});
```

### [](/guides/audio-tracks/#removing-an-audio-track-from-the-player)Removing an Audio Track from the Player

Assuming a player already exists and has an audio track that you want to remove, you might do something like the following:

```js
// Get the track we created in an earlier example.
var track = player.audioTracks().getTrackById('my-spanish-audio-track');

// Remove it from the audio track list.
player.audioTracks().removeTrack(track);
```

## [](/guides/audio-tracks/#api)API

For more complete information, refer to the [Video.js API docs](https://docs.videojs.com/), specifically:

*   `Player#audioTracks`
*   `AudioTrackList`
*   `AudioTrack`

### [](/guides/audio-tracks/#videojsaudiotrack)`videojs.AudioTrack`

This class is based on [the `AudioTrack` standard](https://html.spec.whatwg.org/multipage/embedded-content.html#audiotrack) and can be used to create new audio track objects.

Each property below is available as an option to the `AudioTrack` constructor.

#### [](/guides/audio-tracks/#id)`id`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-id)

A unique identifier for this track. Video.js will generate one if not given.

#### [](/guides/audio-tracks/#kind)`kind`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-kind)

Video.js supports standard `kind` values for `AudioTracks`:

*   `"alternative"`: A possible alternative to the main track.
*   `"descriptions"`: An audio description of a video track.
*   `"main"`: The primary audio track for this video.
*   `"main-desc"`: The primary audio track, mixed with audio descriptions.
*   `"translation"`: A translated version of the main audio track.
*   `"commentary"`: Commentary on the primary audio track, e.g. a director's commentary.
*   `""` (default): No explicit kind, or the kind given by the track's metadata is not recognized by the user agent.

#### [](/guides/audio-tracks/#label)`label`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-label)

The label for the track that will be shown to the user. For example, in a menu that lists the different languages available as alternate audio tracks.

#### [](/guides/audio-tracks/#language)`language`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-language)

The valid [BCP 47](https://tools.ietf.org/html/bcp47) code for the language of the audio track, e.g. `"en"` for English or `"es"` for Spanish.

For supported language translations, please see the [languages folder (/lang)](https://github.com/videojs/video.js/tree/main/lang) located in the Video.js root and refer to the [languages guide](/guides/languages/) for more information on languages in Video.js.

#### [](/guides/audio-tracks/#enabled)`enabled`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-audiotrack-enabled)

Whether or not this track should be playing.

In Video.js, we only allow one track to be enabled at a time; so, if you enable more than one, the last one to be enabled will end up being the only one. While the spec allows for more than one track to be enabled, Safari and most implementations only allow one audio track to be enabled at a time.

---

# Text Tracks | Video.js

**URL:** https://videojs.org/guides/text-tracks

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Text Tracks

## Table of Contents

*   [A Note on "Remote" Text Tracks](#a-note-on-remote-text-tracks)
*   [Creating the Text File](#creating-the-text-file)
*   [Adding Text Tracks to Video.js](#adding-text-tracks-to-videojs)
    *   [track Attributes](#track-attributes)
        *   [kind](#kind)
        *   [label](#label)
        *   [default](#default)
        *   [srclang](#srclang)
    *   [Text Tracks from Another Domain](#text-tracks-from-another-domain)
*   [Working with Text Tracks](#working-with-text-tracks)
    *   [Showing Tracks Programmatically](#showing-tracks-programmatically)
    *   [Listen for a Cue Becoming Active](#listen-for-a-cue-becoming-active)
*   [Emulated Text Tracks](#emulated-text-tracks)
    *   [Text Track Settings](#text-track-settings)
*   [Text Track Precedence](#text-track-precedence)
*   [API](#api)
    *   [Remote Text Tracks](#remote-text-tracks)
    *   [Text Tracks](#text-tracks)

Text tracks are a feature of HTML5 for displaying time-triggered text to the end-user. Video.js offers a cross-browser implementation of text tracks.

## [](/guides/text-tracks/#a-note-on-remote-text-tracks)A Note on "Remote" Text Tracks

Video.js refers to so-called "remote" text tracks. This is a convenient term for tracks that have an associated `<track>` element rather than those that do not.

Either can be created programmatically, but _only remote text tracks can be removed from a player._ For that reason, we recommend _only_ using remote text tracks.

## [](/guides/text-tracks/#creating-the-text-file)Creating the Text File

Timed text requires a text file in [WebVTT](https://dev.w3.org/html5/webvtt/) format. This format defines a list of "cues" that have a start time, an end time, and text to display. [Microsoft has a builder](https://dev.modern.ie/testdrive/demos/captionmaker/) that can help you get started on the file.

> **Note:** When creating captions, there are additional [caption formatting techniques](https://www.theneitherworld.com/mcpoodle/SCC_TOOLS/DOCS/SCC_FORMAT.HTML#style) to make captions more meaningful, like brackets around sound effects (e.g. `[ birds chirping ]`).
> 
> For a more in depth style guide for captioning, see the [Captioning Key](https://www.dcmp.org/captioningkey/), but keep in mind not all features are supported by WebVTT or (more likely) the Video.js WebVTT implementation.

## [](/guides/text-tracks/#adding-text-tracks-to-videojs)Adding Text Tracks to Video.js

Once you have your WebVTT files created, you can add them to your `video` element using the `track` tag. Similar to `source` elements, `track` elements should be added as children of the `video` element:

```html
<video
  class="video-js"
  controls
  preload="auto"
  width="640"
  height="264"
  data-setup='{}'>
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <source src="//vjs.zencdn.net/v/oceans.webm" type="video/webm">
  <track kind="captions" src="//example.com/path/to/captions.vtt" srclang="en" label="English" default>
</video>
```

Video.js will automatically read `track` elements from the `video` element. Tracks (remote and non-remote) can also be added programmatically.

### [](/guides/text-tracks/#track-attributes)`track` Attributes

#### [](/guides/text-tracks/#kind)`kind`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#text-track-kind)

One of the track types supported by Video.js:

*   `"subtitles"` (default): Translations of the dialogue in the video for when audio is available but not understood. Subtitles are shown over the video.
*   `"captions"`: Transcription of the dialogue, sound effects, musical cues, and other audio information for viewer who are deaf/hard of hearing, or the video is muted. Captions are also shown over the video.
*   `"chapters"`: Chapter titles that are used to create navigation within the video. Typically, these are in the form of a list of chapters that the viewer can use to navigate the video.
*   `"descriptions"`: Text descriptions of the action in the content for when the video portion isn't available or because the viewer is blind or not using a screen. Descriptions are read by a screen reader or turned into a separate audio track.
*   `"metadata"`: Tracks that have data meant for JavaScript to parse and do something with. These aren't shown to the user.

#### [](/guides/text-tracks/#label)`label`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#text-track-label)

Short descriptive text for the track that will used in the user interface. For example, in a menu for selecting a captions language.

#### [](/guides/text-tracks/#default)`default`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-track-default)

The boolean `default` attribute can be used to indicate that a track's mode should start as `"showing"`. Otherwise, the viewer would need to select their language from a captions or subtitles menu.

> **Note:** For chapters, `default` is required if you want the chapters menu to show.

#### [](/guides/text-tracks/#srclang)`srclang`

> [standard definition](https://html.spec.whatwg.org/multipage/embedded-content.html#dom-track-srclang)

The valid [BCP 47](https://tools.ietf.org/html/bcp47) code for the language of the text track, e.g. `"en"` for English or `"es"` for Spanish.

For supported language translations, please see the [languages folder (/lang)](https://github.com/videojs/video.js/tree/main/lang) folder located in the Video.js root and refer to the [languages guide](/guides/languages) for more information on languages in Video.js.

### [](/guides/text-tracks/#text-tracks-from-another-domain)Text Tracks from Another Domain

Because Video.js loads the text track file via JavaScript, the [same-origin policy](https://en.wikipedia.org/wiki/Same_origin_policy) applies. If you'd like to have a player served from one domain, but the text track served from another, you'll need to [enable CORS](https://enable-cors.org/) on the server that is serving your text tracks.

In addition to enabling CORS, you will need to add the [`crossorigin` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_settings_attributes) to the video element itself. This attribute has two possible values `"anonymous"` and `"use-credentials"`. Most users will want to use `"anonymous"` with cross-origin tracks:

```html
<video class="video-js" crossorigin="anonymous">
  <source src="//vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
  <track src="//example.com/oceans.vtt" kind="captions" srclang="en" label="English">
</video>
```

One thing to be aware of is that the video files themselves will _also_ need CORS headers. This is because some browsers apply the `crossorigin` attribute to the video source itself and not just the tracks. This is considered a [security concern by the spec](https://html.spec.whatwg.org/multipage/embedded-content.html#security-and-privacy-considerations).

## [](/guides/text-tracks/#working-with-text-tracks)Working with Text Tracks

### [](/guides/text-tracks/#showing-tracks-programmatically)Showing Tracks Programmatically

Certain use cases call for turning captions on and off programmatically rather than forcing the user to do so themselves. This can be easily achieved by modifying the `mode` property of the text tracks.

The `mode` can be one of three values `"disabled"`, `"hidden"`, and `"showing"`. When a text track's `mode` is `"disabled"`, the track does not show on screen as the video is playing.

When the `mode` is set to `"showing"`, the track is visible to the viewer and updates while the video is playing.

```js
// Get all text tracks for the current player.
var tracks = player.textTracks();

for (var i = 0; i < tracks.length; i++) {
  var track = tracks[i];

  // Find the English captions track and mark it as "showing".
  if (track.kind === 'captions' && track.language === 'en') {
    track.mode = 'showing';
  }
}
```

### [](/guides/text-tracks/#listen-for-a-cue-becoming-active)Listen for a Cue Becoming Active

One of the supported values for `mode` is `"hidden"`. This `mode` means that the track will update as the video is playing, but it won't be visible to the viewer. This is most useful for tracks where `kind="metadata"`.

A common use case for metadata text tracks is to use them to trigger behaviors when their cues become active. For this purpose, tracks emit a `"cuechange"` event.

```js
// Get all text tracks for the current player.
var tracks = player.textTracks();
var metadataTrack;

for (var i = 0; i < tracks.length; i++) {
  var track = tracks[i];

  // Find the metadata track that's labeled "ads".
  if (track.kind === 'metadata' && track.label === 'ads') {
    track.mode = 'hidden';

    // Store it for usage outside of the loop.
    metadataTrack = track;
  }
}

// Add a listener for the "cuechange" event and start ad playback.
metadataTrack.addEventListener('cuechange', function() {
  player.ads.startLinearAdMode();
});
```

## [](/guides/text-tracks/#emulated-text-tracks)Emulated Text Tracks

By default, Video.js will use native text tracks and fall back to emulated text tracks if the native functionality is broken, incomplete, or non-existent.

The Video.js API and TextTrack objects were modeled after the W3C specification. Video.js uses [Mozilla's vtt.js](https://github.com/mozilla/vtt.js) library to parse and display emulated text tracks.

To disable native text track functionality and force Video.js to use emulated text tracks always, the `nativeTextTracks` option can be passed to a tech:

```js
// Create a player, passing `nativeTextTracks: false` to the HTML5 tech.
var player = videojs('myvideo', {
  html5: {
    nativeTextTracks: false
  }
});
```

### [](/guides/text-tracks/#text-track-settings)Text Track Settings

When using emulated text tracks, captions will have an additional item in the menu called "Caption Settings". This allows the user to alter how captions are styled on screen.

This feature can be disabled by turning off the `TextTrackSettings` component and hiding the menu item.

```js
var player = videojs('myvideo', {
  // Make the text track settings dialog not initialize.
  textTrackSettings: false
});
```

```css
/* Hide the captions settings item from the captions menu. */
.vjs-texttrack-settings {
  display: none;
}
```

## [](/guides/text-tracks/#text-track-precedence)Text Track Precedence

In general, `"descriptions"` tracks are of lower precedence than `"captions"` and `"subtitles"`. What this mean for developers using Video.js?

*   If you are using the `default` attribute, Video.js will choose the first track that is marked as `default` and turn it on. If there are multiple tracks marked `default`, it will turn on the first `"captions"` or `"subtitles"` track _before_ any `"descriptions"` tracks.
    *   This only applied to the emulated text track support, native text tracks behavior will change depending on the browser.
*   If a track is selected from the menu, Video.js will turn off all the other tracks of the same kind. While this suggests Video.js supports both `"subtitles"` and `"captions"` being turned on simultaneously, this is currently not the case; Video.js only supports one track being displayed at a time.
    *   This means that for emulated text tracks, Video.js will display the first enabled `"subtitles"` or `"captions"` track.
    *   When native text tracks are supported, other tracks of the same kind will still be disabled, but it is possible that multiple text tracks are shown.
    *   If a `"descriptions"` track is selected and subsequently a `"subtitles"` or `"captions"` track is selected, the `"descriptions"` track is disabled and its menu button is also disabled.
*   When enabling a track programmatically, Video.js performs minimal enforcement.
    *   For emulated text tracks, Video.js chooses the first track that's `"showing"` - again choosing `"subtitles"` or `"captions"` over `"descriptions"`.
    *   For native text tracks, this behavior depends on the browser. Some browsers will allow multiple text tracks, but others will disable all other tracks when a new one is selected.

## [](/guides/text-tracks/#api)API

For more complete information, refer to the [Video.js API docs](https://docs.videojs.com/).

### [](/guides/text-tracks/#remote-text-tracks)Remote Text Tracks

As mentioned [above](/guides/text-tracks/#a-note-on-remote-text-tracks), remote text tracks represent the recommended API offered by Video.js as they can be removed.

*   `Player#remoteTextTracks()`
    
*   `Player#remoteTextTrackEls()`
    
*   `Player#addRemoteTextTrack(Object options)`
    
    Available options are the same as the [available `track` attributes](/guides/text-tracks/#track-attributes). And `language` is a supported option as an alias for the `srclang` attribute - either works here.
    
    **Note**: If you need a callback, instead of a callback you could use the technique below:
    
    ```js
    const trackEl = player.addRemoteTextTrack({src: 'en.vtt'}, false);
    trackEl.addEventListener('load', function() {
      // your callback goes here
    });
    ```
    
*   `Player#removeRemoteTextTrack(HTMLTrackElement|TextTrack)`
    

### [](/guides/text-tracks/#text-tracks)Text Tracks

It is generally recommended that you use _remote_ text tracks rather than these purely programmatic text tracks for the majority of use-cases.

*   `Player#textTracks()`
    
*   `Player#addTextTrack(String kind, [String label [, String language]])`
    
    > **Note:** Non-remote text tracks are intended for _purely programmatic usage_ of tracks and have the important limitation that they _cannot be removed once created_.
    > 
    > The standard `addTextTrack` does **not** have a corresponding `removeTextTrack` method; so, we actually discourage the use of this method!
    
*   `TextTrackList()`
    
*   `TextTrack()`

---

# Webpack and Video.js | Video.js

**URL:** https://videojs.org/guides/webpack

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Webpack and Video.js

## Table of Contents

*   [Video.js CSS:](#videojs-css)

Video.js and official libraries and plugins work in a Webpack-based build environment, however some configuration may be needed to ensure code that is executed in workers is not broken by transpilation.

The solutions [documented by the Mapbox project](https://docs.mapbox.com/mapbox-gl-js/guides/install/#targeting-transpilation-to-es6-with-browserslist) apply:

1.  Either set the production `browserslist` to

```text
">0.2%",
"not dead",
"not op_mini all",
"not safari < 10",
"not chrome < 51",
"not android < 5",
"not ie < 12"
```

2.  Or import using the ! syntax

```js
// eslint-disable-next-line import/no-webpack-loader-syntax
import videojs from "!video.js";
```

## [](/guides/webpack/#videojs-css)Video.js CSS:

You may need to add [`style-loader`](https://webpack.js.org/loaders/style-loader/) to your Webpack configuration.

Then add the CSS that the player requires, add the following to the file where the player is also included or initialized:

```js
require('!style-loader!css-loader!video.js/dist/video-js.css')
```

---

# Vue and Video.js | Video.js

**URL:** https://videojs.org/guides/vue

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Vue and Video.js

This is a basic Vue and Video.js player implementation. This example component instantiates the player on `mounted` and destroys it on `beforeDestroy`:

```jsx
<template>
  <div>
    <video ref="videoPlayer" class="video-js"></video>
  </div>
</template>

<script>
import videojs from 'video.js';

export default {
  name: 'VideoPlayer',
  props: {
    options: {
      type: Object,
      default() {
        return {};
      }
    }
  },
  data() {
    return {
      player: null
    }
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, this.options, () => {
      this.player.log('onPlayerReady', this);
    });
  },
  beforeDestroy() {
    if (this.player) {
      this.player.dispose();
    }
  }
}
</script>
```

Finally, use the component like this (see [Video.js Options Reference](https://videojs.com/guides/options)):

```jsx
<template>
  <div>
    <video-player :options="videoOptions" />
  </div>
</template>

<script>
import VideoPlayer from '@/components/VideoPlayer.vue';

export default {
  name: 'VideoExample',
  components: {
    VideoPlayer
  },
  data() {
    return {
      videoOptions: {
        autoplay: true,
        controls: true,
        sources: [
          {
            src:
              '/path/to/video.mp4',
              type: 'video/mp4'
          }
        ]
      }
    };
  }
};
</script>
```

Don't forget to include the Video.js CSS, located at `video.js/dist/video-js.css`!

---

# Playback Technology ("Tech") | Video.js

**URL:** https://videojs.org/guides/tech

## Video.js Guides

These guides cover a range of topics for users of Video.js

[Back to Guides](/guides)

# Playback Technology ("Tech")

## Table of Contents

*   [Building an API Wrapper](#building-an-api-wrapper)
*   [Required Methods](#required-methods)
*   [Required Events](#required-events)
*   [Optional Events (include if supported)](#optional-events-include-if-supported)
*   [Adding Playback Technology](#adding-playback-technology)
    *   [Tag Method:](#tag-method)
    *   [Object Method:](#object-method)
    *   [Posters](#posters)
*   [Technology Ordering](#technology-ordering)
*   [Flash Technology](#flash-technology)

Playback Technology refers to the specific browser or plugin technology used to play the video or audio. When using HTML5, the playback technology is the video or audio element. When using the [videojs-youtube](https://github.com/videojs/videojs-youtube) tech, the playback technology is the YouTube player. The tech also includes an API wrapper to translate between the Video.js controls and API to the specific playback technology used.

Essentially we're using html5 and plugins only as video decoders, and using HTML and JavaScript to create a consistent API and skinning experience across all of them.

In addition to techs there are source handlers. Source handlers add the capability to play additional source types to techs. For example, the [http-streaming](https://github.com/videojs/http-streaming) source handler (included with Video.js 7+ by default) enables the HTML5 tech to play HLS and DASH.

## [](/guides/tech/#building-an-api-wrapper)Building an API Wrapper

We'll write a more complete guide on writing a wrapper soon, but for now the best resource is the [Video.js](https://github.com/videojs/video.js/tree/main/src/js/tech) source where you can see how the HTML5 API wrapper is created.

## [](/guides/tech/#required-methods)Required Methods

canPlayType play pause currentTime volume duration buffered supportsFullScreen

## [](/guides/tech/#required-events)Required Events

loadstart play pause playing ended volumechange durationchange error

## [](/guides/tech/#optional-events-include-if-supported)Optional Events (include if supported)

timeupdate progress enterFullScreen exitFullScreen

## [](/guides/tech/#adding-playback-technology)Adding Playback Technology

When additional techs are added they are automatically added to the `techOrder`. You can modify the `techOrder` to change the priority of each tech.

### [](/guides/tech/#tag-method)Tag Method:

```html
<video data-setup='{"techOrder": ["html5", "other supported tech"]}'>
```

### [](/guides/tech/#object-method)Object Method:

```js
videojs("videoID", {
  techOrder: ["html5", "other supported tech"]
});
```

### [](/guides/tech/#posters)Posters

By default, techs will have to handle their own posters and are somewhat locked out of the player's poster lifecycle. However, when the player is initialized with the `techCanOverridePoster` option it will be possible for techs to integrate into that lifecycle and the player's `PosterImage` component to be used.

Techs can check if they have this capability by checking the `canOverridePoster` boolean in their options.

**`techCanOverridePoster` requirements**

*   `poster()` which returns the tech's current poster url
*   `setPoster()` which updates the tech's poster url and triggers a `posterchange` event which the player will handle

## [](/guides/tech/#technology-ordering)Technology Ordering

When Video.js is given an array of sources, which to use is determined by finding the first supported source / tech combination. Each tech will be queried in the order specified in `techOrder` whether it can play the first source. The first match wins. If no tech can play the first source, then the next will be tested. It's important to set the `type` of each source correctly for this test to be accurate.

> These examples use the obsolete [Flash tech](https://www.adobe.com/products/flashplayer/end-of-life.html) for illustration of tech ordering with techs which have a greater degree of overlap in sources they can play

For example, given the following video element, assuming the videojs-flash tech is available:

```html
<!-- "techOrder": ["html5", "flash"] -->
<video>
  <source src="http://your.static.provider.net/path/to/video.m3u8" type="application/x-mpegURL">
  <source src="http://your.static.provider.net/path/to/video.mp4" type="video/mp4">
</video>
```

The HLS source will be tested first. The first tech is html5.

*   Safari can play HLS in a standard HTML5 video element, so HLS will be played using the html5 tech.
*   Chrome can't play HLS in the standard HTML5 video element on its own, but the [http-streaming](https://github.com/videojs/http-streaming) source handler (included in Video.js 7+ by default) _can_ play HLS via [Media Source Extensions](https://en.wikipedia.org/wiki/Media_Source_Extensions) in HTML5. So HLS will be played in the html5 tech.
*   IE 10 can't play HLS natively, and doesn't support Media Source Extensions. As the source cannot be played in HTML5, the Flash tech will be tested.

Now take the same sources again but without videojs-flash:

```html
<!-- "techOrder": ["html5"] -->
<video>
  <source src="http://your.static.provider.net/path/to/video.m3u8" type="application/x-mpegURL">
  <source src="http://your.static.provider.net/path/to/video.mp4" type="video/mp4">
</video>
```

*   Safari can play HLS in a standard HTML5 video element, so HLS will be played using the html5 tech.
*   Chrome will play HLS in the html5 tech using the [http-streaming](https://github.com/videojs/http-streaming) source handler via [Media Source Extensions](https://en.wikipedia.org/wiki/Media_Source_Extensions).
*   IE 10 can't play HLS in either the html5 or Flash tech. Next the MP4 source will be tested. MP4 can be played by HTML5, so that source-tech pair will be used.

## [](/guides/tech/#flash-technology)Flash Technology

Flash is no longer supported as it has reached [end of life](https://www.adobe.com/products/flashplayer/end-of-life.html).

---

