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

## Old situation

![old situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/old_situation.png)

- ~65 min to finish

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
- Logic scattered throughout TeamCity

--

## How can we solve this?

--

<!-- .slide: data-background="https://github.com/Barsonax/CI-Improvements/raw/master/images/atomicbomb.gif" -->

---

## Current situation

![new situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/new_situation.png)

- ~40 min to finish

--

## Decreasing build duration

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/BuildDurationTrend.png)

--

## Advantages

- Logic in NUKE build (C#)
- Branching
- Fail fast
- Better logging
- Parallel execution
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

## Uptrends build example

```csharp
    Target Uptrends4Build => _ => _
        .DependsOn(
            NugetAuthenticate,
            Uptrends4CopyPatchConfigs,
            Uptrends4FrontendBuild,
            Uptrends4BackendBuild,
            UptrendsCreateNuGetPackages,
            UptrendsPushOctopusPackages,
            ErrorCodeDocumentationExport,
            ReviewUntranslatedTexts
        );
--

## Logging

- By default NUKE build shows command invocations with parameters
- Some build steps were changed to add additional logging

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/Logging.png)

--

## Split up build

- Allows running builds in parallel on multiple machines.
- Better isolation, if octopus is down unit tests can still be run for instance
- Faster feedback

--

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/MultipleAgents.png)

--

## Build reuse

- Runs only when sources of snapshot changed
  
![reusebuilds](https://github.com/Barsonax/CI-Improvements/raw/master/images/ReuseBuilds.png)

--

## Checkout rules

- Is not a trigger rule
- Allows for checking out part of the repository
- Affects snapshots -> Build reuse

![checkoutrules](https://github.com/Barsonax/CI-Improvements/raw/master/images/CheckkoutRules.png)

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
- DB on a tmpfs mount to eliminate the disk bottleneck
- Zoo test connect locally to the container

---

## Questions
