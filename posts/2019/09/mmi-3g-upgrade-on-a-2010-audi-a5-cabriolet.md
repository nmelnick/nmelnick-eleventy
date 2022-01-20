---
title: "MMI 3G+ Upgrade on a 2010 Audi A5 Cabriolet"
date: "2019-09-25"
categories: 
  - "audio"
  - "cars"
tags: 
  - "a5"
  - "audi"
  - "mmi"
  - "upgrade"
---

![](/static/img/IMG_20190925_160437.jpg)

Completed Facelift MMI 3G+ Installation

I recently completed an infotainment upgrade on my B8 Audi A5 Cabriolet 2.0T Prestige, bringing it from the stock MMI 3G system to MMI 3G Plus. The updated MMI unit brings an updated interface, speed increase, Audi Connect, online map destinations, Google Earth overlays, bluetooth audio over A2DP, and without any data to back it up, better audio quality.

I did all of this with used parts, which meant a trip to an Audi service center to remove component protection. This amounted to an hour of labor charged, which is still far cheaper than buying _any_ of these parts new. This was done in the US, on a left hand drive model, so other countries may have different part numbers, or may require a reflash -- particularly the 5F or 56 modules.

There are a ton of HOWTO guides on the forums, all with slightly different information. I'm adding to the chorus with things I ran into while installing this in an A5 cabriolet, which can be different than those installing in an A4 sedan or Q5 crossover.

## Tools Required

- Audi Radio Keys: The radio keys are required for removing the original stock MMI unit. They slide into slots on either side and allow the unit to slide out.
- Plastic Trim Removal Tools: I used the trim tools for removing the shift boot while removing the MMI control panel, for easing out the temperature control unit, for jimmying apart the plastic pieces behind the screen for snaking through the antenna connector from the top vent down to the 5F unit, and for removing trim pieces during trunk disassembly to install the radio
- Flathead screwdriver
- Torx screwdriver - T25 (radio) and T20 (antenna)
- 10mm and 13mm sockets and wrench (Radio only)

## Parts Used

- **8R1 035 746 B - MMI Control Unit** **(5F)**: This is the brains of the upgrade, powering the user interface, housing the hard disk, DVD drive, and cellular module, and interfacing with CAN and MOST buses. They have revisions all the way up to G, and it looks like F and G have an updated cellular module with UMTS support. These can be sourced from any B8.5 model -- A4, S4, RS4, A5, S5, Q5, SQ5.
- **8T0 919 611 L WFX - MMI Control Panel**: This is the tactile interface to MMI in your center console, providing the control knob, and function buttons. This model has the start/stop button, as mine was originally equipped with it, the model without is 8T0 919 611 K WFX. This has to be changed due to the communication speed change between the two models. Though you can use an older control panel with VCDS changes, the updated layout is really nice. These can be sourced from any B8.5 model -- A4, S4, RS4, A5, S5, Q5, SQ5.
- **4G0 035 082 G - Radio (56)**: This can be optional. Some radio units have difficulties communicating with the updated control unit, and will throw errors or reset itself while operating. Mine was one of them, but it wasn't a huge deal, but I also wanted HD Radio, so did the upgrade. These can be sourced from a /ton/ of Audi and VAG models.
- **8K1 820 043 AR - Temperature Control Unit (08)**: This is absolutely optional, skipping this will still result in a fully functional upgrade. I wanted this for aesthetic reasons -- it matches with the new 5F well, and I like the white text and simple ventilation buttons. The model number shown here provides dual zone and heated and vented seat controls. These can be sourced from any B8.5 model -- A4, S4, RS4, A5, S5, Q5, SQ5. The Q5/SQ5 models will have an additional plastic strip on the bottom with a foam tape backing. This can be pulled off to fit in the car models.
- **[An external GSM antenna](https://www.ebay.com/itm/GSM-UMTS-Antenna-Fakra-Z-for-BMW-CIC-NBT-Mercedes-COMAND-VW-Audi-RNS-Bluetooth/152151902470)**: It appears, according to other guides, that many A4 and A5 models have a built in cellular antenna to connect the new MMI unit to, my cabriolet either didn't have it, or just wasn't accessible enough for me to find. I ended up buying an external antenna on eBay with a FAKRA connector to wire into the unit
- **Ross-Tech [HEX-V2 cable](https://www.ross-tech.com/vcds/hex-v2.php) and VCDS**: VCDS is required for enabling diagnostic mode and coding your new devices. There are other tools that may allow this functionality, and some less than above board options, but these are the tools I used.

## Preparation

**Make an appointment at your Audi dealership, or Audi-enabled service center with access to Audi's service network. The MMI Control Unit, Radio, and Temperature Control Unit will all need to have component protection removed to operate. That means the drive will be without music and without heating or air conditioning, so plan accordingly.**

Before getting started, retrieve the current coding and configuration of the installed modules using a combination of VCDS and the "green menu" diagnostic screens of the existing unit.

**To enable the "green menu" in VCDS**

- Open module 5F - Control Head
- Select the 10 - Adaptation button
- Select Channel 06 and press the Read button
- If the value is 0, change to 1 and press the Save button
- Exit the module
- Reboot the MMI by pressing SETUP + Control Knob + Upper Right button
- Once rebooted, go to RADIO, and then hold down SETUP and CAR at the same time to enter the green menu

![](https://lh3.googleusercontent.com/VoSvui5uSVxWVV9RR-zvnsVdHlDKMmwHTC10DrZT9CKXNKECddBrAQ20sCH5oERQEBr9pvarCsO-DuNCe_mAdrdwJDvZlx-RigK81Pnx1axET4pBWHa6LP3FT-YJXAysMehIlKCx3zTNIdNoMOatvJEjwY_2cG-s2o92lcNXoDXaJb6ow4rstCKGOH6wSQIpK9T5VGJUeIJixEiDjCZVA-SXH136gAVbNwtpt2xPK-rX5-vogJp0-C9sTt_jxcxDbYgrFRzzIqF2XVOxUVTfrKbVDNU8rIq8FLqto6XmXr-8lyHdic-0MzlBIqQJ20jwydDvSbPENLNHKjpDTlsUkTTCJqwM_5smJoAVI3tCJuPy7bGsPAWuDsvAJ1ZjiF04_g9XgraSS40xH2NMzN6WvJxQXz3g4OiHb7EBujKZTtWDrzP0HLXqaMs0MVNqULU6clCDIoXnFpyB-1jI5GI3rvFBUaOYFnrtWKMxR9YQH56LyG2VNBSKZ7Cd0tsCejNz4BvnkW5R0j52sfqMOXHKDmDShS9peJnUdcvD7g_RNnMrfE2Fuu2AHfPUbBQ1kN6rlYbowWn1qS53QL7PiQkVKlRwpNmPfsAQNStheKo4CCFTCZrO6MwIMa_OGpm4S_4tz6uOz_CT-qe0dOrvL0uIQ2vpsGIqpl-fIYWPeUClwffhHbVcE7FQgWTa=w3045-h1917-no)

"Green Menu" Main Screen

Grab your phone or digital camera, and start taking shots of some screens in here, as they will need to be duplicated once the new unit is installed. Each of the headings above have subheadings, and then potentially multiple pages of options to scroll through. You will want to capture:

- car > carcodingvehicle (1 page)
- car > cardevicelist (3 pages)
- car > carextdevicelist (1 page)
- car > carfunctionlist (1 page)
- car > carmenuoperation (3 pages)

Now we want to capture coding in VCDS, but only if replacing the radio or temperature control unit. If not, skip ahead.

Radio:

- Open module 56 - Radio
- Select the 07 - Coding option
- Take a screenshot or copy the code directly to another file or note taking application

HVAC:

- Open module 08 - Auto HVAC
- Select the 07 - Coding option
- Take a screenshot or copy the code directly to another file or note taking application

## MMI GSM Upgrade

I created a bit of a monster for mine. My first MMI Control Unit was a F-model, but a dud. It was sold as a non-working model, and I was hoping it was just a bricked logic board, and I could [recover it with a serial cable and a laptop](http://forum.a8parts.co.uk/attachment.php?attachmentid=10277&d=1425477422), but it was truly and completely dead. It was in fantastic condition, though, so I kept it around.

My next model was a B model with a carved up fascia. I transplanted the nice fascia from the F-model to make it look great, and then I took the GSM module out of the F-model and placed it in the B-model so I could access UMTS towers. That module just requires the top cover to be unscrewed, and then one screw from the back of the module with the purple connector on the back.

The one hiccup in place is that the upgraded GSM module requires drivers for the control unit. This can be accessed at the Audi dealership under ServiceNet >> AUDI >> Technician References >> Audi MMI Scripts : MMI3GP\_UMTS\_Driver\_Script.zip. I am still working on acquiring this, but everything connects okay at 2G speeds with the old module.

## Fitting the MMI Control Unit (5F)

This is actually incredibly easy, but if installing the optional components, I'd almost install it last, as it's easier to take care of some of the other components while this unit is taken out.

- Make sure the vehicle is off, and the parking brake is on
- Shift the vehicle into neutral. This gives you more room to slide out the MMI without a fight
- Place the two Audi radio removal keys into the two corresponding slots on the unit until they lock into place
- Using the keys, slide the unit out from the dashboard
- Remove the connectors from the rear of the unit, and the button modules on the front of the unit
- Remove the button modules from the control unit. There are four tabs -- two visible, two on the top of the module, you can slide a wedge in to release them, and work them out.
- Place the button modules in the new unit
- **Now is a good time to pause until you're done with everything else.**
- **I'll wait.**
- Reconnect each of the connectors, matching color to color. All of the connectors are the same, but the purple connector will be used by the optional GSM antenna
- Slide the unit back into the dashboard
- Shift back into Park

## Fitting the MMI Control Panel

This one is futzy, but not awful. It's highly recommended that the HVAC control panel is removed to be able to get this out.

- Make sure the vehicle is off, the parking brake is engaged, and the vehicle is in neutral

![](https://lh3.googleusercontent.com/LwiP-hiamF0FjAGkICvrUNta0a3PiZZfhZGOtBA6MfzLgjN_lAAGxQgfLTAZFF5mbA-EL4AQt5TZTcAwvPGKBjFozB_oQmjq73l_9sAwZS2sK1lT_DuQ8qO9yu3xwmYZjQhDzzLZMVjOscZdUHH5DyPSf5tbk7x-KdBv4ApMKjfwj35n-CzGtG-uCgOOwCLL56QkCqxMTH3z3iALACOpmZ13Ni-t8f371KH2q6r0hBAwcKys0tKN3A7ImE6xWuMXRLvSMBK6yv-PsDY3Pz2EnwYRkE6Y4ASsOQKVxNnLG0p76XkkF48kumgkFfewqA8oeAThSesnbUeWzTsvw3vwSWCqJhNN76jG8_xEBpbJF9xrq7fWlHb8t-UL4dK-PUfCot616Gt4q4qI1aGzYdZ4IVJpJzZL7EU1rqW7uS22CfehvH9jN5NUAXzY-8Amicgvq_miVMsWF8LXEoHi3l1bvW1DlcyT1gQRrkExF-_vYmqR_r5NxNzQHZHk6uPJZnsu5l1QWP1JbJsGqLqOPuGRmH87BfGjHALVzwCZT9Fwn4k_sT7jo5qoSrgJuX94BTRnDiHRX3Y5qaEBxkXR_8fcIde0LPZveIhdw3q1oQCmM7J-Hjm0fZ7e7G_PvkL1Vj81TYENDSKx8BIDRnxEzdXf9a3AZxmDH_Cy2vnoPPCUhkk_axcawPG8dnUf=w1780-h2372-no)

- Grab a plastic wedge tool and insert it to the right of the shift boot, near the bottom, and gently pry it up. The bottom of the boot should pop up slightly, and you can work out the rest of it
- Lift the boot up and over the knob to give yourself some room. Don't try to remove the boot, we're just creating a little cone.
- Pry up the shift indicator (PRNDS) vertically with your hand, and disconnect the cable
- Pry up the remainder of the unit from the bottom of the new hole you've created, and it'll pop out of the clips holding it into the center console. Be gentle, there are connectors.
- Remove connectors from the bottom center, upper left under the parking brake switch, and under the start/stop button if equipped
- Install the new unit in reverse order. There are no new connectors or surprises, but the new unit will have a difference shift indicator that doesn't match how the B8 is set up, which is why we removed the old one.

## Optional: Installing the External GSM Antenna

As I mentioned at the start of this entry, I was unable to find a GSM antenna on my cabriolet. The A4 and Q5, and presumably the A5 coupe have a sharkfin antenna that leads to a breakout box with a FAKRA connector that transmits GSM signals. My service manual states that I may have one, but I did not find the module on mine, nor was I particularly looking forward to running 500cm of cable from the rear of my car to the front, so I took the "easy" way. If anyone would like that 500cm of cable, let me know, and I'll ship it to you for the cost of shipping.

The unit I purchased provides 3 meters of cable connecting to a small antenna. This is far more cable than I needed, but it was readily available to ship without doing anything custom. I chose to fit it underneath the top vent/speaker cover and route the cable down to the MMI unit. To do this, one has to remove that vent cover, and then get behind the MMI display for access to that area.

- Remove the 5F MMI control unit if it is not yet removed. You will be threading a cable into that area, and connecting the cable to the rear of the MMI unit.
- Remove the top vent using the plastic trim tools. The vent is secured by 10 plastic clips. By inserting a thin wedge and gently tilting it to pry them out, I was able to remove the piece without breaking clips. Make sure each clip is released before trying to pull, as the cover is incredibly flimsy, and then you'll be heading over to [wolfautoparts.com](http://wolfautoparts.com) for part 8T1 819 636 (in black).
- Remove the silver trim surrounding the MMI display. This is also secured by clips, but it's far less flimsy. Note that the silver portion is a cover over the frame assembly, so make sure you're pulling from under the frame (slide in from the top of the vents), and not the flimsy cover, or they will separate. A cable is connected to the warning flasher button -- pressing down on the tab facing away from the edge, and gently pulling the connector out in the same direction will disconnect it.
- To remove the MMI display, there are four T20 torx screws. Please, for the love of everything holy, use a screwdriver or bit that is magnetized. The area underneath the display has two cavities on either side that love swallowing bolts, and I have literally no idea where they go. I have lost two bolts and a microSD card. Don't ask. The display simply pulls away, and there are a few cables connected. You could lay a cloth down and let it dangle, there should be some wiggle room.
- It will be hard to see, but looking straight back into that newly found cavity, there's a seam in the plastic that can be revealed using a small wedge trim tool. Pushing that open will show light on the other side. Using that sliver, push the antenna itself through the left hand side of that slot will get that antenna into the left chamber of that top vent. Pull it through, and adhere the antenna to either the front or rear side.
- Toward the right of that cavity, push the connector side of that cable into the void, and continue to thread it until you can't anymore. More often than not, this will send it down the right hand side of the stack. Reach into the cavity where the MMI control unit once was, up the right hand side, and attempt to fish the FAKRA connector down into that cavity, and pull the rest of the cable through.
- Wrap the remaining cable into a bundle, leaving enough to stretch to the control unit, and zip tie the bundle.
- Connect the FAKRA end to the upper purple connector at the rear of the unit, connect any other missing cables, and reinstall the control unit.
- Reinstall the MMI screen. This is done in reverse of the above with no real gotchas. Place screen back in front of the cavity. The bottom two mounting holes also have bumps above them that fit into small holes on the screen, allowing one to align the screen properly. Screw bolts into place.
- Reinstall the trim piece. Reconnect the emergency flasher button to avoid a fault code by inserting the cable back in the module. No force should be required. The trim piece snaps into place, paying careful attention to the top of the trim, as it requires some finesse to slide into place.
- Reinstall the top vent. Align each clip carefully and gently push into place. Remember how flimsy it is.

## Optional: Installing the Radio (56)

Audi makes the infotainment rack really easy to find and test against, it's in the trunk behind an easy-to-open panel. Unfortunately, the convertible makes the process of replacing the radio far more difficult than the HOWTOs elsewhere describe. Apparently, on other models, that easy-to-open panel is all that's required to unbolt the assembly, get the radio out, and replace it. On the Cabriolet, we have to worry about a hydraulic pump, and the whole side trim piece had to come out as it didn't provide enough room for the rack to come out.

- Remove trunk floor covering
    - Lift the floor release, as if getting to the spare tire
    - Using a forked plastic trim tool, release the three expanding clips at the hinge of the floor covering, save them
    - Pull out the floor covering
- Remove front floor covering
    - Fold down the rear seats using the release levers
    - Inside the passenger compartment, release the four expanding clips between the seats and the floor covering
    - Remove the floor covering in the direction of the trunk
- Remove rear cross panel trim (plastic piece surrounding the lip and pin where the trunk closes)
    - Pull back the rubber seal and use a wide trim tool to pull the plastic piece up and over the seal
    - Using the wide tool, start pulling the whole plastic piece up vertically to release the clips holding it in
    - You'll note at the bottom of the inside portion of the plastic piece that two arms come down and align with metal pins that come out, which won't be affected if one is pulling vertically, but you'll need those to align to when reinstalling
- Remove left tie-downs
    - Fold up the tie down hooks, revealing 2 phillips-head screws
    - Unscrew those screws
    - Pull out the tie downs
- Remove release lever
    - Pull the lever, revealing a circular expanding rivet
    - Remove the rivet using a small pry tool or flathead screwdriver. It is stubborn, just keep prying at the edges, following the circle until it heads out.
    - Pull out the remaining rivet, save
    - Use the trim tool to gently pull the assembly away from the carpet. There is something of a retaining hinge on the left side, so pull from the top and right to get it to come out
    - Leave it dangling, do not remove the cable

![](https://i2.wp.com/www.nicholasmelnick.com/wp-content/uploads/2019/09/IMG_20190925_160520.jpg?fit=760%2C570)

Location of the metal bar that needs to swivel upward

- Prepare top of panel
    - Close the trunk
    - Open the roof enough that the back glass portion convertible top is fully up, and the compartment cover is fully up
    - Support the back of the convertible top with a wood stick or something else supportive
    - Reach under the enclosure trim where the top would lay, and push it up as if putting a large object in the trunk
    - Unclip the left hand side of that enclosure. There's a vague L shape from the metal piece that you pushed up, down a couple of inches, and then toward the seat back. That portion is a plastic frame pushed with 4 clips toward where you are standing. Gently push them out so that the piece dangles.
    - Those were attached to a carpet piece that continues to taper forward toward the seat backs. At the end of that taper is another expanding clip that can be removed with the forked trim tool.
    - Remove wood support
    - Close roof
    - Open trunk
- Remove panel
    - To remove the side trim, use the plastic trim tool to cleanly separate it from the rubber trim, and then pull the clips away from the body. There are three clips to separate, and they aren't adhered strongly, so make sure the trim is getting under the clips, and not just pushing at the side carpet. One clip is left and slightly down from the left of the release lever. One is to the right and down slightly further of the release lever. One is down further from that left hand clip, closer to the opening of the trunk. Once pulled open, be mindful of the cable connecting to the trunk light.

![](https://i1.wp.com/www.nicholasmelnick.com/wp-content/uploads/2019/09/IMG_20190925_160337.jpg?fit=760%2C570)

Inside of the side panel on an A5 Cabriolet

- Move hydraulic pump
    - Remove the two bolts securing the retaining bracket over the green foam pump cover
    - Remove two connectors from the top of the retaining bracket, but no need to disconnect
    - Remove two connectors from the side of the bracket, and it's far easier to disconnect them by pinching the side buttons and gently pulling apart
    - Remove the bracket
    - Swivel the hydraulic pump out. The lines on the right side of the pump should not be removed, the pump can just swivel out that direction.
- Remove radio
    - There's a rack and possibly an amplifier now in view. There are 4 nuts securing the rack in place -- left of amplifier, bracket right lower amplifier, right lower rack, bottom center rack, remove them
    - Disconnect cables from the rear of the radio
    - Swivel the rack out so that the radio can slide out toward the front of the car. This will require some screwing around, I ended up pulling it toward me, and leaning the top toward me so the radio could slide out nearly horizontally
    - There are two "buttons" of sorts on the sides of the radio, but as the radio is positioned in the car, it'll be on the top and bottom of the unit, on the edge closest to you. Those have to be pushed in, and then the radio will slide toward the front of the car.
- Install radio
    - Slide the new radio in just like the old one came out, connectors facing the rear of the car, buttons on the edge closest to you
    - Push the rack into place. Note the bottom center stud almost requires a slight lift of the rack to set into place. Once that's in place, it's much easier to guide back into place
    - Connect cables to the rear of the radio
    - Replace 4 nuts
- Reassemble
    - Do it all in reverse order. Some hints and tricks:
        - If the clip came off the back of the carpet, use a torch to melt the plastic into the carpet fibers. A quick hit with a butane torch does wonders. Don't melt it or start a fire, just re-engage what's already there
        - Don't forget to align the arms of the cross panel trim with the pins, or things will break
- VCDS fun
    - Open module 56 - Radio
    - Select the 07 - Coding option
    - Select Long Coding
    - Coding is as follows
        - 0: 02 (USA)
        - 1: 00 (Sirius, US)
        - 2: as is
        - 3: 01 if standard amp, 02 if B&O
        - 4: 00
        - 5: 00
        - 6: 00
        - 7: 00
        - 8: 01

## Optional: Installing the Temperature Control Unit (08)

This is the easiest thing to install, with the most annoying software.

- Remove the old unit
    - With the 5F out, pull back on the temperature control unit with two hands, applying equal pressure. The unit is held in place by 4 clips.
    - Disconnect the two cables at the back. There's a plastic pin at the top center of each that slides easily away from the unit, and then a tab that is pushed down while the cable is slid out.
- Install the new unit, same layout, same cables
- VCDS fun
    - Open module 08 - Auto HVAC
    - Select the 07 - Coding option
    - Enter in the old coding value from your previous HVAC unit, but append an additional '00', as there's an additional byte on these new units
    - Go back
    - Select the 10 - Adaptation button
    - In channel 79, change from 1 to 0. This changes the blower unit to this generation to allow fan control speed to work.
    - In channel 35, use '0' if you have a humidity sensor, '1' if you do not. Chances are, you do not.
    - In channel 85, change 0 to 1
