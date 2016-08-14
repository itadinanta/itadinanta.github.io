I've just given a name to my Rust A-Life experiments and released them as a project at [Rust-oids](https://github.com/rust-oids)

## Rust-oids

This project started as a test bed for https://github.com/gfx-rs/gfx and box2d wrapper https://github.com/Bastacyclop/rust_box2d. It gradually evolved to a sandbox emulator for little artificial things which were, possibly aptly, renamed "rust-oids". I'm now looking into breeding/genetic algorithms and possibly simple neural networks.

Eventually I plan to plug in some sort of gameplay and release as a free game. Strictly evening/weekend toy project: don't hold your breath.

Feedback welcome, feel free to [submit issues to the GitHub repo](https://github.com/itadinanta/rust-oids/issues)

## Screenshots

Some procedurally generated rust-oids:

![screenshot](https://github.com/itadinanta/rust-oids/raw/master/img/screenshot_003.png)

![screenshot](https://github.com/itadinanta/rust-oids/raw/master/img/screenshot_004.png)

## Prerequisite

I've only built on Ubuntu GNU/Linux but I've got reports of successful builds on Mac OS + Homebrew. Aside from the full Rust toolchain, the following packages are required:

- libbox2d-dev
- libfreetype6-dev

## How to play

- Left mouse click: create bioid.
- Left mouse drag: drop some balls.
- Right mouse click, drag: move light.
- B: set background tone
- L: change light intensity
