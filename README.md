# random

Soothing scrolling random ASCII text.

# How it's made

I remember and love the good-old days [of ASCII (specifically extended ascii)](https://www.asciitable.com/). I loved watching scrolling random ASCII text on my old 286, 386, 486 and Pentium machines in the 90s. Absolutely loved it. I found the scrolling pixel text, with all the strange symbols really relaxing. I created many programs back in the day to pump random ASCII text to the screen (using I think, QBASIC, C, Java, Ruby, Perl). In fact, I loved that so much, such a program was basically my "Hello World" for picking up a new language. I was a kid then.

I created this repo a couple of years ago, but never could find the correct font that would display all the block characters from [the extended ASCII set](https://www.asciitable.com/) that I remembered from my youth. All those block characters and strange (and cute, hello smiley face guy, and card suite guys :)) symbols. 

This weekend on a whim (probably some procrastination, too :)) I decided to set out online and see if I could track down "The One True Font". 

I quickyl discovered that [block](https://en.wikipedia.org/wiki/Block_Elements) and [box](https://en.wikipedia.org/wiki/Box-drawing_character) characters in Unicode do not exactly seem to correspond to the characters I loved of yore. Oh woe, so sad. I thought everything was lost. 

Then it dawned on my, little by little, (like those little random characters creeping across the screen), that I may need some sort of "ugly" and "tiresome" transpose matrix...or more simply just a map or table, to translate from 0x00 through 0xFF to the wider Unicode fields of the Matrix in which we all now live apparently. Ugly and tiresome because I didn't want to track down, line up, assess, decide, etc, which of my little favs from the 90s corresponded to which Unicode ditty in the massive Universe of unicodes. Ugh. So tiresome. And ugly....ugh. 

Anyway...I went a searching and a jaunting online to see what I can find. And [somehow](#I-now-forget), I now forget, but probably down some Stackoverflow rabbit hole, I discovered [this gem of obsessive retro fetishism](https://int10h.org/oldschool-pc-fonts/fontlist/font?ibm_vga_9x14), and it had my font (or well a font that looked and sounded pretty much like my font, and had the cute little box characters that I missed so dearly), which I promptly downloaded. 

Thank god for crazy people because this [Old-school Font resource](https://int10h.org/oldschool-pc-fonts/) totally saved me and let me roll around in my  relaxation-focused tech nostalgia tonight, and share it with you. 

But my first trial of the new font was blaargh lost. I tried a simple: 

```html
@font-face {
  font-family: DOS;
  src: url("./WebPlus_IBM_VGA_9x14.woff");
}
  
... snip ...


for( let i = 0; i < 256; i++ ) {
  p.innerText += String.fromCharCode(i);
}
```

Hoping, with a lot of glee, to see some old-time ASCII goodness. But no. It was not to be. So sad. Really. 

Where all my box chars should be stood empty screen. So sad. Really. Truly very sad.

Anyway, I went back to the crazy Old School font resource and studied the tables there provided. It seemed that some crazy nutjob (crazy but adorable and lovely) had created a map from the old-school CP 437, to something roughly corresponding in Unicode, and had provided all this information in a really cute tooltip over their table of 0x00 - 0xFF. 

Another lazy ugly tiresome avoidance moment lay in wait for me here. I didn't want to read over the entire table, find out which guys were Unicode, and then transpose the codepoints into a table by hand. Ugh. No. Just NO.

Anyway, I pulled quick:

```js
Array.from(charset437.querySelectorAll('strong:last-of-type')).map(e => e.innerHTML)
```

extracted the JSON from Chrome DevTools, pasted it into my vim editor window in iTerm2 conjured with a hotkey (⌘+`), and turned my simple innocent little loop above into the momentous:

```js
 for( let i = 0; i < 256; i++ ) {
    p.innerText += String.fromCharCode(M[i]);
  }
```

Reloading my browser page, was greeted with the lovel boxes. So happy. 

No, with font found, and map created, I could paste this unrivaled genius code into my existing little ditty (née random, above), and rock on. Boxes everywhere.

I made a few more adjustments.

I'll leave them as easter eggs. (keys and pointers, essentially for "flow control" :P ;) xx ;p ;P xx ;P )

ENJOY :heart:

**Readme line from the original version:**

Using `crypto.getRandomValues` and old fonts, some of which are [here](https://int10h.org/oldschool-pc-fonts/readme/).




