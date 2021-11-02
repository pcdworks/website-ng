---
title: 'Home'
description: ''
nav_name: 'Home'
order: 0

# page content
carouselImages:
  -
    src: "images/stock-slide-1.jpg"
    text: ""
  - 
    src: "images/stock-slide-2.jpg"
    text: ""
  - 
    src: "images/stock-slide-3.jpg"
    text: ""
  - 
    src: "images/stock-slide-4.jpg"
    text: ""
  - 
    src: "images/stock-slide-5.jpg"
    text: ""
  -
    src: "images/stock-slide-6.jpg"
    text: ""
---

<carousel :images="carouselImages"></carousel>

<banner
    message="Home of the HARDTECH Basecamp Incubator"
    path="/hardtechbasecamp"
    elevation="10"
    color="secondary"
    button=true
    button-text="Learn More About the basecamp"
    button-olor="accent">
</banner>
