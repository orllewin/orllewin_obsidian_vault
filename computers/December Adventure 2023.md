A [December Adventure](https://eli.li/december-adventure) Posts are in reverse order, latest first.

## 21

Travelling home today, so no time for coding, I'm on the train wrapping up some dayjob work before the Xmas break. I did spend last night in the hotel moving my old software projects from Codeberg to Github, and referencing them here in this Obsidian vault (all available to browse in the sidebar to the left).

## 20

On-site day with the day job, so no project work. On the train down yesterday though I rewrote my net-radio project. Previously I'd implemented it with [KotlinJS](https://kotlinlang.org/docs/js-overview.html) and it was having some new issues with CORs, possibly due to me stopping paying for [Neocities](https://neocities.org/). Fixing it would have meant finding the original project and probably ignoring Jetbrains IDEA prompts to update all the build dependencies. Instead I rewrote the project from scratch in three files: `index.html`, `style.css`, and `script.js` and removed the external JSON file dependency entirely, instead encoding the various parameters as a Base64 query string. It's installable as PWA, and sets the audio metadata so works really well on mobile (or at least Android): [https://orllewin.github.io/radio/](https://orllewin.github.io/radio/index.html?eyJ0aXRsZSI6Ik9ybGxld2luIFJhZGlvIiwic3RhdGlvbnMiOlt7ImxhYmVsIjoiRE8hWU9VIVdPUkxEISIsInVybCI6Imh0dHBzOi8vZG95b3V3b3JsZC5vdXQuYWlydGltZS5wcm8vZG95b3V3b3JsZF9hIiwiY29sb3VyIjoiI2Y0ZGU3ZiIsImljb25VcmwiOiJodHRwczovL29ybGxld2luLnVrL3JhZC9yYWRfZG95b3VfMjU2LnBuZyJ9LHsibGFiZWwiOiJOZXRpbCBSYWRpbyIsInVybCI6Imh0dHBzOi8vbmV0aWxyYWRpby5vdXQuYWlydGltZS5wcm8vbmV0aWxyYWRpb19hIiwiY29sb3VyIjoiIzQwN2VlZSIsImljb25VcmwiOiJodHRwczovL29ybGxld2luLnVrL3JhZC9uZXRpbF9yYWRpb18yNTYucG5nIn0seyJsYWJlbCI6Ik5UUyAxIiwidXJsIjoiaHR0cHM6Ly9zdHJlYW0tcmVsYXktZ2VvLm50c2xpdmUubmV0L3N0cmVhbSIsImNvbG91ciI6IiNjOTlkYzQiLCJpY29uVXJsIjoiaHR0cHM6Ly9vcmxsZXdpbi51ay9yYWQvcmFkX250c18yNTYucG5nIn0seyJsYWJlbCI6Ik5UUyAyIiwidXJsIjoiaHR0cHM6Ly9zdHJlYW0tcmVsYXktZ2VvLm50c2xpdmUubmV0L3N0cmVhbTIiLCJjb2xvdXIiOiIjOEU4MUE2IiwiaWNvblVybCI6Imh0dHBzOi8vb3JsbGV3aW4udWsvcmFkL3JhZF9udHNfMjU2LnBuZyJ9XX0=)
## 19

A travel day, heading down to Salisbury for an on-site work visit. As usual I'm the only person wearing a mask on the train. Even without COVID it's a good habit, why risk getting a cold just before Christmas. Tech-wise I've switched to a `sampleplayer` for the Granular module as mentioned yesterday, it has fixed the ui-locking problems so the input automation sockets can stay - which is a relief because it sounds fantastic. I've also done some lower-tech work, pulling together various projects and crafts into this Obsidian vault, you should be able to browse in the side-bar to the left.

## 18

I ran Granular on hardware and it works great except for the clock sync, those subsamples really do hit the framerate too much, two choices: remove the clock input sockets entirely or rewrite the subsample logic. The subsamples currently involve file io, which is slow of course, but in-memory subsamples was showing some weird behaviour with the Playdate sound API, switching from `sampleplayer` to `fileplayer` fixed everything. The code has been much improved and simplified since then, maybe reverting to `sampleplayer` would be fine...

I've also ported the ModularPlay manual web page to here on Obsidian: [[ModularPlay]]. Doing this daily update for December Adventure has reminded me how much more convenient Obsidian is than manually writing web pages.

## 17

![[signal-2023-12-17-174002_002.jpeg]]

Little progress on anything today, other than parenting; we visited [Samlesbury Hall](https://www.samlesburyhall.co.uk/). I've fixed the start and end constraints in the Granular module. Getting granular sounds back into Granular won't be possible though I don't think, at least not without significant effort - the pseudo oscillator module is based on a timer, and in order to not impact the ui performance too much it's fairly slow. To slowly step through a sample at a granular scale the oscillator would need to perform at much smaller discreet increments, any other way of implementing it would still require high frequency updates, with the Playdate being single-threaded it's just asking too much. The module sounds fantastic though, it's just badly named. Even in 'normal' use as a random looper it still locks the ui occasionally when it's generating a subsample. Monday tomorrow, so lots of day job work to do, but I'll try and record a video with progress to far running on hardware.

![[signal-2023-12-17-174052_002.jpeg]]
## 16

The Granular module in ModularPlay on Playdate is now stable. Still some work to do with the start and end limit points, and it'd be useful to display which sample is loaded, but other than that it's in, already more useful than the standalone Granular app; you have access to everything else already in ModularPlay. It's the weekend, we have kids Christmas fairs and things to go to, I'm not sure if I'll find time to do more coding.

<iframe width="700" height="480" src="https://www.youtube.com/embed/JQPFtF1w3R4" title="December Adventure Day 16: Granular in Modular Play progress" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 15

Granular inside Modular Play! I've never seen the Playdate crash so much as while developing this. The sample player API doesn't like what I'm trying to make it do here. It's still extremely buggy and fragile, the start/end range bars don't work correctly, it crashes if you change sample more than once, it crashes if you look at it wrong, it's not hooked up to the patch cable system yet, you can't change octave range, etc etc but... it already sounds great.

<iframe width="700" height="480" src="https://www.youtube.com/embed/CqJDza1-KV0" title="Deember Adventure Day 15: Granular in Modular Play" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 14

Lento 2 building, slowly bringing the dependencies up-to-date. Android is terrible, you have to juggle Gradle versions, Kotlin versions, multiple dependency versions, OS versions and their ever-changing breaking API policies, particularly around file io permissions - any of which can break and leave you hunting solutions on Stack Overflow with other unfortunate souls, and it all requires a huge amount of network bandwidth which we don't have here up on the hill.

In happier news I've started bringing [Granular](https://orllewin.github.io/playdate/granular/) functionality over to ModularPlay. Granular's main screen was great but the effects section wasn't as well designed. If I can get the same audio experience I think I'll code-freeze Granular and add a note to use ModularPlay instead. This was spurred by Luca posting this lovely clip using Granular:

<iframe width="700" height="480" src="https://www.youtube.com/embed/c35bCGW594M" title="Playdate and Teenage Engineering TX-6" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Because ModularPlay is ... modular, all that needs writing to get all Granular features is the main sub-sample selection, the random moving logic, the nice track view, there's already a Sample Playback module which handles loading samples which I've cloned to turn into 'GranularMod'. Each Granular module will have a single track, to mirror the Granular app you just add five granular modules and whatever effects you like. I might also add some automation - so you could control movement via an oscillator or a new random position in time with some external clock event.

## 13

Having a day off projects, although I have started bringing back Lento from the dead. The page makes little sense currently as it's just a copy-paste of the original page from when it was available on Google Play: [orllewin.github.io/android/lento](https://orllewin.github.io/android/lento/). I've pulled the Lento 2 repository to try and get that building again, some screens may need rewriting in Compose, the main Camera screen can stay using old-school XML though, I'm going to reduce the scope and just have a bare-bones functional LUT camera. I'll rip out the support for anamorphic lenses too, Moment cases kept falling apart on me and the hard-sell marketing started to grate too much.

The old webpage also had a hacked together javascript gallery: [orllewin.github.io/android/lento/gallery/001/](https://orllewin.github.io/android/lento/gallery/001/). It's nice seeing the example photos featuring my kids, and how much they've grown in the year or two since the Lento page was put together:

![[Screenshot-2021-12-27-at-19.01.34.png]]

## 12

No work on ModularLöve today, instead I'm trying to set up [Nova IDE](https://nova.app/) for C development. Creating a custom build and run task is simple enough, but the only way I can find of getting syntax highlighting is by using the C-Dragon plugin. That can't see SDL which my build task is linking via clang: `clang main.c -I/Library/Frameworks/SDL2.framework/Headers -F/Library/Frameworks -framework SDL2 -o HelloSDL`. I'm a beginner with C but C-Dragon setup seems a bit obtuse and I'd prefer to use Nova than Xcode. I have just found the [Icarus](https://github.com/panicinc/icarus) extension via the web, will see if I can make better progress with that (Update: Icarus did indeed work perfectly):

<iframe width="780" height="599" src="https://www.youtube.com/embed/Z9A2WCTL0pU" title="C + SDL HelloWorld in Nova IDE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Yesterday I also managed to finish the Ever-Ready bike light project, short video here: [youtube.com/shorts/s2od27oFNTo?si=hwue9HoYmk3jcEGj](https://youtube.com/shorts/s2od27oFNTo?si=hwue9HoYmk3jcEGj) 

![[P_20231211_144627.jpg]]
![[P_20231211_144612.jpg]]
![[P_20231211_144622.jpg]]
## 11

A Monday, very busy, but I've added Flanger and Ring Modulator modules. I've also pushed a public repository and released the project under the [Parity License](https://paritylicense.com/).

[github.com/orllewin/love2d_modular_love](https://github.com/orllewin/love2d_modular_love)

<iframe width="695" height="460" src="https://www.youtube.com/embed/UkHTfvCUOYM" title="December Adventure Day 11 - Flanger and Ring Modulator" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 10

Timed switches, so you can toggle different parts of a patch, not very musically interesting this recording but it also serves as a stress test with a large number of modules. Every module does have a check in it's draw method so that it can determine if it's on-screen or not before drawing but at the moment it's unimplemented and just returns true: `if self:visible(x, y) then --do drawing operations ... end`, maybe that'll be the next bit of work. I'm also trying to decide whether I have the time and energy to develop this further and eventually sell it on itch.io or to just find a suitable license and put it in a public repo:
<iframe width="850" height="599" src="https://www.youtube.com/embed/DRj2BKFvBdY" title="December Adventure Day 10: Timed Switches" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 9

Posting this a little early as I'm unlikely to get much free time this weekend. I've added a couple of the smaller modules from the Playdate version to ModularLove: Bifurcate 2 which splits/duplicates an event, and the Blackhole module which swallows random events depending on the gravity level. This little patch has some moments that sounds a little like [Bola](https://bleep.com/release/10758-bola-soup).

Relaxen und watchen das blinkenlichten.

<iframe width="775" height="599" src="https://www.youtube.com/embed/w2R-u6DJ0zQ" title="December Adventure Day 9" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 8

More effects: Chorus, Delay, Distortion, Reverb, and Compressor. The midi keyboard has been improved quite a bit, it now takes input from the computer keyboard, with a shift modifier to move up an octave. Plus and Minus also shift the octave range up and down.

<iframe width="755" height="599" src="https://www.youtube.com/embed/9qmXLPM0WuU" title="December Adventure Day 8 - more ModularLove" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


## 7

Effects pedals. I'm not sure how LÖVE combines effects, I don't think when you chain a reverb after a chorus the chorus is having reverb applied etc etc. The distortion is lacking low end too, I'll have a look at filters next I think.

<iframe width="795" height="599" src="https://www.youtube.com/embed/Txy7zXphLt0" title="December Adventure Day 7: effects pedals." frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 6

A lot of progress, but I might slow down and look for something a bit more off the beaten path to work on for a while. I've completed the clock modules by adding Clock Delay and Clock Divider - both simple because Delay was already implemented in the Generative module, and Divider just emits every other event. An on-screen midi keyboard is also largely done, the only thing it doesn't have from the Playdate version is the ability to move up and down octaves. I've also added the logic to move cables when you move a module, it breaks visually in some circumstances but it's largely finished.

<iframe width="755" height="599" src="https://www.youtube.com/embed/ltcRREo2z1o" title="December Adventure Day 6 - Clock nodules and midi keyboard" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 5 

* Bubble Chamber 'clock' added, when a molecule hits a module side a clock event is emitted. 
* A copy of Generative Std. called Generative Small, has everything the original has apart from the clock delay and black hole.
* The sample synth now has two samples internally, so if two notes are played in quick succession the first can decay naturally. If both are playing when a third note comes in one is picked at random to stop and re-trigger with the new note.
* Ability to move a module by pressing 'm' while hovering (doesn't move any attached cables yet).

<iframe width="755" height="599" src="https://www.youtube.com/embed/CUIyjFUM8Vc" title="December Adventure Day 5: bubble chamber clock, move modules, &#39;generative small&#39; module" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 4 

We're snowed-in, so this morning I have to walk the eldest to school before finding somewhere to work in the valley (Update: we did get out in the car without issue in the end). I have finished the 'Generative' module though, all the behaviour from the Playdate version is in place: when the module receives a clock event there's a 1 in 4 chance of the note being delayed by the set interval, the gravity encoder sets the chance of the event being swallowed entirely by a blackhole, and the rest of the controls set the key and scale, and the pitch range.

<iframe width="755" height="599" src="https://www.youtube.com/embed/VH0Ha0fvcyg" title="ModularLove: December Adventure Day 4 - Generative Module done" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

I found some time throughout the day to start work on the front light of the Ever-Ready Exide modernisation project:  
<iframe width="966" height="543" src="https://www.youtube.com/embed/qF_bLLfFxhw" title="4 December 2023" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 3

Today's adventure was adding a dropdown menu so modules can easily set different parameters. As only one dropdown can be shown at a time it's actually a single view shared by all modules, they just set the items and coordinates and listen for the selected index. Adding this means the sample synth can now change samples, not what I planned to work on today but we've had snow and I need to take the kids out to play and fetch the Christmas tree from storage. Towards the end of the video you can see a new option to toggle the module type labels by pressing a key.

<iframe width="755" height="599" src="https://www.youtube.com/embed/ibRNMksFKrw" title="ModularLove: Dropdown menu for sample selection" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 2

Today I added a rotary encoder to the clock and all the logic required to add knobs and sliders to modules by capturing the mouse down and mouse move combination correctly: when there's a mouse down event the framework looks for a collision with a module, then it asks the module if it accepts scroll events, if it does a `controlLock` boolean is set, from that point all scroll events are sent to that individual module until a mouse up event resets `controlLock`. At the moment there's a basic clock-event-to-midi-note Generative module which emits a random C Pentatonic scale note - the next step is to port the rest of that modules feature from Modular Play.

<iframe width="755" height="599" src="https://www.youtube.com/embed/kOIWEnhdSx8" title="ModularLove rotary encoder implemented (December Adventure day 2)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## 1

I've started porting [Modular Play](https://orllewin.github.io/playdate/modular_play/) to [LÖVE](https://love2d.org/). It started a few days ago getting the basic framework in place for a 'canvas'/patch which you can drop modules onto and connect with 'catenary curve' cables: [YouTube](https://www.youtube.com/watch?v=zfKJy0-MRQ8)You can click and drag with a mouse to pan around the canvas, or use a two-finger scroll on a trackpad to do the same. Dragging a cable from one module to another is done with the 'c' key and mouse - it all feels very intuitive. One last thing I added late at night was copy/paste - you can 'command-c' while hovering on a module to copy the module type, then 'command-v' to drop a new instance, the menu is quick, but key combos are quicker.