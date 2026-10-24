---
title: The Wave Clock
date: 2026-10-24 09:42:05 +0000
categories: [3d printing, product design]
tags: [fusion360, 3dsmax, bambustudio, tolerances, clockdesign, 3dprinting, productdevelopment, aiassisted]
image: /assets/media/wave_clock/wave_clock.png
pin: true
---

<div class="skills-box">
  <strong>Skills:</strong>
  <ul>
    <li>Product design and CAD modelling in Autodesk Fusion 360</li>
    <li>Mesh editing and model preparation in 3ds Max</li>
    <li>Design for additive manufacturing</li>
    <li>Tolerance testing and iterative prototyping</li>
    <li>Bambu Studio print optimisation</li>
    <li>Multi-part assembly design using alignment dowels</li>
    <li>AI-assisted concept development</li>
  </ul>
</div>

## Bringing a Landscape to Life

The Wave Clock started as a simple idea: create a wall clock that felt more like a piece of art than a functional household object.

Inspired by layered landscapes, mountains and flowing waves, I wanted to design something that created a sense of depth and movement while remaining practical to manufacture on a consumer 3D printer.

What began as an AI-generated concept eventually evolved into a fully engineered product involving Fusion 360, 3ds Max, extensive prototyping and dozens of design refinements.

The final result is a layered wall clock that combines art, engineering and 3D printing into a unique decorative piece.

![Clock Rendering](/assets/media/wave_clock/clock.png)

*Fusion 360 render of the completed Wave Clock.*

---

## From AI Concept to Manufacturable Product

The initial landscape artwork was generated using Gemini AI to explore different mountain and wave compositions.

While the AI helped spark the original concept, transforming that artwork into a physical product required significant redesign and engineering.

The design was imported into 3ds Max where the landscape was separated into four independent layers to create the depth effect visible in the final clock.

Since the artwork exceeded the size of the printer's build volume, each layer was carefully divided into smaller printable sections while maintaining the visual flow of the scene.

![Splitting the wave design](/assets/media/wave_clock/8-3dsmax_splt.png)

*The original wave artwork being separated into printable sections in 3ds Max.*

Each layer was:

- Split into printable sections
- Aligned using custom-designed joints
- Prepared for assembly after printing
- Optimised to minimise visible seams

This approach allowed a large decorative design to be produced on a standard print bed without sacrificing detail.

---

## Engineering the Clock in Fusion 360

With the landscape layers complete, the project moved into Autodesk Fusion 360.

Rather than simply creating a frame around the artwork, every component was designed from scratch to ensure strength, ease of assembly and repeatable manufacturing.

Fusion 360 was used to:

- Design the four internal landscape rings
- Create locating features for each layer
- Develop the outer frame
- Design the clock mechanism housing
- Create the integrated keyhole wall mount
- Verify dimensions and clearances
- Refine assembly tolerances

Several prototypes were printed throughout development to validate every design decision before progressing to the next stage.

![Cross Section](/assets/media/wave_clock/section1.png)

*Cross section showing how the individual landscape layers are housed within the clock body.*

![Ticks](/assets/media/wave_clock/hour_ticks.png)

*The hour markers were designed to snap securely into the frame using integrated recesses.*

![Keyhole Hanger](/assets/media/wave_clock/keyhole_hanger.png)

*The integrated keyhole hanger was initally attached to the central clock mechanism but was moved to the top and designed directly into the rear housing for easy wall mounting.*

---

## Solving Real Design Problems

One of the most enjoyable parts of the project was solving the challenges that appeared throughout development.

### Wall Mount Testing

A clock only works as a wall clock if it stays securely on the wall.

Various mounting designs were tested before settling on the final keyhole system, ensuring the clock remained safely hung and properly supported while remaining simple to install.

![Keyhole Hanger Prints](/assets/media/wave_clock/1-keyhole_hanger_prints.JPG)

*Three iterations of the keyhole mounting system were tested before reaching the final design.*

### Eliminating Hull Lines

Early prints revealed visible hull-line banding on the outer frame.

Initially, I explored textured surfaces to disguise the issue, but after additional investigation I discovered that increasing the frame thickness by 5 mm completely resolved the problem.

The final version achieved a cleaner finish through design improvements rather than hiding imperfections.

![Frame Iterations](/assets/media/wave_clock/2-frame_iterations.JPG)

*Increasing the frame thickness eliminated visible hull lines and produced a much cleaner finish.*

### Finding the Best Assembly Method

The larger frame sections needed a reliable joining system.

Throughout development I tested:

- Bow-tie connectors
- L-shaped dowels
- Hexagonal dowels

After comparing strength, ease of assembly and manufacturing simplicity, I settled on 10 mm hexagonal dowels and removed the bow ties and L shaped dowels.

The final solution provided excellent alignment while keeping assembly straightforward and repeatable.

![Fixing Iterations](/assets/media/wave_clock/3-fixings_iterations.JPG)

*Comparing different joining methods before selecting the final hexagonal dowel design.*

![Fixing Iterations](/assets/media/wave_clock/6-rear_clock.JPG)

*An earlier revision showing the original bow tie rear joint design which were removed.

---

## Prototyping and Assembly

Like most successful products, the final version is the result of multiple iterations.

Every prototype revealed opportunities for improvement.

Tolerances were adjusted repeatedly to achieve the perfect balance between ease of assembly and secure fitment.

Support placement was refined to improve print quality. Ironing settings were improved and calibrated (flow ratio/speed testing) to create smoother error free top surfaces.

![Clock Assembled](/assets/media/wave_clock/4-clock_assembled.JPG)

*Prototype assembly before the final finishing process.*

At this stage the hour markers and clock hands had not yet received their copper finish, but the overall design and assembly concept had been validated.

![Clock Assembled](/assets/media/wave_clock/5-closeup_clock.JPG)

*Close-up showing the layered landscape effect created by the four internal scene layers. Subtle marble like particles create a natural stone texture.*

---

## Bambu Studio Optimisation

Creating the model was only half the challenge.

I also wanted the final files to be easy for others to print.

A complete Bambu Studio project was developed containing:

- Organised build plates
- Printer-specific settings
- Material profiles
- Support configurations
- Three preset quality profiles

These profiles allow makers to prioritise either print speed or print quality depending on their needs while maintaining reliable results.

The final build plates were arranged to minimise preparation time and simplify production.

---

## Features

- **Four-layer landscape design** creating depth and detail
- **Integrated keyhole wall mount**
- **Multi-part construction optimised for consumer print beds**
- **Hidden dowel assembly system**
- **Optimised Bambu Studio print profiles**
- **Designed specifically for easy assembly and repeatable printing**

---

## Materials Used

- **Sunlu HS Marble PLA**
- **Silent quartz clock mechanism**
- **Wooden clock hands**
- **Copper spray paint**
- **Superglue for final assembly**


---

## AI Assistance

AI played an important role during the creative phase of the project.

Gemini was used to generate 2d images of the clock face wave design and explore landscape concepts that ultimately inspired the final mountain and wave scene. Meshy.ai was using to turn the 2d image into a 3d model.

While AI helped accelerate idea generation, the frame design, engineering, CAD work, tolerance testing, assembly design and manufacturing optimisation were completed manually.

This project demonstrates how AI can complement the design process while still requiring engineering expertise to transform a concept into a manufacturable product.

---

## Final Thoughts

The Wave Clock is one of those projects that perfectly combines creativity and engineering.

What started as an AI-generated landscape evolved into a fully realised product involving CAD design, mesh editing, prototyping, troubleshooting, manufacturing optimisation and assembly design.

More importantly, it highlights something I enjoy most about product development: taking an idea from concept to reality through experimentation, iteration and continuous improvement.
