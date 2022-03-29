# propacc

### Computational Music Creativity

##### Final project, March 2022, Christos Plachouras

### Overview

The main principle of this system is to allow the user to accompany themselves with sounds derived from their past input, in order to create interesting melodic output or simply practice their improvisational singing or monophonic instrument playing. The name **propacc** is inspired by **prop**agation delay in electronic circuits and music **acc**ompaniment, which are the two conceptual inspirations for the system.

The basic process for using the system is as follows. When the system detects loud enough input by the user, it starts recording the microphone input to memory. When it detects that the phrase sang or played has ended, it stops recording. It then analyzes the recorded sound, and transforms its timbre using differentiable digital signal processing (DDSP) to that of a different instrument, while keeping the pitch, rhythm, and expressive characteristics (such as vibratos, inflections, etc.). The next time a user sings another phrase, the transformed recording starts playing at the same time, accompanying the user. In this implementation, two delayed versions of the user's input are recorded and played simultaneously when the user provides new input.

While the original motivation of the system was centered around creating interesting melodic output, it quickly became apparent how fun of an improvisation and practicing system it can be. In the case the user uses this with voice, it provides a challenging, time-constrained harmonization exercise, as the user has to quickly think about their two previous inputs and come up with a fitting third melody to sing simultaneously. In addition, since DDSP resynthesizes the new track from a continuous fundamental frequency estimation of the original, there is no quantization in the resynthesized tracks, which means the user is challenged to remain almost perfectly in-tune for each three consecutive melodic phrases.

### Motivation

The initial motivation for creating the system was being able to create interesting polyphonic output with a single control: the user's singing voice. While neural network-based and also simpler approaches were considered for generating variations of the input melody, they were dismissed for three main reasons:

* I wanted the output to be predictable and solely controllable by the user. The user is not dependent on unpredictable output by a neural network and has full responsibility of the output, just like in acoustic, electric, and most digital instruments.

* Unpredictability wouldn't allow for equally unconfined improvisation. Obviously, starting a saxophone improvisation without knowing what the chords that the rest of the band is going to play next will not go well in most cases. Variations generated would have had to fit the harmonic framework that the user would be required to imply, but implicit inference of it is not accurate enough, and explicit specification of it defeats the single-control model I wanted.

* Freedom in composition is important, but constraints are necessary. I felt like this level of improvisational freedom and this level of framework-derived constraint was a nice balance for making something creative while retaining simplicity in the control of the system.

While the system was built with these principles, as mentioned in the overview it became apparent that the challenge of controlling it was bigger than anticipated. While a good singer won't have any trouble staying in-tune when there is accompaniment, it opens up the possibility for people like me to practice their singing. It can also be seen as a challenging memory and improvisation game, where the person that manages to sing the most phrases without making a "harmonic" mistake wins. 

### Implementation

##### Platforms

Pure Data was primarily used for controlling the process flow, including recording to memory, detecting singing/playing, visualizing past input, applying convolutional reverb, and interfacing with the DDSP module. The IRCAM Acids DDSP implementation used provides a DDSP module and the included preprocessing in a Pure Data wrapper. This wrapper includes Pure Data objects like sigmoid~ for pitch tracking, and interfaces with Torch to do the inference (i.e. neural audio synthesis). It is primarily built in C++, which is what allows timbre transfer inference to be done faster than real-time.

##### Recording

One of the challenges of this project was having a simple, predictable, but well-working approach for splitting the audio from the microphone input into phrases in real-time. 



##### Delayed copies

##### Differentiable Signal Processing

### Future work
