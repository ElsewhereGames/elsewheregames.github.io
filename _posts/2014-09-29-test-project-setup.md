---
published: false
---

## Testing is Secondary

Before I cover how I usually set up my test projects, I want to provide some background on where I see automated testing being useful to help explain my approach.

Ensuring a code-base can be quickly validated to perform certain functions and features based on a set of automated tests is nice, but it is not where the main pay-off comes from. A good suite of tests:

- Provides a deepder understanding of the code base
- Enforces modularity of the code base
- Allows a developer to quickly diagnose and address bugs

## There's One Way and There's the Right Way

There are generally two approaches for adding automated tests to projects which are composed of multiple sub-projects; Either have a single test project that covers the entire code base, or have smaller test projects for each sub-project. Because of the reasons I gave earlier, I prefer the second approach.

If all unit tests are part of a global project:

- Modularity is not enforced automatically; The test project will have dependencies to all sub-projects, and therefore it becomes fairly easy to mix code from different projects in the same test.
- It becomes difficult to see what code is tested where; When working on the code of a sub-project, it will not be immediately clear if and where it is covered in the unit tests without spelunking to the massive test project.

If a test project is created for each sub-project:

- Modularity is easily enforced; The test project only needs one dependency, the project to which it belongs to.
- Tests are easily found; Especially if you use a similar package naming convention in the tests as in the sub-project, finding the test which covers a section of code is straight-forward.