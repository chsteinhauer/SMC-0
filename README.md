
<style>
    section {
        /* margin: 7px 0;
        padding-left: 10px;
        border-left: 3px solid gray;
        border-radius: 0px; */
    }

    video {
        max-width: 100%;
    }
</style>

# SMC-0 Project

## Companies and products

<section>

* **Brüel & Kjær:** A lot of specialized software in acoustic analysis.

* **Izotope:** Ozone

* **Oeksound:** soothe2

* **Bose:** Bose Frames


### Chosen product

**Soothe2:** A VST plugin that removes resonance and harshness from soundsources in realtime and makes the mixing process easier for music producers in the final stages of their workflow.



<figure>
    <video title="Video of Soothe2 in use" 
        autoplay="" 
        loop="loop"  
        class="w-100 blue-shadow" 
        muted="">
            <source src="https://oeksound.com/uploads/soothe_harshness_save_time.mp4"       
            type="video/mp4">Your browser does not support video.
</video>
    <figcaption>
        <b>soothe2</b> in action. <a href="https://oeksound.com/uploads/soothe_harshness_save_time.mp4">Link to source.</a>
    </figcaption>
</figure>




https://user-images.githubusercontent.com/47811509/189107737-2b37c664-c014-4f3e-986a-cbe0225f4abb.mp4




</section>


## Problem

It is an enervating process for a music producer to detect resonant frequencies & ensure that their track sounds good in all sound systems and contexts, and lives up to a certain standard of commercialized music in the music industry.


### Problem description:

* How can we create a VST plugin that detects unwanted resonant frequencies and removes them in realtime, ensuring better audio quality on sound systems and lives up to a certain standard of commercialized music in the music industry? 

<!--* Make music sound good
* How can we implement a tool to make the mastering process easier for music producers in the final stages of their workflow-->

### Target user group

Music producers and all who works with audio post-production.

### Pains

* Current tools for finding and removing unwanted resonance frequencies are not particually intuitive.
* It is a time consuming task to find and remove unwanted frequencies.
* It is difficult to only target the unwanted overtones when adjusting the resonance.
* Ensuring the audio is commercializable is complex.
* Less experienced producers have a hard time to get into the the audio refinement process because of the complexity.
* Listeners may have an unpleasant experience if the audio is not refined correctly.

## Requirements

### Functional

<!-- Something the system must do (will fail if not) -->

* Must be able to detect problematic resonant frequencies in sound data
* Must be able to smoothen/remove the detected resonant frequencies
* Must be able to target only the undesirable overtones when modifying resonant frequencies
* User must be able to configure how the algorithm modifies the target resonants
* Must be able to compare the processed and unprocessed sound
* Must be able to select from a span of default presets which serves as an entry proposal of resonance soothing in different categories

### Non-functional

<!-- Requirements that describe how the system works -->

* Must be very user friendly - a user must intuitively understand the basic functionality when using the product for the first time
* Must be fast and reliable, response delay must be brought to a minimum for a better user experience
* Must be intuitive for the user to select and distinguish the range of frequencies that are affected
* Calculation processing must be done in real time when using the product
* Must not be heavily demanding of the CPU

## Milestones

| Milestones      | Outcome |   Tasks |
| ----------- | ----------- | ----------- |
| ***Milestone 1:*** <p>Conceptualizing</p>      | Determine if the concept/idea/product is possible based on requirements.       | <ul><li>Investigate user pains and needs in the refinemet process in sound post-production.</li><li>Create user stories.</li></ul> |
| ***Milestone 2:*** <p>Prototyping</p>      | Design and prototype of product.       |
| ***Milestone 3:*** <p>Initial implementation</p>   | Text        |
| ***Milestone 4:*** <p>AI</p>      | Title       |
| ***Milestone 5:*** <p>Sound processing</p>   | Text        |
| ***Milestone 6:*** <p>UI</p>      | Title       |
| ***Milestone 7:*** <p>Functionality</p>      | Title       |
| ***Milestone 8:*** <p>Testing</p>      | Title       |



#### Milestone 1:
* Determine if the concept/idea/product is possible.
#### Milestone 2:
* Refine concept/product/idea in respect to the findings made in milestone 1.
#### Milestone 3:
* Initial prototyping & concept/idea/product validation.
#### Milestone 4:
* Design software architecture
#### Milestone 5:
* Implement a resonant frequency detection algoritm
#### Milestone 6: 
* Implement sound processing that reduce/remove/smoothens a list of given frequencies in amplitude.
#### Milestone 7: 
* Implement UI & funcionality


### Tasks

**Analyze**

<ul> <li>Research how to utilize machine learning to detect problematic resonant frequencies and sibilance sounds in sound data.</li><li>Research how the problematic resonant frequencies and sibilance sounds can and should be modified.</li><li>Research how detection and modification of problematic resonant frequencies and sibilance sounds can be applied efficiently in real time.</li><li>Collect datasets of occurrences of resonance in sound.</li></ul>

* Investigate user pains and needs in the refinemet process in sound post-production.
* Research how to utilize machine learning to detect problematic resonant frequencies and sibilance sounds in sound data.
* Research how the problematic resonant frequencies and sibilance sounds can and should be modified.
* Research how detection and modification of problematic resonant frequencies and sibilance sounds can be applied efficiently in real time.
* Collect datasets of occurrences of resonance in sound.


**Design**

* Create user stories.
* Create initial sketches of user interface.
    * Main interface with an interactive bandpass
    * A control panel to customize bandpass shape and settings
    * A control panel to customize how the resonants should be modified

* Create wireframes of user interface.
* Create prototype of user interface with basic functionality flow.
* Test prototype on target users to get feedback.
* Revisit user stories and prototype based on user feedback.
* Determine what should be configurable by the user in how the algorithm modifies the selected frequencies.
* Describe the software architecture
    * Describe interface for bandpass update events
    * Describe interface for configuration update events
    * Describe store interface for caching the current customization settings (variables), current imported sound file(s) etc.


**Implementation**

* Implement the detection algorithm to detect unwanted resonant frequencies, returns a list of adresses
    * Create unit tests
    * Implement function that determines if a resonant is problematic or not based on variables, returns a boolean
    * Import chosen machine learning library and setup conditions and variables
    * Train the detection algorithm with training data set

* Implement the modification algorithm to modify resonant frequencies based on configured conditions, returns the updated sound data
    * Create unit tests
    * Implement function that copies and prepares the data to be modified
    * Implement function to modify the data based on variables (preset/user configuration) - only modify the changed part of 

* Implement user interface
    * Implement main interface with an interactive bandpass
    * Implement bandpass control panel
    * Implement configuration control panel

* Implement functionality
    * Detection
        * When sound data is provided, run the detection algorithm and adjust the bandpass configuration to a default proposal
        * Then run modification algorithm with the updated variables
        * Save the modified data and variables in the store
    * Modification
        * Throw events when a control component is updated
        * Catch update event and run the modification algorithm with the updated variables
        * Save the modified data and variables in the store

**Test**

* Run benchmark tests of the algorithm to test the runtime and memory usage
* Do usability test on target user participants for feedback

## Proposed iterations and evaluations

## Timeline


| Date         | Activities                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| *02/09/2022* | We brainstormed some companies with products that could be interesting to look into. Our first choice was Ozone from the company Izotope. Also, first draft of problem description is formulized.                                                                                                                                                                                                    |
| *05/09/2022* | We changed our product to **soothe2** by Oeksound, as we concluded that Ozone was too complex regarding all its features that are outside our scope. **soothe2** attempts to solve the same problem, but is much simpler in its approach, and only focus on the refinement of ressonance in the mastering process. Furthermore, we brainstormed pains and gains and created requirements from these. |
| *07/09/2022* | We refined the requirements. Planning the project by breaking it down into milestones and tasks. This was send to our supervisor for feedback.                                                                                                                                                                                                                                                       |
| *08/09/2022* | Prioritized the milestones and time estimated tasks. This was setup in a gannt diagram. Here we reprioritized tasks also when we had a better overview of the milestones.                                                                                                                                                                                                                            |
| *09/09/2022* | stuff                                                                                                                                                                                                                                                                                                                                                                                                |


