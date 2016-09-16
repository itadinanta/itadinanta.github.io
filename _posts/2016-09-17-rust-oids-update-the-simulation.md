---
title: Rust-oids, genes and brains
---

It's starting to get interesting. In the last few weeks [the little critters](https://github.com/itadinanta/rust-oids) have acquired some digital *genetic code* and simple ANN-based *brains*.

**TL;DR** The intriguing bit about all of this is that AI, body shape and brain are **bred** via *artificial natural selection* - for want of a better name. Practically all observed behaviour is **emergent**.

Here's how the simulation works.

## Simulation

There are 3 types of agents in the world:

### Resources and Emitters.

- Resources look like little triangles. They spawned at a fixed rate by Emitters.
- Their lifespan is very short and their only purpose is to provide nourishment for the Minions.
- Minions can detect nearby Resources with their sensor, and detect the nearest Emitters at any distance.

### Minions. 

These are the little rustoid critters.

- Each Minion shape and behaviour is determined by its, practically unique, **genotype**, which is basically just a string of bits.
- Body plan, limb geometry and mass distribution are fully simulated via the box2d **physics** engine.
- Body plan, gender, appearance, and brain aspects of the **phenotype** of each Minion are fully determined by its genetic code.
- Each Minion's **brain** is implemented via a simple 3 layer neural network. Brain has no learning capabilities, all behaviour is hardcoded at birth by genotype alone.
- Each Minion has a **sensor** to detect nearby Resources and the nearest Emitter, among other variables.
- Up to 4 **inputs** from the **sensor** determine the **outputs** of the brain which enable **actuators** if their value exceed certain **personality**-dependent **thresholds**. Left and right **rudders** which exert pull, **thrusters** push, and a linear **brake** reduces forward speed.
- Each action by a Minion, including waiting idle and reproducing, consumes a certain amount of **energy**. When energy is depleted, the Minion **dies** and some of its body is released back as Resources.
- Minions who **eat** resources can top-up their energy pool, survive longer and **reproduce** via **spores**.
- Minions who are unsuccessful at finding and eating food will not leave offspring driving their lineage **extinct**. 

### Spores.
- The little 5-lobed balls produced by the Minions by means of which they **reproduce**.
- During reproduction, the genotype is transmitted but the process introduces a variable number of **mutations**. Each mutation flips a random bit of the genotype.
- After a short time, Spores **hatch** into Minions.
- If an unfertilized Spore is touched by a Minion of a different **gender**, of which there are four, it acquires its genetic material and the resulting Minion will have a gene which is a **crossover** of the two.

I'm still trying to figure out what kind of gameplay can be built out of the emergent mechanics.

## Build/run

- ```git clone https://github.com/itadinanta/rust-oids.git && cd rust-oids```
- ```cargo run --release``` to run starting with the default gene pool
- ```cargo run --release -- <gene_pool_file.csv>``` to run starting with a snapshotted gene pool (DDDDMMYYY_hhmmss.csv).
