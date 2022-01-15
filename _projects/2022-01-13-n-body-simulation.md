---
title: 'N-Body Simulation'
subtitle: 'An astronomer&apos;s perspective'
date: 2022-01-13 23:00:00
description: The story of an N-body simulation &mdash; a program that calculates the motion of gravitationally-bound objects in space &mdash; and what it can teach us about the universe.
featured_image: '/images/planetesimal-disk.png'
---

## Backstory

Imagine a whole bunch of stuff (preferably coalesced into bodies like stars or planets) out there in space. Anywhere, anytime. Just, _imagine_. What are those things doing? Are they still? Spinning? Moving towards or away from one another? If only we could look at it for ourselves... But wait, **we can!** -- and this tool (or toy?) can help.

This _N-Body Simulation_ started its life as my final project for CU Boulder's ASTR 2600: Introduction to Scientific Programming, but back then I didn't know what I was doing or how to do it, at least as far as useful programs go. So I decided to give that old IPython notebook a facelift and turn it into something others could experience and (hopefully) learn from.

But wait, what _is_ an N-Body simulation? First, it's worth discussing something called the "N-Body Problem" -- a historically difficult problem to solve by hand. Given the current understanding of orbital mechanics (how gravitationally bound objects move in space), finding an analytical (i.e., **not** step-by-step) solution for the motion of a three body gravitational system is incredibly tricky.

The beauty of programming a computer to do this work for us is that we don't need an analytical solution -- we can have the computer run the process step-by-step to show us a "really good" approximation of the motion of the bodies. That is exactly what this program is doing, and that is the essence of an N-Body simulation.

## The Program

Under the hood, the program starts by creating some lists of numbers representing the positions and starting velocities (in three dimensions) of particles in space. These initial conditions are user-selected and either hard-coded/predetermined (in the case of some of the geometric examples like the figure-8 or uniform cube) or "intelligently" generated (in the case of more realistic systems like the planetesimal disk or tiny star cluster).

From here -- after a few more user customizations -- the program begins the simulation, stepping all of the particles forward through time, moment by moment. Specifically, it uses the [Runge-Kutta method](https://en.wikipedia.org/wiki/Runge–Kutta_methods), which is a mathematical method for calculating numbers from one discrete moment of time to another.

This method was suggested and implemented by Brandon Korb[^1], in order to conserve as energy as much as possible. This is a major issue with these kinds of simulations: when massive bodies pass very close to one another, the gravitational force (which increases with mass, and as distance gets smaller) grows to effectively infinity. This means that the objects are accelerated incredibly fast and -- TO BE FINISHED SON

[^1]: a close friend, former roommate, and the one who got me into computer science. Check out [his site](http://brandonkorb.com).

Read more about the [N-Body Problem](https://en.wikipedia.org/wiki/N-body_problem) or [N-Body Simulations](https://en.wikipedia.org/wiki/N-body_simulation).

## Insights

Look at this cool thing