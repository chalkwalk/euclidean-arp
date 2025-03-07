# Euclidean Arp
A prototype of a Euclidean rhythm based arpeggiator with MPE support

## Introduction

This is an HTML and Javascript prototype for an idea I had for an arpeggiator, based on a concept of using two euclidean rhythms, one to skip notes in the typical arpeggio sequence, and one to select the rhythm with which the selected notes are played. In addition to this concept it eventually gained an interesting mode based on note permutations to form chord progressions. Finally, it's intended to have MPE support; in the simplest case MPE channel pressure (and non MPE poly aftertouch messages) map to playback velocity.

This project was a combination of an experiment in using AI assisted coding as a way to bring a concept to life, using otherwise idle time, by doing it all from my phone.

Note: I didn't record what changes were made by me or the AI system, I also didn't record what each revision changes. This means all the commit descriptions were made after the fact, by examining the diffs.

## How to use

You load the html file into a browser that supports web MIDI (e.g Chrome, Opera, Edge, etc). You allow the page access to your MIDI deviices then select an appropriate input and output to receive notes from and send notes to. With the arpeggiator set to internal clock, you may click "start arpeggiator" then press notes on your input device, or put the arp into "key sync" mode, in which case the clock will start when you press keys (and stop when you release them).

A fun way to use this is if you have an external synth connected via MIDI to the computer. Set the synth to "local off" mode, then choose it as both the input and output device. This will allow you to play with the arpeggiator directly on device (I used a Hydrasynth Explorer to test the Poly aftertouch and MPE pressure, and it worked nicely like this).

## How it was made

About 95% of this code was made on my phone, through Gemini 2 flash thinking (through AI Studio), and the QuickEdit+ editor. The remaining 5% was done on my computer in Vim. Since the AI model originally had a relatively short context window, I didn't have an ongoing session, but rather created a new session for each change. This means I needed to give context to the system. I ended up settling on the following workflow:

1. Make a design for the project (around 3000 words in the latest revision, but incrementally grew as features were added);
1. Feed the design as prompt text and the current code revision as an attachment;
1. Add a paragraph describing what I want to change, typically requesting that the code changes be made directly such that I can download and run the code (This is much more convenient when working on a phone as I can download then test immediately);
1. Test the resulting app to see if it works.
1. If several attempts fail to get the system to make the change correctly, I fall back to writing the code myself and move on.

You'll note that I have no testing infrastucture here, nor an easy way to diff on my phone, so I had to just try it out, then occasionally go to my computer to test further.

## Future

Though this was intended more as a proof of concept for an AI assited coding workflow, I quite like the outcome. In making changes I've come to realise several limitations in the implementation and opportunities for improvement. Here are the next big steps I'd like to work towards:

1. Replace the relatively fragmented arp generation code with a node based system, with inputs (held notes, scales, sequences), modifiers (the different arp types) and outputs (that have the euclidean aspect and send messages);
1. Move away from Javascript into JUCE so this can become a plugin.
