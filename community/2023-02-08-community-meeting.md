---
title: 2023-02-08 Community Meeting
authors: [brooks]
tags: [community, meeting]
description: Agenda, notes, and recording for the 2023-02-08 community meeting
---

import ReactPlayer from 'react-player/youtube';

### Agenda
- DEMO: The revival of wasm-air 
- Tune in for BCA Wasm standards at 3pm EST! https://www.youtube.com/watch?v=B4PPDNxeRlw
- wash 0.14.1 yanked, 0.15.0 incoming
- wasmCloud roadmap final call for feedback
- Actor models, wasmCloud actors, and actors creating actors

<!--truncate-->

### Meeting Notes
- Demo: wasm-air - Jordan
  - We all remember how irritated Elon Musk was when his plane was tracked - great example of how insecure the SDR (Software Defined Radio) space is.
  - Really easy to buy a $24 dongle from Amazon that lets you stream the unencrypted data of aircraft locations to your computer. 
  - Demo shows a provider that attaches to the lattice and streams ADSP data to find and connect to a Raspberry Pi, live in Liam’s house.
  - Tower is visible by the provider which knows its location. It pulls the data out of the air and can calculate latitude and longitude of planes, for example, even their ID numbers and air speed.
  - At the same time, we can stream from multiple different locations - Liam is streaming from his Pi, Jordan streams from his VM in Colorado.
  - We can essentially use wasmCloud to replicate FlightAware (flight tracking app) and overlay deeper insight e.g. heading, trajectory etc.
  - How it works: 
  - Dump1090 - open source piece of software that's been around for a while - written in C - grabs data out of the air, and then serves it over a Telnet server. 
  - Our provider picks it up from the Telnet server and sends it to our processor.
  - Our processor creates the data and sticks it in the Key-Value store. 
  - Typical API is created - if we were to hit the API we would see the data and the front end scraping those endpoints every few seconds. 
  - Our Provider is written in Go Dump1090 is written in C so Dump1090, in this context, is running as a process.
  - It's serving its standard to a Telnet server at that point our provider picks it up; streams the Telnet data back then takes the raw message, extracts and edits the data then delivers to the processor.
  - Jordan and Kevin to look at building out as a community example/demo.
  - Check out the wider discussion in the recording.

- Demo: wasmCloud Roadmap
  - Roadmap is more a set of guidelines for what the maintainers are considering, not like a restrictive document.
  - Definitions have been added under each of the categories to say exactly what we mean for each one - please provide your additional feedback. 
  - Final week before merging with approvals. So do you have anything else to say there, that'd be a good one to drop your comments on. 
  - 0.60 has just landed - breaking change release, changing everything under the hood with how Link defs etc. are being stored. 
  - There were a bunch of bugs that people would run into, so we are now backed by the Nasty Value Store rather than just across the stream normally. 
  - Cleans up all the old data from your lattice cache and writes it into Key-Value
  - Make sure you update from 0.59 to 0.60 hosts to avoid issues when you start/delete an actor.
  - High level change is 0.60 is forward compatible, not backward compatible. So anything that you use prior to zero dot 60 will still work just fine. But if you've signed something with the new libraries that are coming out in wash 15, they will not run on a zero 59 host.
  - Updating with wash up is super easy if you’re doing local testing.

- Demo: wash 0.15.0 - what’s in store
  - Expecting wash 0.15 to release next week or so and looks like it will be a fun update.
  - Few bug fixes added to 0.14 - allowing people to test the release candidate.
  - 0.60 hosts with wash up and just a little bug fix for creating default wash context.
  - PR for 0.15 will soon be complete - to include 0.60 of the wasmCloud host as the default host version.
  - As soon as you upgrade to the newest version of wash, and you run wash up to get a new host you’ll be running on latest. You won't have to worry about coordinating breaking changes in that way. 


- Actors and Actor Models
  - Looking at a framework like Akka for actors, our wasmCloud actors really embody the term actor in the same way that AKKA uses it, except for the fact they cannot spawn their own actors.
  - We’re curious to explore how actors can spawn other actors, which is technically possible with wasmCloud - using the the lattice control interface to launch an actor.
  - The notion that actors need to start other actors is a characteristic of the generic of the actor model which predates Akka.
  - In Akka, creating an actor within an actor is mandatory.with ours. 
  - 3 common use cases:
  - The first is an actor needs to spawn some children to do some work and then retire those children when the work is completed.
  - The next most common use case is for building supervision trees, where when an actor starts another actor, the actor has logic built into it. Commonly used to deal with the failure of the child actor when behavior analysis is important - typically done with an actor supervisor.
  - Third main reason: resiliency. Running a backup actor in case one dies, you want to be able to resurrect one if it dies. 
  - All of our actors are stateless, at least in today's world. And so if you consider the list of children that an actor supervises to be state, but then it starts to get you start to see where the waters get a little muddy there, which is you know, how does a stateless actor manage a supervision tree of stateless actors without maintaining its own internal state or without forcing children to maintain their own internal state?


### Recording
<ReactPlayer url='https://youtu.be/eMmZr0JNwNA' controls />
