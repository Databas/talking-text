# talking-text

talking-text is a jQuery plugin that helps you recreate the typing-it-out-by-itself effect used in many of your favourite RPG games.

Here's what make this more than a typewriter effect:
- Pauses on punctuation
- Slows down on specified elements so you can E-M-P-H-A-S-I-S-E things
- Optionally makes little beep boop sounds as it types using the Web Audio API! With customisable 'voices'!

I originally made talking-text for [a webcomic of mine](http://gwil.co/peaches/tales/2.html).

## Usage

talking-text works on any element with text in it. Here's an example:

```html
<p class="wizard">Fool! One must <span class="angry-red-text">never</span> even think of the <em>Forest of Impenetrable Sadness</em>!</p>  
```

Link the plugin, and you're ready to go:

```javascript
$(document).ready(function() {
	$('.wizard').talkingText();
});
```

This will make the effect fire as soon as the page loads, but you can link it up with whichever events you choose.

## Options

You can tweak the behaviour of talking-text with three options: `slowTag`, `pace`, `voice` and `callback`.

Here's a sample with all options:

```javascript
$('.talking-text').talkingText({slowTag: 'B', pace: 100, voice: { accent: 1, pitch: 200}, callback: function() {
	alert('Finished typing!');
}});
```

### slowTag

`slowTag` tells talking-text which element you'd like to use for typing out emphasised, slow text. It is `em` by default.


### pace

`pace` sets the number of milliseconds taken between typing out each character. It is `30` by default.

### voice

Supplying a `voice` object with your options will make talking-text utilise the Web Audio API to make little beep boop noises as it types out, just like the good old days!

To customise the 'voice' of the sound, you can do so by supplying `accent`, `pitch` and `volume` values, like so:

```javascript
$('.talking-text').talkingText({ voice: { accent: 1, pitch: 200, volume: 0.7});
```

The lower the number for `accent`, the more characters tone varies from one another. The higher the number given for `pitch`, the higher the pitch of all tones made. `volume` accepts a float from `0` (mute) to `1.0` (quite loud), and defaults on `0.25`.

And if you leave it out, talking-text makes no sound by default.

### charCallback(c)

`charCallback` is a function called each time a character is printed out, with the optional argument `c` as that just-printed character.

An example: printing out each character to the console:

```javascript
$('.talking-text').talkingText({ charCallback: function(char) {
	console.log(char);
}});
```

`null` by default.

### callback(t)

`callback` allows you to supply a function that is fired after the text has finished typing out. The optional argument `t` returns the entire text content of the element that was just typed out.

`null` by default.

## Caveats

Keep in mind that until `talkingText` is fired, the element will appear as it normally would. A simple work around is to set elements to `display: none;` and firing something like `$('.something').show()` right before firing talking-text.

You may also want to account for the fact that this plugin will change the size of the element as it takes all of the content out of the element and then pours it back in. So be explicit with your styles!

## License

Copyright &copy; 2015 Sam Gwilym

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
