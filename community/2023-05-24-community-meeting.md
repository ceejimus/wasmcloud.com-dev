---
title: 2023-05-24 Community Meeting
authors: [brooks]
tags: [community, meeting]
description: Agenda, notes, and recording for the 2023-05-24 community meeting
---

import ReactPlayer from 'react-player/youtube';

### Agenda

- Update on Wadm from Taylor
- [RFC: Defining Interfaces Using Wit](https://github.com/wasmCloud/wasmCloud/issues/336) from Kevin
- What's happening in the wider Wasm community?
  - Component model update from Bailey

<!--truncate-->

### Meeting Notes

- **DEMO: Wadm Progress & Prep for Release**: Taylor
- Good progress has been made in getting Wadm closer to official release. We expect to release Wadm in the next couple of weeks, depending on bug fixes and e2e tests.
- We welcome as much feedback as we can get as we near this milestone.
- This is the first big release. It is pretty feature-complete and you should be able to build real things on top of it.
  - Demo shows significant improvements in stability - no more jitters, it launches instantaneously.
  - Not a fully-tested scenario but you can see providers running on every host.
  - Take a look at the demo section of the recording to see the improvements that have been made.
  - Architecture diagram forthcoming shortly.
  - Next up - e2e testing and release.
  - Docs, resources and deployment guides are now avail [link]
  - {Link to project board}
- **RFC: Finding a Smooth Path from Smithy to WIT**: Bailey for Kevin
  - This fresh RFC covers the early thinking here and we'd love to hear your thoughts and contributions.
  - Kevin has come up with some of the initial interfaces - wasi-cloud is the intention when stable.
  - Dan Chiarlone and Joe at Deis are working on standardizing wasi-cloud interfaces as we speak.
  - We showed a prototype at Wasmio - take a look if you haven't already seen the talk.
  - This was one of the first examples of showing a component running e2e with WIT interfaces, early was-cloud APIs and running in wasmCloud.
  - We're now able to pick a path and run it down.
- **Community Update**: Bailey
  - In the Bytecode Alliance, a ton of progress has been made on the implementation of the Component Model. In particular, we're really starting to land new capabilities in Wasmtime.
  - Wasmtime has the wasi-preview 2 adaptor brought over.
  - We also bring up a couple of high level types - handles and references - which are faster, easier to use and suited to language interoperability.
  - Call for builders will come in June to time with the Wasmtime release.
  - We will bring this over to the wasmCloud host as quickly as we can.

### Recording

<ReactPlayer url='https://youtu.be/y1CIrTZUpxA' controls />
