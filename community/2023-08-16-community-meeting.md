---
title: 2023-08-16 Community Meeting
authors: [brooks]
tags: [community, meeting]
description: Agenda, notes, and recording for the 2023-08-16 community meeting
---

import ReactPlayer from 'react-player/youtube';

### Agenda

- DEMO: wadm actor daemonscaler
- DEMO: Concordance (event sourcing) code generation and documentation enhancements _preview_
- DISCUSSION: roadmap update
- REMINDER: WasmCon is September 6-7 in Bellevue Washington and registration is still open! [https://events.linuxfoundation.org/wasmcon/](https://events.linuxfoundation.org/wasmcon/)

<!--truncate-->

### Meeting Notes

- **DEMO: wadm actor daemonscaler**
  - An exciting new development and something Brooks is working on for an upcoming talk.
  - Wadm currently has what we call a spreadscaler, which supports running a certain number of replicas across a specified set of hosts based on labels.
  - The daemonscaler - just like K8s DaemonSet - will spread this across _every_ matching host in a lattice.
  - Depending on the app you're writing - it could be useful to dynamically scale based on the infrastructure that is connected to the lattice.
  - Because of the way that wadm is written, it didn't take too much logic to add this feature.
  - There will also be a provider side - more on this soon.
  - You can look at the code [here](https://github.com/wasmCloud/wadm/pull/157) and all comments, suggestions are welcome.
- **DEMO: Concordance (event sourcing) code generation and documentation enhancements - preview**
  - Background: [Concordance](https://github.com/cosmonic/concordance) is an event sourcing framework built on wasmCloud.
  - You build your Wasm primitives as components and concordance takes care of the hard work.
  - One of the samples we built is a simple bank account example - simple aggregate which does some simple processing.
  - We also have a pile of boilerplate where we switch on the type name and variables - when we handle a command, we switch on type commands and run the right function.
  - It's the same with events - we switch on the data type and manually invoke deserialisation.
  - This is not ideal. We don't have strongly typed handlers - we must switch each time.
  - We have developed a way to surface the event flow - if you use Concordance you may have noticed there is an rdf turtle file that we used to define the event flow.
  - Again, our tolerance for friction is low - even editing a turtle file is not ideal.
  - We want to be able to write documentation on the event model.
  - Open source model of the event catalog - if we fuse site generators like Hugo or Docusaurus it will look familiar.
  - We have events for a sample application - lunar rover - see applications running on the (hypothetical) moon!
  - We're now able to see how things have changed over time, all in one place. The overwhelming ability to view and discover will make a huge difference to developers.
  - We recommend watching the recording to see the details.
- **DISCUSSION: wasmCloud roadmap update**
  - We always want to keep you updates and, of course, to keep Brooks honest! You can see the [wasmCloud Roadmap](https://wasmcloud.com/docs/roadmap).
  - Top level - leveraging WIT for all interfaces = language support is our major focus.
  - wasi-cloud instead of was Cloud interface - with a focus on backwards compatibility with the way you build wasmCloud apps today.
  - For devs looking at wasmCloud as a project and are seeing these major ecosystem changes there is a desire to know which ones are really an effort on the maintainer side and what is changing in the experience for people building applications with wasmCloud.
  - It's really important to be able to leverage WIT to define interfaces rather than in Smithy which will start to be deprecated.
  - Active milestones can be seens in the [wasmCloud repo](https://github.com/wasmCloud/wasmcloud).
  - We will be publishing out a Smithy to WIT interface migration guide.
  - Another major milestone is getting the rust host up to feature parity with the wasmCloud OTP. Having the rust host become a drop-in replacement for the OTP host.
  - For net new deployments using WebAssembly components we'll be using standard interfaces - awesome way to bring this to wasmCloud without a proprietary interface.
  - Wadm will soon be ready for `v0.5.0-rc.1`.

REMINDER: [WasmCon](https://events.linuxfoundation.org/wasmcon/) is September 6-7 in Bellevue Washington and registration is still open! The wasmCloud maintainers will be there - we hope to see you!
Join us for the [Componentize the World Hackathon](https://bytecodealliance.org/articles/announcing-componentize-the-world) - register now!

### Recording

<ReactPlayer url='https://www.youtube.com/watch?v=NX5EPcBukMs' controls />
