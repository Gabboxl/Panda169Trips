# Blaupunkt radio without AUX input

As many other people did, I wanted a way to listen to my music on the radio. The only obvious way was through a CD. So I started searching for ways to inject audio from other sources into the radio.

There are a few variants of Blaupunkt car radios that ship with the Panda 169.
There are two "old" versions, which have the Blaupunkt logo on the frontend, and a "new" version without a logo on it. The newer version doesn't have a logo because it was produced after the acquisition of Blaupunkt by Bosch.
This is the generic ISO pinout of the radio:
-image-

On forums, the only solution that gets shared is to use the phone AUX input. Then you would press the CD (or SOURCES button) on the radio to enable the AUX mode so you can start listening to audio from the auxiliary input source.

SO I tried following this tutorial. I bought a yellow ISO connector, plugged it into the radio, and pressed the CD button, but on the radio's display appeared the phrase "No sources available" (it appeared even before connecting anything).

So I started searching on forums deeply, and found that I had the ONLY model that didn't support the AUX source for phones. Shit. Typical of Fiat doing those things. I would have bought the phone connector as a car optional. 
In fact, looking at the pinout diagram, we can see that those pins are marked as "NC", which means Not Connected or something like that. So those pins aren't connected to anything useful on my radio model.

I kept searching.
I thought that practice by Fiat was not a very economically viable practice. Even for Bosch, which had to produce and ship different circuitry and software only for Fiat.

I had no solution. So I started developing a little project to analyze the circuit (with my oscilloscope) to find the right and left channels coming from the CD reader, solder my right/left sources to inject my audio, but only before having the sources processed by the mixer (so I could retain all functionality of the radio's built-in equalizer).
I also wanted to find the data input that signals that a CD had been inserted into the reader, so that by pressing the "CD" button on the radio, it actually switches to the CD reader's audio channels (so I could avoid inserting a CD to make that happen).

I found some internal documents with circuit schematics of a very similar model of my radio.

But before starting actually analyzing something... I found that video...

<video>

Basically, what he does is to short-circuit the DATA-IN and DATA-OUT pins on the opposite part of the pinout. And magically, they seem to enable the AUX input of the radio. Then he uses those AF-L and AF-R pins to inject the audio from an aux. source. That seemed to me crazy. Also, because literally NO ONE talked about this ANYWHERE!

So I tried to do that.

I brought home my radio, I set up a bench power supply, and shorted those DATA pins.
It worked! By pressing the CD button, the AUX word appeared on the screen! I only had to test if I could actually listen to any audio coming externally.

------so

