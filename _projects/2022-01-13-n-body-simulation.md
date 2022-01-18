---
title: "N-Body Simulation"
subtitle: "An astronomer&apos;s perspective"
date: 2022-01-13 23:00:00
description: The story of an N-body simulation &mdash; a program that calculates the motion of gravitationally-bound objects in space &mdash; and what it can teach us about the universe.
featured_image: "/images/planetesimal-disk.png"
---

[View on GitHub](https://github.com/collinsinclair/N-Body-Improved)

## Backstory

Imagine a whole bunch of stuff (preferably coalesced into bodies like stars or planets) out there in space. Anywhere, anytime. Just, _imagine_. What are those things doing? Are they still? Spinning? Moving towards or away from one another? If only we could look at it for ourselves... But wait, **we can!** -- and this tool (or toy?) can help.

This _N-Body Simulation_ started its life as my final project for CU Boulder's ASTR 2600: Introduction to Scientific Programming, but back then I didn't know what I was doing or how to do it, at least as far as useful programs go. So I decided to give that old IPython notebook a facelift and turn it into something others could experience and (hopefully) learn from.

But wait, what _is_ an N-Body simulation? First, it's worth discussing something called the "N-Body Problem" -- a historically difficult problem to solve by hand. Given the current understanding of orbital mechanics (how gravitationally bound objects move in space), finding an analytical (i.e., **not** step-by-step) solution for the motion of even a three body gravitational system is incredibly tricky -- let alone dozens of bodies.

The beauty of programming a computer to do this work for us is that we don't need an analytical solution -- we can have the computer run the process step-by-step to show us a "really good" approximation of the motion of the bodies. That is exactly what this program is doing, and that is the essence of an N-Body simulation.

## The Program

Under the hood, the program starts by creating some lists of numbers representing the positions and starting velocities (in three dimensions) of particles in space. These initial conditions are user-selected and either hard-coded/predetermined (in the case of some of the geometric examples like the figure-8 or uniform cube) or "intelligently" generated (in the case of more realistic systems like the planetesimal disk or tiny star cluster).

From here -- after a few more user customizations -- the program begins the simulation, stepping all of the particles forward through time, moment by moment. Specifically, it uses the [Runge-Kutta method](https://en.wikipedia.org/wiki/Runge–Kutta_methods), which is a mathematical method for calculating numbers from one discrete moment of time to another.

This method was suggested and implemented by Brandon Korb[^1], after my initial Euler method algorithm resulted in significant loss of energy. This is a major issue with these kinds of simulations: when massive bodies pass very close to one another, the gravitational force (which increases as the distance between objects decreases) grows to effectively infinity, which means that the objects experience incredibly large accelerations (remember: _a = f / m_), and in discrete timesteps an object will travel a large distance before the next force is calculated. Once the object moves this large distance from this huge acceleration, it is no longer near enough to the object that caused this slingshot effect to be slowed down by gravity (the force due to gravity _decreases_ as distance increases, and quickly). In this way, these close fly-bys can produce very non-physical results, breaking the conservation of energy.

So, back to the Runge-Kutta method: this way of iterating over timesteps to calculate forces, velocities, and positions is specifically designed to minimize these crazy effects, but it isn't perfect. In some of the examples below, you'll see phenomena that probably wouldn't happen out there in actual space (also gravitational slingshotting a _does_ happen, and it's how we do a lot a interplanetary space travel), just not to the extent that we see here.

## Visualization

There are a couple of interesting things to consider regarding the visual aspect of the program. I opted for a dark background with a [perceptually uniform colormap](https://colorcet.com) to invoke a space-y feeling.

The 3D simulation is presented from three angles: edge-on, face-on, and isometric, to provide maximum understanding of the relative positions and motions of the bodies. I've also included a plot of the _kinetic energy_ of the bodies (whose colors match those of the bodies) to demonstrate some of the strange interactions described above.

The sizes of the bodies are scaled to demonstrate their relative masses (especially obvious in the planetary systems and tiny cluster), though things aren't perfectly proportional because in reality stars are _so_ much more massive than planets that either

1. the star would fill up the whole screen or
2. the planets would be invisible.

And yes, this assumes that all bodies have the same density (which is not true in reality).

The sizes of the bodies are also designed to respond to situations where objects get ejected, displaying a sort of zoom-out effect as the bounds of the plots grow larger (another feature implemented by Brandon).

[^1]: a close friend, former roommate, and the one who got me into computer science. Check out [his site](http://brandonkorb.com).

## Insights

Here is the first and most basic of the simulations: it's just the Sun and the Earth! And because I haven't programmed in any sort of friction or otherwise resistive forces, nothing is changing!

Videos coming soon!

Read more about the [N-Body Problem](https://en.wikipedia.org/wiki/N-body_problem) or [N-Body Simulations](https://en.wikipedia.org/wiki/N-body_simulation).
