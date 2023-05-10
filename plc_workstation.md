---
Title: PLC Workstation
---

# PLC Workstation

<iframe width="560" height="315" src="https://www.youtube.com/embed/xUBj3sQjYIQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

This is a small PLC workstation set up at Arizona State University's Industrial Automation lab. It features SMC PLCs, an assortment of pneumatic actuators, and common industrial sensors such as reed switches and prox sensors.

For the final project, I was given an open-ended description of functionality, with no PLC-specific instructions. I had to decide how to PLC program should be structured in order to accomplish the required functionality. The functionality required was described as follows:

> The machine must have the following functionality:
>
> * A production mode that moves a box from the magazine to the end of the conveyor belt
> * A reset function that returns the machine to a safe "home" position
> * Motion must stop when the stop button is pressed, and resume when the start button is pressed
> * Logic must prevent the machine from crashing under any circumstance
> * Motion must be smooth
> * The state of the machine must be indicated via the tower lights

I chose to implement the required features by separating different machine behaviors into subroutines. First, the production subroutine:

<embed src="https://LeviTranstrum.github.io/files/PLC_Production_Routine.pdf" width="600px" height="500px" />

In order to create smooth motion, I implemented step logic that would not let the next step of the routine begin before the previous had ended. To prevent crashing, I made a list of all possible conditions under which a crash could occur, and devised logic that would not prevent such a combination of outputs to occur.

Second, the reset subroutine:

<embed src="https://LeviTranstrum.github.io/files/PLC_Reset_Routine.pdf" width="600px" height="500px" />

As before, step logic along with safety conditions were used to make this program safe, smooth, and functional.

Third, a flasher routine which would give me access to three different on/off frequencies throughout the rest of my program:

<embed src="https://LeviTranstrum.github.io/files/PLC_Flasher_Routine.pdf" width="600px" height="500px" />

And finally, the main routine to tie it all together:

<embed src="https://LeviTranstrum.github.io/files/PLC_Main_Routine.pdf" width="600px" height="500px" />

This routine included logic that would not allow the Production and Reset subroutines to run at the same time, as well as support for the stop and start buttons.

It was extremely satisfying to see all of the pieces come together to create smooth, coordinated, predictable machine behavior!
