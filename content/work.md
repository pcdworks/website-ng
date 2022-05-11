---
title: Work
nav_name: Work
order: 2
oil:
  title: "Oil & Gas"
  image: "/images/work-3.png"
  works:
    - 
        title: "Subsea safety valve"
        problem: "Down hole safety valves are a
                mission-critical application. Current valves
                are driven by hydraulics that threaten
                pollution when the hydraulic lines are
                ruptured. A non-hydraulic valve is needed."
        solution: "We designed and built from
scratch a linear magnetic motor to drive the
valve open and a magnetic, low power hold
open to ensure fail safe operation."
        results: "Initial feasibility study was six
months. First prototype was built within three
months after go-ahead. Full-sized prototype
took less than nine months from design to
completion."
    - 
        title: "Water cut sensor"
        problem: "The flow parameters of a newly
                developed ratio of water to oil detection
                method needed to be understood to
                determine measurement efficacy."
        solution: "Using sophisticated
                Computational Fluid Dynamics modeling
                software we determined our client's
                proprietary sensor would accurately measure
                the ratio of water to oil in production pipe for
                avery wide flow regimen. We then developed
                a tool that integrated the sensor into the tool
                for the downhole environment for “water cut”
                measurement. Finally, we built a complete
                flow loop simulator in two weeks, and then
                ran tests at Tulsa University to validate the
                modeling."
        results: "Initial study completed in 30 days.
                    Project completed in 6 months."
    - 
        title: "LEAP pump"
        subtitle: "An elegant solution to crude extraction"
        problem: "How to cost-effectively retrieve
                    the final drops of crude from aging oil fields."
        solution: "We developed the LEAP System, a
                single artificial lift system that can be used
                for the life of the well. This linear
                electromagnetically actuated pump is
                effective with wells producing as little as a
                single barrel a day and is seen as a potential
                replacement for the nodding donkey pump.
                Compared to the millions of dollars needed to
                drill a new well, adding artificial lift
                technology is a cheaper alternative to
                maintain production from older wells."
        results: "We spent less than a year to design
                and deliver the 90Kw, LEAP tubular linear
                motor. Five months were spent in
                multi-physics modeling and another four
                months were spent building and testing this
                new, disruptive technology."

# - title: 'Consumer Goods'
# - title: 'Transportation'
# - title: 'Medical'
# - title: 'Military'
# - title: 'Food'
---

<text-image image="/images/work-1.png">
<template v-slot:left>
<h2>We specialize in</h2>
<h1>Not specializing</h1>
<p>
    The diversity of industries we work in is one of
    our greatest strengths. Our ability to
    cross-pollinate information, ideas, and insights
    from a wide swath of sectors leads to pioneering
    outcomes. Check out these customer success
    briefs to see how we found innovative solutions
    to some of their toughest problems.
</p>
</template>
</text-image>

<work-hor :work="oil">
</work-hor>