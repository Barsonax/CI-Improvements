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
    <img style="border: unset; box-shadow: unset" data-src="https://github.com/Barsonax/CI-Improvements/raw/master/images/BuildChains.png">
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

![old infra situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/infra_old_situation.png)

- ~50 min to finish

--

## How did it feel to maintain?

--

![minefield](https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield.jpg)

--

<!-- .slide: data-background="https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield2.gif" -->

--

## Why

- No branching
- Continue after errors
- Missing logging
- Hidden dependencies between steps
- Logic scattered throughout TeamCity (powershell, TC tools, command line)

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

## Downtrend build duration

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/BuildDurationTrend.png)

--

## Why so much focus on the build?

- Core feedback loop
- Humans are bad multitaskers
- Productive developers are happy developers

--

## 2020 DevSecOps Community Survey

<img style="border: unset; box-shadow: unset" width="70%" data-src="https://github.com/Barsonax/CI-Improvements/raw/master/images/sonatype_survey.png">

--

## Not just faster

- Logic in NUKE build (C#)
- Branching
- Fail fast
- Better logging
- More isolation
- Build reuse

--

## Nuke build

- Build automation tool
- C# console project
- full IDE and debugging support
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

- Command invocations with parameters
  - By default in NUKE build
- Some build steps were changed to add additional logging

![logging](https://github.com/Barsonax/CI-Improvements/raw/master/images/Logging.png)

--

## Split up build

- Parallel builds on multiple machines
- Better isolation
  - e.g. octopus is down unit tests are still executed
- Faster feedback

--

![multiple_agents](https://github.com/Barsonax/CI-Improvements/raw/master/images/MultipleAgents.png)

--

## Build reuse

- Runs only when sources of snapshot changed
- <https://www.jetbrains.com/help/teamcity/snapshot-dependencies.html#Suitable+Builds>
  
![reusebuilds](https://github.com/Barsonax/CI-Improvements/raw/master/images/ReuseBuilds.png)

--

## Checkout rules

- Allows for checking out part of the repository
- Affects snapshots -> Build reuse
- <https://www.jetbrains.com/help/teamcity/vcs-checkout-rules.html>

![checkoutrules](https://github.com/Barsonax/CI-Improvements/raw/master/images/CheckkoutRules.png)

--

## Other improvements

- Packagereferences
- Binding redirects
- NET sdk projects
- Faster local feedback loop
- Test projects naming convention

---

## Future Improvements

- Nuke all the builds
- Further separate builds
- Use artifact dependencies
- Run zoo tests in Docker

--

## Further separate builds

- Increase parallelism
- More effective use of checkout rules

--

## Use artifact dependencies

- Prevent redundant builds

--

## Run zoo tests with Docker

- Run SQL container with Docker
- Horizontal scaling
- DB on a `tmpfs` mount to eliminate the disk bottleneck
- Zoo tests run on local container instead of the `NUKA`

---

## Questions

---

## Links

- https://nuke.build/
- https://marketplace.visualstudio.com/items?itemName=evilz.vscode-reveal