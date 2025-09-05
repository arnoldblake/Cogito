# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

COGITO is a First Person Immersive Sim Template Project for Godot 4.4, providing a framework for creating immersive sim games with various interactive objects, items, and game mechanics.

## Development Commands

### Documentation
- Build documentation: `make html` (run from `docs/` directory using Sphinx)

### Godot Project
- Main scene: `res://addons/cogito/DemoScenes/COGITO_0_MainMenu.tscn`
- Run project: Use Godot Editor's play button or `godot --path .` from command line
- Export builds: Configure via Godot Editor's Project Settings > Export

## Architecture Overview

### Core Systems

**Addon Structure**: The main functionality is contained in the `addons/cogito/` directory, following Godot's plugin architecture.

**Autoloaded Singletons** (defined in project.godot):
- `CogitoGlobals` - Global settings and debug utilities 
- `CogitoSceneManager` - Handles scene transitions, save/load system, and world state
- `CogitoQuestManager` - Manages quest system and states
- `MenuTemplateManager` - UI menu management

**Component-Based Architecture**: The project uses a component-based system for interactive objects:
- `Components/` - Reusable components for interactions, attributes, UI elements
- `CogitoObjects/` - Interactive object classes that use components
- `Scripts/` - Core gameplay scripts and utilities

**Key Directories**:
- `Components/Interactions/` - Interaction system components
- `Components/Attributes/` - Player attribute system (health, stamina, etc.)
- `InventoryPD/` - Resource-based inventory system with items
- `PackedScenes/` - Pre-built scenes like Player, HUD, menus
- `DemoScenes/` - Example implementation scenes
- `EasyMenus/` - Complete menu system with save slots, options, controls
- `SceneManagement/` - Save/load system and scene persistence
- `QuestSystem/` - Quest management framework

### Save System
- Uses resource-based save system with `.res` files
- Player states and scene states are saved separately
- Supports multiple save slots (A, B, C, etc.)
- World dictionary for global game state
- Scene persistence for objects in "Persist" and "save_object_state" groups

### Player System
- First-person controller with movement, interaction, inventory
- Attribute system (health, stamina, visibility, etc.)
- Inventory with grid-based system and quickslots
- Player state includes position, attributes, inventory, quest progress

### Interaction System
- Component-based interactions (pickup, carryable, readable, etc.)
- Dual interaction system (primary/secondary actions)
- Integration with Dialogic and Dialogue Manager plugins

## Important Notes

- This is a Godot 4.4 project using the Jolt Physics engine
- The project includes localization support (English/German)
- Full gamepad support is implemented
- Uses component-based architecture extensively
- Save/load system handles complex state persistence across scenes