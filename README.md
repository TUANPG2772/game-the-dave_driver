# Abyssal Haul

A first-person 3D underwater hunting and progression game built with Unity.

## Product direction

- Commercial Windows PC game targeting a Steam demo first.
- Two dives per in-game day, followed by selling and upgrading.
- Gameplay-first development with primitive assets before final art.
- Offline single-player initially, with module boundaries that preserve future expansion options.

## Core loop

Prepare equipment -> Dive -> Hunt fish and gather resources -> Manage oxygen, health, pressure and carry weight -> Extract -> Sell haul -> Upgrade equipment -> Complete missions -> Unlock deeper biomes.

## Technology

- Unity 6 LTS
- Universal Render Pipeline
- Unity Input System
- Cinemachine
- TextMeshPro
- ProBuilder
- Unity Test Framework

## Branch strategy

- `main`: stable and review-ready builds
- `develop`: integration branch
- `feature/AH-<id>-short-name`: one atomic task per branch
- Pull requests target `develop`; milestone releases merge `develop` into `main`

## Project management

Task planning, roadmap, acceptance criteria and progress tracking are maintained in Notion. GitHub Issues mirror implementation tasks using the same `AH` task identifiers.

## Legal and creative direction

The project may study genre and gameplay-loop patterns, but must use original names, characters, environments, UI, audio, missions, creature designs and visual identity.