Musical Keyboard Objective
In this experiment
-­‐ creating ISR’s to handle interrupts on the TS7250 board
-­‐ using and combining most of what they have learned in previous assignments

Part 1: The Keyboard

For this part you are to create a module that contains code to set up an ISR and
a real time task. The purpose of the real time task is to create a square wave that will be played
on a speaker. To create the square wave, you will need to toggle pin 1 of port F.


Part 2: Master – Slave, Software Interrupt
For this part you are to use your code from the previous lab to decide a master
slave relationship with the other students’ boards in the lab. This time, however, the master board
sends the current note that it is playing to all of the other boards, so that all of them play the same
note as the master board. This requires a few steps:
1. You must program your master/slave server program to accept messages that begin with @.
These messages represent one of the five notes to be played: @A, @B, @C, @D, @E.
2. If your board is a slave and it receives one of those messages, it must change the frequency
of the note being played. To do this, you will use software interrupts. Specifically, you will
use software interrupt 63 (reference the ep93xx manual), so you need to write a handler for
this interrupt in your module. To trigger the interrupt in your server program, you simply
write a 1 to the bit in the software interrupt register that corresponds to interrupt 63.
Your module should still change the notes when the buttons are pressed. In other words, your
module should handle both interrupts.
3. If your board is a master and it receives a note message, it must also change the frequency of
the note being played. Furthermore, it should “forward” that message to all the slave boards
in the network.
