---
title: Rust-oids update
---

It's been a while since I last wrote about the [Rust-oids](https://github.com/itadinanta/rust-oids).

Or, for what is worth, since I actually did anything on this blog.

Anyway, if you just tuned in: Rust-oids is a simple artificial life playground, written in Rust, simulated by [rust_box2d wrapper](https://github.com/Bastacyclop/rust_box2d) physics and rendered via [gfx-rs](https://github.com/gfx-rs/gfx). The executable and package is very compact as all the "assets" (geometry, sound, graphics) are procedurally generated, mostly in real-time.

In retrospective, looking from a progress point of view, the project went from looking like this:

<img class="screenshot" src="/img/screenshot_004.png"/>

to this:

<img class="screenshot" src="/img/capture_00003350.png"/>

which is not a total disaster in my eyes.

Here are the highlights of what happened in no particular order:

- suspended the project's development for a year and then resumed it just less than a year ago, and being on-and-off since
- implemented audio output using a simple custom sound synth written from scratch and output via [Portaudio](https://github.com/RustAudio/rust-portaudio)
- implemented some interaction, adding a twin-stick-shooter style avatar which can be controlled by a DualShock 4 in [gilrs](https://gitlab.com/gilrs-project/gilrs) 
- made the subsystems update in parallel by throwing [Rayon](https://github.com/rayon-rs/rayon) in the mix
- added automatic serialization/deserialization of the world state so the simulation can be stopped and resumed
- added screen sequence capture
- added Debian `.deb` packaging
- improved shaders to give a more "organic" look while keeping the spirit of the original "Tron" style
- switched development from RustDT in Eclipse because it had been discontinued, to CLion (non-free) and the JetBrains Rust plugin
- switched back from CLion to Eclipse as soon as the Corrosion plugin was even barely usable, as I couldn't get myself used to the CLion workflow
- introduce [Clippy](https://github.com/rust-lang-nursery/rust-clippy) in my workflow, which made my Rust code bump up a couple of notches
- many other little things, which you can look at in detail by having a look at the [repository history](https://github.com/itadinanta/rust-oids/commits/develop)
- all while the Minion population was constantly evolving

In the end, I *git* a bit more *gud* at Rust - to the point I can actually use it for work-related stuff now. In fact,
I would say it's now my favourite "go-to" language. Chuffed!
