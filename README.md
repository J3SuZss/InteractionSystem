#  Interaction System - Unreal Engine 5

A flexible, component-based interaction system for Unreal Engine 5 built entirely in **Blueprints**. This system enables any actor to become interactable through a clean interface-driven architecture with visual feedback.

##  Demo

### NPC Interaction
![NPC Interaction](https://github.com/J3SuZss/InteractionSystem/blob/main/ajiojc.gif)

*Hover detection with outline material and interaction prompt*

### Door Interaction
![Door Interaction](https://github.com/J3SuZss/InteractionSystem/blob/main/ajiolo.gif)

*Same system works seamlessly with different object types*

---

##  Features

- ** Component-Based Design** - Attach `InteractableComponent` to any actor to make it interactable
- ** Interface-Driven** - Uses Blueprint Interface for flexible, decoupled implementation
- ** Visual Feedback** - Automatic outline material on hover for clear player communication
- ** Line Trace Detection** - Raycast system for accurate player interaction targeting
- ** Versatile Responses** - Support for multiple interaction types:
  - Door opening/closing
  - NPC dialogue triggers
  - Custom interactions per object
- ** Blueprint-Based** - Fully built in Blueprints, no C++ required
- ** Plug & Play** - Easy integration into existing projects

---

##  System Architecture

### Core Components

**1. Interactable Component (Blueprint Component)**
- Blueprint component that can be attached to any actor
- Handles hover state management (`Hover` and `UnHover` functions)
- Manages outline material application

**2. Interactable Interface (Blueprint Interface)**
- Blueprint Interface for interaction logic
- Defines `Interact` function
- Allows each object to define its own interaction behavior
- Decouples interaction logic from detection logic

**3. Line Trace System**
- Raycasts from player camera/character
- Detects objects with `InteractableComponent`
- Checks for `InteractableInterface` implementation
- Triggers hover/unhover states automatically

---

##  How It Works

### Interaction Flow

```
Player Line Trace → Detects Actor → Has InteractableComponent? 
    ↓
    YES → Apply Outline Material (Hover State)
    ↓
    Show "E TO INTERACT" UI Prompt
    ↓
    Player Presses E Key → Has InteractableInterface?
    ↓
    YES → Call Interact Event → Object Executes Custom Behavior
```

### Key Design Features

- **Separation of Concerns**: Component handles visuals and detection, Interface handles behavior
- **Reusability**: Same component works for any interactable type (NPCs, doors, items)
- **Extensibility**: Easy to add new interaction types without modifying core system
- **Visual Clarity**: Outline shader 
- **Blueprint Flexibility**: Fully customizable without code compilation

---

##  Use Cases

This system supports various gameplay interactions:

| Interaction Type | Implementation |
|-----------------|----------------|
| **NPCs** | Implement `InteractableInterface`, trigger dialogue system on `Interact` event |
| **Doors** | Implement `InteractableInterface`, toggle open/close animation on `Interact` event |

---

##  Getting Started

### Prerequisites
- Unreal Engine 5.x
- Basic knowledge of UE5 Blueprints, Components, and Interfaces

### Installation
1. Clone or download this repository
2. Copy the Blueprint files to your UE5 project's Content folder
3. Open your project in Unreal Engine 5

### Quick Setup Guide

**Step 1: Make an Actor Interactable**
1. Select the actor you want to make interactable (Door, NPC, Item, etc.)
2. In the Details panel, click **Add Component**
3. Search for and add `InteractableComponent`

**Step 2: Define Interaction Behavior**
1. Open the actor's Blueprint
2. Go to **Class Settings** → **Interfaces** → Click **Add** → Select `InteractableInterface`
3. Implement the `Interact` event in the Event Graph
4. Add your custom logic (open door, start dialogue, pick up item, etc.)

**Step 3: Test!**
- Play your level
- Aim at your interactable object
- See the outline appear and "E TO INTERACT" prompt
- Press E to trigger your custom interaction

---

##  Technical Highlights

### Blueprint Architecture

**Interactable Component Blueprint:**
- Custom events: `Hover()`, `UnHover()`
- Material instance creation and application
- Dynamic outline rendering
- Widget component management for UI prompts

**Player Controller/Character:**
- Tick event for continuous line tracing
- Hit detection and component checking
- Input handling for interaction key
- UI prompt toggle logic

**Blueprint Interface:**
- Clean contract for `Interact` event
- Allows polymorphic behavior across different actors
- No tight coupling between player and interactable objects

### Why This Design Works

✅ **Modular** - Each actor defines its own interaction without affecting others  
✅ **Scalable** - Add 100 different interactables without system changes  
✅ **Maintainable** - Changes to one interaction don't break others  
✅ **Designer-Friendly** - No code needed, pure Blueprint workflow  

---

##  What I Learned

Building this system taught me:
- Blueprint component architecture and composition
- Interface pattern implementation in UE5 Blueprints
- Line trace optimization and hit detection
- Dynamic material instance creation and manipulation
- UI widget integration with gameplay systems
- Event-driven programming in Blueprints
- Separation of concerns in game system design

---

##  Tech Stack

- **Engine:** Unreal Engine 5
- **Development:** 100% Blueprints
- **Patterns:** Component-Based Design, Interface Pattern, Event-Driven Architecture
- **Systems:** Line Tracing, Material Instances, Widget Components, Input Handling

---

##  System Showcase

The system demonstrates:
-  Clean outline shader on hover
-  Multiple object type support
-  Consistent player feedback
-  Reusable component architecture

Both GIFs show the same component and interface working with completely different actors (NPC and Door) - demonstrating true modularity and reusability.

---

##  License

This project is available for learning and portfolio purposes. Feel free to use and modify for your own UE5 projects!

---

##  About the Developer

Built by a Math Engineering student at Istanbul Technical University with 1 year of Unreal Engine 5 experience. This project demonstrates understanding of game systems architecture, Blueprint programming, and player interaction design.

**Check out my other projects:**
- [C++ Console Projects](https://github.com/J3SuZss/CPP-Console-Projects) - Algorithms and game logic fundamentals

---

*If you found this system helpful or useful for your project, consider giving it a ⭐!*
