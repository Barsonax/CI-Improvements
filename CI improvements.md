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

![minefield](https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield.jpg)

--

![minefield2](https://github.com/Barsonax/CI-Improvements/raw/master/images/minefield2.gif)

--

## Cons

- No branching
- Fail slow
- Hidden dependencies

---

## Current situation

![new situation](https://github.com/Barsonax/CI-Improvements/raw/master/images/new_situation.png)

- ~35 min to finish

--

## Trend towards faster

![trend](https://github.com/Barsonax/CI-Improvements/raw/master/images/BuildDurationTrend.png)

--

## Advantages

- Config in git, branching is possible
- Logic in NUKE build
- Fail fast
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

## Build reuse

- If configured Teamcity will only run builds if snapshots changed

![reusebuilds](https://github.com/Barsonax/CI-Improvements/raw/master/images/ReuseBuilds.png)

--

## Checkout rules

- Is not a trigger rule
- Affects the files that are checked out
- Also affects snapshots

![reusebuilds](https://github.com/Barsonax/CI-Improvements/raw/master/images/CheckkoutRules.png)

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
- DB on a tmpfs mount
- Zoo test connect locally to the container

---

## Questions
