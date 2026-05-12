---
title: Bambu Labs A1 AC Board replacement
date: 2026-05-12 12:10:05 +0000
categories: [3d-printing, troubleshooting, hardware]
tags: [bambu-labs, ac-board, power, maintenance, 3d-printer, support, repair, workflow]     # TAG names should always be lowercase
image: /assets/media/ac_board/ac_board_header.png
pin: false
---

<div class="skills-box">
  <strong>Skills:</strong>
  <ul>
    <li>Identifying issue with A1 Printer not turning on</li>
    <li>Following troubleshooting guides by Bambu Labs</li>
    <li>Found burnt component on ac power board and steps to replace</li>
  </ul>
</div>

This is a quick post documenting the replacement of the ac board for the A1 3d Printer. A few weeks ago the printer failed to turn on. I contacted Bambu Support and they helped find the issue. Steps below...

## Part List

Bambu Labs AP board

## Initial Troubleshooting

Issue: Power LED on main switch turned on showing green but no power to the 3d printer.

Bambu Labs asked me to remove the SD card but there was no change in the issue.

## Futher Troubleshooting
I then follwed instructions given by Bambu support to check the various LED's on the boards by removing the bottom tray. Transcript below:

Dear Customer,

Thank you for reaching out to our Bambu Lab Support team.

May I ask if you have tried disconnecting the mainboard power cables and checking whether the 24V power module indicator light returns to normal?

• If the indicator still does not light up after disconnecting the cables, it indicates a possible fault in the 24V power module, and we can provide a replacement.

• If the indicator returns to normal, the issue may be related to another part of the mainboard or connected circuitry. 

1.After removing the bottom shell, with the TH board, X motor, Z motor, and camera component ribbon cables already removed, you can turn on the power switch to test whether the mainboard light language lights up normally. 

If it still does not light up normally, you can further remove the Y - axis motor, AMS lite, AC board, and screen ribbon cables and then turn on the power switch again.

![MAIN Board](/assets/media/ac_board/1.JPG)
*The main power board showing cables to remove*

If the mainboard is normal, after turning on the printer, the three indicator lights on the mainboard will light up normally.

2.Then connect other cables in turn. If the mainboard light language goes out when a certain cable is inserted, you can troubleshoot along this link and replace relevant accessories; 

3.If the mainboard light language still fails to light up normally after all the mainboard cables are removed, it can be judged as a mainboard abnormality. 

![MAIN Board](/assets/media/ac_board/2.JPG)
*The main power board LED lights*

Please let us know the result after this check so that we can determine the appropriate next steps. Best regards,

​Bambu Lab Customer Support

## What I learnt

After following these steps I noticing that the 24V power module indicator did not turn on even after unplugging the main board power cables (X Motor, Z Motor, Y Motor, Screen Ribbon, AC board & Camera) The 3 indicator lights on the mainboard (HMS, AP & MC) were off. So this indicated a problem with the AC power board. 

## The Solution

### The AC Power Board
On closer inspection I noticed a burn MOV (Metal Oxide Varistor) on the AC power board.

![MAIN Board](/assets/media/ac_board/4.JPG)
*The burnt MOV*

![MAIN Board](/assets/media/ac_board/5.JPG)
*Close up of burnt MOV*

Bambu Labs gave me the below wiki to follow and shipped the replacement board. 

[Bambu Lab A1 AC Board Replacement Guide](https://wiki.bambulab.com/en/a1/maintenance/ac-board-replacement?appSharePlatform=copy)

Some of the connectors had a triangular push tab which differed from the wiki.
Cables 4 & 5 difficult to remove - had to pull out the power board slightly to grip the cables.

### The Bottom Cover
They also send a new bottom cover as existing one was slighytly warped.

[Bambu Lab A1 Bottom Base Guide](https://wiki.bambulab.com/en/a1/maintenance/bottom-base?appSharePlatform=copy)

I found the bottom cover difficult to pull off and used a pry tool to slide carefully around the opening which helped alot.

![MAIN Board](/assets/media/ac_board/3.JPG)
*Bottom cover difficult to take off*

### Hurray Printer is working again

After installing the new board the printer came back to life and everything worked as normal.

![MAIN Board](/assets/media/ac_board/6.JPG)
*Last few connectors to push back in*

## Further steps
I notice the new power board had no MOV so I installed a surge protector extension lead. I will monitor the status LED on the extension lead periodically to check that the MOV inside is still functioning.
