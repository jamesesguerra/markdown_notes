---
tags: [Notebooks/CSCI 60]
title: 08/13/22 Introduction
created: '2022-08-13T05:14:43.143Z'
modified: '2022-08-13T08:39:58.745Z'
---

# 08/13/22 Introduction

> - __digital__ - data/signals expressed as a series of the digits 0 and 1
> - __digitize__ - converting (pictures, text, sound) into a digital form that can be processed by computers

## Human vs Data communication

Human communication is more ambiguous because it is richer and therefore, also less predictable. 
- words vary from context to context
- different factors influence how people perceive messages

Data communication is more precise
- information is replicated exactly 
- computers don't need to interpret, they just relay messages

## Types of information

- voice, data, image, video

Information sources can produce information in __digital__ or __analog__ form.
- __digital__
  - discrete values
  - digital clock, finite values
- __analog__
  - continuous
  - infinite values
  - information rate & channel capacity measured in Hz
    - __hertz__ - unit of measure for the # of times a wave cycle occurs in a second
  - bandwidth measures the limits

## How data is transmitted

- __face to face__ - same space, same time, multiple sense
- __written__ - different space, different time, one sense e.g. telegraphy
- __remote verbal__ - different space, same time, one sense e.g. telephone
- __remote face to face__ - different space, same time, two senses e.g. video conferencing

## How networks are described
__function of time__
- analog (varies smoothly over time)
- digital (constant level over time, followed by a change to another level)

__function of frequency__
- spectrum (range of frequencies)
- bandwidth (width of spectrum)

### Periodic signal characteristics
- __amplitude (volts)__ - the height from the center line to the top/bottom 
- __frequency (hertz)__ - cycles/per unit time; cycle = 2 mountains
- __period__ - amt of time for 1 cycle; space between mountains
- __phase__ - relative position in time

## Signal Modulation

It defines how info is stored in the signal wave; process of converting data into radio waves by adding info to an electric signal
- amplitude modulation
- frequency modulation
- phase modulation

## Digitization of information
- Represented as a sequence of discrete symbols from a finite alphabet of text and/or digits
- Bandwidth = rate and capacity of a digital channel in bps
- bits can be represented as voltage pulses

### Characters/Text/Symbols
- earliest example -  morse code
- ASCII - limited to only a few characters (7 bits)
- UTF-8 - represents foreign characters as well (8 bits)

### Images
- Compression can be used

#### Converting images
- break image up into small units
  - more units means more detail; units called pixels
- use photocell to reach each unit & assign a value

#### Image quality issues
- more pixels = better quality
- more compression = reduced quality
  - lossy - 10:1 - 20:1 compression
  - lossless - < 5:1 compression
- less compression = reduced speed of transfer
- the larger the resolution, the more space required to represent the image

#### Computing image size

```sh
A digital camera is capable of taking GB pictures at 15M pixel resolution at an assumed compression rate of 1:10.

How many images can be stored in a 32 MByte memory card?

storage = 15M pixel * 24 bits per pixel * 1 bytes per 8 bits * 1/10 = 4.5 MBytes 
# pictures = 32 MBytes / 4.5 Mbytes ~= 7 pictures

How many more pictures can be stored if only greyscale pictures were taken?
storage = 15M pixel * 8 bits per pixel * 1 bytes per 8 bits * 1/10 = 1.5 Mbytes 
# pictures = 32 MBytes / 1.5 MBytes ~= 21 pictures
```

### Audio
- easily converted from sound frequencies (measured in db) to electromagnetic frequencies, measured in voltage
- human voice has frequency components ranging 20Hz to 20KHz
- telephone system bandwidth: 300 - 3400Hz

#### Audio Communications
- applications: telephone, audio conferencing, radio
- quality of sound is characterized mainly by the bandwidth used
  - telephone - 3000Hz
  - high fidelity - 15KHz
  - compact disks - 20 KHz per channel for stereo

#### Digitization
__Nyquist Sampling Theory__ - for good representation, must sample amplititude at a rate of at least twice the maximum frequency
- measured in samples per second (smp/sec)

example:
- telephone quality -  8000smp/sec, each sample using 8 bits
  - 8 bits * 8000smp/sec = 64kbps to transmit
- CD audio quality - 44,000smp/sec sample using 16 bits
  - 16 bits * 44,000smp/sec = 704kbps to transmit

```sh
You have recorded an audio file with 5 stereo channels. Each channel has a 16-bit 44Khz audio stream.

How much bandwidth is needed to stream this audio file?
How much disk space is needed to store 5 minutes of this audio file?

Channels = 5
Frequency  = 44Khz = 44,000 smp/sec
Bit Depth = 16 bits = 16 bits per sample

Bandwidth = Channel * Frequency * Bit Depth 
          = 5 * 44,000 smp/sec * 16 bits/sample
          = 44,000 * 5 * 16 bits/sec
          = 3,520,000 bits/sec
          = 3.5 Mbits/sec = 3.5Mbps

Storage   = Bandwidth * Time
          = 3.5 Mbits/sec * 5 minutes
          = 3.5 Mbits/sec * 300 seconds
          = 1,050 Mbits * 1 byte/8 bits
          = 131.25 MBytes
```


funciton of frequency
- transmit via note; different ferquency
- 
signal modulation
- different height and speed could mean different things
- 
AM stations have a wder reach

FM better quality

analog converted to digital converted to bits

use 1000 bits per second


50 mb picture = 5mb in storage

dolby channel 6

