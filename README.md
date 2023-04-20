# Dependency Investigator

## Why this project

I've been working on a project exposed to internet and we used CheckMarx to check vulnerabilities. I've been struggling a lot with some vulnerabilities found by CheckMarx.
After searching a lot, I've found that these vulnerabilities were embedded because of transitive dependencies of packages (either downloaded on `nuget.org` or developped by other team in our company) on which we do not have access to source code. It was also because of the nuget rules that say "When you need a package, I'll download the lowest available version that meet your requirements".

## Purpose

At first, my goal is to provide a CLI that will analyze `YourProject.deps.json` which is in the build folder. This file contains all the needed dependencies (explicit or implicit). Just because this file os mostly top-downed (your project have dependencies which have dependencies and so on). But when you need to analyze outdated libraries on a solution, you need the opposite: this dependency is used by, and by, and finaly is used in this and this project...

Later, I think of providing resolution hints. For example, I used packages developped by other team in `.Net core 2.1`. When migrating to `net 6.0`, they did not upgrade dependencies. So we still had dependencies on `Microsoft.AspNetCore.Http` when they should have relied on `System.Net.Http`.

## Roadmap

I'll develop this when I have time. This will take long but here are my thoughts:

* Use of `System.Text.Json` to read the json files
