# So, you’ve gotten a keyboard…

When I started designing this board, I was mostly designing it for myself and a friend. But over time, two turned into four, and four into seven. So, there are ~~seven~~ five people with vastly different levels of knowledge in relation to keyboards that I need to explain what this board can do, what they need to make it work, and what they can do to not break it.
Because of that, I have decided to split this page into three sections: getting the thing built, how it works and what is included on the board, and why I designed certain things the way I did.

## Section 1: Oh my god just tell me what I need to do to get this working I just want to use the thing
### Buying the parts:

If you just want to get this thing built, you will need three things:
-	82 Mechanical Keyboard Switches (any kind of linear, tactile, clicky, etc. – not hall effect or embedded LED)
-	Keycaps – at least a full keyboard worth (not just a 60%)
-	(Optionally) Standard Mechanical Keyboard Stabilizers
    -	3x 2U, 1x 6.25U

“But I don’t know what the heck a keyboard switch is pls help me” - you possibly

Here are some of the components I would choose for someone wanting a balanced/generic keyboard:
-	Switches: https://a.co/d/072NNe7i
-	Keycaps: https://a.co/d/04j6aQRz
-	Stabilizers: https://a.co/d/0dAz1Hp8

That’s pretty much all you need in terms of components. They can all be swapped out of course, but that’s just in case you want something very basic that can get the job done.

Some sites I would recommend if you are looking for more enthusiast components are [Divinikey](https://divinikey.com/), [keeb.io](https://keeb.io/), [CannonKeys](https://cannonkeys.com/), and [KBDfans](https://kbdfans.com/), though you can find good stuff on Amazon and AliExpress if you look hard enough.

Here is the keymap in case you want specific keycaps or a switch count.

<img src=https://i.imgur.com/tMpCEa1.png alt="topdown" width="500"/>

### Assembly

Once you have your components, the hardest part of assembly is installing the stabilizers (If I didn't install them for you).
To do this, unscrew all of the perimeter screws on the top layer, and pull the top four layers off of the PCB. Once the PCB is out, you can screw in the stabilizers on the shift, enter, backspace, and spacebar. The holes should be clear, but if not reference the switchplate. The part that hooks into the PCB is on the bottom, the top is where the screw goes in, and the wire goes into the part that moves and clips into the bottom.

<img src=https://i.imgur.com/Gi92fFP.jpeg alt="backside of pcb" width="500" />

Make sure to attach the wire bar that connects the two sides, and you should be good. Drop the PCB into the bottom half and reassemble the case as you took it apart. Once that is done, you are ready to drop in your switches. 

Place them into the slots making sure to push just hard enough to click them into the switch plate. It is Delrin so it shouldn’t break, but don’t put an unnecessary amount of pressure on it as the PCB underneath is not invincible and may bend the pins on the switch or push out the hotswap socket.
Once finished, you can put your keycaps on (the switch next to the knob can be whatever extra keycap you have) and plug it in. 

By this step you should be ready to use it. Whatever swicthes and keycaps you chose should make this a one of one keyboard and I am glad to say that I am very glad you were able to put it together and that you will use something I made. Thank you once again!

<img src=https://i.imgur.com/3wWebMq.jpeg alt="topdown" width="500"/>

## Section 2: What is going on in there and how do I customize it

### What is going on in there?

The Model-B (yes that is the name can you believe it took me that long to get there) is a bespoke 75% keyboard based on the RP2040 microcontroller running QMK firmware. It has 82 keys, a rotary encoder for volume control, and an SSD1306 OLED 128x32 display for showing a handful of screens. The keymap is custom as well as some of the code running the OLED. The switchplate is made of polyacetal (POM - Delrin) and the case is standard clear acrylic, all sandwiching a standard FR4 PCB. The window on the switchplate is meant to show off the hardware running the keyboard while still allowing for the nice feel and sounds of POM. 
 
### How do I customize it?

Modifying the switches, keycaps, knob color, etc. is a given, and I intended for them to be as easily changed as possible. Things like the case design, colors, and hardware function were not. The only hardware things I think are reasonable to consider changing would be adding foam or changing the board angle.

If you do want to add foam to this board, removing the bottom panel and adding a sheet of 1mm EVA foam should not affect the build quality and may improve the sound depending on the layering.

Other than that, the firmware this board runs is open source and any keymaps/screens can be modified to your liking. You can either modify the firmware yourself with QMK if you have it installed, or I can make whatever changes you would like and send you a compiled hex file to install it. I am working on adding this board to the QMK repository as well as getting VIA support to take me out of the equation.

### Firmware

To modify the firmware yourself, install the QMK MSYS CLI and setup your environment according to the docs. Hopefully, my board is listed as an available option, but you may be too quick and beat me to getting it up there. If that is the case, copy the model_b folder in the firmware section of my repository to `qmk_firmware/keyboards/trojan_pinata`. You can then run the command `qmk compile -kb trojan_pinata/model_b/rev0 -km default` which will compile the keyboard to a uf2 and place it in the qmk_firmware folder. 

As this is a RP2040, you can either hold the bootsel button (the top one on the right side) and reset (the button right below bootsel) to get to the RP2040 firmware drive or hit FN+ESC to automatically reset it. Drag the uf2 onto the drive and you are good to go.

<img src=https://i.imgur.com/oQIsvQG.jpeg alt="mountains" width="500"/>

## Section 3: Why did you bother making this???

Currently, I use a 75% keyboard I made for myself – the Model K. It is a very basic keyboard with all through hole components which I designed to be easy to put together, easy to program, and durable – all while being able to meet a bunch of the specifications I had in mind. The idea stemmed from not being able to find exactly what I wanted on the market, and designing a board which I could practically manufacture and reasonably expect to maintain. The Pi Pico was one of my favorite boards on the market at the time (it was still reasonably new then) and I wanted to use it in something. I did not have the experience to make a PCB with SMD components, so I made something derivative using THT components and a prebuilt development board. The whole project was basically a bunch of compromises in order to make something both functional and personal.

The project was a success, which is great! Though it does come with the caveat that I don’t really have anyway to talk about keyboards with my friends as I have a entirely different relationship with the subject as a result of interacting and thinking about them from a manufacturing and design perspective – not even to mention that I know literally nothing about the other brands as I never interact with them other than looking at them to steal ideas and implement them into my own. 

One day, I was talking to my friend about this, and I kind of wanted to make something for them as a way of both connecting and expanding my project further. So, this started. And it hasn’t stopped in over a year. The biggest reason why I am making this now is that I want to make something I can send to my friends. Pretty cut and dry, really. It has kind of expanded outside of the region of practicality and fallen into a well of wanting to do it because it is both cool and is a gift. When I realized how much I was going to spend on my first keyboard, I was not happy. It was cost prohibitive at the time, and this project beats that by six times. 

I am at the point where I am simply designing a keyboard with what I know, with the intention of gifting it to friends. I’m really worried that by sending this to certain people, I might scare them with the cost of the components I cannot provide. I don't really care if someone receives this and throws it in a closet forever. I hope, that someone reading this will understand why I built this, not why I did certain things - hopefully that is obvious as I made the best choices I could make given a budget – but I really hope that someone getting this will take the time to actually put it together and use it for a while with the context that this was made for them.

It does stress me out knowing that other people will use the thing I made for them. I am worried that people will send me messages describing issues they have and the like.

As much as I say that, I really hope you enjoy this as much as I did making it. I am sorry if I don’t respond immediately if you message me, I am really bad at this whole two-way communication thing. Thank you once again for enjoying this keyboard with me, and if you are just reading this and are not part of this, thank you for taking the time to read through all of this~
