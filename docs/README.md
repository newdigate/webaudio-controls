# webaudio-controls

**webaudio-controls** is a Javascript library for displaying the GUI parts required to Web Music applications.  
webaudio-controls consists of knobs, sliders, switches, parameter displays and keyboards.
By loading webaudio-controls.js to your page, custom tags for component display will be added using WebComponents.  
You can configure the GUI screen just by writing custom tags in HTML.  

<br/>

**Webaudio-controls is Available At**
* GitHub Repository : **<a href="https://github.com/g200kg/webaudio-controls">https://github.com/g200kg/webaudio-controls</a>**
* Introduction Page : **<a href="https://g200kg.github.io/webaudio-controls">https://g200kg.github.io/webaudio-controls</a>**

<br/>

**webaudio-controls** is consist of following components  

Component         | Description
------------------|------------
webaudio-knob     | Rotating or some other frame-by-frame animation knob. 
webaudio-slider   | Vertical or Horizontal slider.
webaudio-switch   | Toggle/Kick/Radio switches.
webaudio-param    | Editable value display field.
webaudio-keyboard | Mouse/Touch playable keyboard. multi-touch support.

* Also available 'webaudio-pianoroll' at : [https://github.com/g200kg/webaudio-pianoroll/](https://github.com/g200kg/webaudio-pianoroll/)

Chrome / Firefox / Edge compatible  
iOS and Android touch devices compatible  

[![](img/demo.png)](https://g200kg.github.io/webaudio-controls/samples/sample1.html)  

## Working Samples 

- [Default styles](https://g200kg.github.io/webaudio-controls/docs/defstyle.html)  
- [Examples of various attributes](https://g200kg.github.io/webaudio-controls/docs/attributes.html)  
- [Various knob images](https://g200kg.github.io/webaudio-controls/docs/knobsamples.html)  
- [Multi-Touch Fader](https://g200kg.github.io/webaudio-controls/docs/multifader.html)  
- [webaudio-keyboard to MIDI](https://g200kg.github.io/webaudio-controls/docs/keyboard.html)  
- [webaudio-controls Resize Test](https://g200kg.github.io/webaudio-controls/docs/resizetest.html)  
- [webaudio-controls NonLinear values Test](https://g200kg.github.io/webaudio-controls/docs/nonlinear.html)
- [Renoid : Practical application using webaudio-controls](http://www.g200kg.com/renoid/)  

## To Operate  
Following user actions are supported.

Operation | Component | Description
---|---|---
**Click** | Switch<br/>Other | Switch : Toggle / activate the switch.<br/>Other : Focus the component.
**Drag** | Knob<br/>Slider | Up/Right to increase value<br/>Down/Left to decrease value.
**Shift+Drag** | Knob<br/>Slider | Fine control. Increase or decrease by the value specified in the `step`.
**Ctrl+Click <br/> Command+Click(Mac)** | Knob<br/>Slider<br/>Switch | Set to default value.
**Keyboard** | Knob<br/>Slider<br/>Param<br/>Keyboard | To manipulate with the keyboard, it is necessary to get the focus by clicking each component once.<br/><br/>Knob/Slider : ArrowUp/ArrowDown to increase or decrease by the value specified in the `step`.<br/>Param : Edit the param value directly.<br/>Keyboard : [ZSXDCV...for lowest visible 'C' octave] and [Q2W3E... one octave higher] as a music keyboard.
**MouseWheel** | Knob<br/>Slider | Rotate upward to increase value, downward to decrease value.
**Shift+MouseWheel** | Knob<br/>Slider | Fine control. Increase or decrease by the value specified in the `step`.
**Mouse Button Press <br/> Touch** | Keyboard | Play keyboard. multi-touch is supported.

---
## How to use


- webaudio-controls.js
  - Place "webaudio-controls.js" to an appropriate directory. <br/>This is the only file needed. There are no dependencies on other libraries.

- WebComponents polyfill
  - If you want to support legacy browsers that not support WebComponents, the polyfill for WebComponents is needed :  
  ```<script src="./webcomponents-lite.js"></script>```

- load webaudio-controls :  
  - ```<script src="./webaudio-controls.js"></script>```  
  Or, if you want to load webaudio-controls.js directly from this GitHub page as CDN :  
  - ```<script src="https://g200kg.github.io/webaudio-controls/webaudio-controls.js"></script>```

- insert webaudio-knob / slider / switch / param / keyboard elements. For example...  
  - `<webaudio-knob src="img/LittlePhatty.png" sprites="100" min="0" max="100"></webaudio-knob>`
  - `<webaudio-slider src="img/hsliderbody.png"></webaudio-slider>`
  - `<webaudio-switch src="img/switch_toggle.png" width="32" height="32"></webaudio-switch>`
  - `<webaudio-param src="" link="knob-1"></webaudio-param>`
  - `<webaudio-keyboard keys="25"></webaudio-keyboard>`


---
## Attributes

### webaudio-knob

Attribute       | Options| Default| Description
----------------|--------|--------|------------
**src**         | string | null   | url of the knob image, Single frame or vertical stitched. Internal embedded resource is used if not specified.
**value**       | float  | `0`    | The current value. Also used as initial value if specified
**defvalue**    | float  | Initial 'value' is used if not specified | The default value that will be used when ctrl+click
**min**         | float  | `0`    | Minimum value of the knob
**max**         | float  | `100`  | Maximum value of the knob
**step**        | float  | `1`    | Value step of the control. The 'value' is always rounded to multiple of 'step'
**width**       | int    | `null` | Knob width in px. diameter value is used if this value is not specified.
**height**      | int    | `null` | Knob height in px. diameter value is used if this value is not specified.
**diameter**    | int    | `64`   | Knob diameter in px. This attribute can be used instead of width / height if the display image is square.
**sprites**     | int    | `null` | If `0`, the `src` image should be single frame knob image that indicate middle position. the image will be rotated -135deg to +135deg.<br/>If `sprites` is 1 or more, the `src` image should be vertically stitched multi-framed image. `sprites` specify the max frame number in the stitched knob image. Note that this is (number of frames) - 1.<br/> If `sprites` attribute is not specified (default), assuming one knob image is a square, it will be calculated from the width and height of the image specified in `src`, i.e. height / width - 1 will be used as the `sprites`.
**sensitivity** | float  | `1`    | Pointing device sensitivity. min-max range correspond to (128 / `sensitivity`) px
**log**         | int    | `0`    | If this value is set to 1, then the value change is logarithmic. For example, if `min="10"` and `max="1000"`, then the center value of the knob will be 100. Here, if `min` is 0 or negative, an error occurs. If `log` is set to 0, then the change in value is linear.
**valuetip**    | `0`,`1`| `0`    | Enable the overlaid value-tip display. This is equivalent to `tooltip="%s"`.
**tooltip**     | string | `null` | Specifies the tooltip text that appears when you hover the mouse cursor for a while. If the text contains "%s", it will be replaced with the current value. Also, if the `conv` attribute is specified, the converted current value, `convValue` is  used for display. 
**conv**        | string | `null` | If this attribute is specified, That string will be evaluated as an expression and stored to `convValue` as a string. This `convValue` will be used for the valuetip, tooltip and the linked webaudio-param display. In this expression, the `x` will represent current `value`. For example, `conv="(Math.pow(10,x)*20).toFixed(0)"` is specified, for range of value between 0 and 3, the range of convValue corresponds to 20 to 20000. As another example, if `conv="['sin','saw','sqr','tri'][x]"` is specified, for values from 0 to 3, each string are assigned respectively.
**enable**      | `0`,`1`| `1`    | Enable control with the pointing device.
**colors**      | string | "#e00;#000;#000" | Semicolon separated 3 colors for 'indicator', 'body' and 'highlight'. These colors are used in default knob (when `src` is not provided).
**outline**     | `0`,`1`, string| `0`    | Border style when focused. `0`:no outline. `1`:equivalent to `"1px solid #ccc"`. Any other string will be applied to the style's outline attribute only when it has focus. 
**midilearn**   | `0`,`1`| `0`    | If `1`, MIDI learn function with right-click menu is enabled.
**midicc**      | string | null   | Assign MIDI control change to this knob, with format `ch.cn`, here the `ch` is channel (1-16, ignore channel if 0) and `cn` is control number (0-119).

### webaudio-slider

Attribute       | Options| Default | Description
----------------|--------|---------|------------
**src**         | string | null    | url of the slider background image. Solid background color if not specified.
**knobsrc**     | string | null    | url of the slider knob part image. Internal embedded resouce is used if not specified.
**value**       | float  | `0`     | The current value. Also used as initial value if specified.
**defvalue**    | float  | Initial 'value' is used if not specified | The default value that will be used when ctrl+click.
**min**         | float  | `0`     | Minimum value of the slider.
**max**         | float  | `100`   | Maximum value of the slider.
**step**        | float  | `1`     | Value step of the control. The 'value' is always rounded to multiple of 'step'.
**width**       | int    | `24`    | Slider display width in px.
**height**      | int    | `128`   | Slider display height in px.
**knobwidth**   | int    | same as 'width' if 'direction' is `vert`, or same as 'height' if 'direction' is `horz` | Slider knob part width in px.
**knobheight**  | int    | same as 'width' if 'direction' is `vert`, or same as 'height' if 'direction' is `horz` | Slider knob part height in px.
**ditchlength** | int    | ('height'-'knobheight') or ('width'-'knobwidth')  depends on 'direction' | Knob movable length.
**direction**   | `"vert"`,`"horz"`| `"vert"` | Slider direction. vertical or horizontal.
**tracking**    | `rel`,`abs`| `rel` | If 'abs', the slider follows 1:1 to the position of the pointing device. In this mode, sensitivity is ignored. Otherwise, the slider will move by the offset you dragged the pointing device.
**sensitivity** | float  | `1`     | Pointing device sensitivity. min-max range correspond to (128 / 'sensitivity') px.
**log**         | int    | `0`     | If this value is set to 1, then the value change is logarithmic. For example, if `min="10"` and `max="1000"`, then the center value of the knob will be 100. Here, if `min` is 0 or negative, an error occurs. If `log` is set to 0, then the change in value is linear.
**valuetip**    | `0`,`1`| `0`     | Enable the overlaid value-tip display.
**tooltip**     | string | `null`  | Tooltip text that will be shown when mouse hover a while. If the text include a C-printf style value formatter like `%8.2f`, it will be replaced by current value. This formatter should be `%[n][.][m]{d,f,x,X,s}`. Here the 'n' is total columns, 'm' is after the decimal point columns. If the `conv` function is specified, the converted value `convValue` is used for display.
**conv**        | string | `null`  | If this attribute is specified, That string will be evaluated as an expression and stored as `convValue` as a string. This `convValue` will be used for the valuetip, tooltip and the linked webaudio-param display. In this expression, the `x` will represent current `value`. For example, `conv="(Math.pow(10,x)*20).toFixed(0)"` is specified, for range of value between 0 and 3, the range of convValue corresponds to 20 to 20000. As another example, if `conv="['sin','saw','sqr','tri'][x]"` is specified, for values from 0 to 3, each string are assigned respectively.
**enable**      |`0`, `1`| `1`     | Enable control with the pointing device.
**colors**      | string | "#e00;#000;#fff" | Semicolon separated 3 colors for 'knob', 'background' and 'highlight'. These colors are used in default knob (when `src` or `knobsrc` is not provided).
**outline**     | `0`,`1`, string| `0`    | Border style when focused. `0`:no outline. `1`:equivalent to `"1px solid #ccc"`. Any other string will be applied to the style's outline attribute only when it has focus. 
**midilearn**   | `0`,`1`| `0`     | If `1`, MIDI learn function with right-click menu is enabled.
**midicc**      | string | null    | Assign MIDI control change to this slider. with format `ch.cn`, here the `ch` is channel (1-16, ignore channel if 0) and `cn` is control number (0-119).


### webaudio-switch

Attribute       | Options   | Default | Description
----------------|-----------|---------|------------
**src**         | string    | Internal embedded resource is used if not specified | url of the vertical stitched switch image
**value**       | `0`,`1`   | `0`     | The current value (`0` or `1`). Also used as initial value of the switch if specified
**defvalue**    | `0`,`1`   | Initial 'value' is used if not specified | The default value that will be used when ctrl+click
**width**       | int       | `32`    | Switch display width in px
**height**      | int       | `32`    | Switch display height in px
**type**        | `"toggle"`,`"kick"`,`"radio"` | `"toggle"` | Switch type. `"toggle"` switch has so-called 'checkbox' function. `"radio"` switch is a radio-button and the `"kick"` switch is a general command button
**group**       | string    | `null`  | Group id string used if the 'type' is `"radio"`. Only one switch will be set to `"1"` in same group
**invert**      | `0`,`1`   | `0`     | exchange on and off image
**tooltip**     | string    | `null`  | Tooltip text that will be shown when mouse hover a while
**enable**      | `0`,`1`   | `1`     | Enable control with the pointing device.
**colors**      | string    | "#e00;#000;#fff" | Semicolon separated 3 colors for 'knob', 'background' and 'highlight'. These colors are used in default switch (when `src` is not provided).
**outline**     | `0`,`1`, string| `0`    | Border style when focused. `0`:no outline. `1`:equivalent to `"1px solid #ccc"`. Any other string will be applied to the style's outline attribute only when it has focus. 
**midilearn**   | string    | null    | If `true`, MIDI learn function with right-click menu is enabled.
**midicc**      | string    | null    | Assign MIDI control change to this switch. with format `ch.cn`, here the `ch` is channel (1-16, ignore channel if 0) and `cn` is control number (0-119).

### webaudio-param

Attribute      | Options | Default | Description
---------------|---------|---------|------------
**src**        | string  | Black rectangle if not specified | Background image or color. Transparent if set to `""`, or url to background image.
**value**      | float   | `0`     | The current value. Usually same as linked control
**width**      | int     | `32`    | Parameter display width in px
**height**     | int     | `20`    | Parameter display height in px
**fontsize**   | int     | `9`     | Font-size of the parameter display
**colors**     | string  | `"#fff;#000"` | Semicolon separated 2 colors for text and background. background color is used when `src` is not defined.
**outline**     | `0`,`1`, string| `0`    | Border style when focused. `0`:no outline. `1`:equivalent to `"1px solid #ccc"`. Any other string will be applied to the style's outline attribute only when it has focus. 
**link**       | string  | `null`  | Specify the linked webaudio-knob/slider/switch by Id
**rconv**      | string  | `null`  | Specify the reverse conversion of target's `conv`. It is needed if the target knob/slider use conversion by `conv` attribute and the user edit the `webaudio-param` value directory by keyboard. The reverse converted value will be set to linked target. For example, when the target knob/slider use `conv="Math.pow(10,x)*20"` attribute, this `webaudio-param` should be `rconv="Math.log10(x/20)"`.

### webaudio-keyboard

Attribute  | Options   | Default| Description
-----------|-----------|--------|------------
**values** | int array | `[]`   | The array of current pressed key numbers. "values" may has more than one element in multi-touch environment.
**width**  | int       | `480`  | Keyboard display width in px
**height** | int       | `128`  | Keyboard display height in px
**min**    | int       | `0`    | Lowest Key number. Each key is numbered incrementally from this number. If the "min" is not `0` and the modulo 12 is not zero, the keyboard is started from corresponding position (not-C). Note that the specified key should be a 'white-key'.
**keys**   | int       | `25`   | Number of keys. `25` means 25 keys keyboard.
**colors** | string    | '#222; #eee;#ccc; #333;#000; #e88;#c44; #c33;#800' | semicolon separated 9 keyboard colors. 'border; whitekey-grad-from;whitekey-grad-to; blackkey-grad-from;blackkey-grad-to; active-whitekey-grad-from;active-whitekey-grad-to; active-blackkey-grad-from;active-blackkey-grad-to'. Each key surface can has garadient left to right with 'from' and 'to'.
**outline**     | `0`,`1`, string| `0`    | Border style when focused. `0`:no outline. `1`:equivalent to `"1px solid #ccc"`. Any other string will be applied to the style's outline attribute only when it has focus. 
**enable** | `0`,`1`   | `1`    | Enable control with the pointing device.

---
## Functions
### setValue(value, fire)  
`webaudio-knob` | `webaudio-slider` | `webaudio-switch`  
**description**: Each control can be setup and redraw by calling this function from JavaScript.
If the `fire` parameter is `undefined` or `false`, this function will not fire `'change'` event. Or the `change` event will be fired.


### setNote(state, note [,audioContext, when])  
`webaudio-keyboard`  
**description**: webaudio-keyboard can be setup pressing state with this function from JavaScript. corresponding key specified by the `note` is pressed if the `state` is non-zero otherwise the key is released. This function will NOT fire the 'change' event. If the `audioContext` and `when` arguments are specified, the pressing state will be updated after the specified time. `when` is the time in seconds on the `currentTime` time axis of the `audioContext`.

---
## Events

### 'input'  
`webaudio-knob` | `webaudio-slider`  
**description**: 'input' event is fired when knob / slider value changes while dragging.

### 'change'  
`webaudio-knob` | `webaudio-slider` | `webaudio-switch` | `webaudio-keyboard`  
**description**: 'change' event is fired when value changes is decided. It means mouse button release for knobs and sliders, or switch / keyboard state changes.
 Also issued when setValue() function call with fire flag is nonzero.
In the event handler of `webaudio-knob`,`webaudio-slider` or `webaudio-switch`, current value can be get with referring `event.target.value`.  

```
var knobs = document.getElementsByTagName('webaudio-knob');
for (var i = 0; i < knobs.length; i++) {
  var knob = knobs[i];
  knob.addEventListener('change', function(e) {
    console.log(e.target.value);
  });
}
```

For the `webaudio-keyboard`, each 'change' event has the property '.note' that contain a array `[key-state, key-number]`. For example `event.note = [1, 60]` if the key#60 is on, or `event.note = [0, 60]` if the key#60 is off.

```
var keyboard = document.getElementsById('keyboard');
keyboard.addEventListener('change', function(e) {
	if(e.note[0])
		console.log("Note-On:"+e.note[1]);
	else
		console.log("Note-Off:"+e.note[1]);
});
```

### 'click'  
`webaudio-switch (kick)`  
**description**: 'click' event is emitted if the 'kick' type webaudio-switch has clicked.

---
## WebAudioControlsOptions
By setting the global object, WebAudioControlsOptions, you can specify default values such as the knob size or colors etc when attribute setting on each tag is omitted.
This declaration should be prior to the webaduio-controls.js loading.
```
<script>
WebAudioControlsOptions={
  useMidi:1,
  knobDiameter:80,
  switchWidth:40,
  switchHeight:20,
};
</script>
<script src="webaudio-controls.js"></script>
```
The items that can be set are as follows

name        | default | description
------------|---------|----------------
useMidi     |0        | enable control from midi devices
midilearn   |0        | enable midilearn function for each knobs/sliders/switches
outline     |0        | border display when focused
valuetip    |0        | valuetip display
knobWidth   |0        | width for knobs
knobHeight  |0        | height for knobs
knobDiameter|64       | diameter for knobs
knobSrc     |null     | knob image source
knobSprites |0        | knob image number of frames
knobColors  |"#e00;#000;#000"| color setting for knobs
sliderWidth |24       | width for sliders
sliderHeight|128      | height for sliders
sliderKnobWidth|0     | width of slider knob
sliderKnobHeight|0    | height of sliderknob
sliderColors|"#e00;#000;#fcc"| color setting for sliders
switchWidth |0        | width for switches
switchHeight|0        | height for switches
switchDiameter|24     | diameter for switches
switchColors|"#e00;#000;#fcc"| color setting for switches
paramWidth  |32       | width for param
paramHeight |20       | height for param
paramSrc    |null     | param background image source
paramColors |"#fff;#000"| color setting for param

---
## Creating knob images
webaudio-knob (with sprites is `0` (default)) use a single frame knob image that indicate center position.
For example,  
![](img/testknob.png)  
This image will be rotated from -135deg to +135deg. This approach will works well if the image is flat designed, but more complex animation (for example, drop-shadowed, highlighted or something elastic) will need pre-rendered frame-by-frame animation as below.

webaudio-knob (with non zero "sprites") use a vertical 'stitched' multi-frames animation image, and webaudio-switch use a vertical 'stitched' two-frames animation image.
For example,   
![](img/LittlePhatty_sample.png)
![](img/switch_toggle.png)  

This knob example has only 5 frames but it should has more frames for smooth animation. I recommend to use JKnobMan/WebKnobMan for making these stitched images,

- [JKnobMan](http://www.g200kg.com/en/software/knobman.html) -- Java based Knob image creation tool.
- [WebKnobMan](http://www.g200kg.com/en/webknobman/) -- WebApp version of the JknobMan
- [KnobGallery](http://www.g200kg.com/en/webknobman/gallery.php) -- knob data sharing space

---

Here is a brief instruction  to export knob-image from KnobGallery

- Go to [KnobGallery](http://www.g200kg.com/en/webknobman/gallery.php)
- Find your favorite knob design and click 'Open with WebKnobMan'
- Click on 'Export' to download `png` file
- Of course, you can create your own!

**Note: comply with license requirements**

---
## MIDI support: knobs, sliders and switches have midilearn/midicc support built-in

To enable MIDI related functions, add the following line before the &lt;link&gt; tag that loads `webaudio-controls.html`  

`<script>WebAudioControlsOptions={useMidi:1}</script>`

<b>Midilearn right click menu</b>: add a <code>midilearn=1</code> attribute to the <code>&lt;webaudio-knob&gt;</code>,  <code>&lt;webaudio-slider&gt;</code> and  <code>&lt;webaudio-switch&gt;</code> elements. Then right click on the element in the GUI, a midi learn menu should appear. Then, operate one of your midi controller and it should start actionning the webaudio-controls widget in the HTML page. <!--You can associate more than one controller to each widget. -->You can hot plug/unplug midi devices, they will be detected.

![Midi Learn Menu](img/midilearn.png)

<b>Declarative association between a midi controller and a GUI webaudiocontrol</b>: There is also an HTML <code>midicc="channel.cc#"</code> attribute that works like this:  <code>midicc="3.2"</code> means "listen to a cc event on channel 3, cc number 2". If you don't know the channel/cc number of your controller: 1) add a <code>midilearn=1</code> attribute so that a right click on the GUI widget will display the midilearn menu, 2) select "learn" in the menu, 3) operate your knob/slider/switch, normally the midi controller and the GUI object are in sync. 4) look at the devtool console, there is a message indicating the channel and cc number, for example "channel 0, cc 28". Then if you add the attribute midicc="0.28" to the HTML of your knob/slider/switch, the midi mapping between your GUI webaudiocontrol and your midi controller will be automatic. Follow the links at the end of this section and look at the HTML source code to see some examples.

Example: associate a knob with a controller on channel 7, cc number 7:

```
<webaudio-knob midilearn=true midicc="7.7" ...></webaudio-knob>
```

<b>External midi event listener (hook): </b>you can also declare in your HTML file your own midi event listener (for example for listening to program changes events): use the <code>webAudioControlsMidiManager</code> object, that comes with an <code>addMidiListener</code> method. Like that you will benefit from the MIDI code included in the webaudiocontrols. Here is an example (also, look at the source code of the Sample1.html demo, and open the devtool console to see midi messages received by the hook at the end of the HTML file).

```
<script>
// add this to your html page that uses webaudiocontrols
webAudioControlsMidiManager.addMidiListener(function(event) {
    var data = event.data;
    var channel = data[0] & 0xf;
    var controlNumber = data[1];

    console.log("Midi event hook: data:[" + data + "] channel:" + channel + " cc:"+controlNumber);

    // do whatever you want with the event
    // ...
});
</script>
```

Demo at: https://wasabi.i3s.unice.fr/AmpSimFA/ and at https://wasabi.i3s.unice.fr/AmpSimFA/sample1.html


---
## License
WebAudio-Controls is developped based on:  
- [WebAudio-Knob](https://github.com/agektmr/webaudio-knob) by [Eiji Kitamura](http://google.com/+agektmr)  
- [WebAudio-Slider](https://github.com/ryoyakawai/webaudio-slider) by [Ryoya KAWAI](https://plus.google.com/108242669191458983485/posts)  
- [WebAudio-Switch](http://aikelab.net/switch/) by [Keisuke Ai](http://d.hatena.ne.jp/aike/)  
Integrated and enhanced by [g200kg](http://www.g200kg.com/)

Copyright (c) 2013 Eiji Kitamura / Ryoya KAWAI / Keisuke Ai / g200kg /  @micbuffa / @CellouBalde  
Licensed under the Apache License, Version 2.0

---

Knob/Switch images in samples are from [Knob Gallery](http://www.g200kg.com/en/webknobman/gallery.php)  
[switch_toggle.knob](http://www.g200kg.com/en/webknobman/gallery.php?m=p&p=58) by [az](http://bji.yukihotaru.com/) (c) 2011 [CC-BY](http://creativecommons.org/licenses/by/3.0/)  