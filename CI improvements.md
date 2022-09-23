---
theme : "white"
transition: "slide"
highlightTheme: "vs2015"
slideNumber: true
#logoImg: "https://github.com/Barsonax/nukepresentation/raw/master/images/nukeIcon.png"
title: "CI improvements"
enableTitleFooter: false
---

## CI improvements

<a>
    <img style="border: unset; box-shadow: unset" data-src="https://github.com/Barsonax/nukepresentation/raw/master/images/nukeIcon.png">
</a>

---

## In this presentation

- Old situation
- Current situation
- Future Improvements
- Questions

---

## Old situation

![old situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/old_situation.png)

- ~65 min to finish

--

![minefield](https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield2-1017461915.jpg)

--

## Cons

- No branching
- No fail fast
- Hidden dependencies

---

## Current situation

![new situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/new_situation.png)

- ~35 min to finish

--

## Trend

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/BuildDurationTrend.png)

- ~35 min to finish

--

## Advantages

- Config in git, branching is possible
- Logic in C# with NUKE build
- Fail fast
- More isolation
- Build reuse

--

## Nuke build

- Build automation tool
- Target dependency model

--

## Build reuse

- Teamcity will only run builds if snapshots changed
- Checkout rules

--

## Checkout rules

- Is not a trigger rule
- Checkout only what you need
- Reuse a previous build if snapshot is not changed

---

## Future Improvements

- Further separate builds.
- Use artifact dependencies.
- Run zoo tests in docker

--

## Further separate builds

- Increase parallelism
- More effective use of checkout rules

--

## Use artifact dependencies

- Prevent having to build multiple times

--

## Run zoo tests with docker

- Run sql container with docker
- Zoo test connect locally to the container

---

## Questions
