---
title: About
nav_name: About
order: 3
team:
  - name: 'Donna Rainone'
    degrees: 'AIA'
    position: 'President'
    image: '/images/donna-headshot.png'
    bio: '
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
    '
  - name: 'Mike Rainone'
    degrees: 'NPDP, IDSA'
    position: 'Vise president'
    image: '/images/mike-headshot.png'
    bio: '
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
    '
  - name: 'Bert Sackett'
    degrees: 'B.S.E.E, M.S.E.E,'
    position: 'Partner'
    image: '/images/bert-headshot.png'
    bio: '
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
    '

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
    subtitle: ''
  - image: '/images/phase-3.png'
    title: 'Phase 3'
    subtitle: ''
  - image: '/images/phase-4.png'
    title: 'Phase 4'
    subtitle: ''
  - image: '/images/phase-5.png'
    title: 'Phase 5'
    subtitle: ''
---
<backing>
  <center>
    <h1>Meet the team</h1>
    <br>
    <People :people="team"></People>
    <br>
    <br>
    <h2>Advisory Board</h2>
    <People :people="board"></People>
  </center>
</backing>

<Phases :phases="phases">
</Phases>