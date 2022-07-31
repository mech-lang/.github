<p align="center">
  <img width="500px" src="http://mech-lang.org/img/logo.png">
</p>

Mech is a language for developing **data-driven**, **reactive** systems like robots, games, and interfaces. It makes **composing**, **transforming**, and **distributing** data easy, allowing you to focus on the essential complexity of your project.

You can try Mech online at [try.mech-lang.org](http://try.mech-lang.org). Read about progress on our [blog](http://mech-lang.org/blog/), and follow us on Twitter [@MechLang](https://twitter.com/MechLang).

## An Example Mech Program

```
Bouncing Balls Simulation
==========================
 
This program is a forward kinematic simulation of three balls 
bouncing in a 2D bounded arena. The balls are accelerated by 
simulated gravity and are repelled by the bounds of the arena.

#balls = [|x<m> y<m> vy<m/s> vx<m/s>|
           20   10   2.4     0
           100  50   0       3
           300  100  0      -5]
#gravity = 9.8<m/s^2>
#dt = 16<ms>
#bounds = [x<m>: 500 y<m>: 600] 

Indented code runs in an asynchronous “block”. These blocks 
are composable and reactive; they recompute automatically when 
dependent data change, or some condition is met. This block 
updates the state the balls every 16ms.

  ~ #dt
  #balls.x,y :+= #balls.vx,vy * #dt
  #balls.vy :+= #gravity * #dt
 
The following block enforces boundary constraints, ensuring that 
the balls will never leave the bounded area.

  ix = #balls.x,y > #bounds
  #balls.x,y{ix} := #bounds
  #balls.vx,vy{ix} := #balls.vx,vy * -80%
```

## Installation

Usage and installation instructions can be found in the [documentation](http://docs.mech-lang.org/#/docs/install.mec) or the [main Mech repository](https://github.com/mech-lang/mech).

## Documentation

Documentation is hosted online at [mech-lang.org](http://docs.mech-lang.org), and is open sourced on [GitHub](http://github.com/mech-lang/docs).
  
## Project Roadmap

Mech is currently in the **alpha** stage of development. This means that while some features work and are tested, programs are still likely to crash and produce incorrect results. There is a "happy path" that works well, but it's quite narrow. We've implemented many language features, but most are incomplete and some are not yet implemented at all. 

The project will hit the **beta** stage of development when all currently planned features have been implemented at least as a prototype. The current target for this milestone is October 2022.

See [ROADMAP.md](https://github.com/mech-lang/mech/blob/main/ROADMAP.md?plain=1) for more.

## License

Apache 2.0
