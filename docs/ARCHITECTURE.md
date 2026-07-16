# Abyssal Haul Architecture Baseline

## Principles

1. Gameplay modules own their rules and expose narrow interfaces.
2. ScriptableObjects contain authored definitions, never mutable save state.
3. Runtime state is plain C# where practical and serialized through explicit save DTOs.
4. Cross-module communication uses interfaces and typed events.
5. Scene objects do not search globally for dependencies.
6. Core gameplay remains independent from final art, animation and UI implementation.

## Planned modules

- Core: composition root, typed events, state machine utilities, common contracts.
- Input: Unity Input System adapter and remappable action maps.
- Player: underwater movement, camera-facing state, interaction and damage receiver.
- Survival: oxygen, health, pressure/depth restrictions, carry-weight penalties.
- Combat: weapon contracts, harpoon, knife, guns, nets, traps and damage pipeline.
- Creatures: species data, steering, fish state machines, predators and bosses.
- Inventory: weighted stacks, capacity checks, discarding, loot intake and drone transfer.
- World: biome definitions, modular generation, hazards, currents, darkness and extraction.
- Missions: objectives, unlock conditions, depth progression and rewards.
- Progression: currency, materials, blueprints and equipment upgrade branches.
- TimeCycle: morning dive, afternoon dive, evening sell/upgrade and next-day transition.
- Save: local versioned saves, migrations, autosave triggers and backup slot.
- UI: presentation layer consuming read-only view models/events.
- Localization: Vietnamese and English string tables.
- Tests: edit-mode domain tests and play-mode integration tests.

## Scene flow

Bootstrap -> Main Menu -> Boat Hub -> Dive Loading -> Dive Runtime -> Results -> Evening Hub -> Next Day.

## Authority boundaries

Even though version one is offline, commands that mutate gameplay state should pass through explicit systems rather than arbitrary scene scripts. This keeps future co-op or authoritative simulation possible without promising multiplayer support now.

## Data strategy

Stable authored IDs are mandatory for fish species, items, upgrades, missions, biomes and equipment. Save files store IDs and runtime values, not direct Unity object references.

## Performance target

Baseline target: Windows 10 64-bit, 3 GHz four-core CPU, 8 GB RAM, GTX 1060 or RX 580, and 8 GB available storage. Prototype systems should avoid per-frame allocations and use pooling for projectiles, creatures and transient effects.