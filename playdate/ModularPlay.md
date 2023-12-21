## About

Modular Play is a casual playground game on [Playdate](https://play.date) for building little music making patches by connecting modules with cables. It's meant to be fun and not really for serious use but it can create some beautiful music.

Itch.io link: [orllewin.itch.io/modularplay](https://orllewin.itch.io/modularplay)
## Use Headphones

**Important**: Modular Play needs to be used with external speakers of some kind, either with headphones or as part of a bigger music-making setup. The in-built Playdate speaker is tiny and has a very narrow range of usable frequencies.

## Volume

**Important**: The Playdate audio engine is additive - if you have 5 audio sources each should be set to have a volume of around 2 to avoid clipping. You get used to it, but it's painful at first.

![[dronescape.gif]]
Screenshots on this site might include unfinished or older versions of modules.

## Found a bug?

This is a complex piece of software, there will be bugs, especially in the Alpha and Beta releases. [Please open a ticket on Github](https://github.com/orllewin/modular_play_public/issues) or [comment in the itch.io community thread](https://itch.io/t/3248289/bug-reports)

## Kinopio

Development is managed using Kinopio, [you can track progress there.](https://kinopio.club/orllewin-modular-play-hobVkZawudc7bwByphsLx)

# General Info and Instructions

- When you tap (A) in empty space a context menu appears where you can navigate around all the available patch options: save, load, delete, and browse all the module categories. (A) drills down into a menu until you hit a leaf node. (B) closes and dismisses the menu with no action.
- If you tap (B) on a module and there's an empty out socket a cable will appear to plug into somewhere else - move around the patch space to another module and tap (B) again to connect the two together. Modules will generally use the next available input or output. Some modules will use whichever in or out socket is closest when you tap (B) (Unplugging individual cables isn't supported yet, you'll need to delete a module, then reconnect the cables, it's a complex feature and needs to be developed down the line).
- Tapping (B) in empty space zooms the interface. The Playdate screen is quite small so this can help a lot, get used to using it.
- While moving around patch space with the direction pad if you hold down (B) the speed increases a lot. If you have a large patch this is invaluable.
- You can invert the screen in `System > Invert Screen` (fixed in 0.0.10 Alpha, coming soon)
- There are some sound effects when adding modules and cables, you can turn these off in `System > Sound Effects Off`
- **Remember you can set the global Playdate volume from anywhere by holding the main yellow menu button and pressing left and right.**
- If you want to share a screenshot of a patch go to `System > Screenshot`, this will hide the reticle cross and pan around the patch capturing screenshots before stitching them together (see the patch images on this page). The screenshot is saved under `Disk/Data/orllewin.playdate.modularplay/images` - you'll need to put your Playdate into mass storage mode and copy the images from your computer. Alternatively you can run Modular Play in the Playdate simulator where the images are easily retrieved from the simulator menu (on MacOS: `Playdate Simulator > Reveal Data folder in Finder)`
- Patches are saved in `.orlam` files, you can share patches by putting the Playdate into mass storage mode and finding the files under `Disk/Data/orllewin.playdate.modularplay/`.  
      
    _Trivia: .orlam stands for Orllewin Analog Modular, which is what this project used to be called before I settled on Modular Play._
    
![[another_patch.png]]

# Modules

All the included modules, in the order they appear in the main menu (a popup that appears when you tap (A) in empty space)

# Clock

## Clock

![[clock.png]]

The first module you'll add to most patches, generates a periodic 'bang' that's passed from module to module until it finds something that transforms clock events to a midi note or controls some other parameter. There's a single encoder to control the tempo, and four sockets to connect to other clock routing modules.

## Bubble Chamber

![[bubble_chamber.png]]

Balls/Particles/Molecules bounce around a box, when they hit the sides a clock event is emitted. Change the velocity and add and remove balls from the menu to change the random tempo.

## Clock Delay

![[clock_delay.png]]

Randomly holds on to a note for a precise interval, the chance of this happening controlled by the right-hand encoder. Useful for adding a little randomness to sequenced melodies and drum patterns.

## Clock Divider

![[clock_divider.png]]

Swallows every other clock event, halving the tempo.

# Core

## Midi Keyboard

![[midi_keyboard.png]]

Emits midi notes. Not practical but useful for trying out synth sounds quickly. Try _System > Midi/Serial Input_ with external hardware instead.

## Pedal

 ![[pedal.png]]

Emits a single event when pressed, and another when released. Used for controlling the sampler, or toggling a switch. The default mode emulates a momentary pedal: fires an event when pressed and another when released. To switch modes tap the top header area where you can change the pedal to fire a single event when clicked.

## Random

![[random.png]]

Emits a random number from 0.0 to 1.0 when it receives a bang. Limited use currently.

## Oscillator

![[oscillator.png]]

Pseudo-oscillator for controlling various parameters. Top encoder controls centre position (in range 0.0 to 1.0), middle encoder controls width (0.0 to 1.0), and bottom encoder sets the period.

## Oscillator 2

![[oscillator2.png]]

Same as Oscillator but uses less space on the screen, switch between encoders by tapping and selecting from the popup menu.

## Bifurcate x2

![[bifurcate2.png]]

Splits a clock signal into two allowing you to extend your patch. Can be rotated via a menu option before the first cable is connected.

## Bifurcate x4

![[bifurcate4.png]]

As above but splits a clock signal into four.

## Blackhole

![[blackhole.png]]

Swallows events. Encoder controls gravity, the higher the gravity the lower the chance an event will escape.

## XY Tilt

![[xy_tilt.png]]

Physically tilt your Playdate to emit events along the X and Y axis. Useful for live control of synth parameters. This is a fairly intensive module so limit to one per patch if possible.

## Y Tilt

![[y_tilt.png]]

Same as XY Tilt but only operates on the Y axis.

## Print/Log

![[print_log.png]]

Displays event value and relays it on to next module. Only really useful for debugging.

# Sequencing

## Generative Standard

  ![[generative.png]]

A key module, Generative combines a handful of modules internally, when it receives a clock event it decides whether to delay the bang, maybe swallow it in a black hole, and then converts it to a random midi note in the given scale. Combine in a simple patch with a Clock, a Synth, and a Speaker/Output to generate a random arpeggiated sequence.

## Generative Random

![[generative_random.png]]  

Combines Bubble Chamber with the logic of Generative Standard: every time a ball/particle/molecule hits a wall a random note is emitted from the selected scale.

## Arpseq

![[arpseq.png]]

A traditional 'piano roll'/'swimlane' arpeggiator style sequencer. Create short melodies/hooks in otherwise random patches. Works well with Bubble Chamber as a clock event source.

## Micro Sequencer

![[micro_sequencer.png]]

16 step sequencer. Write simple melodies. Put a Clock Delay and/or Blackhole before this module to add some variation to timings. A more versatile variable step sequencer is under development, not quite ready for the Alpha release.

## Drone Seq

![[droneseq.png]]

Emits up to four midi notes which never turn off. Combine with a synth with automated parameters to generate unending evolving drones. If you change a synth preset you'll need to re-trigger the note in this module.

# Midi/Seq Utils

## Random Repeater

 ![[random_repeater.png]]

Spread midi note events across multiple synths; when a note event is received it's emitted at one of the connected output sockets, chosen at random

## Random Shifter

![[random_shifter.png]]

When Random Shifter receives a midi note event it randomly decides whether to emit at the original pitch, up and octave, or down an octave - each with 33.3% probability.

## Linear Switch

![[linear_switch.png]]

Control if clock events reach a section of your patch with a Linear Switch, can be toggled manually or automated with the bottom socket.

## Dual Switch

 ![[dual_switch.png]]

Switch between two different paths, can be toggled manually or automated with the bottom socket.

## Timed Switch

![[timed_switch.png]]

Automate toggling areas of your patch with a timed switch controlled by a number of clock events. `mm.` is musical notation for a bar. Use a Timed Switch to automate a Dual Switch to move between two areas of a patch every n bars.

# Drum Machines

## Orl Drum Machine

 ![[orl_drum_machine.png]]

A 16 step drum machine. Use the encoders to choose from the built-in 606, 808, and 909 sample sets. Use a Clock Delay and/or Blackhole to add randomness to your patterns.

## OR-606

 ![[or606.png]]

A simple emulation of the classic Roland TR-606.

## OR-808

![[or808.png]]

A simple emulation of the classic Roland TR-808.

## OR-909

A simple emulation of the classic Roland TR-909.

# Synths

## Wavetable

![[wavetable.png]]

A wavetable synth with a single dimension modifier. This allows you to morph the sound in the X axis. The axis position can be automated with one of the accelerometer modules or an oscillator.

## 2D Wavetable

![[wavetable_2d.png]]

Same as Wavetable but allows morphing the sound across the X and Y axis.

## ORL Sample Synth

![[orl_sample_synth.png]]

A simple synth that pitches samples to midi notes. There's a variety of built-in categories but you can also use your own samples (record samples tuned to C with the Sampler module), this is limited somewhat by the gain of the condenser microphone, a method to import pre-recorded WAVs will come soon.

## ORL Synth

![[orl_synth.png]]

A basic synth with the usual waveform primitives (Sine, Square, Triangle, Saw) plus three Teenage Engineering presets from their Pocket Operator series. The Teenage Engineering synths have two additional parameters which can be automated from the two input sockets

## Noise Box

![[noise_box.png]]

Generates evolving noise. Internally a low-pass filter with oscillator modulates the sound.

## Micro synth

![[micro_synth.png]]

Same sounds as the Orl Synth but without envelope or parameter controls, tap to open the menu and change the waveform. Useful for larger patches with multiple synths to lower the strain on the processor (it uses less resources to draw).

## Stochastic Primitives

![[stochastic_primitives.png]]

A trio of synth modules developed for use in the onboarding/introduction patches. Internally they have a simple synth controlled by a random number generator, clock delay, a blackhole and a delay effect, they play random melodies in C Major.

## Wavetable Sigen

![[wavetable_sig_gen.png]]

Another test module that's been left in, was used to debug x-axis wavetable interpolation. Sounds awful.

# Sampling

## Sample Record

![[sample_record.png]]

Records audio from the Playdate internal microphone. Can be toggled with a menu item, or combine with a Pedal module. There's a built-in sampler patch `File > Load > Sample` for this purpose, the module is quite processor heavy so shouldn't be used as part of another patch. Currently you need to delete samples with a computer via a USB cable and putting the Playdate into storage mode, sample management will be added in the future to simplify things.

## Sample Play

![[sample_play.png]]

Play back recorded samples. The encoders control start point, end point, and pitch. There's an in socket for use with the Pedal module or automation.

## Hexagram

![[hexagram.png]]

![[hexagram_patch.png]]

A Modular Play implementation of the Hexagram Playdate app. This is very powerful but can summon demons. It records samples in a circular buffer and plays subsamples back at different pitches and randomly reversed. Allow it to record for a while then switch to idle mode to prevent excessive sampling of it's own output. There's a built-in patch to use Hexagram as a live effect in a larger hardware setup in `File > Load > Hexagram`

# Effects

## Krush

 ![[krush.png]]

A Bitcrusher. Controls are 'amount', 'undersampling', and 'mix'. Use to add some dirt to drums and drones.

## Delay

![[delay.png]]

A Delay. Controls are 'time', 'feedback', and 'mix'. I use this a lot.

## Lo-Pass

![[lo_pass.png]]

A low-pass filter. Controls are 'frequency', 'resonance', and 'mix'.

## Hi-Pass

![[hi_pass.png]]

A high-pass filter. Controls are 'frequency', 'resonance', and 'mix'.

## Overdrive

![[overdrive.png]]

Overdrive. Controls are 'gain', 'limit', and 'mix'. Can also be used to make quiet recorded samples louder.

## Ring Modulator

![[ring_modulator.png]]

A ring modulator. Controls are 'frequency' and 'mix'. Sounds awful.

# Output

_All outputs mimic a real-world amp and speaker. The Playdate audio engine is additive - if you have 5 audio sources each should be set to have a volume of around 2 to avoid clipping. You get used to it, but it's painful at first. I could treat this as an implementation detail where it's all done behind the scenes but it's a lot of effort to code._

## Basic Output

![[basic_output.png]]

A speaker. You can change the volume by tapping to open the menu.

## Single Output

![[single_output.png]]

Same as Basic Output but there's an on-screen encoder for the volume. We don't really need two but earlier in development on-screen encoders had a performance overhead, that's been fixed but both modules remain.

## 4 Channel

![[four_channel.png]]

A 4 channel mixer. Makes managing volumes easier than having single/basic output modules everywhere (remember there's a performance overhead with long cables though).

## 4 Channel Pro

![[four_channel_pro.png]]

Similar as the 4 Channel mixer but with encoders to control left-right panning, the bottom of the module has four input sockets to automate volume - this is useful for fading parts of a patch in and out, especially good for drones.

# UI

_These modules were added for the built-in introduction patches but they're still available so you can customise areas of your patches._

## Label

![[label_keyboard.png]]

![[label.png]]

A small label using the default Modular Play font. When you add the module an on-screen keyboard is displayed so you can add your text.

## Large Label

![[large_label.png]]

As above, but with larger font and no border.

## Label Arrow

![[label_arrow.png]]

To point at things, use together with the text labels.

# System

The system menu contains various system-wide toggles as well as a couple of modules.

## Midi/Serial Input

![[midi_serial_input.png]]

For use with external hardware - more on this soon.  
_Will not work with standard USB Midi, though it'd be amazing if Panic added support for that._

# Planned Roadmap

Although the Alpha is a paid app on itch.io you'll get all future upgrades and improvements. **Only purchase if you understand there will be rough edges and occasional crashes** - there are no refunds unless the software is utterly non-functional.

- 28/10/2023: 0.0.9 Alpha - initial release for early adopters, will have too many bugs, some unfinished modules are hidden. Here be dragons.
- 0.0.10 .. 0.0.n Alphas - patch releases with regular fixes over the first month or two, including adding currently unfinished new modules.
- 0.1.0 Beta - a release candidate, approaching stability.
- 1.0.0 - Fewer unwelcome surprises.
- ?.?.? - Desktop midi to serial bus.
- ?.?.? - Companion Android app (code will be freely available if anyone wants to port to iOS, I may try myself if I can find the time).
- ?.?.? - Hardware foot pedal project with instructions and code for recording samples.

# Performance and Limitations

_This is lengthy and won't be of interest for everyone, if you just want to make nice melodies while sitting on the train or whatever you can skip all of the information below._

The Playdate does incredibly well considering how tiny it is, and for most patches it'll perform fine without extra steps, but on larger patches with dozens of modules and automation you will get some UI slowdown; the bigger the patch the bigger the performance hit. Thankfully the audio fidelity isn't impacted, there's no audible artefacts, but the clock may emit slower occasionally making syncing to external sequenced music impossible. I've spent a lot of time optimising the modules themselves but one easy thing you can do to minimise the amount of work done when rendering the patches is to keep the length of cables sensible, if a cable is wider than the screen you're likely to see some performance issues if the patch is doing lots of other work too.

Modular Play is primarily a wrapper around the Playdate's audio API, it's not a true simulation of a modular synth setup in that you can't route signals wherever you like. Once audio leaves a synth it can only be routed through effects modules before finally escaping to your ear via one of the amp/speaker modules. The clock bangs are however produced within Modular Play and can be manipulated however we like. You should be prevented from doing things that don't work in Modular Play, like routing a clock signal into an audio-in socket, but there may be missing logic in some modules; if you find anything that doesn't seem correct [raise an issue](https://github.com/orllewin/modular_play_public/issues).

Another limitation of the Playdate is that audio input can only be done by the built-in condenser microphone and the levels may be fairly low compared to the output of the synths. The Playdate should be able to record from a line-in with a TRRS cable but this has been broken since launch and there's no sign of a fix yet. I will try and offer a desktop 'WAV to Playdate audio' utility if you want to use your own samples instead of recording with the Sample Record module.