# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a personal AI/ML studies repository (`Estudos_IA` = "AI Studies" in Portuguese). Its main content today is a set of Claude Code skills (see `skills/`) rather than application source code.

## Skills

### create-solution-using-clean-architecture

Located at [skills/create-solution-using-clean-architecture/SKILL.md](skills/create-solution-using-clean-architecture/SKILL.md).

Guides Claude Code through scaffolding a new .NET Solution following Clean Architecture, with these projects under `src/`:

- `{SolutionName}.API` (`dotnet new webapi`)
- `{SolutionName}.Application` (`dotnet new classlib`)
- `{SolutionName}.Domain` (`dotnet new classlib`)
- `{SolutionName}.Infrastructure` (`dotnet new classlib`)
- `{SolutionName}.UnitTests` (`dotnet new classlib`)

Key rules enforced by the skill:

- Asks the user for the Solution name and target .NET version (minimum .NET 5) before doing anything.
- Uses NuGet Central Package Management (`Directory.Packages.props`) and a shared `Directory.Build.props`.
- Enforces the dependency direction API → Infrastructure → Application → Domain, with Domain depending on nothing and UnitTests starting with no project references.
- Does not create extra projects, subfolders, or unrequested dependencies/packages, and warns before overwriting an existing Solution/folder.
- Validates the result by building the Solution with `dotnet build`.

See [README.md](README.md) for installation instructions (global vs. project-local).

## Notes

- This repository will likely contain exploratory code, experiments, and studies — not production software
- As projects are added, update this file with build commands, project structure, and architecture details
