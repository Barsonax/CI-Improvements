---
theme : "moon"
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

## Old Uptrends situation

![old situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/old_situation.png)

- ~65 min to finish

--

## Old Infra situation

![old infra situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/infra_old_situation)

- ~50 min to finish

--

## How did it feel to maintain?

--

![minefield](https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield.jpg)

--

<!-- .slide: data-background="https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield2.gif" -->

--

## Why

- No branching possible
- Continue after errors
- Missing logging
- Hidden dependencies between steps
- Impossible to reproduce locally

--

## How can we solve this?

--

<!-- .slide: data-background="https://github.com/Barsonax/CI-Improvements/raw/master/images/atomicbomb.gif" -->

---

## Current Uptrends situation

![new situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/new_situation.png)

- ~36 min to finish (44.6% faster)

--

## Current Infra situation

![new situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/infra_new_situation.png)

- ~28 min to finish (44% faster)

--

## Trend towards faster

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/BuildDurationTrend.png)

--

## Why so much focus on faster builds?

- Core feedback loop
- Humans are bad multitaskers

--

## Not just faster

- Logic in NUKE build
- Branching is possible
- Fail fast
- Beter logging
- More isolation
- Build reuse

--

## Nuke build

- Build automation tool
- C# console project and thus has full IDE and debugging support.
- Target dependency model
- <https://www.nuke.build/>

```csharp
    Target MyTarget => _ => _
        .Executes(() =>
        {
            Console.WriteLine("Hello!");
        });
```

--

## Logging

- By default NUKE build shows command invocations with parameters
- Some build steps were changed to add additional logging

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/Logging.png)

--

## Split up build

- Allows running builds in parallel on multiple machines.
- Better isolation, if octopus is down unit tests can still be run for instance

--

## Build reuse

- If configured Teamcity will only run builds if snapshots changed

![reusebuilds](https://github.com/Barsonax/CI-Improvements/raw/master/images/ReuseBuilds.png)

--

## Checkout rules

- Is not a trigger rule
- Affects the files that are checked out
- Also affects snapshots

![checkoutrules](https://github.com/Barsonax/CI-Improvements/raw/master/images/CheckkoutRules.png)

--

## Other improvements

- Packagereferences
- Binding redirects
- NET sdk projects
- Faster local feedback loop

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
- Horizontal scaling
- DB on a tmpfs mount to eliminate the disk bottleneck
- Zoo test connect locally to the container

---

## Questions

---

## Links

- https://nuke.build/
- https://marketplace.visualstudio.com/items?itemName=evilz.vscode-reveal