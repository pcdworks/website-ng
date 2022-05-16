---
title: About
nav_name: About
order: 3
team:
  - name: 'Donna Rainone'
    degrees: 'AIA'
    position: 'President'
    image: '/images/donna-headshot.png'
    bio: "
    Donna honed her design and
    management skills working as an
    architect designing and building
    multi-million-dollar healthcare
    facilities. She has a graduate
    degree in architecture from the
    University of Texas in Austin, and
    her work has been featured in
    several publications, including AIA
    Architect magazine.
    "
  - name: 'Mike Rainone'
    degrees: 'NPDP, IDSA'
    position: 'Vice president'
    image: '/images/mike-headshot.png'
    bio: "
    With 30+ patents to his name, Mike
    has a broad knowledge of emerging
    technologies coupled with a strong
    background in psychology and
    design. He has taught architecture,
    industrial design, and business, and
    has developed products for 70+
    clients over a 30-year career. Mike
    earned an M. Arch from the
    University of Texas at Austin, and an
    MA in Psychology from the
    University of North Texas. He also
    has done doctoral work in cognitive
    psychology at MTSU.
    "
  - name: 'Bert Sackett'
    degrees: 'B.S.E.E, M.S.E.E,'
    position: 'Partner'
    image: '/images/bert-headshot.png'
    bio: "
    Bert is a seasoned engineer with
    extensive experience designing
    and developing embedded
    systems, both electronic- and
    software-based. A master of many
    technologies, his key skills in
    power supply systems, motor
    control, RF communications, and
    circuit design are a huge benefit to
    all PCDworks projects.
    "

board:
  - name: 'Dan Overly'
    degrees: ''
    position: ''
    image: '/images/donna-headshot.png'
    bio: '
    '
  - name: 'Yoda'
    degrees: ''
    position: ''
    image: '/images/donna-headshot.png'
    bio: '
    '
  - name: 'Chewbacca'
    degrees: ''
    position: ''
    image: '/images/donna-headshot.png'
    bio: '
    '


phases:
  - image: '/images/phase-1.png'
    title: 'Phase 1'
    subtitle: 'Immersive Innovation session'
    bullets:
      - "Background research"
      - - "Patent searches"
        - "What's already been tried"
        - "Technology landscape"
        - "Research enabling technologies"
        - "Competitor analysis"
      - "Immersive ideation session (3-4-day session)"
      - "Initial concepts"
      - "Concept refinement"
  - image: '/images/phase-2.png'
    title: 'Phase 2'
    subtitle: 'Engineering Design'
    bullets:
      - "Concept refinement collaboration"
      - "Initial engineering analysis"
      - "Detailed design"
      - "Initial proof of concept test of most difficult aspect"
  - image: '/images/phase-3.png'
    title: 'Phase 3'
    subtitle: 'Full Prototype Development'
    bullets:
      - "Collaborative prototype drawing development/refinement"
      - "Develop prototype"
      - "Prototype testing"
  - image: '/images/phase-4.png'
    title: 'Phase 4'
    subtitle: 'Design for Manufacturing'
    bullets:
      - "Develop full set of documentation for manufacturing"
  - image: '/images/phase-5.png'
    title: 'Phase 5'
    subtitle: 'Product Optimization / Enhancement'
    bullets:
      - "Background research on product use in market"
      - "Immersive ideation session to focus on product Improvement Initial concepts"
      - "Jointly developed proposal for next phase of targeted improvements"
      - "Next phase go ahead"

---
<text-image image="/images/about-1.png">
<template v-slot:left>

## We've got the experience to
# Make it happen
<br/>

For a quarter of a century, we've developed
innovative solutions for 50+ companies across a
range of industries. And we've racked up more
than 30 patents along the way. Our projects span
industries including renewable energy,
transportation, medical, oil and gas, food
processing, military, and consumer goods. To us,
diversity is our strength.

Made up of a core team of passionate and experienced scientists,
engineers, and technical development experts, we also call upon a global
network of industry and academic resources with deep knowledge and
expertise in their respective fields to bring together the right team for your
particular project.

Bottom line? When you're ready to get your idea out into the world, we've got
the big brains (not to mention, small egos) to make it happen.

</template>
</text-image>

<backing>
<center>

# Meet the team

<br/>
<people :people="team"></people>
<br/>
<br/>

## Advisory Board

<br/>
<people :people="board"></people>
</center>
</backing>
<text-image image="/images/about-2.png" :has_right="true">
<template v-slot:left>

## Our goal is to help you<br/>know you can succeed.
# Period
<br/>

As a knowledge-based company, we use a stage gate
approach that involves constant testing, refinement,
and communication. This cycle of gaining knowledge
through iterative research, experimentation, and
discovery results in learning, which we apply to reduce
risk; it's a proven methodology that breaks down a
complex problem, prioritizes next steps, and increases
your likelihood of success.

Here's what you can expect when you work with us.

</template>
<template v-slot:right>

## Initial discussion where we cover:
<br/>

* NDA agreement
* Understanding of Ownership of IP
* Joint Development of Problem Statement
* Joint Development of Approach
* Phase 1 Proposal

</template>
</text-image>
<phases :phases="phases">
</phases>

<image-fader image="/images/mickey.png">

## The most magical place on earth
### (sorry, Mickey)
<br/>

Schedule a visit and experience the magic
of PCDworks for yourself.

<br/>

**PCDworks**
<br/>
410 Private Road 8315
<br/>
Palestine, TX 75803

</image-fader>
