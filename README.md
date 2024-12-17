# Demo Reel
An extremely not-comprehensive set of stuff I've played around with outside of my day jobs.

## Makefile tricks
Not limited to any one project or repo are some of the Makefile patterns I like to use. One pattern I put together a few years ago allows one to add new source files without having to explicitly add them to a list in the Makefile so long as they wind up in a pre-determined directory. For example:
```
OBJS += $(patsubst ./%.cpp,./%.opp,$(wildcard ./*.cpp))
```
Will form a set of post-compilation object files based on the source files present within the directory where make is called. From there, rules can be based on this set, such as:
```
ouput: $(OBJS)
    @$(CXX) -o "$@" $(OBJS)
```
to link them all together. Then, to compile all of the individual source files, all that's necessary is one other rule:
```
./%.opp: ./%.cpp
	@$(CXX) -g -c -o "$@" "$<" 
```

### Makefile though? Aren't there like a billion newer build tools?
Yes! But while GNU Make is the oldest and one of the most-side-eyed, it *is* ubiquitious, lightweight, and probably not going away for a while.

## D-Stack
I built my own website managing everything from the Docker compose files to the nginx configurations to the Sanic routes. It's not the flashiest but it was more about learning the server side of things than the user-side sparkle.
### What's involved?
Um, Docker, nginx, and Sanic, among some other things.
### How do I check it out?
If it's live, head to [http://www.donnybrook.boston](http://www.donnybrook.boston). You can also read about the details [here](http://www.donnybrook.boston/about) or in the [README file with the source](https://github.com/altersun/d-stack).


## X Macro
The X macro is a neat trick which has been available in C for decades but almost no one seems to know about. It allows a developer to maintain parallel sets of data, like enumerated values and string representations of the names of those values, with little extra effort over time.
### What's involved?
Some "creative" macro usage in C and some fairly standard container usage in C++.
### How do I check it out?
It's a submodule of this repo. Do `git submodule update --init` and it will be ready to use (along with any other submodules). More info will be availible in its README.

## Ring Buffer
Ring buffer design is something I like to use as an interview quesion. I've done it so many times over the years I got to thinking of what I would "show" a candidate if they asked me what my ideal implementation would be...so I made a few of them.
### What's involved?
Pointer arithmetic, structs and a constructor "macro" in C, classes and templates in C++, and less dynamic memory allocation than one would expect.
### How do I check it out?
It's a submodule of this repo. Do `git submodule update --init` and it will be ready to use (along with any other submodules). More info will be availible in its README.

## Before Main
I came up with the C++ trick of using the static object constructors to run code before `main()` starts a while ago but eventually turned the concept into a macro.
### What's involved?
An unexpected mix of `constexpr`, custom macros, and lesser-known macros like `__COUNTER__`.
### How do I check it out?
It's a submodule of this repo. Do `git submodule update --init` and it will be ready to use (along with any other submodules). More info will be availible in its README.

## Spider
Eventually a set of C, C++, and python tools that suite my taste for embedded stuff.
### "Eventually?"
Yeah I have a lot of ideas and not a ton of time. Right now there's a C++ event loop for Linux though.
### Why "Spider"
Because - let's be honest - everyone wants to be Spiderman.
### Everyone? *Really*?
As of this writing I live in a pretty diverse neighborhood. Lots of folks from different parts of the world with different native languages, different religeons, and different cutures. I see them with their kids when I bring my own kid to the playground. It makes me really happy to watch them all play together. And so many of the kids, no matter where they or their parents started in life or what cultural habits they have, all have Spiderman paraphanelia. Backpacks, shoes, dolls, ballons, tricycles, popsicles, they all want a little piece of Spiderman in their lives.

Because everyone wants to be Spiderman.
### How do I check it out?
For now just check out the [initial pre-release](https://github.com/altersun/spider/releases/tag/v0.1.0) of the C++ event loop.
