
<!-- <style>
    section {
        /* margin: 7px 0;
        padding-left: 10px;
        border-left: 3px solid gray;
        border-radius: 0px; */
    }

    video {
        max-width: 100%;
    }
</style> -->

# SMC-0 Project

## Outline

* Introduction
  * Background
  * Problem description
* Analysis
  * Problem background
    * User cases
  * User research
    * Target user group
    * User pains
* Product
* Requirements
  * Functional
  * Non-functional
* Milestones
* Planning
* Appendix
  * A: SMC companies and products
  * B: Timeline

## Introduction 

It is an enervating process for a music producer to detect resonant frequencies & ensure that their track sounds good in all sound systems and contexts, and lives up to a certain standard of commercialized music in the music industry.


### Problem description

* How can we create an intuitive VST plugin that help in detecting unwanted resonant frequencies and removes them in realtime, ensuring better audio quality on sound systems and lives up to a certain standard of commercialized music in the music industry?




## Analysis

### Problem background

<!--Something SMC related-->

#### User cases

<!--Real world and concrete examples where resonants appears-->

##### Harshness
* Sound sources like eg. synthesizers often gives an audio output with difficult resonant frequencies. With included effects on top of the synthesizer like distortion, delay, reverb these frequencies might increase in amplitude. These frequencies will take a lot of space in the audio and might irritate the audience who is listening. 

##### Sibilance 
* Every vocal recording include lots of sibilants. This is the consonants most likely recognized by the 's', 'ch' & 'z'-sounds in every language.

##### Plosives 
* Another type of unavoidable troublesome consonants are plosives. These are 'p' and 'b' produced by lips, as well as 't', 'd', 'k', 'g' produced by tongue. The effect of those consonants is mitigated with a microphone screen, but it is still audible to some extent in recordings.

##### Breaths 
* Vocal performances contain moments when a singer takes breath. It is not always audible enough to become a problem. However, quier singing recording may be disrupted by the unwanted breating sounds.

##### Tonal balance
* When working with audio, specifically musical pieces, producers, sound engineers & composers would often like the tonal balance to be evened out across the frequency spectrum. The goal is *not* have some segments of the audio be much higher in eg. the mid frequencies in comparision to the lows.

##### Muddiness & Boominess
* Muddiness occur in audio when having a variety of sound sources in the lower frequency field clashing with eachother. In addition to muddiness 'boominess' is a similar term known as an excessive amount of bass in the sound reproduced by a loudspeaker.

### User research

#### Target user group

Music producers and in general all who works with audio in post-production.

#### User pains

* Current tools for finding and removing unwanted resonance frequencies are not particually intuitive.
* It is a time consuming task to find and remove unwanted frequencies.
* It is difficult to only target the unwanted overtones when adjusting the resonance.
* Ensuring the audio is commercializable is complex.
* Less experienced producers have a hard time to get into the the audio refinement process because of the complexity.
* Listeners may have an unpleasant experience if the audio is not refined correctly.

### Requirements

#### Functional

<!-- Something the system must do (will fail if not) -->

* Must be able to detect problematic resonant frequencies in sound data
* Must be able to smoothen/remove the detected resonant frequencies
* Must be able to target only the undesirable overtones when modifying resonant frequencies
* User must be able to configure how the algorithm modifies the target resonants
* Must be able to compare the processed and unprocessed sound
* Must be able to select from a span of default presets which serves as an entry proposal of resonance soothing in different categories

#### Non-functional

<!-- Requirements that describe how the system works -->

* Must be very user friendly - a user must intuitively understand the basic functionality when using the product for the first time
* Must be fast and reliable, response delay must be brought to a minimum for a better user experience
* Must be intuitive for the user to select and distinguish the range of frequencies that are affected
* Calculation processing must be done in real time when using the product
* Must not be heavily demanding of the CPU

### Technologies



## Product
### Chosen product

**Soothe2:** A VST plugin (created by the finnish company *Oeksound*) that removes resonance and harshness from soundsources in realtime and makes the mixing process easier for music producers in the final stages of their workflow. 

![189107737-2b37c664-c014-4f3e-986a-cbe0225f4abb](https://user-images.githubusercontent.com/43750048/189302824-9cdc790d-7a2d-47e7-9369-57b3d3bbe15a.gif)




## Milestones

| Milestones      | Outcome |   Tasks |
| ----------- | ----------- | ----------- |
| ***Milestone 1:*** <p>Conceptualizing</p>      | Determine if the concept/idea/product is possible based on requirements.       | <ul><li>Investigate user pains and needs.</li><li>Create user stories.</li><li>Create initial sketches of user interface.</li><ul><li>Main panel with an interactive bandpass</li><li>A control panel to customize bandpass shape and settings</li><li>A control panel to customize how the resonants should be modified</li></ul></ul> |
| ***Milestone 2:*** <p>Prototyping</p>      | Design and prototype of product.       | <ul><li>Create wireframes of user interface.</li><li>Determine what should be configurable by the user in how the algorithm modifies the selected frequencies.</li><li>Create prototype of user interface with basic functionality flow.</li><li>Test prototype on target users to get feedback.</li></ul>
| ***Milestone 3:*** <p>Initial implementation</p>   | Design of software architecture.    | <ul><li>Revisit user stories and prototype based on user feedback.</li><li>Describe the software architecture</li><ul><li>Describe interface for bandpass update events</li><li>Describe interface for configuration update events</li><li>Describe store interface for caching the current customization settings</li></ul></ul>
| ***Milestone 4:*** <p>Detection algorithm</p>      | Implementation of a resonant frequency detection algoritm.       | <ul><li>Research how to most efficiently and accurately detect problematic resonant frequencies and sibliance sounds in sound data.</li><li>Collect testdata of occurrences of resonance in sound.</li><li> Implement the detection algorithm to detect unwanted resonant frequencies, returns a list of adresses of where the resonances occures.</li><li>Create unit tests</li></ul>
| ***Milestone 5:*** <p>Sound processing</p>   | Implementation sound processing that reduce/remove/smoothens a list of given frequencies in amplitude.        | <ul><li>Research how the problematic resonant frequencies and sibilance sounds can and should be modified.</li><li>Research how detection and modification of problematic resonant frequencies and sibilance sounds can be applied efficiently in real time.</li><li>Implement the modification algorithm to modify resonant frequencies based on configured conditions, returns the updated sound data.</li><li>Create unit tests</li></ul>
| ***Milestone 6:*** <p>UI</p>      | Implementation of the UI based on the validated wireframes/prototypes      | <ul><li>Implement main panel with an interactive bandpass</li><li>Implement bandpass control panel</li><li>Implement configuration control panel</li><li>Create End-2-End tests</li><li>Create demo and do a usability test on target user participants</li></ul>
| ***Milestone 7:*** <p>Functionality</p>    | Implementation of functionality behind the UI to utilize the algorithms       | <ul><li>Implement detection functionality</li><ul><li>When sound data is provided, run the detection algorithm and adjust the bandpass configuration to a default proposal</li><li>Then run modification algorithm with the updated variables</li><li>Save the modified data and variables in the store</li></ul><li>Implement configuration functionality</li><ul><li>Throw events when a control component is updated</li><li>Catch update event and run the modification algorithm with the updated variables</li><li>Save the modified data and variables in the store</li></ul></ul>
| ***Milestone 8:*** <p>Testing and final adjustments</p>      | Final tests and preparation for deployment to production       | <ul><li>Usability test of the overall product and interview target user participants for feedback</li><li>Run benchmark tests of the algorithm to test the runtime and memory usage</li><li>Use test feedback to plan further milestones if necessary</li></ul>

## Planning
<img width="880" alt="SMC-0-Gantt" src="https://user-images.githubusercontent.com/43750048/189137403-6bea0f9c-8dfc-4df6-82bd-b40ee74ca04f.png">

## Appendix

### A: SMC companies and products

* **Brüel & Kjær:** A lot of specialized software in acoustic analysis.

* **Izotope:** Ozone

* **Oeksound:** soothe2

* **Bose:** Bose Frames

### B: Timeline


| Date         | Activities                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| *02/09/2022* | We brainstormed some companies with products that could be interesting to look into. Our first choice was Ozone from the company Izotope. Also, first draft of problem description is formulized.                                                                                                                                                                                                    |
| *05/09/2022* | We changed our product to **soothe2** by Oeksound, as we concluded that Ozone was too complex regarding all its features that are outside our scope. **soothe2** attempts to solve the same problem, but is much simpler in its approach, and only focus on the refinement of ressonance in the mastering process. Furthermore, we brainstormed pains and gains and created requirements from these. |
| *07/09/2022* | We refined the requirements. Planning the project by breaking it down into milestones and tasks. This was send to our supervisor for feedback.                                                                                                                                                                                                                                                       |
| *08/09/2022* | Prioritized the milestones and time estimated tasks. This was setup in a gannt diagram. Here we reprioritized tasks also when we had a better overview of the milestones.                                                                                                                                                                                                                            |
| *09/09/2022* | We used the given feedback from the TA and incorporated the changes in our documentation. This included the addition of user-cases                                                                                                                                                                                                                                                                                                                                                                                                 |

| *12/09/2022* |                                                                                                                                                                                                                                                                                                                                                                                                  |
